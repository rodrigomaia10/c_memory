---
tipo: otrs-processo
tags: [otrs, otrs/processo, estado/active]
atualizado: 2026-10-23
fonte: snapshot do repo otrs (ZZZProcessManagement.pm / ZZZACL.pm)
entity: Process-02f4ecb1397d6dc35826527c83b9f199
estado: Active
---

# Processo - Chamado Frete Bloqueado

**Chamado Frete Bloqueado** — estado **Active** · criado 2021-01-11 15:15:17 · alterado 2026-08-17 09:15:04

Hub: [[Hub - OTRS Processos]] · [[Hub - OTRS]] · [[otrs]]

Início: **1.Abertura Chamado Frete Bloqueado** → diálogo [[Dialog - Formulario  Frete Bloqueado]]

## Fluxo
```mermaid
flowchart LR
  A1cbdadd5["2.Atendimento Filial Frete Bloqueado"]
  Ab2d33d06["3.Atendimento Societário Frete Bloqueado"]
  A27d5495f["1.Abertura Chamado Frete Bloqueado"]
  Adf1e167a["3.1 Fecha Chamado Societario Frete Bloqueado"]
  A3bb0079b["2.1 Fechamento Filial Frete Bloqueado"]
  style A27d5495f stroke-width:3px
  A1cbdadd5 -->|"Fecha Chamado >> Filial"| A3bb0079b
  A1cbdadd5 -->|"Repassa Fila >> Societario"| Ab2d33d06
  Ab2d33d06 -->|"Fecha Chamado >> Societario"| Adf1e167a
  A27d5495f -->|"Envia Fila>> Societario"| Ab2d33d06
  A27d5495f -->|"Envia Fila>> Fila do Contas a Receber"| A1cbdadd5
```

## Atividades e diálogos
- **1.Abertura Chamado Frete Bloqueado** (início): [[Dialog - Formulario  Frete Bloqueado]]
- **2.1 Fechamento Filial Frete Bloqueado**: [[Dialog - Formulario  Frete Bloqueado]]
- **2.Atendimento Filial Frete Bloqueado**: [[Dialog - Formulario  Frete Bloqueado]] · [[Dialog - Controle Atendimento Processo (b2e090)]]
- **3.1 Fecha Chamado Societario Frete Bloqueado**: [[Dialog - Formulario  Frete Bloqueado]]
- **3.Atendimento Societário Frete Bloqueado**: [[Dialog - Formulario  Frete Bloqueado]] · [[Dialog - Controle Atendimento Processo (b2e090)]]

## Transições
- **Fecha Chamado >> Filial**: 2.Atendimento Filial Frete Bloqueado → 2.1 Fechamento Filial Frete Bloqueado
  - Condição: (and: [[DF - CteControleAtividades]] String `Finalizar Atendimento Filial`; [[DF - CteDB]] Regexp `.`; [[DF - CtePlaca]] Regexp `.`)
  - Ação *Muda Estado Chamado >> Fechado* — TicketStateSet: StateID=`2`
- **Repassa Fila >> Societario**: 2.Atendimento Filial Frete Bloqueado → 3.Atendimento Societário Frete Bloqueado
  - Condição: (and: [[DF - CteControleAtividades]] String `Repasse Societario`; [[DF - CteDB]] Regexp `.`; [[DF - CtePlaca]] Regexp `.`)
  - Ação *Envia Fila>> Societario* — TicketQueueSet: Fila [[Fila - CRC]]
- **Fecha Chamado >> Societario**: 3.Atendimento Societário Frete Bloqueado → 3.1 Fecha Chamado Societario Frete Bloqueado
  - Condição: (and: [[DF - CteControleAtividades]] String `Finalizar Atendimento Societario`; [[DF - CteDB]] Regexp `.`; [[DF - CtePlaca]] Regexp `.`)
  - Ação *Muda Estado Chamado >> Fechado* — TicketStateSet: StateID=`2`
- **Envia Fila>> Societario**: 1.Abertura Chamado Frete Bloqueado → 3.Atendimento Societário Frete Bloqueado
  - Condição: (and: [[DF - CteClienteTipoNestle]] String `NAONESTLE`; [[DF - CteDB]] Regexp `.`; [[DF - CtePlaca]] Regexp `.`)
  - Ação *Envia Fila>> Societario* — TicketQueueSet: Fila [[Fila - CRC]]
  - Ação *Atribui>>Titulo Processo* — TicketTitleSet: Title=`Placa: <OTRS_TICKET_DynamicField_CtePlaca> | CT-e :<OTRS_TICKET_DynamicField_CteNumero> | Cliente : <OTRS_TICKET_DynamicField_CteNomePagador>`
- **Envia Fila>> Fila do Contas a Receber**: 1.Abertura Chamado Frete Bloqueado → 2.Atendimento Filial Frete Bloqueado
  - Condição: (and: [[DF - CteClienteTipoNestle]] String `NESTLE`; [[DF - CteDB]] Regexp `.`; [[DF - CtePlaca]] Regexp `.`)
  - Ação *Envia Fila>> Filial do Cte* — TicketQueueSet: Fila [[Fila - Contas a Receber]]
  - Ação *Atribui>>Serviço Processo: Chamado Frete Bloqueado* — TicketServiceSet: Serviço [[Servico - Processo- Chamado Frete Bloqueado]]

## ACLs que se aplicam (diretas ou por diálogo)
- [[ACL - 1 - Esconde Campos Chamado - Ativo]]
- [[ACL - 2- Mostra Campos Chamado]]

> Fonte: snapshot do repo (espelho da prod); fila/serviço aparecem como nomes nas ações.
