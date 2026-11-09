---
tipo: aws-glue-database
tags: [aws, aws/glue, parquet, camada/silver, regiao/us-east-1]
tabelas: 15
atualizado: 2026-10-22
fonte: aws-cli (conta 152774997921)
---
# GlueDB - hml_silver (us-east-1)

Hub: [[Hub - AWS]] · [[datalake-glue]] · [[AWS - Athena]] · [[AWS - Glue Jobs]]

- **15 tabelas** — formatos: parquet: 15
- Região: us-east-1 · camada: silver
- Exemplos: carga_cte, carga_ocorrencia, cte, custos_rateados, historico_finalizacao, log_alteracao_modalidade, ocorrencia, operacional_carga

## Armazenamento (S3)
- [[S3 - cootravale-layer-silver-us]] — 15 tabelas
- Bucket de camada: [[S3 - cootravale-layer-silver-us]]

## Fluxo (mapa)
- Escrito por: [[GlueJob - bronze_to_silver_manual (us-east-1)]]

## Consumidores
- [[PowerBIClaudio]] · [[Apolo11]] (views Athena)
