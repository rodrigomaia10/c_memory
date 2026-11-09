---
tipo: otrs-acl
tags: [otrs, otrs/acl]
atualizado: 2026-10-23
fonte: snapshot do repo otrs (ZZZProcessManagement.pm / ZZZACL.pm)
---

# ACL - 2 - Mostra Anexo Comprovante de Entrega - Recibo de Descarga

Hub: [[Hub - OTRS ACLs]] · [[Hub - OTRS]] · ordem de execução: alfabética pelo nome, a última que casa por campo vence.

Criada 2021-10-29 10:27:25 (rodrigo.maia) · alterada 2021-11-03 10:25:07 (samuel.euzebio) · comentário: 2 - Mostra Anexo Comprovante de Entrega · StopAfterMatch=0

## Quando se aplica (Properties)
- DF [[DF - CteNomePagador]]: `FINI`, `M DIAS BRANCO`, `GENOMMA`
- Process.ActivityDialogEntityID: [[Dialog - Formulario Recibo de Descarga]]
- Process.ProcessEntityID: [[Processo - Chamado Recibo de Descarga]]

## Efeito
**ShowHide**
- [[DF - AnexoComprovanteEntrega]]: 2 (obrigatório)
