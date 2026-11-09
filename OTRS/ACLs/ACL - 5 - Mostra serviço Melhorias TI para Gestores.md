---
tipo: otrs-acl
tags: [otrs, otrs/acl]
atualizado: 2026-10-23
fonte: snapshot do repo otrs (ZZZProcessManagement.pm / ZZZACL.pm)
---

# ACL - 5 - Mostra serviço Melhorias TI para Gestores

Hub: [[Hub - OTRS ACLs]] · [[Hub - OTRS]] · ordem de execução: alfabética pelo nome, a última que casa por campo vence.

Criada 2025-07-22 10:14:16 (samuel.euzebio) · alterada 2025-08-25 10:10:17 (samuel.euzebio) · comentário: 5 - Mostra serviço Melhorias TI para Gestores · StopAfterMatch=0

## Quando se aplica (Properties)
- CustomerUser.Group_rw: `Gestores Melhorias TI`, `TI - Melhorias`

## Efeito
- PossibleAdd Ticket.TI::Melhorias: `TI::Melhorias`
