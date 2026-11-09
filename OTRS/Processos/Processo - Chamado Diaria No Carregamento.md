---
tipo: otrs-processo
tags: [otrs, otrs/processo, estado/active]
atualizado: 2026-10-23
fonte: snapshot do repo otrs (ZZZProcessManagement.pm / ZZZACL.pm)
entity: Process-56ca5a2f78e80b672d746c80e1ef0e95
estado: Active
---

# Processo - Chamado Diaria No Carregamento

**Chamado Diaria No Carregamento** — estado **Active** · criado 2026-10-14 13:10:09 · alterado 2026-10-14 13:10:09

Hub: [[Hub - OTRS Processos]] · [[Hub - OTRS]] · [[otrs]]

Início: **1.Abertura Chamado Diria no Carregamento** → diálogo [[Dialog - Formulario Diaria no Carregamento]]

## Fluxo
```mermaid
flowchart LR
  A66636c36["1.Abertura Chamado Diria no Carregamento"]
  A7924ef19["3.1 Fecha Chamado Societario Diario no Carregamento"]
  A27952ae1["2.Atendimento Filial Diaria no Carregamento"]
  A2fc36749["2.1 Fechamento Filial Diaria no Carregamento"]
  A333c2053["3.Atendimento Societário Diaria no Carregamento"]
  style A66636c36 stroke-width:3px
  A66636c36 -->|"Envia Fila>> Societario"| A333c2053
  A66636c36 -->|"Envia Fila>> Fila do Contas a Receber"| A27952ae1
  A27952ae1 -->|"Fecha Chamado >> Filial"| A2fc36749
  A27952ae1 -->|"Repassa Fila >> Societario"| A333c2053
  A333c2053 -->|"Fecha Chamado >> Societario"| A7924ef19
```

## Atividades e diálogos
- **1.Abertura Chamado Diria no Carregamento** (início): [[Dialog - Formulario Diaria no Carregamento]]
- **2.1 Fechamento Filial Diaria no Carregamento**: [[Dialog - Formulario Diaria no Carregamento]]
- **2.Atendimento Filial Diaria no Carregamento**: [[Dialog - Formulario Diaria no Carregamento]] · [[Dialog - Controle Atendimento Processo (b2e090)]] · [[Dialog - Adcionar Valor Previsível da Estadia]]
- **3.1 Fecha Chamado Societario Diario no Carregamento**: [[Dialog - Formulario Diaria no Carregamento]]
- **3.Atendimento Societário Diaria no Carregamento**: [[Dialog - Formulario Diaria no Carregamento]] · [[Dialog - Controle Atendimento Processo (b2e090)]]

## Transições
- **Envia Fila>> Societario**: 1.Abertura Chamado Diria no Carregamento → 3.Atendimento Societário Diaria no Carregamento
  - Condição: (and: [[DF - CteClienteTipoNestle]] String `NAONESTLE`; [[DF - CteDB]] Regexp `.`; [[DF - CtePlaca]] Regexp `.`)
  - Ação *Envia Fila>> Societario* — TicketQueueSet: Fila [[Fila - CRC]]
  - Ação *Atribui>>Titulo Diaria no Carregamento* — TicketTitleSet: Title=`Placa: <OTRS_TICKET_DynamicField_CtePlaca> | CT-e :<OTRS_TICKET_DynamicField_CteNumero> | Cliente : <OTRS_TICKET_DynamicField_CteNomePagador>`
- **Envia Fila>> Fila do Contas a Receber**: 1.Abertura Chamado Diria no Carregamento → 2.Atendimento Filial Diaria no Carregamento
  - Condição: (and: [[DF - CteClienteTipoNestle]] String `NESTLE`; [[DF - CteDB]] Regexp `.`; [[DF - CtePlaca]] Regexp `.`)
  - Ação *Envia Fila>> Contas Receber* — TicketQueueSet: Fila [[Fila - Contas a Receber]]
  - Ação *Atribui>>Serviço Processo: Chamado Diária No Carregamento* — TicketServiceSet: Serviço [[Servico - Processo- Chamado Diária No Carregamento]]
  - Ação *Atribui>>Titulo Diaria no Carregamento* — TicketTitleSet: Title=`Placa: <OTRS_TICKET_DynamicField_CtePlaca> | CT-e :<OTRS_TICKET_DynamicField_CteNumero> | Cliente : <OTRS_TICKET_DynamicField_CteNomePagador>`
- **Fecha Chamado >> Filial**: 2.Atendimento Filial Diaria no Carregamento → 2.1 Fechamento Filial Diaria no Carregamento
  - Condição: (and: [[DF - CteControleAtividades]] String `Finalizar Atendimento Filial`; [[DF - CteDB]] Regexp `.`; [[DF - CtePlaca]] Regexp `.`)
  - Ação *Muda Estado Chamado >> Fechado* — TicketStateSet: StateID=`2`
- **Repassa Fila >> Societario**: 2.Atendimento Filial Diaria no Carregamento → 3.Atendimento Societário Diaria no Carregamento
  - Condição: (and: [[DF - CteControleAtividades]] String `Repasse Societario`; [[DF - CteDB]] Regexp `.`; [[DF - CtePlaca]] Regexp `.`)
  - Ação *Envia Fila>> Societario* — TicketQueueSet: Fila [[Fila - CRC]]
- **Fecha Chamado >> Societario**: 3.Atendimento Societário Diaria no Carregamento → 3.1 Fecha Chamado Societario Diario no Carregamento
  - Condição: (and: [[DF - CteControleAtividades]] String `Finalizar Atendimento Societario`; [[DF - CteDB]] Regexp `.`; [[DF - CtePlaca]] Regexp `.`)
  - Ação *Muda Estado Chamado >> Fechado* — TicketStateSet: StateID=`2`

## ACLs que se aplicam (diretas ou por diálogo)
- [[ACL - 1 - Esconde Campos Chamado - Ativo]]
- [[ACL - 1- Esconde Anexo Posicao Rastreador HelpDeskTransportador]]
- [[ACL - 1- Esconde Nota Débito MARFRIG DIÁRIA AO DESCARREGAR]]
- [[ACL - 1- Esconde Numero Registro BRF  DIÁRIA AO DESCARREGAR]]
- [[ACL - 1- Esconde Senha Marfrig HelpDeskTransportador]]
- [[ACL - 2 - Mostra Diária no Carregamento - Nota Fiscal]]
- [[ACL - 2- Mostra Anexo Posicao Rastreador Processo - DIÁRIA AO DESCARREGAR]]
- [[ACL - 2- Mostra Campos Chamado]]
- [[ACL - 2- Mostra NotaDébito Marfrig Processo - DIÁRIA AO DESCARREGAR]]
- [[ACL - 2- Mostra Numero Registro BRF Processo - DIÁRIA AO DESCARREGAR]]
- [[ACL - 2- Mostra Ocorrencia Todos Processos  NESTLE]]
- [[ACL - 2- Mostra Senha Marfrig Processos - DIÁRIA]]
- [[ACL - 3 - Esconde DACTE Carimbado Assinado e Posicao Rastreador BRF Diarias]]
- [[ACL - 3- Esconde Ocorrencia Todos Processos  Não NESTLE]]

> Fonte: snapshot do repo (espelho da prod); fila/serviço aparecem como nomes nas ações.
