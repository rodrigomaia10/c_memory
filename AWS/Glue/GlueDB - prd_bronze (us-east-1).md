---
tipo: aws-glue-database
tags: [aws, aws/glue, parquet, camada/bronze, regiao/us-east-1]
tabelas: 223
atualizado: 2026-10-22
fonte: aws-cli (conta 152774997921)
---
# GlueDB - prd_bronze (us-east-1)

Hub: [[Hub - AWS]] · [[datalake-glue]] · [[AWS - Athena]] · [[AWS - Glue Jobs]]

- **223 tabelas** — formatos: parquet: 223
- Região: us-east-1 · camada: bronze
- Exemplos: atss_dbo_view_alerta, atss_dbo_view_entidade_equipamento, atss_dbo_view_localizacao, atss_dbo_view_status_cavalo, atss_dbo_view_status_viagem, atss_dbo_view_viagem, f_lista_descarga, kmm_abastecimento_abastecimento

## Armazenamento (S3)
- [[S3 - cootravale-layer-bronze-us]] — 222 tabelas
- [[S3 - cootravale-infrabi-staging]] — 1 tabelas
- Bucket de camada: [[S3 - cootravale-layer-bronze-us]]

## Fluxo (mapa)
- Escrito por: [[GlueJob - jdbc_to_bronze (us-east-1)]]

## Consumidores
- [[PowerBIClaudio]] · [[Apolo11]] (views Athena)
