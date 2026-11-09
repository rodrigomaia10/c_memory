---
tipo: otrs-processo
tags: [otrs, otrs/processo, estado/active]
atualizado: 2026-10-23
fonte: snapshot do repo otrs (ZZZProcessManagement.pm / ZZZACL.pm)
entity: Process-29d7aad86f50e8197f56341c71c4bf90
estado: Active
---

# Processo - Chamado Diária ao Descarregar

**Chamado Diária ao Descarregar** — estado **Active** · criado 2021-01-11 15:16:45 · alterado 2026-07-30 14:20:26

Hub: [[Hub - OTRS Processos]] · [[Hub - OTRS]] · [[otrs]]

Início: **1.Abertura Chamado Diaria** → diálogo [[Dialog - Formulário Diária]]

## Fluxo
```mermaid
flowchart LR
  A8b8f3372["3.1 Fecha Chamado Societario"]
  Aeaf8243a["3.Atendimento Societário"]
  Aa9b13444["2.1 Fechamento Filial"]
  Ae2921bab["1.Abertura Chamado Diaria"]
  Af67322b1["2.Atendimento Filial Diaria ao Descarregar"]
  style Ae2921bab stroke-width:3px
  Aeaf8243a -->|"Fecha Chamado >> Societario"| A8b8f3372
  Ae2921bab -->|"Envia Fila>> Societario"| Aeaf8243a
  Ae2921bab -->|"Envia Fila>> Contas Receber"| Af67322b1
  Af67322b1 -->|"Repassa Fila >> Societario"| Aeaf8243a
  Af67322b1 -->|"Fecha Chamado >> Filial"| Aa9b13444
```

## Atividades e diálogos
- **1.Abertura Chamado Diaria** (início): [[Dialog - Formulário Diária]]
- **2.1 Fechamento Filial**: [[Dialog - Formulário Diária]]
- **2.Atendimento Filial Diaria ao Descarregar**: [[Dialog - Formulário Diária]] · [[Dialog - Controle Atendimento Processo (aadcb8)]] · [[Dialog - Adcionar Valor Previsível da Estadia]]
- **3.1 Fecha Chamado Societario**: [[Dialog - Formulário Diária de Devolução]]
- **3.Atendimento Societário**: [[Dialog - Formulário Diária de Devolução]] · [[Dialog - Controle Atendimento Processo (aadcb8)]]

## Transições
- **Fecha Chamado >> Societario**: 3.Atendimento Societário → 3.1 Fecha Chamado Societario
  - Condição: (and: [[DF - CteControleAtividades]] String `Finalizar Atendimento Societario`; [[DF - CteDB]] Regexp `.`; [[DF - CtePlaca]] Regexp `.`)
  - Ação *Muda Estado Chamado >> Fechado* — TicketStateSet: StateID=`2`
- **Envia Fila>> Societario**: 1.Abertura Chamado Diaria → 3.Atendimento Societário
  - Condição: (and: [[DF - CteClienteTipoNestle]] String `NAONESTLE`; [[DF - CteDB]] Regexp `.`; [[DF - CtePlaca]] Regexp `.`)
  - Ação *Envia Fila>> Societario* — TicketQueueSet: Fila [[Fila - CRC]]
  - Ação *Atribui>>Serviço Processo: Chamado Diária ao Descarregar* — TicketServiceSet: Serviço [[Servico - Processo- Chamado Diária ao Descarregar]]
  - Ação *Atribui>>Titulo Processo* — TicketTitleSet: Title=`Placa: <OTRS_TICKET_DynamicField_CtePlaca> | CT-e :<OTRS_TICKET_DynamicField_CteNumero> | Cliente : <OTRS_TICKET_DynamicField_CteNomePagador>`
- **Envia Fila>> Contas Receber**: 1.Abertura Chamado Diaria → 2.Atendimento Filial Diaria ao Descarregar
  - Condição: (and: [[DF - CteClienteTipoNestle]] String `NESTLE`; [[DF - CteDB]] Regexp `.`; [[DF - CtePlaca]] Regexp `.`)
  - Ação *Envia Fila>> Contas Receber* — TicketQueueSet: Fila [[Fila - Contas a Receber]]
  - Ação *Atribui>>Serviço Processo: Chamado Diária ao Descarregar* — TicketServiceSet: Serviço [[Servico - Processo- Chamado Diária ao Descarregar]]
  - Ação *Atribui>>Titulo Processo* — TicketTitleSet: Title=`Placa: <OTRS_TICKET_DynamicField_CtePlaca> | CT-e :<OTRS_TICKET_DynamicField_CteNumero> | Cliente : <OTRS_TICKET_DynamicField_CteNomePagador>`
- **Repassa Fila >> Societario**: 2.Atendimento Filial Diaria ao Descarregar → 3.Atendimento Societário
  - Condição: (and: [[DF - CteControleAtividades]] String `Repasse Societario`; [[DF - CteDB]] Regexp `.`; [[DF - CtePlaca]] Regexp `.`)
  - Ação *Envia Fila>> Societario* — TicketQueueSet: Fila [[Fila - CRC]]
  - Ação *Muda Estado Chamado >> Aberto* — TicketStateSet: StateID=`4`
- **Fecha Chamado >> Filial**: 2.Atendimento Filial Diaria ao Descarregar → 2.1 Fechamento Filial
  - Condição: (and: [[DF - CteControleAtividades]] String `Finalizar Atendimento Filial`; [[DF - CteDB]] Regexp `.`; [[DF - CtePlaca]] Regexp `.`)
  - Ação *Muda Estado Chamado >> Fechado* — TicketStateSet: StateID=`2`

## ACLs que se aplicam (diretas ou por diálogo)
- [[ACL - 1 - Esconde Campos Chamado - Ativo]]
- [[ACL - 1- Esconde Anexo Posicao Rastreador HelpDeskTransportador]]
- [[ACL - 1- Esconde CET BRF HelpDeskTransportador]]
- [[ACL - 1- Esconde Numero Registro BRF HelpDeskTransportador]]
- [[ACL - 1- Esconde Senha Marfrig HelpDeskTransportador]]
- [[ACL - 2- Mostra Anexo Posicao Rastreador Processo - DIÁRIA AO DESCARREGAR]]
- [[ACL - 2- Mostra Campos Chamado]]
- [[ACL - 2- Mostra Numero Registro BRF Processo - DIÁRIA AO DESCARREGAR]]
- [[ACL - 2- Mostra Ocorrencia Todos Processos  NESTLE]]
- [[ACL - 2- Mostra Senha Marfrig Processos - DIÁRIA]]
- [[ACL - 3 - Esconde DACTE Carimbado Assinado e Posicao Rastreador BRF Diarias]]
- [[ACL - 3- Esconde Ocorrencia Todos Processos  Não NESTLE]]

> Fonte: snapshot do repo (espelho da prod); fila/serviço aparecem como nomes nas ações.
