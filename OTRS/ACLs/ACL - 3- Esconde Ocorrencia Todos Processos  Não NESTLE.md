---
tipo: otrs-acl
tags: [otrs, otrs/acl]
atualizado: 2026-10-23
fonte: snapshot do repo otrs (ZZZProcessManagement.pm / ZZZACL.pm)
---

# ACL - 3- Esconde Ocorrencia Todos Processos  Não NESTLE

Hub: [[Hub - OTRS ACLs]] · [[Hub - OTRS]] · ordem de execução: alfabética pelo nome, a última que casa por campo vence.

Criada 2026-01-28 17:02:46 (diogo.viana) · alterada 2026-10-14 14:32:27 (rodrigo.maia) · comentário: 3- Esconde Ocorrencia Todos Processos  Não NESTLE · StopAfterMatch=0

## Quando se aplica (Properties)
- DF [[DF - CteClienteTipoNestle]]: `CLIENTENAONESTLE`
- Process.ProcessEntityID: [[Processo - Chamado Diária Troca de Nota]], [[Processo - Chamado Diaria No Carregamento]], [[Processo - Chamado Diária em Posto Fiscal]], [[Processo - Chamado Diária ao Descarregar]], [[Processo - Chamado Diária na Devolução]]

## Efeito
**ShowHide**
- [[DF - CteOcorrencia]]: 0 (esconde)
