---
tipo: otrs-acl
tags: [otrs, otrs/acl]
atualizado: 2026-10-23
fonte: snapshot do repo otrs (ZZZProcessManagement.pm / ZZZACL.pm)
---

# ACL - 2- Mostra Numero Registro BRF Processo - DIÁRIA AO DESCARREGAR

Hub: [[Hub - OTRS ACLs]] · [[Hub - OTRS]] · ordem de execução: alfabética pelo nome, a última que casa por campo vence.

Criada 2021-01-11 16:19:05 (samuel.euzebio) · alterada 2026-10-14 14:46:45 (rodrigo.maia) · comentário: Mostra Numero Registro BRF Processo : DIÁRIA AO DESCARREGAR · StopAfterMatch=0

## Quando se aplica (Properties)
- DF [[DF - CteNomePagador]]: `BRF`
- Process.ActivityDialogEntityID: `ActivityDialog-645dce235354bf7b59c721b690b9bc4b`, [[Dialog - Formulario Diaria no Carregamento]], [[Dialog - Formulario Deslocamento]], [[Dialog - Formulário Diária]]
- Process.ProcessEntityID: `Process-ffae7f17de2c0db2c5df95bbf3dd281f`, [[Processo - Chamado Diaria No Carregamento]], [[Processo - Chamado de Deslocamento]], [[Processo - Chamado Diária ao Descarregar]]

## Efeito
**ShowHide**
- [[DF - CteNumeroRegistroBRF]]: 1 (mostra)
