---
tipo: otrs-acl
tags: [otrs, otrs/acl]
atualizado: 2026-10-23
fonte: snapshot do repo otrs (ZZZProcessManagement.pm / ZZZACL.pm)
---

# ACL - 3 - Esconde CNPJ - CPF Placa NewKMM

Hub: [[Hub - OTRS ACLs]] · [[Hub - OTRS]] · ordem de execução: alfabética pelo nome, a última que casa por campo vence.

Criada 2025-12-15 11:25:24 (diogo.viana) · alterada 2026-01-22 16:28:41 (diogo.viana) · comentário: 3 - Esconde CNPJ / CPF Placa NewKMM · StopAfterMatch=0

## Quando se aplica (Properties)
- DF [[DF - NewKMMTela]]: `[Not]Cadastro`

## Efeito
**ShowHide**
- [[DF - NewKMMCnpjCpf]]: 0 (esconde)
- [[DF - NewKMMPlaca]]: 0 (esconde)
