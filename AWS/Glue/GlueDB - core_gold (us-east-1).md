---
tipo: aws-glue-database
tags: [aws, aws/glue, parquet, camada/gold, regiao/us-east-1]
tabelas: 30
atualizado: 2026-10-22
fonte: aws-cli (conta 152774997921)
---
# GlueDB - core_gold (us-east-1)

Hub: [[Hub - AWS]] · [[datalake-glue]] · [[AWS - Athena]] · [[AWS - Glue Jobs]]

- **30 tabelas** — formatos: parquet: 30
- Região: us-east-1 · camada: gold
- Exemplos: bridge_carga_cte, bridge_carga_motorista, bridge_carga_veiculos_vinculados, bridge_contrato_frete_terceiro_valor, bridge_cte_pagamento, dimcargadadossumarizados, dimcentrocustoviagem, dimcliente

## Armazenamento (S3)
- [[S3 - cootravale-athena-us]] — 27 tabelas
- [[S3 - cootravale-layer-gold]] — 3 tabelas
- Bucket de camada: [[S3 - cootravale-athena-us]]
- Bucket de camada: [[S3 - cootravale-layer-gold]]

## Consumidores
- [[PowerBIClaudio]] · [[Apolo11]] (views Athena)
