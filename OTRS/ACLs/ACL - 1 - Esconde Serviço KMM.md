---
tipo: otrs-acl
tags: [otrs, otrs/acl]
atualizado: 2026-10-23
fonte: snapshot do repo otrs (ZZZProcessManagement.pm / ZZZACL.pm)
---

# ACL - 1 - Esconde Serviço KMM

Hub: [[Hub - OTRS ACLs]] · [[Hub - OTRS]] · ordem de execução: alfabética pelo nome, a última que casa por campo vence.

Criada 2026-02-05 11:22:52 (diogo.viana) · alterada 2026-02-05 14:29:18 (diogo.viana) · comentário: 1 - Esconde Serviço KMM · StopAfterMatch=0

## Quando se aplica (Properties)
- CustomerUser.Group_rw: `Filiais`

## Efeito
- PossibleNot Ticket.Service: [[Servico - TI › Sistemas e Portais › KMM]]
