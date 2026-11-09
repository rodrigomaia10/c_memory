---
tipo: otrs-acl
tags: [otrs, otrs/acl]
atualizado: 2026-10-23
fonte: snapshot do repo otrs (ZZZProcessManagement.pm / ZZZACL.pm)
---

# ACL - 3 - Esconde Serviços Processo

Hub: [[Hub - OTRS ACLs]] · [[Hub - OTRS]] · ordem de execução: alfabética pelo nome, a última que casa por campo vence.

Criada 2021-01-11 17:06:35 (samuel.euzebio) · alterada 2021-10-20 11:33:29 (rodrigo.maia) · comentário: Esconde Serviços Processo · StopAfterMatch=0

## Quando se aplica (Properties)
- CustomerUser.Group_rw: `Usuários Clientes Geral`

## Efeito
- PossibleNot Ticket.Service: `[RegExp]^Processo`
