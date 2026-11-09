---
tipo: aws-glue-job
tags: [aws, aws/glue, regiao/us-east-1, categoria/pipeline-medalhao, ambiente/outro]
regiao: us-east-1
tipo: glueetl
atualizado: 2026-10-22
fonte: aws-cli (conta 152774997921)
---
# GlueJob - jdbc_to_bronze_manual (us-east-1)

Hub: [[Hub - AWS Dados]] · [[AWS - Glue Jobs]]

- Categoria: pipeline-medalhao — bronze/silver/gold em parquet
- Tipo `glueetl` · Glue 5.0 · G.1X × 4
- Role: [[IAM - GlueJobBronzeSilverCatalog]]
- Script: `s3://cootravale-glue/scripts/jdbc_to_bronze_manual.py`
- Conexões: `multitms-network` (rede para SQL Azure Nstech (multitms) via VPN)
- Última alteração: 2026-10-21
- Monitorado por EventBridge (falha/timeout): não ([[AWS - Monitoramento]])
- Tags AWS: **nenhuma**

## Camadas S3 envolvidas
- [[S3 - cootravale-layer-bronze-us]]

## Fluxo (mapa)
- Origem: [[Host - SQL Azure multitms (Nstech)]]
- Escreve: [[GlueDB - prd_bronze (us-east-1)]]

## Relacionados
- [[datalake-glue]]
- [[dw_aso]]
- [[airflow-prod-dags]]
