---
tipo: aws-glue-database
tags: [aws, aws/glue, parquet, camada/outros, regiao/sa-east-1]
tabelas: 9
atualizado: 2026-10-22
fonte: aws-cli (conta 152774997921)
---
# GlueDB - cootravale (sa-east-1)

Hub: [[Hub - AWS]] · [[datalake-glue]] · [[AWS - Athena]] · [[AWS - Glue Jobs]]

- **9 tabelas** — formatos: parquet: 7, view: 2
- Região: sa-east-1 · camada: outros
- Exemplos: d_carga, d_carga_ocorrencia, d_carga_ocorrencia_documentos, d_chamado, d_chamado_ocorrencia, d_ocorrencia, tb_rls_usuario, v_ocorrencias

## Armazenamento (S3)
- [[S3 - cootravale-infrabi-consumer]] — 7 tabelas

Região legada (pré-migração para us-east-1): catálogo da stack infrabi.

## Fluxo (mapa)
- Catalogado pelo crawler `get_cootravale` ([[AWS - Glue Crawlers e Conexões]])

## Consumidores
- [[PowerBIClaudio]] · [[Apolo11]] (views Athena)
