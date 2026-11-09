---
tipo: aws-glue-database
tags: [aws, aws/glue, parquet, camada/silver, regiao/us-east-1]
tabelas: 18
atualizado: 2026-10-22
fonte: aws-cli (conta 152774997921)
---
# GlueDB - prd_silver (us-east-1)

Hub: [[Hub - AWS]] · [[datalake-glue]] · [[AWS - Athena]] · [[AWS - Glue Jobs]]

- **18 tabelas** — formatos: parquet: 18
- Região: us-east-1 · camada: silver
- Exemplos: aging, carga_cte, carga_ocorrencia, cte, custos_rateados, kmm_beneficios_abastecimento, kmm_beneficios_lancamentos, kmm_estoque_lancamentos

## Armazenamento (S3)
- [[S3 - cootravale-layer-silver-us]] — 17 tabelas
- [[S3 - cootravale-layer-silver]] — 1 tabelas
- Bucket de camada: [[S3 - cootravale-layer-silver-us]]

## Fluxo (mapa)
- Escrito por: [[GlueJob - bronze_to_silver (us-east-1)]]

## Consumidores
- [[PowerBIClaudio]] · [[Apolo11]] (views Athena)
