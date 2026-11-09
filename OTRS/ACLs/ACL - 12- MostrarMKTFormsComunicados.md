---
tipo: otrs-acl
tags: [otrs, otrs/acl]
atualizado: 2026-10-23
fonte: snapshot do repo otrs (ZZZProcessManagement.pm / ZZZACL.pm)
---

# ACL - 12- MostrarMKTFormsComunicados

Hub: [[Hub - OTRS ACLs]] · [[Hub - OTRS]] · ordem de execução: alfabética pelo nome, a última que casa por campo vence.

Criada 2024-05-03 10:54:50 (leonardo.marcal) · alterada 2024-05-03 10:58:47 (leonardo.marcal) · comentário: Mostrar quando o tipo de arte for RedeSocial · StopAfterMatch=0

## Quando se aplica (Properties)
- DF [[DF - MKTFormsTipoDeArte]]: `COMUNICADOS`

## Efeito
**ShowHide**
- [[DF - MKTFormsCampanhas]]: 0 (esconde)
- [[DF - MKTFormsComunicados]]: 2 (obrigatório)
- [[DF - MKTFormsEvento]]: 0 (esconde)
- [[DF - MKTFormsRedeSocial]]: 0 (esconde)
