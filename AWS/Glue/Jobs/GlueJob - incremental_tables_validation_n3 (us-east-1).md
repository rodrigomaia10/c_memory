---
tipo: aws-glue-job
tags: [aws, aws/glue, regiao/us-east-1, categoria/validacao, ambiente/outro]
regiao: us-east-1
tipo: glueetl
atualizado: 2026-10-22
fonte: aws-cli (conta 152774997921)
---
# GlueJob - incremental_tables_validation_n3 (us-east-1)

Hub: [[Hub - AWS Dados]] · [[AWS - Glue Jobs]]

- Categoria: validacao — validação de tabelas incrementais
- Tipo `glueetl` · Glue 5.0 · G.2X × 3
- Role: [[IAM - GlueJobBronzeSilverCatalog]]
- Script: `s3://cootravale-glue/scripts/incremental_tables_validation_n3.py`
- Conexões: `multitms-network` (rede para SQL Azure Nstech (multitms) via VPN)
- Última alteração: 2026-09-14
- Monitorado por EventBridge (falha/timeout): não ([[AWS - Monitoramento]])
- Tags AWS: **nenhuma**

## Fluxo (mapa)
- Origem: [[Host - SQL Azure multitms (Nstech)]]

## Relacionados
- [[Monitoramento_Gateway_job_cootravale]]
- [[datalake-glue]]
