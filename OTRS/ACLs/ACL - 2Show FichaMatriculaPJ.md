---
tipo: otrs-acl
tags: [otrs, otrs/acl]
atualizado: 2026-10-23
fonte: snapshot do repo otrs (ZZZProcessManagement.pm / ZZZACL.pm)
---

# ACL - 2Show FichaMatriculaPJ

Hub: [[Hub - OTRS ACLs]] · [[Hub - OTRS]] · ordem de execução: alfabética pelo nome, a última que casa por campo vence.

StopAfterMatch=0

## Quando se aplica (Properties)
- DF [[DF - FichaMatriculaPersonType]]: `Jurídica`

## Efeito
**ShowHide**
- [[DF - CodCGCCnpj]]: 2 (obrigatório)
- [[DF - FichaMatriculaAnexoContratoSocial]]: 2 (obrigatório)
