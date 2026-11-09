---
tipo: otrs-acl
tags: [otrs, otrs/acl]
atualizado: 2026-10-23
fonte: snapshot do repo otrs (ZZZProcessManagement.pm / ZZZACL.pm)
---

# ACL - 2 - Mostra Troca de Nota - Nota Fiscal

Hub: [[Hub - OTRS ACLs]] · [[Hub - OTRS]] · ordem de execução: alfabética pelo nome, a última que casa por campo vence.

Criada 2025-12-01 18:28:27 (diogo.viana) · alterada 2025-12-01 18:31:21 (diogo.viana) · comentário: 2 - Mostra Troca de Nota - Nota Fiscal · StopAfterMatch=0

## Quando se aplica (Properties)
- DF [[DF - CteClienteTipoNestle]]: `NESTLE`, `NESTLE PURINA`
- Process.ProcessEntityID: [[Processo - Chamado Diária Troca de Nota]]

## Efeito
**ShowHide**
- [[DF - NotaFiscalTroca]]: 2 (obrigatório)
