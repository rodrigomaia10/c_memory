---
tipo: aws-lambda
tags: [aws, aws/lambda, regiao/us-east-1, status/inativa]
regiao: us-east-1
runtime: python3.13
status: INATIVA
atualizado: 2026-10-22
fonte: aws-cli + cloudwatch + READMEs (conta 152774997921)
---
# Lambda - prd_ingestion_postgres_kmn (us-east-1)

**[INATIVA] Ingestão Postgres KMM → bronze (parquet) via JDBC.**

Hub: [[Hub - AWS Computação]] · [[AWS - Mapa]] · [[AWS - Lambdas (índice)]]

## Quem aciona
- Nenhum (sem resource policy nem event source).
- Resource policy: nenhuma · event source mappings: 0 · destinos assíncronos: não

## Com o que se liga
- Fonte: Postgres KMM externo (Nstech) pela VPN [[VPN - nstech-us-east-1]], dentro da VPC us-east-1 (2 sub-redes).
- Destino: [[S3 - cootravale-layer-bronze-us]]. Hoje feito pelo job [[GlueJob - jdbc_to_bronze (us-east-1)]].
- **Legado — substituída pelo Glue.** O pipeline atual orquestrado pelo Airflow (DAGs `prd_bronze_silver_gold`, `prd_carga_diaria_split_fluxo_datalake`, `prd_jdbc_2_bronze`) usa só `GlueJobOperator` (`jdbc_to_bronze` → `bronze_to_silver` → `silver_to_gold`); nenhuma DAG chama Lambda.

## Uso real (CloudWatch)
- Invocações nos últimos 30 dias: **0** · erros: 0 · último log: 2025-11-19

## Plataforma
- Runtime `python3.13` · 10240 MB · timeout 900s · handler `lambda_function.lambda_handler` · código 2 KB · alterada 2025-10-29
- Role [[IAM - CloudDog-SSO-LambdaExecutionRole-7Q2PH7SEQ48X]]
- VPC [[VPC - cootravale-prod-us-east]] (`vpc-0f65f8acd8195e4bb`) · 2 sub-rede(s) · SG sg-0548773bbdbf5acbc ([[AWS - Rede]])
- Variáveis de ambiente (só chaves): —
- Logs: `/aws/lambda/prd_ingestion_postgres_kmn` ([[AWS - Monitoramento]]) · tags AWS: **nenhuma**

## Achados
- Sem execuções nos últimos 30 dias; último log 2025-11-19. Candidata à remoção (mantém ENI na VPC).

## Projetos relacionados
- [[datalake-glue]]
- [[SQL_KMM]]
- [[airflow-prod-dags]]

> Evidência: invocações/erros CloudWatch (30 dias), logs, resource policy e DAGs do projeto [[airflow-prod-dags]]. Itens "inferido" não foram confirmados.
