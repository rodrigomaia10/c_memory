---
tipo: otrs-processo
tags: [otrs, otrs/processo, estado/active]
atualizado: 2026-10-23
fonte: snapshot do repo otrs (ZZZProcessManagement.pm / ZZZACL.pm)
entity: Process-7046c9a397811ca1ff87daf39f87a594
estado: Active
---

# Processo - Chamado Outras Demandas

**Chamado Outras Demandas** — estado **Active** · criado 2021-04-08 09:22:40 · alterado 2021-12-15 13:45:19

Hub: [[Hub - OTRS Processos]] · [[Hub - OTRS]] · [[otrs]]

Início: **1.Abertura Chamado Outras Demanadas** → diálogo [[Dialog - Formulario Outras Demandas]]

## Fluxo
```mermaid
flowchart LR
  Afcdf6f7b["3.Atendimento Societário Outras Demandas"]
  A2ff458d5["1.Abertura Chamado Outras Demanadas"]
  style A2ff458d5 stroke-width:3px
  A2ff458d5 -->|"Envia Fila>> Societario Outras Demandas"| Afcdf6f7b
```

## Atividades e diálogos
- **1.Abertura Chamado Outras Demanadas** (início): [[Dialog - Formulario Outras Demandas]]
- **3.Atendimento Societário Outras Demandas**: [[Dialog - Formulario Outras Demandas]]

## Transições
- **Envia Fila>> Societario Outras Demandas**: 1.Abertura Chamado Outras Demanadas → 3.Atendimento Societário Outras Demandas
  - Condição: (and: `Subject` Regexp `.`)
  - Ação *Atribui>>Titulo Processo Outras Demandas* — TicketTitleSet: Title=`Processo: Chamado Outras Demandas`

## ACLs que se aplicam (diretas ou por diálogo)
- nenhuma

> Fonte: snapshot do repo (espelho da prod); fila/serviço aparecem como nomes nas ações.
