---
tipo: otrs-acl
tags: [otrs, otrs/acl]
atualizado: 2026-10-23
fonte: snapshot do repo otrs (ZZZProcessManagement.pm / ZZZACL.pm)
---

# ACL - 8-  Esconde Formulário Pesquisa Motorista se Chamado Encerrado

Hub: [[Hub - OTRS ACLs]] · [[Hub - OTRS]] · ordem de execução: alfabética pelo nome, a última que casa por campo vence.

StopAfterMatch=0

## Quando se aplica (Properties)
- Process.ProcessEntityID: [[Processo - Chamado Pesquisa Novo Motorista]]
- Ticket.State: `closed successful`, `closed unsuccessful`, `closed with workaround`

## Efeito
- PossibleNot ActivityDialog: `["ActivityDialog-1e7f771b08285cea0537124d9b597e66"]`
