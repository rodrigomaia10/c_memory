---
tipo: otrs-acl
tags: [otrs, otrs/acl]
atualizado: 2026-10-23
fonte: snapshot do repo otrs (ZZZProcessManagement.pm / ZZZACL.pm)
---

# ACL - 2- Mostra CteSenhaBRF Processo - DESLOCAMENTO

Hub: [[Hub - OTRS ACLs]] · [[Hub - OTRS]] · ordem de execução: alfabética pelo nome, a última que casa por campo vence.

Criada 2021-01-11 16:17:14 (samuel.euzebio) · alterada 2021-01-12 15:21:09 (samuel.euzebio) · comentário: Mostra CteSenhaBRF Processo : DESLOCAMENTO · StopAfterMatch=0

## Quando se aplica (Properties)
- DF [[DF - CteNomePagador]]: `BRF`
- Process.ActivityDialogEntityID: [[Dialog - Formulario Deslocamento]]
- Process.ProcessEntityID: [[Processo - Chamado de Deslocamento]]

## Efeito
**ShowHide**
- [[DF - CteCETBRF]]: 2 (obrigatório)
- [[DF - CteSenhaBRF]]: 2 (obrigatório)
