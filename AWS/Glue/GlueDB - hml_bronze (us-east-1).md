---
tipo: aws-glue-database
tags: [aws, aws/glue, parquet, camada/bronze, regiao/us-east-1]
tabelas: 820
atualizado: 2026-10-22
fonte: aws-cli (conta 152774997921)
---
# GlueDB - hml_bronze (us-east-1)

Hub: [[Hub - AWS]] · [[datalake-glue]] · [[AWS - Athena]] · [[AWS - Glue Jobs]]

- **820 tabelas** — formatos: parquet: 816, view: 3, LazySimpleSerDe: 1
- Região: us-east-1 · camada: bronze
- Exemplos: atss_dbo_view_alerta, atss_dbo_view_entidade_equipamento, atss_dbo_view_localizacao, atss_dbo_view_status_cavalo, atss_dbo_view_status_viagem, atss_dbo_view_viagem, f_lista_descarga, function_aging

## Armazenamento (S3)
- [[S3 - cootravale-layer-bronze-us]] — 249 tabelas
- [[S3 - cootravale-infrabi-staging]] — 1 tabelas
- [[S3 - cootravale-lakekmm]] — 559 tabelas
- [[S3 - cootravale-layer-bronze]] — 8 tabelas
- Bucket de camada: [[S3 - cootravale-layer-bronze-us]]
- Bucket de camada: [[S3 - cootravale-lakekmm]]

## Fluxo (mapa)
- Escrito por: [[GlueJob - jdbc_to_bronze_manual (us-east-1)]]
- Catalogado pelo crawler `kmm_test` ([[AWS - Glue Crawlers e Conexões]])

## Consumidores
- [[PowerBIClaudio]] · [[Apolo11]] (views Athena)
