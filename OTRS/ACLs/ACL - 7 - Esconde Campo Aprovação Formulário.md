---
tipo: otrs-acl
tags: [otrs, otrs/acl]
atualizado: 2026-10-23
fonte: snapshot do repo otrs (ZZZProcessManagement.pm / ZZZACL.pm)
---

# ACL - 7 - Esconde Campo Aprovação Formulário

Hub: [[Hub - OTRS ACLs]] · [[Hub - OTRS]] · ordem de execução: alfabética pelo nome, a última que casa por campo vence.

StopAfterMatch=0

## Quando se aplica (Properties)
- Process.ActivityDialogEntityID: [[Dialog - 2 - Formulário Controle Atividade Frota]]
- Process.ProcessEntityID: [[Processo - Chamado Pesquisa Novo Cavalo (Melhoria - Teste) - Inativo]]
- Ticket.State: `open`

## Efeito
**ShowHide**
- [[DF - ControleAprovacaoFrota]]: 0 (esconde)
