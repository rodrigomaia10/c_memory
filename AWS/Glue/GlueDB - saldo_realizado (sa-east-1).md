---
tipo: aws-glue-database
tags: [aws, aws/glue, parquet, camada/outros, regiao/sa-east-1]
tabelas: 1
atualizado: 2026-10-22
fonte: aws-cli (conta 152774997921)
---
# GlueDB - saldo_realizado (sa-east-1)

Hub: [[Hub - AWS]] · [[datalake-glue]] · [[AWS - Athena]] · [[AWS - Glue Jobs]]

- **1 tabelas** — formatos: parquet: 1
- Região: sa-east-1 · camada: outros
- Exemplos: f_realizado

## Armazenamento (S3)
- [[S3 - cootravale-infrabi-consumer]] — 1 tabelas

Região legada (pré-migração para us-east-1): catálogo da stack infrabi.

## Fluxo (mapa)
- Catalogado pelo crawler `teste_saldo_realizado` ([[AWS - Glue Crawlers e Conexões]])

## Consumidores
- [[PowerBIClaudio]] · [[Apolo11]] (views Athena)
