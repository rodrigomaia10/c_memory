---
tipo: otrs-acl
tags: [otrs, otrs/acl]
atualizado: 2026-10-23
fonte: snapshot do repo otrs (ZZZProcessManagement.pm / ZZZACL.pm)
---

# ACL - 12- Esconder MKTFormsRede

Hub: [[Hub - OTRS ACLs]] · [[Hub - OTRS]] · ordem de execução: alfabética pelo nome, a última que casa por campo vence.

Criada 2024-04-30 15:54:32 (leonardo.marcal) · alterada 2024-04-30 16:02:49 (leonardo.marcal) · comentário: Esconder se NÃO for RedeSocial, Evento, Comunicado ou Campanha · StopAfterMatch=0

## Quando se aplica (Properties)
- DF [[DF - MKTFormsTipoDeArte]]: `BRINDES`, `ADESIVOS`, `BANNER`, `FACHADAS`, `LIVRETO`, `OUTDOOR`, `PLACAS`

## Efeito
**ShowHide**
- [[DF - MKTFormsCampanhas]]: 0 (esconde)
- [[DF - MKTFormsComunicados]]: 0 (esconde)
- [[DF - MKTFormsEvento]]: 0 (esconde)
- [[DF - MKTFormsRedeSocial]]: 0 (esconde)
