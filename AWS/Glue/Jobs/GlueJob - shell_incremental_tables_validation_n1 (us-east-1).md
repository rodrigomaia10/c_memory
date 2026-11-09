---
tipo: aws-glue-job
tags: [aws, aws/glue, regiao/us-east-1, categoria/validacao, ambiente/outro]
regiao: us-east-1
tipo: pythonshell
atualizado: 2026-10-22
fonte: aws-cli (conta 152774997921)
---
# GlueJob - shell_incremental_tables_validation_n1 (us-east-1)

Hub: [[Hub - AWS Dados]] · [[AWS - Glue Jobs]]

- Categoria: validacao — validação de tabelas incrementais
- Tipo `pythonshell` · Glue 3.0 · — × —
- Role: [[IAM - GlueJobBronzeSilverCatalog]]
- Script: `s3://cootravale-glue/scripts/shell_incremental_tables_validation_n1.py`
- Conexões: `multitms-network` (rede para SQL Azure Nstech (multitms) via VPN)
- Última alteração: 2026-06-07
- Monitorado por EventBridge (falha/timeout): não ([[AWS - Monitoramento]])
- Tags AWS: **nenhuma**

## Fluxo (mapa)
- Origem: [[Host - SQL Azure multitms (Nstech)]]

## Relacionados
- [[Monitoramento_Gateway_job_cootravale]]
- [[datalake-glue]]
