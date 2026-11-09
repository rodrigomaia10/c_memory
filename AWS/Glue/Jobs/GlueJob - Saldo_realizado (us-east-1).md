---
tipo: aws-glue-job
tags: [aws, aws/glue, regiao/us-east-1, categoria/carga-portal, ambiente/prod]
regiao: us-east-1
tipo: glueetl
atualizado: 2026-10-22
fonte: aws-cli (conta 152774997921)
---
# GlueJob - Saldo_realizado (us-east-1)

Hub: [[Hub - AWS Dados]] · [[AWS - Glue Jobs]]

- Categoria: carga-portal — Athena → portal (MySQL/SQL Server)
- Tipo `glueetl` · Glue 5.1 · G.1X × 10
- Role: [[IAM - GlueAthenaToMySQLRole]]
- Script: `s3://cootravale-glue/scripts/Saldo_realizado.py`
- Conexões: `multitms-network` (rede para SQL Azure Nstech (multitms) via VPN)
- Última alteração: 2026-09-24
- Monitorado por EventBridge (falha/timeout): **sim** ([[AWS - Monitoramento]])
- Tags AWS: **nenhuma**

## Fluxo (mapa)
- Origem: [[Host - SQL Azure multitms (Nstech)]]
- Lê o gold ([[GlueDB - prd_gold (us-east-1)]]) e entrega ao portal ([[EC2 - srv-prod-cootravalejobs]]) — inferido pelo nome/role

## Relacionados
- [[Portal]]
- [[datalake-glue]]
