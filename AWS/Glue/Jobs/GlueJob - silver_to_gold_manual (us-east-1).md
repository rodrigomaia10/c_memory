---
tipo: aws-glue-job
tags: [aws, aws/glue, regiao/us-east-1, categoria/pipeline-medalhao, ambiente/outro]
regiao: us-east-1
tipo: glueetl
atualizado: 2026-10-22
fonte: aws-cli (conta 152774997921)
---
# GlueJob - silver_to_gold_manual (us-east-1)

Hub: [[Hub - AWS Dados]] · [[AWS - Glue Jobs]]

- Categoria: pipeline-medalhao — bronze/silver/gold em parquet
- Tipo `glueetl` · Glue 5.1 · G.1X × 3
- Role: [[IAM - GlueJobBronzeSilverCatalog]]
- Script: `s3://cootravale-glue/scripts/silver_to_gold_manual.py`
- Conexões: —
- Última alteração: 2026-10-16
- Monitorado por EventBridge (falha/timeout): não ([[AWS - Monitoramento]])
- Tags AWS: **nenhuma**

## Camadas S3 envolvidas
- [[S3 - cootravale-layer-gold]]

## Fluxo (mapa)
- Lê [[GlueDB - prd_silver (us-east-1)]] · escreve [[GlueDB - prd_gold (us-east-1)]]

## Relacionados
- [[datalake-glue]]
- [[dw_aso]]
- [[airflow-prod-dags]]
