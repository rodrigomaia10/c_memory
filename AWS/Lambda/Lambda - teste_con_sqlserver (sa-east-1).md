---
tipo: aws-lambda
tags: [aws, aws/lambda, regiao/sa-east-1, status/teste]
regiao: sa-east-1
runtime: python3.13
status: TESTE
atualizado: 2026-10-22
fonte: aws-cli + cloudwatch + READMEs (conta 152774997921)
---
# Lambda - teste_con_sqlserver (sa-east-1)

**[TESTE] Teste de conexão SQL Server (sa-east-1).**

Hub: [[Hub - AWS Computação]] · [[AWS - Mapa]] · [[AWS - Lambdas (índice)]]

## Quem aciona
- Manual.
- Resource policy: nenhuma · event source mappings: 0 · destinos assíncronos: não

## Com o que se liga
- Alvo provável: [[EC2 - srv-prod-cootravalejobs]] (SQL Server).

## Uso real (CloudWatch)
- Invocações nos últimos 30 dias: **0** · erros: 0 · último log: 2025-07-05

## Plataforma
- Runtime `python3.13` · 128 MB · timeout 123s · handler `lambda_function.lambda_handler` · código 0 KB · alterada 2025-07-05
- Role [[IAM - CloudDog-SSO-LambdaExecutionRole-7Q2PH7SEQ48X]]
- VPC [[VPC - cootravale-02]] (`vpc-00b4c0dd1d14c8eb3`) · 2 sub-rede(s) · SG sg-00bc4f61843832214 ([[AWS - Rede]])
- Variáveis de ambiente (só chaves): DB_USERNAME, DB_PORT, DB_DATABASE, DB_HOSTNAME, DB_PASSWORD
- Logs: `/aws/lambda/teste_con_sqlserver` ([[AWS - Monitoramento]]) · tags AWS: **nenhuma**

## Achados
- Último log 2025-07-05; **credenciais em texto** nas variáveis. Remover.

> Evidência: invocações/erros CloudWatch (30 dias), logs, resource policy e DAGs do projeto [[airflow-prod-dags]]. Itens "inferido" não foram confirmados.
