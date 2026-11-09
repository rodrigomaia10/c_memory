---
tipo: aws-glue-database
tags: [aws, aws/glue, parquet, camada/outros, regiao/sa-east-1]
tabelas: 6
atualizado: 2026-10-22
fonte: aws-cli (conta 152774997921)
---
# GlueDB - taxa (sa-east-1)

Hub: [[Hub - AWS]] · [[datalake-glue]] · [[AWS - Athena]] · [[AWS - Glue Jobs]]

- **6 tabelas** — formatos: parquet: 4, view: 2
- Região: sa-east-1 · camada: outros
- Exemplos: f_faturamento_taxas, f_taxa, f_taxa_part_0_parquet, full_result_parquet, vw_faturamento_por_razao_social_mes, vw_frete_beneficios_por_transportador

## Armazenamento (S3)
- [[S3 - cootravale-infrabi-staging]] — 4 tabelas

Região legada (pré-migração para us-east-1): catálogo da stack infrabi.

## Fluxo (mapa)
- Catalogado pelo crawler `DimTaxas` ([[AWS - Glue Crawlers e Conexões]])
- Catalogado pelo crawler `f_faturamento_taxas` ([[AWS - Glue Crawlers e Conexões]])

## Consumidores
- [[PowerBIClaudio]] · [[Apolo11]] (views Athena)
