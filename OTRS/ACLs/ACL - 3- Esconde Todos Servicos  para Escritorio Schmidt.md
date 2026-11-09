---
tipo: otrs-acl
tags: [otrs, otrs/acl]
atualizado: 2026-10-23
fonte: snapshot do repo otrs (ZZZProcessManagement.pm / ZZZACL.pm)
---

# ACL - 3- Esconde Todos Servicos  para Escritorio Schmidt

Hub: [[Hub - OTRS ACLs]] · [[Hub - OTRS]] · ordem de execução: alfabética pelo nome, a última que casa por campo vence.

Criada 2021-06-07 17:40:24 (samuel.euzebio) · alterada 2021-06-07 17:44:59 (samuel.euzebio) · comentário: 3- Esconde Todos Servicos  para Escritorio Schmidt · StopAfterMatch=0

## Quando se aplica (Properties)
- CustomerUser.Group_rw: `Usuario Schmidt Cliente`

## Efeito
- PossibleNot Ticket.Service: `[RegExp]^`
