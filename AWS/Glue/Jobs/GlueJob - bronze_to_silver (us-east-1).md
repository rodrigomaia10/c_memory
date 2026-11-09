---
tipo: aws-glue-job
tags: [aws, aws/glue, regiao/us-east-1, categoria/pipeline-medalhao, ambiente/prod]
regiao: us-east-1
tipo: glueetl
atualizado: 2026-10-22
fonte: aws-cli (conta 152774997921)
---
# GlueJob - bronze_to_silver (us-east-1)

Hub: [[Hub - AWS Dados]] · [[AWS - Glue Jobs]]

- Categoria: pipeline-medalhao — bronze/silver/gold em parquet
- Tipo `glueetl` · Glue 5.0 · G.1X × 3
- Role: [[IAM - GlueJobBronzeSilverCatalog]]
- Script: `s3://cootravale-glue/scripts/bronze_to_silver.py`
- Conexões: —
- Última alteração: 2026-10-03
- Monitorado por EventBridge (falha/timeout): **sim** ([[AWS - Monitoramento]])
- Tags AWS: **nenhuma**

## Camadas S3 envolvidas
- [[S3 - cootravale-layer-silver-us]]

## Fluxo (mapa)
- Orquestrado por [[EC2 - srv-prod-airflow]] (DAGs com GlueJobOperator) — [[airflow-prod-dags]]
- Lê [[GlueDB - prd_bronze (us-east-1)]] · escreve [[GlueDB - prd_silver (us-east-1)]]

## Relacionados
- [[datalake-glue]]
- [[dw_aso]]
- [[airflow-prod-dags]]
