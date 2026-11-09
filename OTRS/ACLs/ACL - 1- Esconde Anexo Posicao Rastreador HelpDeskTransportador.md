---
tipo: otrs-acl
tags: [otrs, otrs/acl]
atualizado: 2026-10-23
fonte: snapshot do repo otrs (ZZZProcessManagement.pm / ZZZACL.pm)
---

# ACL - 1- Esconde Anexo Posicao Rastreador HelpDeskTransportador

Hub: [[Hub - OTRS ACLs]] · [[Hub - OTRS]] · ordem de execução: alfabética pelo nome, a última que casa por campo vence.

Criada 2021-01-11 16:13:44 (samuel.euzebio) · alterada 2026-10-14 15:25:11 (rodrigo.maia) · comentário: Esconde Anexo Posicao Rastreador HelpDeskTransportado · StopAfterMatch=0

## Quando se aplica (Properties)
- Process.ActivityDialogEntityID: [[Dialog - Formulário Diária]], `ActivityDialog-e9eced752f80de08ce7a56dec3b12697`, [[Dialog - Formulario Diaria no Carregamento]], `ActivityDialog-e9eced752f80de08ce7a56dec3b12697`
- Process.ProcessEntityID: [[Processo - Chamado Diária ao Descarregar]], [[Processo - Chamado Diária em Posto Fiscal]], [[Processo - Chamado Diaria No Carregamento]], [[Processo - Chamado Diária Troca de Nota]]

## Efeito
**ShowHide**
- [[DF - CteAnexoPosicaoRastreador]]: 0 (esconde)
