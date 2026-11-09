---
tipo: aws-glue-database
tags: [aws, aws/glue, parquet, camada/outros, regiao/sa-east-1]
tabelas: 23
atualizado: 2026-10-22
fonte: aws-cli (conta 152774997921)
---
# GlueDB - faturamento (sa-east-1)

Hub: [[Hub - AWS]] · [[datalake-glue]] · [[AWS - Athena]] · [[AWS - Glue Jobs]]

- **23 tabelas** — formatos: parquet: 12, view: 11
- Região: sa-east-1 · camada: outros
- Exemplos: dimcfop, dimcontrato, dimcontratofretededicado, dimcooperado, dimcte, dimdedicado, dimnotafiscal, dimtipocooperado

## Armazenamento (S3)
- [[S3 - cootravale-infrabi-consumer]] — 12 tabelas

Região legada (pré-migração para us-east-1): catálogo da stack infrabi.

## Fluxo (mapa)
- Catalogado pelo crawler `get_faturamento` ([[AWS - Glue Crawlers e Conexões]])

## Consumidores
- [[PowerBIClaudio]] · [[Apolo11]] (views Athena)
