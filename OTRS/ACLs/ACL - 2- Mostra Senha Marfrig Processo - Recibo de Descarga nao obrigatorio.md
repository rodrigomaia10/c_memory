---
tipo: otrs-acl
tags: [otrs, otrs/acl]
atualizado: 2026-10-23
fonte: snapshot do repo otrs (ZZZProcessManagement.pm / ZZZACL.pm)
---

# ACL - 2- Mostra Senha Marfrig Processo - Recibo de Descarga nao obrigatorio

Hub: [[Hub - OTRS ACLs]] · [[Hub - OTRS]] · ordem de execução: alfabética pelo nome, a última que casa por campo vence.

Criada 2021-01-11 16:19:52 (samuel.euzebio) · alterada 2021-12-23 15:28:51 (gutemberg.souza) · comentário: 2- Mostra Senha Marfrig Processo : Recibo de Descarga nao obrigatorio · StopAfterMatch=0

## Quando se aplica (Properties)
- DF [[DF - CteNomePagador]]: `MARFRIG`
- Process.ActivityDialogEntityID: [[Dialog - Formulario Recibo de Descarga]]
- Process.ProcessEntityID: [[Processo - Chamado Recibo de Descarga]]

## Efeito
**ShowHide**
- [[DF - CteSenhaMarfrig]]: 1 (mostra)
