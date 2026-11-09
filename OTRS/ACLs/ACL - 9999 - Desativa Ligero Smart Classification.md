---
tipo: otrs-acl
tags: [otrs, otrs/acl]
atualizado: 2026-10-23
fonte: snapshot do repo otrs (ZZZProcessManagement.pm / ZZZACL.pm)
---

# ACL - 9999 - Desativa Ligero Smart Classification

Hub: [[Hub - OTRS ACLs]] · [[Hub - OTRS]] · ordem de execução: alfabética pelo nome, a última que casa por campo vence.

StopAfterMatch=0

## Quando se aplica (Properties)
- Ticket.Service: `[RegExp]^`
- Ticket.Type: `[Not]Unclassified`

## Efeito
- PossibleNot Action: `["AgentTicketLigeroSmartClassification"]`
