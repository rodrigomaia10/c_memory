---
tipo: otrs-acl
tags: [otrs, otrs/acl]
atualizado: 2026-10-23
fonte: snapshot do repo otrs (ZZZProcessManagement.pm / ZZZACL.pm)
---

# ACL - 4- Esconde Serviços Cootravale para  Edukar dos usuarios Geral

Hub: [[Hub - OTRS ACLs]] · [[Hub - OTRS]] · ordem de execução: alfabética pelo nome, a última que casa por campo vence.

StopAfterMatch=0

## Quando se aplica (Properties)
- CustomerUser.Group_rw: `EDUKAR Cliente`

## Efeito
- PossibleNot Ticket.Service: [[Servico - CRC]], [[Servico - Comercial]], [[Servico - Emissao Contraturno MultiTMS]], [[Servico - Ficha Matrícula]], [[Servico - GR]], [[Servico - Jurídico Cootravale]], [[Servico - Jurídico Cristofolini]], [[Servico - Logística Operações]], [[Servico - Marketing]], [[Servico - Monitoramento - Torre de Controle]], [[Servico - Qualidade]], [[Servico - Supervisão de Frota]], [[Servico - Viagens]]
