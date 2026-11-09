---
tipo: otrs-acl
tags: [otrs, otrs/acl]
atualizado: 2026-10-23
fonte: snapshot do repo otrs (ZZZProcessManagement.pm / ZZZACL.pm)
---

# ACL - 2- Mostra Campos Chamado

Hub: [[Hub - OTRS ACLs]] · [[Hub - OTRS]] · ordem de execução: alfabética pelo nome, a última que casa por campo vence.

Criada 2021-01-11 16:16:42 (samuel.euzebio) · alterada 2026-10-14 14:47:27 (rodrigo.maia) · comentário: Mostra Campos Chamado · StopAfterMatch=0

## Quando se aplica (Properties)
- DF [[DF - CteDB]]: `[RegExp].`
- DF [[DF - Placa]]: `[RegExp].`
- Process.ActivityDialogEntityID: [[Dialog - Formulário Diária]], [[Dialog - Formulario Deslocamento]], [[Dialog - Formulario Divergencia Valor de Frete]], [[Dialog - Formulario Diária em Posto Fiscal]], [[Dialog - Formulario Diaria no Carregamento]], [[Dialog - Formulario Diária Troca de Nota]], [[Dialog - Formulario  Frete Bloqueado]], [[Dialog - Formulario Pedagio]], [[Dialog - Formulario Recibo de Descarga]], `Activity-1be67e6c0c9b8de86a6fac46eab0119d`, [[Dialog - Formulário Frete Devolução]]
- Process.ProcessEntityID: [[Processo - Chamado Diária ao Descarregar]], [[Processo - Chamado de Deslocamento]], [[Processo - Chamado Recibo de Descarga]], [[Processo - Chamado Divergência Valor de Frete]], [[Processo - Chamado Diária em Posto Fiscal]], [[Processo - Chamado Diaria No Carregamento]], [[Processo - Chamado Diária Troca de Nota]], [[Processo - Chamado Frete Bloqueado]], [[Processo - Chamado Pedágio]], [[Processo - Chamado Frete Devolução]]

## Efeito
**ShowHide**
- [[DF - CteCnpjPagador]]: 2 (obrigatório)
- [[DF - CteDataEmissao]]: 2 (obrigatório)
- [[DF - CteFilial]]: 2 (obrigatório)
- [[DF - CteFilialNome]]: 2 (obrigatório)
- [[DF - CteNomePagador]]: 2 (obrigatório)
- [[DF - CteNumero]]: 2 (obrigatório)
- [[DF - CtePlaca]]: 2 (obrigatório)
- [[DF - CteSerie]]: 2 (obrigatório)
- [[DF - ManifestoData]]: 2 (obrigatório)
- [[DF - ManifestoNumero]]: 2 (obrigatório)
