---
tipo: aws-lambda
tags: [aws, aws/lambda, regiao/us-east-1, status/inativa]
regiao: us-east-1
runtime: python3.13
status: INATIVA
atualizado: 2026-10-22
fonte: aws-cli + cloudwatch + READMEs (conta 152774997921)
---
# Lambda - prd_ingestion_sqlserver_incremental (us-east-1)

**[INATIVA] Ingestão incremental SQL Server → bronze.**

Hub: [[Hub - AWS Computação]] · [[AWS - Mapa]] · [[AWS - Lambdas (índice)]]

## Quem aciona
- Nenhum.
- Resource policy: nenhuma · event source mappings: 0 · destinos assíncronos: não

## Com o que se liga
- Par de [[Lambda - get_incremental_tables (us-east-1)]]; substituída por [[GlueJob - jdbc_to_bronze (us-east-1)]] e pelas validações [[GlueJob - incremental_tables_validation_n3 (us-east-1)]].
- **Legado — substituída pelo Glue.** O pipeline atual orquestrado pelo Airflow (DAGs `prd_bronze_silver_gold`, `prd_carga_diaria_split_fluxo_datalake`, `prd_jdbc_2_bronze`) usa só `GlueJobOperator` (`jdbc_to_bronze` → `bronze_to_silver` → `silver_to_gold`); nenhuma DAG chama Lambda.

## Uso real (CloudWatch)
- Invocações nos últimos 30 dias: **0** · erros: 0 · último log: 2025-10-08

## Plataforma
- Runtime `python3.13` · 4096 MB · timeout 603s · handler `lambda_function.lambda_handler` · código 2 KB · alterada 2025-10-08
- Role [[IAM - CloudDog-SSO-LambdaExecutionRole-7Q2PH7SEQ48X]]
- VPC [[VPC - cootravale-prod-us-east]] (`vpc-0f65f8acd8195e4bb`) · 2 sub-rede(s) · SG sg-0548773bbdbf5acbc ([[AWS - Rede]])
- Variáveis de ambiente (só chaves): —
- Logs: `/aws/lambda/prd_ingestion_sqlserver_incremental` ([[AWS - Monitoramento]]) · tags AWS: **nenhuma**

## Achados
- Último log 2025-10-08.

## Projetos relacionados
- [[datalake-glue]]
- [[airflow-prod-dags]]

> Evidência: invocações/erros CloudWatch (30 dias), logs, resource policy e DAGs do projeto [[airflow-prod-dags]]. Itens "inferido" não foram confirmados.
