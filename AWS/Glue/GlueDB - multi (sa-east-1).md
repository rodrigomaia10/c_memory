---
tipo: aws-glue-database
tags: [aws, aws/glue, parquet, camada/outros, regiao/sa-east-1]
tabelas: 6
atualizado: 2026-10-22
fonte: aws-cli (conta 152774997921)
---
# GlueDB - multi (sa-east-1)

Hub: [[Hub - AWS]] · [[datalake-glue]] · [[AWS - Athena]] · [[AWS - Glue Jobs]]

- **6 tabelas** — formatos: parquet: 5, view: 1
- Região: sa-east-1 · camada: outros
- Exemplos: dimcarga, dimchamados, p1, p2, t_posicao_all, view_t_posicao_all

## Armazenamento (S3)
- [[S3 - cootravale-infrabi-consumer]] — 5 tabelas

Região legada (pré-migração para us-east-1): catálogo da stack infrabi.

## Fluxo (mapa)
- Catalogado pelo crawler `atendimento_coop_24h_p1` ([[AWS - Glue Crawlers e Conexões]])
- Catalogado pelo crawler `t_posicao_full` ([[AWS - Glue Crawlers e Conexões]])

## Consumidores
- [[PowerBIClaudio]] · [[Apolo11]] (views Athena)
