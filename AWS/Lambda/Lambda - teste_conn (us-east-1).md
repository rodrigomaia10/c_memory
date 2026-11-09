---
tipo: aws-lambda
tags: [aws, aws/lambda, regiao/us-east-1, status/teste]
regiao: us-east-1
runtime: python3.13
status: TESTE
atualizado: 2026-10-22
fonte: aws-cli + cloudwatch + READMEs (conta 152774997921)
---
# Lambda - teste_conn (us-east-1)

**[TESTE] Teste de conexão dentro da VPC us-east-1.**

Hub: [[Hub - AWS Computação]] · [[AWS - Mapa]] · [[AWS - Lambdas (índice)]]

## Quem aciona
- Manual.
- Resource policy: nenhuma · event source mappings: 0 · destinos assíncronos: não

## Com o que se liga
- SG compartilhado das Lambdas da VPC.

## Uso real (CloudWatch)
- Invocações nos últimos 30 dias: **0** · erros: 0 · último log: 2025-09-01

## Plataforma
- Runtime `python3.13` · 512 MB · timeout 123s · handler `lambda_function.lambda_handler` · código 0 KB · alterada 2026-02-18
- Role [[IAM - CloudDog-SSO-LambdaExecutionRole-7Q2PH7SEQ48X]]
- VPC [[VPC - cootravale-prod-us-east]] (`vpc-0f65f8acd8195e4bb`) · 1 sub-rede(s) · SG sg-0548773bbdbf5acbc ([[AWS - Rede]])
- Variáveis de ambiente (só chaves): —
- Logs: `/aws/lambda/teste_conn` ([[AWS - Monitoramento]]) · tags AWS: **nenhuma**

## Achados
- Último log 2025-09-01. Pode ser removida.

> Evidência: invocações/erros CloudWatch (30 dias), logs, resource policy e DAGs do projeto [[airflow-prod-dags]]. Itens "inferido" não foram confirmados.
