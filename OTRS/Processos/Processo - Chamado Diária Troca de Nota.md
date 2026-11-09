---
tipo: otrs-processo
tags: [otrs, otrs/processo, estado/active]
atualizado: 2026-10-23
fonte: snapshot do repo otrs (ZZZProcessManagement.pm / ZZZACL.pm)
entity: Process-a0a908b48965ce51bc22e44e3e93bb4e
estado: Active
---

# Processo - Chamado Diária Troca de Nota

**Chamado Diária Troca de Nota** — estado **Active** · criado 2021-01-11 15:18:29 · alterado 2026-01-28 11:07:27

Hub: [[Hub - OTRS Processos]] · [[Hub - OTRS]] · [[otrs]]

Início: **1.Abertura Chamado Diaria Troca de Nota** → diálogo [[Dialog - Formulario Diária Troca de Nota]]

## Fluxo
```mermaid
flowchart LR
  A65c15a82["2.1 Fechamento Filial Diaria Troca de Nota"]
  A0c6506c6["2.Atendimento Filial Diaria Troca de Nota"]
  Ac5c8ecf3["3.1 Fecha Chamado Societario Diario Troca de Nota"]
  Ac8e5895d["1.Abertura Chamado Diaria Troca de Nota"]
  A5a873f22["3.Atendimento Societário Diaria Troca de Nota"]
  style Ac8e5895d stroke-width:3px
  A0c6506c6 -->|"Fecha Chamado >> Filial"| A65c15a82
  A0c6506c6 -->|"Repassa Fila >> Societario"| A5a873f22
  Ac8e5895d -->|"Envia Fila>> Societario"| A5a873f22
  Ac8e5895d -->|"Envia Fila>> Fila do Contas a Receber"| A0c6506c6
  A5a873f22 -->|"Fecha Chamado >> Societario"| Ac5c8ecf3
```

## Atividades e diálogos
- **1.Abertura Chamado Diaria Troca de Nota** (início): [[Dialog - Formulario Diária Troca de Nota]]
- **2.1 Fechamento Filial Diaria Troca de Nota**: [[Dialog - Formulario Diária Troca de Nota]]
- **2.Atendimento Filial Diaria Troca de Nota**: [[Dialog - Formulario Diária Troca de Nota]] · [[Dialog - Controle Atendimento Processo (b2e090)]] · [[Dialog - Adcionar Valor Previsível da Estadia]]
- **3.1 Fecha Chamado Societario Diario Troca de Nota**: [[Dialog - Formulario Diária Troca de Nota]]
- **3.Atendimento Societário Diaria Troca de Nota**: [[Dialog - Formulario Diária Troca de Nota]] · [[Dialog - Controle Atendimento Processo (b2e090)]]

## Transições
- **Fecha Chamado >> Filial**: 2.Atendimento Filial Diaria Troca de Nota → 2.1 Fechamento Filial Diaria Troca de Nota
  - Condição: (and: [[DF - CteControleAtividades]] String `Finalizar Atendimento Filial`; [[DF - CteDB]] Regexp `.`; [[DF - CtePlaca]] Regexp `.`)
  - Ação *Muda Estado Chamado >> Fechado* — TicketStateSet: StateID=`2`
- **Repassa Fila >> Societario**: 2.Atendimento Filial Diaria Troca de Nota → 3.Atendimento Societário Diaria Troca de Nota
  - Condição: (and: [[DF - CteControleAtividades]] String `Repasse Societario`; [[DF - CteDB]] Regexp `.`; [[DF - CtePlaca]] Regexp `.`)
  - Ação *Envia Fila>> Societario* — TicketQueueSet: Fila [[Fila - CRC]]
- **Envia Fila>> Societario**: 1.Abertura Chamado Diaria Troca de Nota → 3.Atendimento Societário Diaria Troca de Nota
  - Condição: (and: [[DF - CteClienteTipoNestle]] String `NAONESTLE`; [[DF - CteDB]] Regexp `.`; [[DF - CtePlaca]] Regexp `.`)
  - Ação *Envia Fila>> Societario* — TicketQueueSet: Fila [[Fila - CRC]]
  - Ação *Atribui>>Titulo Processo* — TicketTitleSet: Title=`Placa: <OTRS_TICKET_DynamicField_CtePlaca> | CT-e :<OTRS_TICKET_DynamicField_CteNumero> | Cliente : <OTRS_TICKET_DynamicField_CteNomePagador>`
- **Envia Fila>> Fila do Contas a Receber**: 1.Abertura Chamado Diaria Troca de Nota → 2.Atendimento Filial Diaria Troca de Nota
  - Condição: (and: [[DF - CteClienteTipoNestle]] String `NESTLE`; [[DF - CteDB]] Regexp `.`; [[DF - CtePlaca]] Regexp `.`)
  - Ação *Envia Fila>> Filial do Cte* — TicketQueueSet: Fila [[Fila - Contas a Receber]]
  - Ação *Atribui>>Serviço Processo: Chamado Diária Troca de Nota* — TicketServiceSet: Serviço [[Servico - Processo- Chamado Diária Troca de Nota]]
  - Ação *Atribui>>Titulo Processo* — TicketTitleSet: Title=`Placa: <OTRS_TICKET_DynamicField_CtePlaca> | CT-e :<OTRS_TICKET_DynamicField_CteNumero> | Cliente : <OTRS_TICKET_DynamicField_CteNomePagador>`
- **Fecha Chamado >> Societario**: 3.Atendimento Societário Diaria Troca de Nota → 3.1 Fecha Chamado Societario Diario Troca de Nota
  - Condição: (and: [[DF - CteControleAtividades]] String `Finalizar Atendimento Societario`; [[DF - CteDB]] Regexp `.`; [[DF - CtePlaca]] Regexp `.`)
  - Ação *Muda Estado Chamado >> Fechado* — TicketStateSet: StateID=`2`

## ACLs que se aplicam (diretas ou por diálogo)
- [[ACL - 1 - Esconde Campos Chamado - Ativo]]
- [[ACL - 1- Esconde Anexo Posicao Rastreador HelpDeskTransportador]]
- [[ACL - 1- Esconde CET BRF HelpDeskTransportador]]
- [[ACL - 2 - Mostra Troca de Nota - Nota Fiscal]]
- [[ACL - 2- Mostra Anexo Posicao Rastreador Processo - DIÁRIA AO DESCARREGAR]]
- [[ACL - 2- Mostra Campos Chamado]]
- [[ACL - 2- Mostra Ocorrencia Todos Processos  NESTLE]]
- [[ACL - 2- Mostra Senha Marfrig Processos - DIÁRIA]]
- [[ACL - 3 - Esconde DACTE Carimbado Assinado e Posicao Rastreador BRF Diarias]]
- [[ACL - 3- Esconde Ocorrencia Todos Processos  Não NESTLE]]

> Fonte: snapshot do repo (espelho da prod); fila/serviço aparecem como nomes nas ações.
