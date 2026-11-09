---
tipo: aws-glue-database
tags: [aws, aws/glue, parquet, camada/silver, regiao/us-east-1]
tabelas: 98
atualizado: 2026-10-22
fonte: aws-cli (conta 152774997921)
---
# GlueDB - silver_kmn (us-east-1)

Hub: [[Hub - AWS]] · [[datalake-glue]] · [[AWS - Athena]] · [[AWS - Glue Jobs]]

- **98 tabelas** — formatos: parquet: 98
- Região: us-east-1 · camada: silver
- Exemplos: abastecimento_abastecimento, agreg_agr_contrato_pagar, agreg_taxa, agreg_termo, agreg_termo_cota, agreg_termo_nivel_vigencia, agreg_termo_veiculo, almoxarifado_material

## Armazenamento (S3)
- [[S3 - cootravale-layer-silver]] — 98 tabelas
- Bucket de camada: [[S3 - cootravale-layer-silver]]

## Fluxo (mapa)
- Origem dos dados: [[Host - Postgres KMM (Nstech)]]
- Escrito por: [[GlueJob - bronze_to_silver (us-east-1)]]

## Consumidores
- [[PowerBIClaudio]] · [[Apolo11]] (views Athena)
- [[API_Lambda]] (API_OTRS consulta esta base)
