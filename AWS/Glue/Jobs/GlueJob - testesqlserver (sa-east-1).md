---
tipo: aws-glue-job
tags: [aws, aws/glue, regiao/sa-east-1, categoria/teste, ambiente/outro]
regiao: sa-east-1
tipo: glueetl
atualizado: 2026-10-22
fonte: aws-cli (conta 152774997921)
---
# GlueJob - testesqlserver (sa-east-1)

Hub: [[Hub - AWS Dados]] · [[AWS - Glue Jobs]]

- Categoria: teste — teste/sandbox
- Tipo `glueetl` · Glue 4.0 · G.1X × 10
- Role: [[IAM - GlueAthenaToMySQLRole]]
- Script: `s3://aws-glue-assets-152774997921-sa-east-1/scripts/testesqlserver.py`
- Conexões: `sqlserver-cootravale-connection` ([[EC2 - srv-prod-cootravalejobs]])
- Última alteração: 2026-04-17
- Monitorado por EventBridge (falha/timeout): não ([[AWS - Monitoramento]])
- Tags AWS: **nenhuma**

## Fluxo (mapa)
- Conecta em: [[EC2 - srv-prod-cootravalejobs]] (SQL Server)

## Relacionados
- [[datalake-glue]]
