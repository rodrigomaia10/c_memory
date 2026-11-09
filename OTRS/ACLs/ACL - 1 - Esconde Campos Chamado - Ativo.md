---
tipo: otrs-acl
tags: [otrs, otrs/acl]
atualizado: 2026-10-23
fonte: snapshot do repo otrs (ZZZProcessManagement.pm / ZZZACL.pm)
---

# ACL - 1 - Esconde Campos Chamado - Ativo

Hub: [[Hub - OTRS ACLs]] · [[Hub - OTRS]] · ordem de execução: alfabética pelo nome, a última que casa por campo vence.

Criada 2021-01-11 16:13:31 (samuel.euzebio) · alterada 2026-10-15 10:30:54 (rodrigo.maia) · comentário: 1 - Esconde Campos Chamado - Ativo · StopAfterMatch=0

## Quando se aplica (Properties)
- Frontend.Action: `AgentTicketProcess`, `CustomerTicketProcess`, `NewTicketProcess`
- Process.ProcessEntityID: [[Processo - Chamado Diária ao Descarregar]], [[Processo - Chamado de Deslocamento]], [[Processo - Chamado Recibo de Descarga]], [[Processo - Chamado Divergência Valor de Frete]], [[Processo - Chamado Diária em Posto Fiscal]], [[Processo - Chamado Diaria No Carregamento]], [[Processo - Chamado Diária Troca de Nota]], [[Processo - Chamado Frete Bloqueado]], [[Processo - Chamado Pedágio]], [[Processo - Chamado Frete Devolução]], [[Processo - Chamado Diária na Devolução]]

## Efeito
**ShowHide**
- `CteDACTECarimbadoAssinado`: 0 (esconde)
- [[DF - CteAnexoCETBRF]]: 0 (esconde)
- [[DF - CteAnexoPosicaoRastreador]]: 0 (esconde)
- [[DF - CteCETBRF]]: 0 (esconde)
- [[DF - CteClienteTipoNestle]]: 0 (esconde)
- [[DF - CteCnpjPagador]]: 3 (esconde mantendo valor)
- [[DF - CteDACTECarimbadoAssinado]]: 3 (esconde mantendo valor)
- [[DF - CteDACTENestle]]: 0 (esconde)
- [[DF - CteDataEmissao]]: 3 (esconde mantendo valor)
- [[DF - CteFilial]]: 3 (esconde mantendo valor)
- [[DF - CteFilialNome]]: 3 (esconde mantendo valor)
- [[DF - CteNomePagador]]: 3 (esconde mantendo valor)
- [[DF - CteNumero]]: 3 (esconde mantendo valor)
- [[DF - CteOcorrencia]]: 2 (obrigatório)
- [[DF - CtePlaca]]: 3 (esconde mantendo valor)
- [[DF - CteSenhaMarfrig]]: 0 (esconde)
- [[DF - CteSerie]]: 3 (esconde mantendo valor)
- [[DF - CteValor]]: 3 (esconde mantendo valor)
- [[DF - ManifestoData]]: 3 (esconde mantendo valor)
- [[DF - ManifestoNumero]]: 3 (esconde mantendo valor)
- [[DF - NotaFiscalCarregamento]]: 3 (esconde mantendo valor)
- [[DF - PagoTransportador]]: 3 (esconde mantendo valor)
