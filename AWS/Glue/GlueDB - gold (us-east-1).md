---
tipo: aws-glue-database
tags: [aws, aws/glue, parquet, camada/gold, regiao/us-east-1]
tabelas: 11
atualizado: 2026-10-22
fonte: aws-cli (conta 152774997921)
---
# GlueDB - gold (us-east-1)

Hub: [[Hub - AWS]] · [[datalake-glue]] · [[AWS - Athena]] · [[AWS - Glue Jobs]]

- **11 tabelas** — formatos: parquet: 11
- Região: us-east-1 · camada: gold
- Exemplos: dim_calendario, dim_cliente, dim_cooperado, dim_documento, dim_filial, dim_ocorrencia, dim_tipo_documento, dim_tipo_operacao

## Armazenamento (S3)
- [[S3 - cootravale-layer-gold]] — 11 tabelas
- Bucket de camada: [[S3 - cootravale-layer-gold]]

## Fluxo (mapa)
- Escrito por: [[GlueJob - silver_to_gold (us-east-1)]]

## Consumidores
- [[PowerBIClaudio]] · [[Apolo11]] (views Athena)
