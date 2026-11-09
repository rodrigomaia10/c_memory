---
tipo: aws-glue-job
tags: [aws, aws/glue, regiao/us-east-1, categoria/teste, ambiente/outro]
regiao: us-east-1
tipo: glueetl
atualizado: 2026-10-22
fonte: aws-cli (conta 152774997921)
---
# GlueJob - testes (us-east-1)

Hub: [[Hub - AWS Dados]] · [[AWS - Glue Jobs]]

- Categoria: teste — teste/sandbox
- Tipo `glueetl` · Glue 5.0 · G.1X × 2
- Role: [[IAM - GlueAthenaToMySQLRole]]
- Script: `s3://cootravale-glue/scripts/testes.py`
- Conexões: `multitms-network` (rede para SQL Azure Nstech (multitms) via VPN)
- Última alteração: 2026-10-07
- Monitorado por EventBridge (falha/timeout): não ([[AWS - Monitoramento]])
- Tags AWS: **nenhuma**

## Fluxo (mapa)
- Origem: [[Host - SQL Azure multitms (Nstech)]]

## Relacionados
- [[datalake-glue]]
