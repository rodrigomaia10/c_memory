---
tipo: aws-lambda
tags: [aws, aws/lambda, regiao/sa-east-1, status/nunca-usada]
regiao: sa-east-1
runtime: nodejs18.x
status: NUNCA USADA
atualizado: 2026-10-22
fonte: aws-cli + cloudwatch + READMEs (conta 152774997921)
---
# Lambda - presign-canhotos (sa-east-1)

**[NUNCA USADA] Geraria URL pré-assinada para canhotos (inferido pelo nome).**

Hub: [[Hub - AWS Computação]] · [[AWS - Mapa]] · [[AWS - Lambdas (índice)]]

## Quem aciona
- Nenhum (sem Function URL, sem log group).
- Resource policy: nenhuma · event source mappings: 0 · destinos assíncronos: não

## Com o que se liga
- Buckets prováveis: [[S3 - cootravale-canhoto]] e [[S3 - canhotos-genomma]] (inferido).

## Uso real (CloudWatch)
- Invocações nos últimos 30 dias: **0** · erros: 0 · último log: nunca

## Plataforma
- Runtime `nodejs18.x` · 128 MB · timeout 3s · handler `index.handler` · código 1 KB · alterada 2025-08-27
- Role [[IAM - role-presign-canhotos]]
- Fora de VPC
- Variáveis de ambiente (só chaves): —
- Logs: `/aws/lambda/presign-canhotos` ([[AWS - Monitoramento]]) · tags AWS: **nenhuma**

## Achados
- Sem log group = nunca foi invocada. Node 18 fora de suporte.

> Evidência: invocações/erros CloudWatch (30 dias), logs, resource policy e DAGs do projeto [[airflow-prod-dags]]. Itens "inferido" não foram confirmados.
