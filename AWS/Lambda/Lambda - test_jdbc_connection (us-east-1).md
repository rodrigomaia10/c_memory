---
tipo: aws-lambda
tags: [aws, aws/lambda, regiao/us-east-1, status/teste]
regiao: us-east-1
runtime: python3.13
status: TESTE
atualizado: 2026-10-22
fonte: aws-cli + cloudwatch + READMEs (conta 152774997921)
---
# Lambda - test_jdbc_connection (us-east-1)

**[TESTE] Teste de conectividade JDBC Postgres e SQL Server (usa variáveis `POSTGRES_*` e `MSSQL_*`).**

Hub: [[Hub - AWS Computação]] · [[AWS - Mapa]] · [[AWS - Lambdas (índice)]]

## Quem aciona
- Manual.
- Resource policy: nenhuma · event source mappings: 0 · destinos assíncronos: não

## Com o que se liga
- Valida conexões da VPC us-east-1 com [[EC2 - postgres01]] e com o SQL Server de origem.

## Uso real (CloudWatch)
- Invocações nos últimos 30 dias: **0** · erros: 0 · último log: 2026-05-30

## Plataforma
- Runtime `python3.13` · 128 MB · timeout 60s · handler `hello.lambda_handler` · código 1 KB · alterada 2026-05-26
- Role [[IAM - test_jdbc_connection-role-0v84f1a3]]
- VPC [[VPC - cootravale-prod-us-east]] (`vpc-0f65f8acd8195e4bb`) · 1 sub-rede(s) · SG sg-0548773bbdbf5acbc ([[AWS - Rede]])
- Variáveis de ambiente (só chaves): POSTGRES_USER, MSSQL_HOST, POSTGRES_HOST, MSSQL_USER, MSSQL_PORT, POSTGRES_PASSWORD, POSTGRES_PORT, MSSQL_PASSWORD, POSTGRES_DB, MSSQL_DB
- Logs: `/aws/lambda/test_jdbc_connection` ([[AWS - Monitoramento]]) · tags AWS: **nenhuma**

## Achados
- Último log 2026-05-30. **Credenciais Postgres e SQL Server em texto** nas variáveis.

## Projetos relacionados
- [[datalake-glue]]

> Evidência: invocações/erros CloudWatch (30 dias), logs, resource policy e DAGs do projeto [[airflow-prod-dags]]. Itens "inferido" não foram confirmados.
