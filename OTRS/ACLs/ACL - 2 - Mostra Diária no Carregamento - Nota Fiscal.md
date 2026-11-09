---
tipo: otrs-acl
tags: [otrs, otrs/acl]
atualizado: 2026-10-23
fonte: snapshot do repo otrs (ZZZProcessManagement.pm / ZZZACL.pm)
---

# ACL - 2 - Mostra Diária no Carregamento - Nota Fiscal

Hub: [[Hub - OTRS ACLs]] · [[Hub - OTRS]] · ordem de execução: alfabética pelo nome, a última que casa por campo vence.

Criada 2025-11-28 16:56:45 (diogo.viana) · alterada 2026-10-14 14:45:38 (rodrigo.maia) · comentário: 2 - Mostra Diária no Carregamento - Nota Fiscal · StopAfterMatch=1

## Quando se aplica (Properties)
- DF [[DF - CteClienteTipoNestle]]: `NESTLE`, `NESTLE PURINA`
- DF [[DF - CteOcorrencia]]: `[RegExp]^.+$`
- Process.ProcessEntityID: [[Processo - Chamado Diaria No Carregamento]]

## Efeito
**ShowHide**
- [[DF - NotaFiscalCarregamento]]: 2 (obrigatório)
