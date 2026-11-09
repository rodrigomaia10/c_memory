---
tipo: aws-lambda
tags: [aws, aws/lambda, regiao/us-east-1, status/infra-parceiro]
regiao: us-east-1
runtime: python3.7
status: INFRA PARCEIRO
atualizado: 2026-10-22
fonte: aws-cli + cloudwatch + READMEs (conta 152774997921)
---
# Lambda - CloudDog-SSO-ProviderCreator-bH4kHgsUW9NO (us-east-1)

**[INFRA PARCEIRO] Custom resource do SSO CloudDog (cria o provider SAML) — criada por CloudFormation do parceiro, python3.7.**

Hub: [[Hub - AWS Computação]] · [[AWS - Mapa]] · [[AWS - Lambdas (índice)]]

## Quem aciona
- CloudFormation (uma vez).
- Resource policy: nenhuma · event source mappings: 0 · destinos assíncronos: não

## Com o que se liga
- Sua role `CloudDog-SSO-LambdaExecutionRole-*` foi reaproveitada pelas Lambdas de ingestão ([[AWS - IAM]]).

## Uso real (CloudWatch)
- Invocações nos últimos 30 dias: **0** · erros: 0 · último log: 2022-04-18

## Plataforma
- Runtime `python3.7` · 128 MB · timeout 30s · handler `index.lambda_handler` · código 1 KB · alterada 2022-04-18
- Role [[IAM - CloudDog-SSO-LambdaExecutionRole-7Q2PH7SEQ48X]]
- Fora de VPC
- Variáveis de ambiente (só chaves): —
- Logs: `/aws/lambda/CloudDog-SSO-ProviderCreator-bH4kHgsUW9NO` ([[AWS - Monitoramento]]) · tags AWS: **nenhuma**

## Achados
- Não remover sem alinhar com a CloudDog; python3.7 está fora de suporte.

> Evidência: invocações/erros CloudWatch (30 dias), logs, resource policy e DAGs do projeto [[airflow-prod-dags]]. Itens "inferido" não foram confirmados.
