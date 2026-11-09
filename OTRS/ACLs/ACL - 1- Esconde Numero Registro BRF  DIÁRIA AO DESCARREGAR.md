---
tipo: otrs-acl
tags: [otrs, otrs/acl]
atualizado: 2026-10-23
fonte: snapshot do repo otrs (ZZZProcessManagement.pm / ZZZACL.pm)
---

# ACL - 1- Esconde Numero Registro BRF  DIÁRIA AO DESCARREGAR

Hub: [[Hub - OTRS ACLs]] · [[Hub - OTRS]] · ordem de execução: alfabética pelo nome, a última que casa por campo vence.

Criada 2021-01-11 16:14:43 (samuel.euzebio) · alterada 2026-10-14 14:47:58 (rodrigo.maia) · comentário: Esconde Numero Registro BRF  DIÁRIA AO DESCARREGAR · StopAfterMatch=0

## Quando se aplica (Properties)
- Process.ActivityDialogEntityID: `ActivityDialog-645dce235354bf7b59c721b690b9bc4b`, [[Dialog - Formulario Diaria no Carregamento]], [[Dialog - Formulario Deslocamento]]
- Process.ProcessEntityID: `Process-ffae7f17de2c0db2c5df95bbf3dd281f`, [[Processo - Chamado Diaria No Carregamento]], [[Processo - Chamado de Deslocamento]]

## Efeito
**ShowHide**
- [[DF - CteNumeroRegistroBRF]]: 0 (esconde)
