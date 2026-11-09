---
tipo: otrs-acl
tags: [otrs, otrs/acl]
atualizado: 2026-10-23
fonte: snapshot do repo otrs (ZZZProcessManagement.pm / ZZZACL.pm)
---

# ACL - 2 Mostra Diária na Devolução - CTE assinado e Rastreamento

Hub: [[Hub - OTRS ACLs]] · [[Hub - OTRS]] · ordem de execução: alfabética pelo nome, a última que casa por campo vence.

Criada 2025-11-28 17:55:28 (diogo.viana) · alterada 2026-10-14 14:49:40 (rodrigo.maia) · comentário: 2 Mostra Diária na Devolução - CTE assinado e Rastreamento · StopAfterMatch=0

## Quando se aplica (Properties)
- DF [[DF - CteClienteTipoNestle]]: `NESTLE`, `NESTLE PURINA`
- Process.ProcessEntityID: [[Processo - Chamado Diária na Devolução]]

## Efeito
**ShowHide**
- [[DF - CteAnexoPosicaoRastreador]]: 2 (obrigatório)
- [[DF - CteDACTECarimbadoAssinado]]: 2 (obrigatório)
