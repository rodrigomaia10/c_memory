---
tipo: aws-glue-database
tags: [aws, aws/glue, parquet, camada/gold, regiao/us-east-1]
tabelas: 5
atualizado: 2026-10-22
fonte: aws-cli (conta 152774997921)
---
# GlueDB - 3_gold (us-east-1)

Hub: [[Hub - AWS]] · [[datalake-glue]] · [[AWS - Athena]] · [[AWS - Glue Jobs]]

- **5 tabelas** — formatos: parquet: 5
- Região: us-east-1 · camada: gold
- Exemplos: tb_creceber_a_faturar, tb_creceber_bloqueados, tb_creceber_comprovantes, tb_creceber_fatura, tb_cte_sem_vinculo_carga

## Armazenamento (S3)
- [[S3 - cootravale-layer-gold]] — 5 tabelas
- Bucket de camada: [[S3 - cootravale-layer-gold]]

## Fluxo (mapa)
- Escrito por: [[GlueJob - silver_to_gold (us-east-1)]]

## Consumidores
- [[PowerBIClaudio]] · [[Apolo11]] (views Athena)
