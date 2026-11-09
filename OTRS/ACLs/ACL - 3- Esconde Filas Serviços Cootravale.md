---
tipo: otrs-acl
tags: [otrs, otrs/acl]
atualizado: 2026-10-23
fonte: snapshot do repo otrs (ZZZProcessManagement.pm / ZZZACL.pm)
---

# ACL - 3- Esconde Filas Serviços Cootravale

Hub: [[Hub - OTRS ACLs]] · [[Hub - OTRS]] · ordem de execução: alfabética pelo nome, a última que casa por campo vence.

Criada 2021-05-07 15:48:36 (samuel.euzebio) · alterada 2021-06-07 17:37:33 (samuel.euzebio) · comentário: Esconde Filas Serviços Cootravale · StopAfterMatch=0

## Quando se aplica (Properties)
- CustomerUser.Group_rw: `Usuario Schmidt Cliente`

## Efeito
- PossibleNot Ticket.Service: [[Servico - Suprimentos › Dúvidas]], [[Servico - Suprimentos › Dúvidas › Lançamentos - Documentos]], [[Servico - Suprimentos]]
