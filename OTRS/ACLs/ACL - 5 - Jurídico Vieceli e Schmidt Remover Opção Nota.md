---
tipo: otrs-acl
tags: [otrs, otrs/acl]
atualizado: 2026-10-23
fonte: snapshot do repo otrs (ZZZProcessManagement.pm / ZZZACL.pm)
---

# ACL - 5 - Jurídico Vieceli e Schmidt Remover Opção Nota

Hub: [[Hub - OTRS ACLs]] · [[Hub - OTRS]] · ordem de execução: alfabética pelo nome, a última que casa por campo vence.

StopAfterMatch=0

## Quando se aplica (Properties)
- Ticket.Queue: `Jurídico Vieceli`, `Jurídico Schmidt`

## Efeito
- PossibleNot Action: `["AgentTicketNote"]`
