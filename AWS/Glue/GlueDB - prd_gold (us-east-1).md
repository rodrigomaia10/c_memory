---
tipo: aws-glue-database
tags: [aws, aws/glue, parquet, camada/gold, regiao/us-east-1]
tabelas: 60
atualizado: 2026-10-22
fonte: aws-cli (conta 152774997921)
---
# GlueDB - prd_gold (us-east-1)

Hub: [[Hub - AWS]] · [[datalake-glue]] · [[AWS - Athena]] · [[AWS - Glue Jobs]]

- **60 tabelas** — formatos: parquet: 32, view: 26, LazySimpleSerDe: 2
- Região: us-east-1 · camada: gold
- Exemplos: dim_calendario, dim_cliente, dim_cooperado, dim_documento, dim_emissor_cte, dim_filial, dim_local_armazenamento, dim_modelo_veicular

## Armazenamento (S3)
- [[S3 - cootravale-layer-gold]] — 32 tabelas
- [[S3 - cootravale-infrabi-staging]] — 2 tabelas
- Bucket de camada: [[S3 - cootravale-layer-gold]]

## Fluxo (mapa)
- Escrito por: [[GlueJob - silver_to_gold (us-east-1)]]

## Consumidores
- [[PowerBIClaudio]] · [[Apolo11]] (views Athena)
