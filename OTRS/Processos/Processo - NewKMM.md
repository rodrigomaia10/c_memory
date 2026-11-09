---
tipo: otrs-processo
tags: [otrs, otrs/processo, estado/inactive]
atualizado: 2026-10-23
fonte: snapshot do repo otrs (ZZZProcessManagement.pm / ZZZACL.pm)
entity: Process-3b50b1fa289e884fd847a6dc707f6c15
estado: Inactive
---

# Processo - NewKMM

**NewKMM** — estado **Inactive** · criado 2025-12-11 11:26:33 · alterado 2025-12-17 08:53:50

Hub: [[Hub - OTRS Processos]] · [[Hub - OTRS]] · [[otrs]]

Início: **NewKMM - Screen** → diálogo [[Dialog - NewKMM - Screen]]

## Fluxo
```mermaid
flowchart LR
  Aa6bc3430["NewKMM - NumCarga"]
  Aeabdc504["NewKMM - Screen"]
  style Aeabdc504 stroke-width:3px
  Aeabdc504 -->|"NewKMM - Trigger Title"| Aa6bc3430
```

## Atividades e diálogos
- **NewKMM - NumCarga**: [[Dialog - NewKMM - NumCarga]]
- **NewKMM - Screen** (início): [[Dialog - NewKMM - Screen]]

## Transições
- **NewKMM - Trigger Title**: NewKMM - Screen → NewKMM - NumCarga
  - Condição: (and: [[DF - NewKMMTela]] Regexp `^(?:Cancelamento de Carga|Carga|Ocorrência|Atendimento)$`)
  - Ação *NewKMM - Change Title* — TicketTitleSet: Title=`<OTRS_TICKET_DynamicField_NewKMMNumCarga>`

## ACLs que se aplicam (diretas ou por diálogo)
- nenhuma

> Fonte: snapshot do repo (espelho da prod); fila/serviço aparecem como nomes nas ações.
