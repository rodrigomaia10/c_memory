---
tipo: otrs-processo
tags: [otrs, otrs/processo, estado/active]
atualizado: 2026-10-23
fonte: snapshot do repo otrs (ZZZProcessManagement.pm / ZZZACL.pm)
entity: Process-ad6521487c4f38dfe7e773b38173223e
estado: Active
---

# Processo - Logística Operações

**Logística Operações** — estado **Active** · criado 2021-12-15 14:41:33 · alterado 2021-12-20 15:06:26

Hub: [[Hub - OTRS Processos]] · [[Hub - OTRS]] · [[otrs]]

Início: **1. Abertura Chamado Logistica Operacoes** → diálogo [[Dialog - Formulario Logistica Operacoes]]

## Fluxo
```mermaid
flowchart LR
  Abfab6a6f["1. Abertura Chamado Logistica Operacoes"]
  Aa6aed5cb["2.Atendimento Fila Logistica Operacoes"]
  style Abfab6a6f stroke-width:3px
  Abfab6a6f -->|"Envia Fila>> Logistica Operacoes"| Aa6aed5cb
```

## Atividades e diálogos
- **1. Abertura Chamado Logistica Operacoes** (início): [[Dialog - Formulario Logistica Operacoes]]
- **2.Atendimento Fila Logistica Operacoes**: [[Dialog - Formulario Logistica Operacoes]]

## Transições
- **Envia Fila>> Logistica Operacoes**: 1. Abertura Chamado Logistica Operacoes → 2.Atendimento Fila Logistica Operacoes
  - Condição: (and: [[DF - ServicoLogistica]] Regexp `.`)
  - Ação *Atribui>>Fila Logistica Operacoes* — TicketQueueSet: Fila [[Fila - Logística Operações]]
  - Ação *Atribui>>Titulo Processo Suporte Logistica Operaçao* — TicketTitleSet: Title=`Processo Suporte Logística Operação <OTRS_TICKET_DynamicField_ServicoLogistica>`
  - Ação *Atribui>>Serviço Processo: Suporte Logistica Operacao* — TicketServiceSet: Serviço [[Servico - Logística Operações]]

## ACLs que se aplicam (diretas ou por diálogo)
- nenhuma

> Fonte: snapshot do repo (espelho da prod); fila/serviço aparecem como nomes nas ações.
