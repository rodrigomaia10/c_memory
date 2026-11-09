---
tipo: otrs-processo
tags: [otrs, otrs/processo, estado/active]
atualizado: 2026-10-23
fonte: snapshot do repo otrs (ZZZProcessManagement.pm / ZZZACL.pm)
entity: Process-e8b53c963d58c49c4e762d95a99fb686
estado: Active
---

# Processo - Chamado Pedágio

**Chamado Pedágio** — estado **Active** · criado 2021-01-11 15:18:56 · alterado 2023-11-13 09:34:39

Hub: [[Hub - OTRS Processos]] · [[Hub - OTRS]] · [[otrs]]

Início: **1.Abertura Chamado Pedágio** → diálogo [[Dialog - Formulario Pedagio]]

## Fluxo
```mermaid
flowchart LR
  A406f5f0a["1.Abertura Chamado Pedágio"]
  Add4819f9["3.1 Fecha Chamado Societario Pedágio"]
  Ae8eaa00d["2.1 Fechamento Filial Pedágio"]
  A27d5d1ae["2.Atendimento Filial Pedágio"]
  A02ab98fe["3.Atendimento Societário Pedágio"]
  style A406f5f0a stroke-width:3px
  A406f5f0a -->|"Envia Fila>> Societario"| A02ab98fe
  A406f5f0a -->|"Envia Fila>> Fila do Contas a Receber"| A27d5d1ae
  A27d5d1ae -->|"Fecha Chamado >> Filial"| Ae8eaa00d
  A27d5d1ae -->|"Repassa Fila >> Societario"| A02ab98fe
  A02ab98fe -->|"Fecha Chamado >> Societario"| Add4819f9
```

## Atividades e diálogos
- **1.Abertura Chamado Pedágio** (início): [[Dialog - Formulario Pedagio]]
- **2.1 Fechamento Filial Pedágio**: [[Dialog - Formulario Pedagio]]
- **2.Atendimento Filial Pedágio**: [[Dialog - Formulario Pedagio]] · [[Dialog - Controle Atendimento Processo (b2e090)]]
- **3.1 Fecha Chamado Societario Pedágio**: [[Dialog - Formulario Pedagio]]
- **3.Atendimento Societário Pedágio**: [[Dialog - Formulario Pedagio]] · [[Dialog - Controle Atendimento Processo (b2e090)]]

## Transições
- **Envia Fila>> Societario**: 1.Abertura Chamado Pedágio → 3.Atendimento Societário Pedágio
  - Condição: (and: [[DF - CteClienteTipoNestle]] String `NAONESTLE`; [[DF - CteDB]] Regexp `.`; [[DF - CtePlaca]] Regexp `.`)
  - Ação *Envia Fila>> Societário Desligamento de Motorista* — TicketQueueSet: Fila [[Fila - CRC]]
  - Ação *Atribui>>Serviço Processo: Chamado Pedágio* — TicketServiceSet: Serviço [[Servico - Processo- Chamado Pedágio]]
  - Ação *Atribui>>Titulo Processo* — TicketTitleSet: Title=`Placa: <OTRS_TICKET_DynamicField_CtePlaca> | CT-e :<OTRS_TICKET_DynamicField_CteNumero> | Cliente : <OTRS_TICKET_DynamicField_CteNomePagador>`
- **Envia Fila>> Fila do Contas a Receber**: 1.Abertura Chamado Pedágio → 2.Atendimento Filial Pedágio
  - Condição: (and: [[DF - CteClienteTipoNestle]] String `NESTLE`; [[DF - CteDB]] Regexp `.`; [[DF - CtePlaca]] Regexp `.`)
  - Ação *Envia Fila>> Filial do Cte* — TicketQueueSet: Fila [[Fila - Contas a Receber]]
  - Ação *Atribui>>Serviço Processo: Chamado Pedágio* — TicketServiceSet: Serviço [[Servico - Processo- Chamado Pedágio]]
- **Fecha Chamado >> Filial**: 2.Atendimento Filial Pedágio → 2.1 Fechamento Filial Pedágio
  - Condição: (and: [[DF - CteControleAtividades]] String `Finalizar Atendimento Filial`; [[DF - CteDB]] Regexp `.`; [[DF - CtePlaca]] Regexp `.`)
  - Ação *Muda Estado Chamado >> Fechado* — TicketStateSet: StateID=`2`
- **Repassa Fila >> Societario**: 2.Atendimento Filial Pedágio → 3.Atendimento Societário Pedágio
  - Condição: (and: [[DF - CteControleAtividades]] String `Repasse Societario`; [[DF - CteDB]] Regexp `.`; [[DF - CtePlaca]] Regexp `.`)
  - Ação *Envia Fila>> Societario* — TicketQueueSet: Fila [[Fila - CRC]]
- **Fecha Chamado >> Societario**: 3.Atendimento Societário Pedágio → 3.1 Fecha Chamado Societario Pedágio
  - Condição: (and: [[DF - CteControleAtividades]] String `Finalizar Atendimento Societario`; [[DF - CteDB]] Regexp `.`; [[DF - CtePlaca]] Regexp `.`)
  - Ação *Muda Estado Chamado >> Fechado* — TicketStateSet: StateID=`2`

## ACLs que se aplicam (diretas ou por diálogo)
- [[ACL - 1 - Esconde Campos Chamado - Ativo]]
- [[ACL - 2- Mostra Campos Chamado]]

> Fonte: snapshot do repo (espelho da prod); fila/serviço aparecem como nomes nas ações.
