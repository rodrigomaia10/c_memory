---
tipo: aws-glue-database
tags: [aws, aws/glue, parquet, camada/gold, regiao/us-east-1]
tabelas: 98
atualizado: 2026-10-22
fonte: aws-cli (conta 152774997921)
---
# GlueDB - hml_gold (us-east-1)

Hub: [[Hub - AWS]] · [[datalake-glue]] · [[AWS - Athena]] · [[AWS - Glue Jobs]]

- **98 tabelas** — formatos: parquet: 75, view: 23
- Região: us-east-1 · camada: gold
- Exemplos: dim_calendario, dim_cliente, dim_cooperado, dim_cooperado_cadastro, dim_documento, dim_emissor_cte, dim_filial, dim_local_armazenamento

## Armazenamento (S3)
- [[S3 - cootravale-layer-gold]] — 81 tabelas
- Bucket de camada: [[S3 - cootravale-layer-gold]]

## Fluxo (mapa)
- Escrito por: [[GlueJob - silver_to_gold_manual (us-east-1)]]

## Consumidores
- [[PowerBIClaudio]] · [[Apolo11]] (views Athena)
