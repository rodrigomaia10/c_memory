---
tipo: otrs-acl
tags: [otrs, otrs/acl]
atualizado: 2026-10-23
fonte: snapshot do repo otrs (ZZZProcessManagement.pm / ZZZACL.pm)
---

# ACL - 11 - Mostra Campos Seguro de Vida

Hub: [[Hub - OTRS ACLs]] · [[Hub - OTRS]] · ordem de execução: alfabética pelo nome, a última que casa por campo vence.

StopAfterMatch=0

## Quando se aplica (Properties)
- DF [[DF - TipoAssegurado]]: `Motorista  `, `Motorista`
- Process.ActivityDialogEntityID: [[Dialog - 1.1 Formulário Seguro de Vida]]
- Process.ProcessEntityID: [[Processo - Chamado Seguro de Vida]]

## Efeito
**ShowHide**
- [[DF - AnexoCnhAssegurado]]: 2 (obrigatório)
