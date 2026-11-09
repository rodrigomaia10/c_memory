---
tipo: aws-lambda
tags: [aws, aws/lambda, regiao/us-east-1, status/inativa]
regiao: us-east-1
runtime: python3.13
status: INATIVA
atualizado: 2026-10-22
fonte: aws-cli + cloudwatch + READMEs (conta 152774997921)
---
# Lambda - ingestao_tabelas_json (us-east-1)

**[INATIVA] Ingestão de tabelas via JSON (experimento).**

Hub: [[Hub - AWS Computação]] · [[AWS - Mapa]] · [[AWS - Lambdas (índice)]]

## Quem aciona
- Nenhum.
- Resource policy: nenhuma · event source mappings: 0 · destinos assíncronos: não

## Com o que se liga
- Sem VPC; sem vínculo com o pipeline atual.

## Uso real (CloudWatch)
- Invocações nos últimos 30 dias: **0** · erros: 0 · último log: 2025-09-24

## Plataforma
- Runtime `python3.13` · 512 MB · timeout 183s · handler `lambda_function.lambda_handler` · código 1 KB · alterada 2025-09-16
- Role [[IAM - CloudDog-SSO-LambdaExecutionRole-7Q2PH7SEQ48X]]
- Fora de VPC
- Variáveis de ambiente (só chaves): —
- Logs: `/aws/lambda/ingestao_tabelas_json` ([[AWS - Monitoramento]]) · tags AWS: **nenhuma**

## Achados
- Último log 2025-09-24.

## Projetos relacionados
- [[datalake-glue]]

> Evidência: invocações/erros CloudWatch (30 dias), logs, resource policy e DAGs do projeto [[airflow-prod-dags]]. Itens "inferido" não foram confirmados.
