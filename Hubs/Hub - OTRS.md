---
tipo: hub
tags: [hub, dominio/suporte, otrs]
atualizado: 2026-10-23
fonte: snapshot do repo otrs (ZZZProcessManagement.pm / ZZZACL.pm)
---
# Hub - OTRS

OTRS/Znuny da Cootravale (produção): estrutura de processos, ACLs, filas, serviços e campos. Snapshot do repo `C:\project\otrs` (espelho da prod); a lista completa de filas/serviços, SLAs, grupos e tipos ainda exige leitura do banco.

Raiz: [[Cootravale]] · [[Hub - Suporte OTRS]] · projeto [[otrs]] · API [[Lambda - API_OTRS (us-east-1)]] ([[API_Lambda]])

## Estrutura
- [[Hub - OTRS Processos]] — 44 processos (29 ativos), 63 diálogos
- [[Hub - OTRS ACLs]] — 113 ACLs
- [[Hub - OTRS Filas e Serviços]] — 9 filas, 155 serviços, 9 SLAs referenciados
- [[Hub - OTRS Dynamic Fields]] — 210 campos

## Infraestrutura
- [[EC2 - srv-prod-otrsapp]] (Apache/Znuny) · [[EC2 - srv-prod-postgresql]] (MySQL otrs) · [[ALB - cootravale]] · [[Host - otrsdb (sem instância)]]
- Autenticação LDAP: [[EC2 - Srv_AD02]]

## Log
- 2026-10-23 — nós gerados do snapshot do repo (ZZZProcessManagement.pm + ZZZACL.pm); pendente: banco (filas, serviços, SLAs, tipos, grupos, DFs).
