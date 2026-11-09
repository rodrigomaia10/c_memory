---
tipo: aws-glue-database
tags: [aws, aws/glue, parquet, camada/outros, regiao/us-east-1]
tabelas: 5
atualizado: 2026-10-22
fonte: aws-cli (conta 152774997921)
---
# GlueDB - validation_db (us-east-1)

Hub: [[Hub - AWS]] · [[datalake-glue]] · [[AWS - Athena]] · [[AWS - Glue Jobs]]

- **5 tabelas** — formatos: parquet: 5
- Região: us-east-1 · camada: outros
- Exemplos: t_carga_rota_frete, t_historico_propriedade, t_monitoramento, t_posicao, t_xml_nota_fiscal

## Armazenamento (S3)
- [[S3 - cootravale-layer-bronze]] — 5 tabelas

## Fluxo (mapa)
- Catalogado pelo crawler `get_validation_tables` ([[AWS - Glue Crawlers e Conexões]])

## Consumidores
- [[PowerBIClaudio]] · [[Apolo11]] (views Athena)
