---
tipo: otrs-processo
tags: [otrs, otrs/processo, estado/active]
atualizado: 2026-10-23
fonte: snapshot do repo otrs (ZZZProcessManagement.pm / ZZZACL.pm)
entity: Process-b4afada8d023a27dcc558935ad7d8eda
estado: Active
---

# Processo - Chamado Divergência Conta Corrente

**Chamado Divergência Conta Corrente** — estado **Active** · criado 2021-04-08 09:52:55 · alterado 2021-12-15 13:42:04

Hub: [[Hub - OTRS Processos]] · [[Hub - OTRS]] · [[otrs]]

Início: **1.Abertura Chamado Divergência Conta Corrente** → diálogo [[Dialog - Formulario Divergencia Conta Corrente]]

## Fluxo
```mermaid
flowchart LR
  A0f961e0c["1.Abertura Chamado Divergência Conta Corrente"]
  A9ed692c8["3.Atendimento Societário Divergencia Conta Corrente"]
  style A0f961e0c stroke-width:3px
  A0f961e0c -->|"Envia Fila>> Societario Divergencia Conta Corrente"| A9ed692c8
```

## Atividades e diálogos
- **1.Abertura Chamado Divergência Conta Corrente** (início): [[Dialog - Formulario Divergencia Conta Corrente]]
- **3.Atendimento Societário Divergencia Conta Corrente**: [[Dialog - Formulario Divergencia Conta Corrente]]

## Transições
- **Envia Fila>> Societario Divergencia Conta Corrente**: 1.Abertura Chamado Divergência Conta Corrente → 3.Atendimento Societário Divergencia Conta Corrente
  - Condição: (and: `Subject` Regexp `.`)
  - Ação *Atribui>>Titulo Processo Divergencia Conta Corrente* — TicketTitleSet: Title=`Divergência Conta Corrente`

## ACLs que se aplicam (diretas ou por diálogo)
- nenhuma

> Fonte: snapshot do repo (espelho da prod); fila/serviço aparecem como nomes nas ações.
