---
tipo: aws-vpc
tags: [aws, aws/vpc, regiao/us-east-1]
vpc_id: vpc-0f65f8acd8195e4bb
atualizado: 2026-10-22
fonte: aws-cli + route53 + sg + projetos locais (conta 152774997921)
---
# VPC - cootravale-prod-us-east

Datalake: Lambdas, Glue (conexões), stage.

Hub: [[Hub - AWS Rede e Segurança]] · [[AWS - Rede]]

- `vpc-0f65f8acd8195e4bb` · 172.20.252.0/22 · us-east-1 · NAT gateways: 1

## Peering (ativos)
- [[VPC - cootravale-01]]
- [[VPC - cootravale-02]]

## VPN
- [[VPN - nstech-us-east-1]]

## EC2 nesta VPC
- [[EC2 - postgres01]]
- [[EC2 - stage-apps]]

## Lambdas em VPC
- [[Lambda - get_incremental_tables (us-east-1)]]
- [[Lambda - prd_ingestion_postgres_kmn (us-east-1)]]
- [[Lambda - prd_ingestion_sqlserver_incremental (us-east-1)]]
- [[Lambda - prd_ingestion_sqlserver_tms (us-east-1)]]
- [[Lambda - test_jdbc_connection (us-east-1)]]
- [[Lambda - teste_conn (us-east-1)]]

## Também aqui
- Glue (conexões JDBC com sub-rede desta VPC): [[AWS - Glue Crawlers e Conexões]]
- Sub-rede aceita no SG do Postgres/MySQL de [[EC2 - srv-prod-postgresql]] (172.20.252.0/26)
