---
tipo: otrs-acl
tags: [otrs, otrs/acl]
atualizado: 2026-10-23
fonte: snapshot do repo otrs (ZZZProcessManagement.pm / ZZZACL.pm)
---

# ACL - 12- MostrarMKTFormsRedeSocial

Hub: [[Hub - OTRS ACLs]] · [[Hub - OTRS]] · ordem de execução: alfabética pelo nome, a última que casa por campo vence.

Criada 2024-04-30 15:24:31 (leonardo.marcal) · alterada 2024-04-30 15:51:33 (leonardo.marcal) · comentário: Mostrar quando o tipo de arte for RedeSocial · StopAfterMatch=0

## Quando se aplica (Properties)
- DF [[DF - MKTFormsTipoDeArte]]: `REDE SOCIAL`

## Efeito
**ShowHide**
- [[DF - MKTFormsComunicados]]: 0 (esconde)
- [[DF - MKTFormsEvento]]: 0 (esconde)
- [[DF - MKTFormsRedeSocial]]: 2 (obrigatório)
