---
tipo: otrs-acl
tags: [otrs, otrs/acl]
atualizado: 2026-10-23
fonte: snapshot do repo otrs (ZZZProcessManagement.pm / ZZZACL.pm)
---

# ACL - 3 - Esconde Serviços Não Juridicos

Hub: [[Hub - OTRS ACLs]] · [[Hub - OTRS]] · ordem de execução: alfabética pelo nome, a última que casa por campo vence.

StopAfterMatch=0

## Quando se aplica (Properties)
- CustomerUser.Group_rw: `Jurídico Cootravale Cliente`

## Efeito
- Possible Ticket.Service: `[RegExp]Jurídico Cootravale`
