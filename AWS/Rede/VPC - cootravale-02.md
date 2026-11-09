---
tipo: aws-vpc
tags: [aws, aws/vpc, regiao/sa-east-1]
vpc_id: vpc-00b4c0dd1d14c8eb3
atualizado: 2026-10-22
fonte: aws-cli + route53 + sg + projetos locais (conta 152774997921)
---
# VPC - cootravale-02

Airflow de produção, DC01, OCS.

Hub: [[Hub - AWS Rede e Segurança]] · [[AWS - Rede]]

- `vpc-00b4c0dd1d14c8eb3` · 192.168.168.0/24 · sa-east-1 · NAT gateways: 1

## Peering (ativos)
- [[VPC - cootravale-prod-us-east]]
- [[VPC - cootravale-01]]

## VPN
- (nenhuma direta)

## EC2 nesta VPC
- [[EC2 - srv-prod-airflow]]
- [[EC2 - srv-prod-dc01]]
- [[EC2 - srv-prod-ocs NAO LIGAR]]

## Lambdas em VPC
- [[Lambda - prd_ingestion_sqlserver_tms (sa-east-1)]]
- [[Lambda - teste_con_sqlserver (sa-east-1)]]
