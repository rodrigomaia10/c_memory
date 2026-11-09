---
tipo: otrs-processo
tags: [otrs, otrs/processo, estado/active]
atualizado: 2026-10-23
fonte: snapshot do repo otrs (ZZZProcessManagement.pm / ZZZACL.pm)
entity: Process-4b491ffe20345a28e32555c19f993a7d
estado: Active
---

# Processo - Chamado Divergência Valor de Frete

**Chamado Divergência Valor de Frete** — estado **Active** · criado 2021-01-11 15:15:43 · alterado 2023-11-13 09:34:02

Hub: [[Hub - OTRS Processos]] · [[Hub - OTRS]] · [[otrs]]

Início: **1.Abertura Chamado Divergencia Valor do Frete** → diálogo [[Dialog - Formulario Divergencia Valor de Frete]]

## Fluxo
```mermaid
flowchart LR
  Ae15e83cf["2.1 Fechamento Filial Divergencia Valor do Frete"]
  Aa9eb3bc6["3.1 Fecha Chamado Societario Divergencia Valor do Frete"]
  A29dd5a45["2.Atendimento Filial Divergencia Valor do Frete"]
  Af9b0362f["3.Atendimento Societário Divergencia Valor de Frete"]
  A09a088ef["1.Abertura Chamado Divergencia Valor do Frete"]
  style A09a088ef stroke-width:3px
  A29dd5a45 -->|"Fecha Chamado >> Filial"| Ae15e83cf
  A29dd5a45 -->|"Repassa Fila >> Societario"| Af9b0362f
  Af9b0362f -->|"Fecha Chamado >> Societario"| Aa9eb3bc6
  A09a088ef -->|"Envia Fila>> Societario"| Af9b0362f
  A09a088ef -->|"Envia Fila>> Fila do Contas a Receber"| A29dd5a45
```

## Atividades e diálogos
- **1.Abertura Chamado Divergencia Valor do Frete** (início): [[Dialog - Formulario Divergencia Valor de Frete]]
- **2.1 Fechamento Filial Divergencia Valor do Frete**: [[Dialog - Formulario Divergencia Valor de Frete]]
- **2.Atendimento Filial Divergencia Valor do Frete**: [[Dialog - Formulario Divergencia Valor de Frete]] · [[Dialog - Controle Atendimento Processo (b2e090)]]
- **3.1 Fecha Chamado Societario Divergencia Valor do Frete**: [[Dialog - Formulário Anulação]]
- **3.Atendimento Societário Divergencia Valor de Frete**: [[Dialog - Formulario Divergencia Valor de Frete]] · [[Dialog - Controle Atendimento Processo (b2e090)]]

## Transições
- **Fecha Chamado >> Filial**: 2.Atendimento Filial Divergencia Valor do Frete → 2.1 Fechamento Filial Divergencia Valor do Frete
  - Condição: (and: [[DF - CteControleAtividades]] String `Finalizar Atendimento Filial`; [[DF - CteDB]] Regexp `.`; [[DF - CtePlaca]] Regexp `.`)
  - Ação *Muda Estado Chamado >> Fechado* — TicketStateSet: StateID=`2`
- **Repassa Fila >> Societario**: 2.Atendimento Filial Divergencia Valor do Frete → 3.Atendimento Societário Divergencia Valor de Frete
  - Condição: (and: [[DF - CteControleAtividades]] String `Repasse Societario`; [[DF - CteDB]] Regexp `.`; [[DF - CtePlaca]] Regexp `.`)
  - Ação *Envia Fila>> Societario* — TicketQueueSet: Fila [[Fila - CRC]]
- **Fecha Chamado >> Societario**: 3.Atendimento Societário Divergencia Valor de Frete → 3.1 Fecha Chamado Societario Divergencia Valor do Frete
  - Condição: (and: [[DF - CteControleAtividades]] String `Finalizar Atendimento Societario`; [[DF - CteDB]] Regexp `.`; [[DF - CtePlaca]] Regexp `.`)
  - Ação *Muda Estado Chamado >> Fechado* — TicketStateSet: StateID=`2`
- **Envia Fila>> Societario**: 1.Abertura Chamado Divergencia Valor do Frete → 3.Atendimento Societário Divergencia Valor de Frete
  - Condição: (and: [[DF - CteClienteTipoNestle]] String `NAONESTLE`; [[DF - CteDB]] Regexp `.`; [[DF - CtePlaca]] Regexp `.`)
  - Ação *Envia Fila>> Societário Desligamento de Motorista* — TicketQueueSet: Fila [[Fila - CRC]]
  - Ação *Atribui>>Titulo Processo* — TicketTitleSet: Title=`Placa: <OTRS_TICKET_DynamicField_CtePlaca> | CT-e :<OTRS_TICKET_DynamicField_CteNumero> | Cliente : <OTRS_TICKET_DynamicField_CteNomePagador>`
- **Envia Fila>> Fila do Contas a Receber**: 1.Abertura Chamado Divergencia Valor do Frete → 2.Atendimento Filial Divergencia Valor do Frete
  - Condição: (and: [[DF - CteClienteTipoNestle]] String `NESTLE`; [[DF - CteDB]] Regexp `.`; [[DF - CtePlaca]] Regexp `.`)
  - Ação *Envia Fila>> Filial do Cte* — TicketQueueSet: Fila [[Fila - Contas a Receber]]
  - Ação *Atribui>>Serviço Processo: Chamado Divergência Valor de Frete* — TicketServiceSet: Serviço [[Servico - Processo- Chamado Divergência Valor de Frete]]

## ACLs que se aplicam (diretas ou por diálogo)
- [[ACL - 1 - Esconde Campos Chamado - Ativo]]
- [[ACL - 2- Mostra Campos Chamado]]

> Fonte: snapshot do repo (espelho da prod); fila/serviço aparecem como nomes nas ações.
