---
tipo: aws-glue
tags: [aws, aws/glue]
atualizado: 2026-10-22
fonte: aws-cli (conta 152774997921)
---
# AWS - Glue Crawlers e Conexões

Hub: [[Hub - AWS]] · [[datalake-glue]] · [[AWS - Glue Jobs]]

## Conexões
| Região | Nome | Destino | Observação |
|---|---|---|---|
| us-east-1 | Jdbc connection - kmm | `jdbc:postgresql://147.15.66.157:5432/datalake_301` | Postgres KMM (externo, via VPN nstech) |
| us-east-1 | Jdbc connection - kmm old | `jdbc:postgresql://144.22.225.175:5430/datalake` | Postgres KMM (externo, via VPN nstech) |
| us-east-1 | Jdbc connection - multitms | `jdbc:sqlserver://sql-mg-nst-core-eus-prd-bi.database.windows.net:1433/` |  |
| us-east-1 | Jdbc connection - otrs | `jdbc:sqlserver://172.31.14.242:1433;databaseName=portalCooperado` | [[EC2 - srv-prod-cootravalejobs]] |
| us-east-1 | multitms-network | `NETWORK` |  |
| sa-east-1 | Jdbc connection | `jdbc:sqlserver://172.31.14.242:1433;databaseName=portalCooperado` | [[EC2 - srv-prod-cootravalejobs]] |
| sa-east-1 | Jdbc connection - otrs | `jdbc:mysql://172.31.28.247:3306/otrs?useSSL=false` | [[EC2 - srv-prod-postgresql]] (MySQL OTRS) |
| sa-east-1 | sqlserver-cootravale-connection | `jdbc:sqlserver://172.31.14.242:1433;databaseName=portalCooperado` | [[EC2 - srv-prod-cootravalejobs]] |

## Crawlers
| Região | Crawler | Database | Alvo |
|---|---|---|---|
| us-east-1 | get_metadado_kmm | [[GlueDB - source_kmm (us-east-1)]] | `datalake/%/%` |
| us-east-1 | get_metadado_multitms | [[GlueDB - source_multi_tms (us-east-1)]] | `sqldb-cootravale-prd/dbo/%` |
| us-east-1 | get_validation_tables | [[GlueDB - validation_db (us-east-1)]] | `s3://cootravale-layer-bronze/validation/dbo/t_xml_nota_fiscal/` |
| us-east-1 | kmm_test | [[GlueDB - hml_bronze (us-east-1)]] | `s3://cootravale-lakekmm/load/cootravale/` |
| sa-east-1 | DimTaxas | [[GlueDB - taxa (sa-east-1)]] | `s3://cootravale-infrabi-staging/kmm/taxa/f_taxa` |
| sa-east-1 | atendimento_coop_24h_p1 | [[GlueDB - multi (sa-east-1)]] | `s3://cootravale-infrabi-consumer/multi/atendimento_coop_24h/p1`, `s3://cootravale-infrabi-consumer/multi/atendimento_coop_24h/p2` |
| sa-east-1 | f_faturamento_taxas | [[GlueDB - taxa (sa-east-1)]] | `s3://cootravale-infrabi-staging/kmm/taxa/f_faturamento_taxas` |
| sa-east-1 | get_agings | [[GlueDB - agings (sa-east-1)]] | `s3://cootravale-infrabi-consumer/kmm/agings/` |
| sa-east-1 | get_cootravale | [[GlueDB - cootravale (sa-east-1)]] | `s3://cootravale-infrabi-consumer/cootravale/` |
| sa-east-1 | get_faturamento | [[GlueDB - faturamento (sa-east-1)]] | `s3://cootravale-infrabi-consumer/faturamento` |
| sa-east-1 | get_kmm | [[GlueDB - kmm (sa-east-1)]] | `s3://cootravale-infrabi-consumer/kmm/` |
| sa-east-1 | get_portal_cooperados | [[GlueDB - portal_cooperado (sa-east-1)]] | `s3://cootravale-datalake-portal/Portal_Cooperados` |
| sa-east-1 | t_posicao_full | [[GlueDB - multi (sa-east-1)]] | `s3://cootravale-infrabi-consumer/multi/t_posicao_all` |
| sa-east-1 | teste_saldo_realizado | [[GlueDB - saldo_realizado (sa-east-1)]] | `s3://cootravale-infrabi-consumer/kmm/portal_cooperado/f_realizado` |
