---
tipo: aws-glue-job
tags: [aws, aws/glue, regiao/us-east-1, categoria/carga-portal, ambiente/outro]
regiao: us-east-1
tipo: glueetl
atualizado: 2026-10-22
fonte: aws-cli (conta 152774997921)
---
# GlueJob - Portal_Beneficios (us-east-1)

Hub: [[Hub - AWS Dados]] · [[AWS - Glue Jobs]]

- Categoria: carga-portal — Athena → portal (MySQL/SQL Server)
- Tipo `glueetl` · Glue 5.1 · G.1X × 10
- Role: [[IAM - GlueAthenaToMySQLRole]]
- Script: `s3://aws-glue-assets-152774997921-us-east-1/scripts/Portal_Beneficios.py`
- Conexões: `Jdbc connection - multitms` (SQL Azure Nstech (multitms))
- Última alteração: 2026-10-20
- Monitorado por EventBridge (falha/timeout): não ([[AWS - Monitoramento]])
- Tags AWS: **nenhuma**

## Fluxo (mapa)
- Origem: [[Host - SQL Azure multitms (Nstech)]]
- Lê o gold ([[GlueDB - prd_gold (us-east-1)]]) e entrega ao portal ([[EC2 - srv-prod-cootravalejobs]]) — inferido pelo nome/role

## Relacionados
- [[Portal]]
- [[datalake-glue]]
