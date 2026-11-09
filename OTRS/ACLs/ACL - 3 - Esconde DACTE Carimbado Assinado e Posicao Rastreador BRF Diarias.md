---
tipo: otrs-acl
tags: [otrs, otrs/acl]
atualizado: 2026-10-23
fonte: snapshot do repo otrs (ZZZProcessManagement.pm / ZZZACL.pm)
---

# ACL - 3 - Esconde DACTE Carimbado Assinado e Posicao Rastreador BRF Diarias

Hub: [[Hub - OTRS ACLs]] · [[Hub - OTRS]] · ordem de execução: alfabética pelo nome, a última que casa por campo vence.

Criada 2021-01-11 16:21:55 (samuel.euzebio) · alterada 2026-10-14 15:50:04 (rodrigo.maia) · comentário: 3 - Esconde DACTE Carimbado Assinado BRF Diarias · StopAfterMatch=0

## Quando se aplica (Properties)
- DF [[DF - CteNomePagador]]: `BRF`
- Process.ProcessEntityID: [[Processo - Chamado Diária ao Descarregar]], [[Processo - Chamado Diária em Posto Fiscal]], [[Processo - Chamado Diaria No Carregamento]], [[Processo - Chamado Diária Troca de Nota]]

## Efeito
**ShowHide**
- [[DF - CteAnexoPosicaoRastreador]]: 0 (esconde)
- [[DF - CteDACTECarimbadoAssinado]]: 0 (esconde)
