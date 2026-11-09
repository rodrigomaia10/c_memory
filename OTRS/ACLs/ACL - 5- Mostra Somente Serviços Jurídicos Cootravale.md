---
tipo: otrs-acl
tags: [otrs, otrs/acl]
atualizado: 2026-10-23
fonte: snapshot do repo otrs (ZZZProcessManagement.pm / ZZZACL.pm)
---

# ACL - 5- Mostra Somente Serviços Jurídicos Cootravale

Hub: [[Hub - OTRS ACLs]] · [[Hub - OTRS]] · ordem de execução: alfabética pelo nome, a última que casa por campo vence.

Criada 2021-04-14 17:13:00 (samuel.euzebio) · alterada 2021-04-14 17:15:19 (samuel.euzebio) · comentário: Mostra Somente Serviços Jurídicos Cootravale · StopAfterMatch=0

## Quando se aplica (Properties)
- CustomerUser.Group_rw: `Jurídico Cootravale Cliente`

## Efeito
- PossibleAdd Ticket.Service: [[Servico - Jurídico Cootravale]], [[Servico - Jurídico Cootravale › Cível Comercial]], [[Servico - Jurídico Cootravale › Cível Financeiro]], [[Servico - Jurídico Cootravale › Cível Operacional]], [[Servico - Jurídico Cootravale › Outros Comercial]], [[Servico - Jurídico Cootravale › Outros Financeiro]], [[Servico - Jurídico Cootravale › Outros Operacional]], [[Servico - Jurídico Cootravale › Trabalhista Cootravale]], [[Servico - Jurídico Cootravale › Trabalhista LKW]]
