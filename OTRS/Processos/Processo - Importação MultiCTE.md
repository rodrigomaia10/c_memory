---
tipo: otrs-processo
tags: [otrs, otrs/processo, estado/inactive]
atualizado: 2026-10-23
fonte: snapshot do repo otrs (ZZZProcessManagement.pm / ZZZACL.pm)
entity: Process-04ef82d7fef0194e6d9828c08f67e415
estado: Inactive
---

# Processo - Importação MultiCTE

**Importação MultiCTE** — estado **Inactive** · criado 2023-05-15 09:38:02 · alterado 2023-07-13 08:33:03

Hub: [[Hub - OTRS Processos]] · [[Hub - OTRS]] · [[otrs]]

Início: **Abertura Chamado Importação MultiCTE** → diálogo [[Dialog - Formulário Chamado MultiCte]]

## Fluxo
```mermaid
flowchart LR
  A916f0a77["Abertura Chamado Importação MultiCTE"]
  A2661d5b2["Termina"]
  style A916f0a77 stroke-width:3px
  A916f0a77 -->|"Envia Fila>>>TI"| A2661d5b2
```

## Atividades e diálogos
- **Abertura Chamado Importação MultiCTE** (início): [[Dialog - Formulário Chamado MultiCte]]
- **Termina**: —

## Transições
- **Envia Fila>>>TI**: Abertura Chamado Importação MultiCTE → Termina
  - Condição: (and: `Dynamic_field` Regexp `.`)
  - Ação *Envia Fila TI* — TicketQueueSet: Fila [[Fila - TI › Sistemas]]

## ACLs que se aplicam (diretas ou por diálogo)
- nenhuma

> Fonte: snapshot do repo (espelho da prod); fila/serviço aparecem como nomes nas ações.
