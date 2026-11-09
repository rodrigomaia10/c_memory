---
tipo: aws-glue-database
tags: [aws, aws/glue, parquet, camada/outros, regiao/sa-east-1]
tabelas: 14
atualizado: 2026-10-22
fonte: aws-cli (conta 152774997921)
---
# GlueDB - portal_cooperado (sa-east-1)

Hub: [[Hub - AWS]] · [[datalake-glue]] · [[AWS - Athena]] · [[AWS - Glue Jobs]]

- **14 tabelas** — formatos: parquet: 14
- Região: sa-east-1 · camada: outros
- Exemplos: f_consulta_all, f_lista_cooperados, f_lista_descarga, f_lista_dim_operacional, f_lista_dim_operacional_rodopar, f_lista_doc_adto_cpg, f_lista_doc_bloq_cpg, f_lista_doc_bloq_cpg_pos_corte

## Armazenamento (S3)
- [[S3 - cootravale-datalake-portal]] — 14 tabelas

Região legada (pré-migração para us-east-1): catálogo da stack infrabi.

## Fluxo (mapa)
- Catalogado pelo crawler `get_portal_cooperados` ([[AWS - Glue Crawlers e Conexões]])

## Consumidores
- [[PowerBIClaudio]] · [[Apolo11]] (views Athena)
