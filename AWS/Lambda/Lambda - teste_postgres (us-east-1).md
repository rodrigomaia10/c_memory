---
tipo: aws-lambda
tags: [aws, aws/lambda, regiao/us-east-1, status/teste]
regiao: us-east-1
runtime: python3.13
status: TESTE
atualizado: 2026-10-22
fonte: aws-cli + cloudwatch + READMEs (conta 152774997921)
---
# Lambda - teste_postgres (us-east-1)

**[TESTE] Teste de conexão Postgres.**

Hub: [[Hub - AWS Computação]] · [[AWS - Mapa]] · [[AWS - Lambdas (índice)]]

## Quem aciona
- Manual.
- Resource policy: nenhuma · event source mappings: 0 · destinos assíncronos: não

## Com o que se liga
- Sem VPC.

## Uso real (CloudWatch)
- Invocações nos últimos 30 dias: **0** · erros: 0 · último log: 2026-02-18

## Plataforma
- Runtime `python3.13` · 128 MB · timeout 123s · handler `lambda_function.lambda_handler` · código 0 KB · alterada 2025-09-02
- Role [[IAM - CloudDog-SSO-LambdaExecutionRole-7Q2PH7SEQ48X]]
- Fora de VPC
- Variáveis de ambiente (só chaves): —
- Logs: `/aws/lambda/teste_postgres` ([[AWS - Monitoramento]]) · tags AWS: **nenhuma**

## Achados
- Último log 2026-02-18. Pode ser removida.

> Evidência: invocações/erros CloudWatch (30 dias), logs, resource policy e DAGs do projeto [[airflow-prod-dags]]. Itens "inferido" não foram confirmados.
