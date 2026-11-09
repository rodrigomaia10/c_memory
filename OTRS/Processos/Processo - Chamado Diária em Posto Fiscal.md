---
tipo: otrs-processo
tags: [otrs, otrs/processo, estado/active]
atualizado: 2026-10-23
fonte: snapshot do repo otrs (ZZZProcessManagement.pm / ZZZACL.pm)
entity: Process-97018c99b310c7426343f6eb090bf6cf
estado: Active
---

# Processo - Chamado Diária em Posto Fiscal

**Chamado Diária em Posto Fiscal** — estado **Active** · criado 2021-01-11 15:18:02 · alterado 2026-01-28 11:06:42

Hub: [[Hub - OTRS Processos]] · [[Hub - OTRS]] · [[otrs]]

Início: **1.Abertura Chamado Diária em Posto Fiscal** → diálogo [[Dialog - Formulario Diária em Posto Fiscal]]

## Fluxo
```mermaid
flowchart LR
  A167258ef["3.Atendimento Societário Diaria em Posto Fiscal"]
  A24c5524b["1.Abertura Chamado Diária em Posto Fiscal"]
  A0852dd1a["3.1 Fecha Chamado Societario Diario em Posto Fiscal"]
  A1c92e237["2.Atendimento Filial Diaria em Posto Fiscal"]
  A2cdfdb9c["2.1 Fechamento Filial Diaria em Posto Fiscal"]
  style A24c5524b stroke-width:3px
  A167258ef -->|"Fecha Chamado >> Societario"| A0852dd1a
  A24c5524b -->|"Envia Fila>> Societario"| A167258ef
  A24c5524b -->|"Envia Fila>> Fila do Contas a Receber"| A1c92e237
  A1c92e237 -->|"Fecha Chamado >> Filial"| A2cdfdb9c
  A1c92e237 -->|"Repassa Fila >> Societario"| A167258ef
```

## Atividades e diálogos
- **1.Abertura Chamado Diária em Posto Fiscal** (início): [[Dialog - Formulario Diária em Posto Fiscal]]
- **2.1 Fechamento Filial Diaria em Posto Fiscal**: [[Dialog - Formulario Diária em Posto Fiscal]]
- **2.Atendimento Filial Diaria em Posto Fiscal**: [[Dialog - Formulario Diária em Posto Fiscal]] · [[Dialog - Controle Atendimento Processo (b2e090)]] · [[Dialog - Adcionar Valor Previsível da Estadia]]
- **3.1 Fecha Chamado Societario Diario em Posto Fiscal**: [[Dialog - Formulario Diária em Posto Fiscal]]
- **3.Atendimento Societário Diaria em Posto Fiscal**: [[Dialog - Formulario Diária em Posto Fiscal]] · [[Dialog - Controle Atendimento Processo (b2e090)]]

## Transições
- **Fecha Chamado >> Societario**: 3.Atendimento Societário Diaria em Posto Fiscal → 3.1 Fecha Chamado Societario Diario em Posto Fiscal
  - Condição: (and: [[DF - CteControleAtividades]] String `Finalizar Atendimento Societario`; [[DF - CteDB]] Regexp `.`; [[DF - CtePlaca]] Regexp `.`)
  - Ação *Muda Estado Chamado >> Fechado* — TicketStateSet: StateID=`2`
- **Envia Fila>> Societario**: 1.Abertura Chamado Diária em Posto Fiscal → 3.Atendimento Societário Diaria em Posto Fiscal
  - Condição: (and: [[DF - CteClienteTipoNestle]] String `NAONESTLE`; [[DF - CteDB]] Regexp `.`; [[DF - CtePlaca]] Regexp `.`)
  - Ação *Envia Fila>> Societario* — TicketQueueSet: Fila [[Fila - CRC]]
  - Ação *Atribui>>Titulo Processo* — TicketTitleSet: Title=`Placa: <OTRS_TICKET_DynamicField_CtePlaca> | CT-e :<OTRS_TICKET_DynamicField_CteNumero> | Cliente : <OTRS_TICKET_DynamicField_CteNomePagador>`
- **Envia Fila>> Fila do Contas a Receber**: 1.Abertura Chamado Diária em Posto Fiscal → 2.Atendimento Filial Diaria em Posto Fiscal
  - Condição: (and: [[DF - CteClienteTipoNestle]] String `NESTLE`; [[DF - CteDB]] Regexp `.`; [[DF - CtePlaca]] Regexp `.`)
  - Ação *Envia Fila>> Filial do Cte* — TicketQueueSet: Fila [[Fila - Contas a Receber]]
  - Ação *Atribui>>Serviço Processo: Chamado Diária em Posto Fiscal* — TicketServiceSet: Serviço [[Servico - Processo- Chamado Diária em Posto Fiscal]]
  - Ação *Atribui>>Titulo Processo* — TicketTitleSet: Title=`Placa: <OTRS_TICKET_DynamicField_CtePlaca> | CT-e :<OTRS_TICKET_DynamicField_CteNumero> | Cliente : <OTRS_TICKET_DynamicField_CteNomePagador>`
- **Fecha Chamado >> Filial**: 2.Atendimento Filial Diaria em Posto Fiscal → 2.1 Fechamento Filial Diaria em Posto Fiscal
  - Condição: (and: [[DF - CteControleAtividades]] String `Finalizar Atendimento Filial`; [[DF - CteDB]] Regexp `.`; [[DF - CtePlaca]] Regexp `.`)
  - Ação *Muda Estado Chamado >> Fechado* — TicketStateSet: StateID=`2`
- **Repassa Fila >> Societario**: 2.Atendimento Filial Diaria em Posto Fiscal → 3.Atendimento Societário Diaria em Posto Fiscal
  - Condição: (and: [[DF - CteControleAtividades]] String `Repasse Societario`; [[DF - CteDB]] Regexp `.`; [[DF - CtePlaca]] Regexp `.`)
  - Ação *Envia Fila>> Societario* — TicketQueueSet: Fila [[Fila - CRC]]

## ACLs que se aplicam (diretas ou por diálogo)
- [[ACL - 1 - Esconde Campos Chamado - Ativo]]
- [[ACL - 1- Esconde Anexo Posicao Rastreador HelpDeskTransportador]]
- [[ACL - 1- Esconde CET BRF HelpDeskTransportador]]
- [[ACL - 2 - Mostrar Diária no Posto Fiscal - Pedir CTE PDF e Rastreamento]]
- [[ACL - 2- Mostra Anexo Posicao Rastreador Processo - DIÁRIA AO DESCARREGAR]]
- [[ACL - 2- Mostra Campos Chamado]]
- [[ACL - 2- Mostra Ocorrencia Todos Processos  NESTLE]]
- [[ACL - 3 - Esconde DACTE Carimbado Assinado e Posicao Rastreador BRF Diarias]]
- [[ACL - 3- Esconde Ocorrencia Todos Processos  Não NESTLE]]

> Fonte: snapshot do repo (espelho da prod); fila/serviço aparecem como nomes nas ações.
