---
tipo: aws-lambda
tags: [aws, aws/lambda, regiao/sa-east-1, status/inativa]
regiao: sa-east-1
runtime: python3.13
status: INATIVA
atualizado: 2026-10-22
fonte: aws-cli + cloudwatch + READMEs (conta 152774997921)
---
# Lambda - prd_ingestion_sqlserver_tms (sa-east-1)

**[INATIVA] Ingestão SQL Server TMS (multitms) → bronze (parquet). (cópia antiga em sa-east-1)**

Hub: [[Hub - AWS Computação]] · [[AWS - Mapa]] · [[AWS - Lambdas (índice)]]

## Quem aciona
- Nenhum.
- Resource policy: nenhuma · event source mappings: 0 · destinos assíncronos: não

## Com o que se liga
- Cópia da época do datalake em sa-east-1 ([[AWS - Rede]] VPC cootravale-01). Último log 2025-07-17.
- **Legado — substituída pelo Glue.** O pipeline atual orquestrado pelo Airflow (DAGs `prd_bronze_silver_gold`, `prd_carga_diaria_split_fluxo_datalake`, `prd_jdbc_2_bronze`) usa só `GlueJobOperator` (`jdbc_to_bronze` → `bronze_to_silver` → `silver_to_gold`); nenhuma DAG chama Lambda.

## Uso real (CloudWatch)
- Invocações nos últimos 30 dias: **0** · erros: 0 · último log: 2025-07-17

## Plataforma
- Runtime `python3.13` · 4096 MB · timeout 900s · handler `lambda_function.lambda_handler` · código 1 KB · alterada 2025-07-06
- Role [[IAM - CloudDog-SSO-LambdaExecutionRole-7Q2PH7SEQ48X]]
- VPC [[VPC - cootravale-02]] (`vpc-00b4c0dd1d14c8eb3`) · 2 sub-rede(s) · SG sg-00bc4f61843832214 ([[AWS - Rede]])
- Variáveis de ambiente (só chaves): —
- Logs: `/aws/lambda/prd_ingestion_sqlserver_tms` ([[AWS - Monitoramento]]) · tags AWS: **nenhuma**

## Achados
- Legado de 2025-07; remover.

## Projetos relacionados
- [[datalake-glue]]
- [[airflow-prod-dags]]

> Evidência: invocações/erros CloudWatch (30 dias), logs, resource policy e DAGs do projeto [[airflow-prod-dags]]. Itens "inferido" não foram confirmados.
