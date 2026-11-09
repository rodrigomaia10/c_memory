---
tipo: aws-glue-job
tags: [aws, aws/glue, regiao/sa-east-1, categoria/carga-portal, ambiente/outro]
regiao: sa-east-1
tipo: glueetl
atualizado: 2026-10-22
fonte: aws-cli (conta 152774997921)
---
# GlueJob - Lista_Operacional (sa-east-1)

Hub: [[Hub - AWS Dados]] · [[AWS - Glue Jobs]]

- Categoria: carga-portal — Athena → portal (MySQL/SQL Server)
- Tipo `glueetl` · Glue 4.0 · G.1X × 5
- Role: [[IAM - GlueAthenaToMySQLRole]]
- Script: `s3://cootravale-glue/scripts/Lista_Operacional.py`
- Conexões: `sqlserver-cootravale-connection` ([[EC2 - srv-prod-cootravalejobs]])
- Última alteração: 2026-04-24
- Monitorado por EventBridge (falha/timeout): não ([[AWS - Monitoramento]])
- Tags AWS: **nenhuma**

## Fluxo (mapa)
- Conecta em: [[EC2 - srv-prod-cootravalejobs]] (SQL Server)

## Relacionados
- [[Portal]]
- [[datalake-glue]]
