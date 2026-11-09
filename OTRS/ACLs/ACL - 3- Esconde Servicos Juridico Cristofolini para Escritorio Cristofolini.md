---
tipo: otrs-acl
tags: [otrs, otrs/acl]
atualizado: 2026-10-23
fonte: snapshot do repo otrs (ZZZProcessManagement.pm / ZZZACL.pm)
---

# ACL - 3- Esconde Servicos Juridico Cristofolini para Escritorio Cristofolini

Hub: [[Hub - OTRS ACLs]] · [[Hub - OTRS]] · ordem de execução: alfabética pelo nome, a última que casa por campo vence.

Criada 2021-06-07 17:24:55 (samuel.euzebio) · alterada 2025-04-24 11:41:45 (samuel.euzebio) · comentário: 3- Esconde Servicos Juridico Cristofolini para Escritorio Cristofolini · StopAfterMatch=0

## Quando se aplica (Properties)
- CustomerUser.Group_rw: `Usuario Cristofolini Cliente`

## Efeito
- PossibleNot Ticket.Service: `[RegExp]^Jurídico Cristofolini`
