---
tipo: aws-glue-database
tags: [aws, aws/glue, parquet, camada/silver, regiao/us-east-1]
tabelas: 111
atualizado: 2026-10-22
fonte: aws-cli (conta 152774997921)
---
# GlueDB - silver_multi (us-east-1)

Hub: [[Hub - AWS]] · [[datalake-glue]] · [[AWS - Athena]] · [[AWS - Glue Jobs]]

- **111 tabelas** — formatos: parquet: 111
- Região: us-east-1 · camada: silver
- Exemplos: dbo_t_alerta_monitor, dbo_t_alerta_tratativa, dbo_t_alerta_tratativa_acao, dbo_t_apolice_seguro_geral, dbo_t_averbacao_integracao_arquivo, dbo_t_carga, dbo_t_carga_cancelamento, dbo_t_carga_carga_integracao

## Armazenamento (S3)
- [[S3 - cootravale-layer-silver]] — 111 tabelas
- Bucket de camada: [[S3 - cootravale-layer-silver]]

## Fluxo (mapa)
- Origem dos dados: [[Host - SQL Azure multitms (Nstech)]]
- Escrito por: [[GlueJob - bronze_to_silver (us-east-1)]]

## Consumidores
- [[PowerBIClaudio]] · [[Apolo11]] (views Athena)
