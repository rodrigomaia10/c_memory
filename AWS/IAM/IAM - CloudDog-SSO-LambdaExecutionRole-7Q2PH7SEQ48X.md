---
tipo: aws-iam-role
tags: [aws, aws/iam]
atualizado: 2026-10-22
fonte: aws-cli + route53 + sg + projetos locais (conta 152774997921)
---
# IAM - CloudDog-SSO-LambdaExecutionRole-7Q2PH7SEQ48X

Role herdada do SSO CloudDog, reaproveitada pelas Lambdas de ingestão legadas.

Hub: [[Hub - AWS Rede e Segurança]] · [[AWS - IAM]]

## Usada por

**Lambda:**
- [[Lambda - CloudDog-SSO-ProviderCreator-bH4kHgsUW9NO (us-east-1)]]
- [[Lambda - get_incremental_tables (us-east-1)]]
- [[Lambda - ingestao_tabelas_json (us-east-1)]]
- [[Lambda - prd_ingestion_postgres_kmn (us-east-1)]]
- [[Lambda - prd_ingestion_sqlserver_incremental (us-east-1)]]
- [[Lambda - prd_ingestion_sqlserver_tms (sa-east-1)]]
- [[Lambda - prd_ingestion_sqlserver_tms (us-east-1)]]
- [[Lambda - teste_con_sqlserver (sa-east-1)]]
- [[Lambda - teste_conn (us-east-1)]]
- [[Lambda - teste_postgres (us-east-1)]]
