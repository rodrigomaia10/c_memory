---
tipo: aws-indice
tags: [aws, aws/lambda]
atualizado: 2026-10-22
---
# AWS - Lambdas (índice)

Hub: [[Hub - AWS Computação]]

**Resumo:** só `API_OTRS` está em uso; a ingestão migrou das Lambdas para jobs Glue orquestrados pelo Airflow.

| Função | Região | Status | Invoc. 30d | Último log | O que faz |
|---|---|---|---|---|---|
| [[Lambda - API_OTRS (us-east-1)]] | us-east-1 | EM USO | 206 | 2026-10-22 | API de consulta por placa para o OTRS: recebe `?placa=` com header `x-api-key` e consulta o Athena  |
| [[Lambda - prd_ingestion_sqlserver_tms (sa-east-1)]] | sa-east-1 | INATIVA | 0 | 2025-07-17 | Ingestão SQL Server TMS  |
| [[Lambda - presign-canhotos (sa-east-1)]] | sa-east-1 | NUNCA USADA | 0 | nunca | Geraria URL pré-assinada para canhotos  |
| [[Lambda - teste_con_sqlserver (sa-east-1)]] | sa-east-1 | TESTE | 0 | 2025-07-05 | Teste de conexão SQL Server  |
| [[Lambda - CloudDog-SSO-ProviderCreator-bH4kHgsUW9NO (us-east-1)]] | us-east-1 | INFRA PARCEIRO | 0 | 2022-04-18 | Custom resource do SSO CloudDog  |
| [[Lambda - get_incremental_tables (us-east-1)]] | us-east-1 | INATIVA | 0 | 2026-05-30 | Lista as tabelas incrementais do SQL Server  |
| [[Lambda - ingestao_tabelas_json (us-east-1)]] | us-east-1 | INATIVA | 0 | 2025-09-24 | Ingestão de tabelas via JSON  |
| [[Lambda - prd_ingestion_postgres_kmn (us-east-1)]] | us-east-1 | INATIVA | 0 | 2025-11-19 | Ingestão Postgres KMM → bronze  |
| [[Lambda - prd_ingestion_sqlserver_incremental (us-east-1)]] | us-east-1 | INATIVA | 0 | 2025-10-08 | Ingestão incremental SQL Server → bronze. |
| [[Lambda - prd_ingestion_sqlserver_tms (us-east-1)]] | us-east-1 | INATIVA | 0 | 2025-11-19 | Ingestão SQL Server TMS  |
| [[Lambda - test_jdbc_connection (us-east-1)]] | us-east-1 | TESTE | 0 | 2026-05-30 | Teste de conectividade JDBC Postgres e SQL Server  |
| [[Lambda - teste_conn (us-east-1)]] | us-east-1 | TESTE | 0 | 2025-09-01 | Teste de conexão dentro da VPC us-east-1. |
| [[Lambda - teste_postgres (us-east-1)]] | us-east-1 | TESTE | 0 | 2026-02-18 | Teste de conexão Postgres. |

Log group órfão: `/aws/lambda/intc_conhecimento_receber_amrt` (função removida; role `intc_conhecimento_receber_amrt-role-fv9yyfu2` ainda existe).
