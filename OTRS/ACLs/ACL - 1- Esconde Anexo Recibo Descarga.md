---
tipo: otrs-acl
tags: [otrs, otrs/acl]
atualizado: 2026-10-23
fonte: snapshot do repo otrs (ZZZProcessManagement.pm / ZZZACL.pm)
---

# ACL - 1- Esconde Anexo Recibo Descarga

Hub: [[Hub - OTRS ACLs]] · [[Hub - OTRS]] · ordem de execução: alfabética pelo nome, a última que casa por campo vence.

Criada 2021-01-11 16:13:53 (samuel.euzebio) · alterada 2021-11-03 14:48:45 (samuel.euzebio) · comentário: 1- Esconde Anexo Recibo Descarga · StopAfterMatch=0

## Quando se aplica (Properties)
- Process.ActivityDialogEntityID: [[Dialog - Formulario Recibo de Descarga]]
- Process.ProcessEntityID: [[Processo - Chamado Recibo de Descarga]]

## Efeito
**ShowHide**
- [[DF - AnexoComprovanteEntrega]]: 0 (esconde)
- [[DF - CteAnexoReciboDescarga]]: 0 (esconde)
- [[DF - CteDACTENestle]]: 0 (esconde)
