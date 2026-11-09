---
tipo: otrs-acl
tags: [otrs, otrs/acl]
atualizado: 2026-10-23
fonte: snapshot do repo otrs (ZZZProcessManagement.pm / ZZZACL.pm)
---

# ACL - 2- Mostra Ocorrencia Todos Processos  NESTLE

Hub: [[Hub - OTRS ACLs]] · [[Hub - OTRS]] · ordem de execução: alfabética pelo nome, a última que casa por campo vence.

Criada 2021-01-11 16:19:17 (samuel.euzebio) · alterada 2026-10-15 09:58:39 (rodrigo.maia) · comentário: MostraOcorrencia Todos Processos  NESTLE · StopAfterMatch=0

## Quando se aplica (Properties)
- DF [[DF - CteClienteTipoNestle]]: `NESTLE`, `NESTLE PURINA`
- Process.ProcessEntityID: [[Processo - Chamado Diária Troca de Nota]], [[Processo - Chamado Diaria No Carregamento]], [[Processo - Chamado Diária em Posto Fiscal]], [[Processo - Chamado Diária ao Descarregar]], [[Processo - Chamado Diária na Devolução]]

## Efeito
**ShowHide**
- [[DF - CteOcorrencia]]: 3 (esconde mantendo valor)
