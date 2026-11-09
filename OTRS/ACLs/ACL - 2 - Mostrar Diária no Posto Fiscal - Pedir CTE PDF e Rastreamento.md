---
tipo: otrs-acl
tags: [otrs, otrs/acl]
atualizado: 2026-10-23
fonte: snapshot do repo otrs (ZZZProcessManagement.pm / ZZZACL.pm)
---

# ACL - 2 - Mostrar Diária no Posto Fiscal - Pedir CTE PDF e Rastreamento

Hub: [[Hub - OTRS ACLs]] · [[Hub - OTRS]] · ordem de execução: alfabética pelo nome, a última que casa por campo vence.

Criada 2025-11-28 18:10:11 (diogo.viana) · alterada 2026-10-14 14:49:23 (rodrigo.maia) · comentário: 2 - Mostrar Diária no Posto Fiscal - Pedir CTE PDF e Rastreamento · StopAfterMatch=0

## Quando se aplica (Properties)
- DF [[DF - CteClienteTipoNestle]]: `NESTLE`, `NESTLE PURINA`
- Process.ProcessEntityID: [[Processo - Chamado Diária em Posto Fiscal]]

## Efeito
**ShowHide**
- [[DF - CTePDF]]: 2 (obrigatório)
- [[DF - CteAnexoPosicaoRastreador]]: 2 (obrigatório)
