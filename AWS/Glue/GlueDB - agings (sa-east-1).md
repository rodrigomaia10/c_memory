---
tipo: aws-glue-database
tags: [aws, aws/glue, parquet, camada/outros, regiao/sa-east-1]
tabelas: 18
atualizado: 2026-10-22
fonte: aws-cli (conta 152774997921)
---
# GlueDB - agings (sa-east-1)

Hub: [[Hub - AWS]] · [[datalake-glue]] · [[AWS - Athena]] · [[AWS - Glue Jobs]]

- **18 tabelas** — formatos: parquet: 10, view: 8
- Região: sa-east-1 · camada: outros
- Exemplos: bloqueados, f_a_faturar, f_a_vencer, f_adr, f_cenarios, f_demais_portadores, f_pdd_sem_faturar, f_vencidos

## Armazenamento (S3)
- [[S3 - cootravale-infrabi-consumer]] — 10 tabelas

Região legada (pré-migração para us-east-1): catálogo da stack infrabi.

## Fluxo (mapa)
- Catalogado pelo crawler `get_agings` ([[AWS - Glue Crawlers e Conexões]])

## Consumidores
- [[PowerBIClaudio]] · [[Apolo11]] (views Athena)
