---
tipo: otrs-acl
tags: [otrs, otrs/acl]
atualizado: 2026-10-23
fonte: snapshot do repo otrs (ZZZProcessManagement.pm / ZZZACL.pm)
---

# ACL - 3 - Esconde CNPJ - CPF NewKMM

Hub: [[Hub - OTRS ACLs]] · [[Hub - OTRS]] · ordem de execução: alfabética pelo nome, a última que casa por campo vence.

Criada 2025-12-15 11:13:46 (diogo.viana) · alterada 2026-01-22 16:07:28 (diogo.viana) · comentário: 3 - Esconde CNPJ / CPF NewKMM · StopAfterMatch=0

## Quando se aplica (Properties)
- DF [[DF - NewKMMCadastro]]: `[NotRegExp]^(?:Motorista|Pessoa)$`

## Efeito
**ShowHide**
- [[DF - NewKMMCnpjCpf]]: 0 (esconde)
