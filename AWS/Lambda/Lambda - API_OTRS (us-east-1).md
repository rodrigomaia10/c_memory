---
tipo: aws-lambda
tags: [aws, aws/lambda, regiao/us-east-1, status/em-uso]
regiao: us-east-1
runtime: python3.12
status: EM USO
atualizado: 2026-10-22
fonte: aws-cli + cloudwatch + READMEs (conta 152774997921)
---
# Lambda - API_OTRS (us-east-1)

**[EM USO] API de consulta por placa para o OTRS: recebe `?placa=` com header `x-api-key` e consulta o Athena (veículo → termo de agregação).**

Hub: [[Hub - AWS Computação]] · [[AWS - Mapa]] · [[AWS - Lambdas (índice)]]

## Quem aciona
- Function URL pública (auth NONE; proteção pela chave `x-api-key` conferida contra a variável `API_KEY`). Chamada pelos formulários do [[otrs]].
- Resource policy: pública (Function URL) · event source mappings: 0 · destinos assíncronos: não

## Com o que se liga
- Consulta o Athena (workgroup `cootravale-s3-athena`, saída em [[S3 - cootravale-athena-rcm]]): hoje `silver_kmn` ([[GlueDB - silver_kmn (us-east-1)]]); migração planejada para [[GlueDB - prd_bronze (us-east-1)]] e [[GlueDB - prd_gold (us-east-1)]] (`dim_cooperado`).
- Consumidor: [[EC2 - srv-prod-otrsapp]] (via [[ALB - cootravale]]/internet). Detalhes e pendências em [[API_Lambda]].
- Não está em VPC (alcança Athena/S3 pela rede pública da AWS).

## Uso real (CloudWatch)
- Invocações nos últimos 30 dias: **206** · erros: 0 · último log: 2026-10-22

## Plataforma
- Runtime `python3.12` · 256 MB · timeout 30s · handler `lambda_function.lambda_handler` · código 1 KB · alterada 2026-10-19
- Role [[IAM - API_OTRS-role-wikqb9wy]]
- Fora de VPC
- Variáveis de ambiente (só chaves): API_KEY
- Logs: `/aws/lambda/API_OTRS` ([[AWS - Monitoramento]]) · tags AWS: **nenhuma**

## Achados
- Única Lambda realmente ativa. Existem 5 roles `API_OTRS-role-*` — só `wikqb9wy` é usada (limpeza em [[AWS - IAM]]). A policy `api_otrs` precisa liberar os buckets bronze/gold quando a query migrar.

## Projetos relacionados
- [[API_Lambda]]
- [[otrs]]
- [[datalake-glue]]

> Evidência: invocações/erros CloudWatch (30 dias), logs, resource policy e DAGs do projeto [[airflow-prod-dags]]. Itens "inferido" não foram confirmados.
