---
tipo: otrs-acl
tags: [otrs, otrs/acl]
atualizado: 2026-10-23
fonte: snapshot do repo otrs (ZZZProcessManagement.pm / ZZZACL.pm)
---

# ACL - 3 - Esconde Serviços Jurídicos Vieceli e Cootravale e Cristofolini

Hub: [[Hub - OTRS ACLs]] · [[Hub - OTRS]] · ordem de execução: alfabética pelo nome, a última que casa por campo vence.

Criada 2020-11-26 09:20:26 (samuel.euzebio) · alterada 2025-04-24 11:40:29 (samuel.euzebio) · comentário: Esconde Serviços Jurídicos · StopAfterMatch=0

## Quando se aplica (Properties)
- CustomerUser.Group_rw: `Usuários Clientes Geral`

## Efeito
- PossibleNot Ticket.Service: `[RegExp]^Jurídico`
