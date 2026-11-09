---
tipo: otrs-acl
tags: [otrs, otrs/acl]
atualizado: 2026-10-23
fonte: snapshot do repo otrs (ZZZProcessManagement.pm / ZZZACL.pm)
---

# ACL - 4 - Esconde Serviços  para Transportadores Cooperados

Hub: [[Hub - OTRS ACLs]] · [[Hub - OTRS]] · ordem de execução: alfabética pelo nome, a última que casa por campo vence.

Criada 2021-01-11 16:22:17 (samuel.euzebio) · alterada 2021-10-13 09:58:07 (samuel.euzebio) · comentário: Somente para os transportadores abrirem chamado via processo. · StopAfterMatch=0

## Quando se aplica (Properties)
- CustomerUser.Group_rw: `Transportadores`

## Efeito
- PossibleNot Ticket.Service: `[RegExp]^`
