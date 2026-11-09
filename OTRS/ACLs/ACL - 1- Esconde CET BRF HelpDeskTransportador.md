---
tipo: otrs-acl
tags: [otrs, otrs/acl]
atualizado: 2026-10-23
fonte: snapshot do repo otrs (ZZZProcessManagement.pm / ZZZACL.pm)
---

# ACL - 1- Esconde CET BRF HelpDeskTransportador

Hub: [[Hub - OTRS ACLs]] · [[Hub - OTRS]] · ordem de execução: alfabética pelo nome, a última que casa por campo vence.

Criada 2021-01-11 16:14:11 (samuel.euzebio) · alterada 2021-01-11 16:14:11 (samuel.euzebio) · comentário: Esconde CET BRF HelpDeskTransportador · StopAfterMatch=0

## Quando se aplica (Properties)
- Process.ActivityDialogEntityID: [[Dialog - Formulário Diária]], [[Dialog - Formulario Diária em Posto Fiscal]], [[Dialog - Formulario Diária Troca de Nota]]
- Process.ProcessEntityID: [[Processo - Chamado Diária ao Descarregar]], [[Processo - Chamado Diária em Posto Fiscal]], [[Processo - Chamado Diária Troca de Nota]]

## Efeito
**ShowHide**
- [[DF - CteAnexoCETBRF]]: 0 (esconde)
- [[DF - CteCETBRF]]: 0 (esconde)
