---
tipo: aws-lambda
tags: [aws, aws/lambda, regiao/us-east-1, status/inativa]
regiao: us-east-1
runtime: python3.13
status: INATIVA
atualizado: 2026-10-22
fonte: aws-cli + cloudwatch + READMEs (conta 152774997921)
---
# Lambda - get_incremental_tables (us-east-1)

**[INATIVA] Lista as tabelas incrementais do SQL Server (apoio à ingestão).**

Hub: [[Hub - AWS Computação]] · [[AWS - Mapa]] · [[AWS - Lambdas (índice)]]

## Quem aciona
- Nenhum.
- Resource policy: nenhuma · event source mappings: 0 · destinos assíncronos: não

## Com o que se liga
- Usa variáveis `MSSQL_*` (host, usuário, senha, banco).
- Papel hoje coberto pelos jobs de validação [[GlueJob - incremental_tables_validation_n2 (us-east-1)]] / `n3`.
- **Legado — substituída pelo Glue.** O pipeline atual orquestrado pelo Airflow (DAGs `prd_bronze_silver_gold`, `prd_carga_diaria_split_fluxo_datalake`, `prd_jdbc_2_bronze`) usa só `GlueJobOperator` (`jdbc_to_bronze` → `bronze_to_silver` → `silver_to_gold`); nenhuma DAG chama Lambda.

## Uso real (CloudWatch)
- Invocações nos últimos 30 dias: **0** · erros: 0 · último log: 2026-05-30

## Plataforma
- Runtime `python3.13` · 1024 MB · timeout 900s · handler `lambda_function.lambda_handler` · código 1 KB · alterada 2026-05-30
- Role [[IAM - CloudDog-SSO-LambdaExecutionRole-7Q2PH7SEQ48X]]
- VPC [[VPC - cootravale-prod-us-east]] (`vpc-0f65f8acd8195e4bb`) · 1 sub-rede(s) · SG sg-0548773bbdbf5acbc ([[AWS - Rede]])
- Variáveis de ambiente (só chaves): MSSQL_HOST, MSSQL_USER, MSSQL_PORT, MSSQL_PASSWORD, MSSQL_DB
- Logs: `/aws/lambda/get_incremental_tables` ([[AWS - Monitoramento]]) · tags AWS: **nenhuma**

## Achados
- Último log 2026-05-30. **Credenciais SQL Server em texto nas variáveis de ambiente** — mover para Secrets Manager ou remover.

## Projetos relacionados
- [[airflow-prod-dags]]
- [[datalake-glue]]

> Evidência: invocações/erros CloudWatch (30 dias), logs, resource policy e DAGs do projeto [[airflow-prod-dags]]. Itens "inferido" não foram confirmados.
