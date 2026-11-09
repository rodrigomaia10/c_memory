---
tipo: otrs-acl
tags: [otrs, otrs/acl]
atualizado: 2026-10-23
fonte: snapshot do repo otrs (ZZZProcessManagement.pm / ZZZACL.pm)
---

# ACL - 3 - Esconde Numero Carga NewKMM-OldKMM

Hub: [[Hub - OTRS ACLs]] · [[Hub - OTRS]] · ordem de execução: alfabética pelo nome, a última que casa por campo vence.

Criada 2025-12-10 19:41:41 (diogo.viana) · alterada 2026-01-22 15:39:52 (diogo.viana) · comentário: 3 - Esconde Numero Carga NewKMM/OldKMM · StopAfterMatch=0

## Quando se aplica (Properties)
- DF [[DF - NewKMMTela]]: `[NotRegExp]^(?:Cancelamento de Carga|Carga|Ocorrência|Atendimento)$`
- DF [[DF - OldKMMTela]]: `[NotRegExp]^(?:Carga)$`

## Efeito
**ShowHide**
- [[DF - NewKMMNumCarga]]: 0 (esconde)
