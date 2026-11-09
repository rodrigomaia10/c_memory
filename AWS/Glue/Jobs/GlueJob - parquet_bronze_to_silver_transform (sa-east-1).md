---
tipo: aws-glue-job
tags: [aws, aws/glue, regiao/sa-east-1, categoria/pipeline-medalhao, ambiente/outro]
regiao: sa-east-1
tipo: glueetl
atualizado: 2026-10-22
fonte: aws-cli (conta 152774997921)
---
# GlueJob - parquet_bronze_to_silver_transform (sa-east-1)

Hub: [[Hub - AWS Dados]] · [[AWS - Glue Jobs]]

- Categoria: pipeline-medalhao — bronze/silver/gold em parquet
- Tipo `glueetl` · Glue 5.0 · G.1X × 2
- Role: [[IAM - GlueJobBronzeSilverCatalog]]
- Script: `s3://cootravale-glue/scripts/parquet_bronze_to_silver_transform.py`
- Conexões: —
- Última alteração: 2025-07-06
- Monitorado por EventBridge (falha/timeout): não ([[AWS - Monitoramento]])
- Tags AWS: **nenhuma**

## Camadas S3 envolvidas
- [[S3 - cootravale-layer-silver-us]]

## Relacionados
- [[datalake-glue]]
- [[dw_aso]]
- [[airflow-prod-dags]]
