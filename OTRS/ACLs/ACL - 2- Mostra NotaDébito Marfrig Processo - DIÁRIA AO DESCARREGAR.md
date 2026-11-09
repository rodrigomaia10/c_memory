---
tipo: otrs-acl
tags: [otrs, otrs/acl]
atualizado: 2026-10-23
fonte: snapshot do repo otrs (ZZZProcessManagement.pm / ZZZACL.pm)
---

# ACL - 2- Mostra NotaDébito Marfrig Processo - DIÁRIA AO DESCARREGAR

Hub: [[Hub - OTRS ACLs]] · [[Hub - OTRS]] · ordem de execução: alfabética pelo nome, a última que casa por campo vence.

Criada 2021-01-11 16:17:51 (samuel.euzebio) · alterada 2026-10-14 14:46:55 (rodrigo.maia) · comentário: Mostra NotaDébito Marfrig Processo : DIÁRIA AO DESCARREGAR · StopAfterMatch=0

## Quando se aplica (Properties)
- DF [[DF - CteNomePagador]]: `MARFRIG`
- Process.ActivityDialogEntityID: `ActivityDialog-645dce235354bf7b59c721b690b9bc4b`, [[Dialog - Formulario Recibo de Descarga]], [[Dialog - Formulario Diaria no Carregamento]], [[Dialog - Formulario Deslocamento]]
- Process.ProcessEntityID: `Process-ffae7f17de2c0db2c5df95bbf3dd281f`, [[Processo - Chamado Recibo de Descarga]], [[Processo - Chamado Diaria No Carregamento]], [[Processo - Chamado de Deslocamento]]

## Efeito
**ShowHide**
- [[DF - CteNotaDebitoMarfrig]]: 2 (obrigatório)
