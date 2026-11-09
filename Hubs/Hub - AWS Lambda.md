---
tipo: hub
tags: [hub, dominio/aws, aws/lambda]
atualizado: 2026-10-23
fonte: aws-cli (conta 152774997921)
---
# Hub - AWS Lambda

13 funções; só API_OTRS está ativa. Ingestão prd_ingestion_* é legada (substituída por Glue jdbc_to_bronze via Airflow).

Hub pai: [[Hub - AWS]] · Raiz: [[Cootravale]] · Categoria: [[Hub - AWS Computação]] · [[AWS - Lambdas (índice)]]

## Funções
- [[Lambda - API_OTRS (us-east-1)]]
- [[Lambda - CloudDog-SSO-ProviderCreator-bH4kHgsUW9NO (us-east-1)]]
- [[Lambda - get_incremental_tables (us-east-1)]]
- [[Lambda - ingestao_tabelas_json (us-east-1)]]
- [[Lambda - prd_ingestion_postgres_kmn (us-east-1)]]
- [[Lambda - prd_ingestion_sqlserver_incremental (us-east-1)]]
- [[Lambda - prd_ingestion_sqlserver_tms (sa-east-1)]]
- [[Lambda - prd_ingestion_sqlserver_tms (us-east-1)]]
- [[Lambda - presign-canhotos (sa-east-1)]]
- [[Lambda - test_jdbc_connection (us-east-1)]]
- [[Lambda - teste_con_sqlserver (sa-east-1)]]
- [[Lambda - teste_conn (us-east-1)]]
- [[Lambda - teste_postgres (us-east-1)]]

Índices: [[AWS - EC2 (índice)]] · [[AWS - Lambdas (índice)]]

## Projetos
- [[API_Lambda]] — Lambdas AWS como API; API_OTRS consulta Athena por placa para o OTRS.

## Relacionados
[[Hub - AWS Glue]] · [[Hub - AWS Athena e SageMaker]] · [[otrs]]
