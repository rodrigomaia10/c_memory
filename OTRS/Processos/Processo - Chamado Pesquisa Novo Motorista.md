---
tipo: otrs-processo
tags: [otrs, otrs/processo, estado/active]
atualizado: 2026-10-23
fonte: snapshot do repo otrs (ZZZProcessManagement.pm / ZZZACL.pm)
entity: Process-bbfccb85289bca9f6a15833bf61e7451
estado: Active
---

# Processo - Chamado Pesquisa Novo Motorista

**Chamado Pesquisa Novo Motorista** — estado **Active** · criado 2021-04-06 16:51:03 · alterado 2021-12-15 13:45:59

Hub: [[Hub - OTRS Processos]] · [[Hub - OTRS]] · [[otrs]]

Início: **1.Abertura Chamado Pesquisa Motorista** → diálogo [[Dialog - Formulario Pesquisa Motorista]]

## Fluxo
```mermaid
flowchart LR
  A825dc472["3.Atendimento Societário Pesquisa Motorista"]
  A4809233c["1.Abertura Chamado Pesquisa Motorista"]
  A07828340["3.1 Fecha Chamado Societario Pesquisa Motorista"]
  style A4809233c stroke-width:3px
  A825dc472 -->|"Fecha Chamado >> Societario Pesquisa Motorista"| A07828340
  A4809233c -->|"Envia Fila>> Societario Pesquisa Motorista"| A825dc472
```

## Atividades e diálogos
- **1.Abertura Chamado Pesquisa Motorista** (início): [[Dialog - Formulario Pesquisa Motorista]]
- **3.1 Fecha Chamado Societario Pesquisa Motorista**: —
- **3.Atendimento Societário Pesquisa Motorista**: [[Dialog - Formulario Pesquisa Motorista]] · [[Dialog - Controle Atendimento Processo (aadcb8)]]

## Transições
- **Fecha Chamado >> Societario Pesquisa Motorista**: 3.Atendimento Societário Pesquisa Motorista → 3.1 Fecha Chamado Societario Pesquisa Motorista
  - Condição: (and: [[DF - CteControleAtividades]] String `Finalizar Atendimento Societario`)
  - Ação *Muda Estado Chamado >> Fechado* — TicketStateSet: StateID=`2`
- **Envia Fila>> Societario Pesquisa Motorista**: 1.Abertura Chamado Pesquisa Motorista → 3.Atendimento Societário Pesquisa Motorista
  - Condição: (and: [[DF - MotoristaCPF]] Regexp `.`; [[DF - MotoristaNome]] Regexp `.`)
  - Ação *Envia Fila>> Societario Pesquisa Motorista* — TicketQueueSet: Fila [[Fila - CRC]]
  - Ação *Atribui>>Serviço Processo: Chamado Pesquisa Novo Motorista* — TicketServiceSet: Serviço [[Servico - Processo- Chamado Pesquisa Novo Motorista]]
  - Ação *Atribui>>Titulo Processo Pesquisa Motorista* — TicketTitleSet: Title=`Motorista: <OTRS_TICKET_DynamicField_MotoristaNome> | Cavalo :<OTRS_TICKET_DynamicField_MotoristaCavalo> |`

## ACLs que se aplicam (diretas ou por diálogo)
- [[ACL - 8-  Esconde Formulário Pesquisa Motorista se Chamado Encerrado]]

> Fonte: snapshot do repo (espelho da prod); fila/serviço aparecem como nomes nas ações.
