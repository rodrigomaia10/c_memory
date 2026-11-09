---
tipo: aws-glue-database
tags: [aws, aws/glue, parquet, camada/silver, regiao/sa-east-1]
tabelas: 7
atualizado: 2026-10-22
fonte: aws-cli (conta 152774997921)
---
# GlueDB - silver_tms (sa-east-1)

Hub: [[Hub - AWS]] · [[datalake-glue]] · [[AWS - Athena]] · [[AWS - Glue Jobs]]

- **7 tabelas** — formatos: parquet: 7
- Região: sa-east-1 · camada: silver
- Exemplos: dbo_t_carga_cte, dbo_t_cte, dbo_t_cte_comp_prest, dbo_t_cte_participante, dbo_t_empresa_serie, dbo_t_localidades, dbo_t_moddocfiscal

## Armazenamento (S3)
- [[S3 - cootravale-layer-silver]] — 7 tabelas

Região legada (pré-migração para us-east-1): catálogo da stack infrabi.

## Consumidores
- [[PowerBIClaudio]] · [[Apolo11]] (views Athena)
