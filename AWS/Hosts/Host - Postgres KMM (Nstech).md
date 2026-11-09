---
tipo: aws-host
tags: [aws, aws/hosts, confirmado-por-dns]
atualizado: 2026-10-22
fonte: aws-cli + route53 + sg + projetos locais (conta 152774997921)
---
# Host - Postgres KMM (Nstech)

Postgres do KMM: origem dos dados KMM no datalake (`silver_kmn`). Acessado pelos jobs Glue via VPN.

Hub: [[Hub - AWS Hosts e Sites]] · [[AWS - Rede]]

- Endereço: `147.15.66.157:5432/datalake_301 (e antigo 144.22.225.175:5430)`
- Site/provedor: [[Site - Nstech (Azure)]]

## Ligações
- [[AWS - Glue Crawlers e Conexões]]
- [[GlueDB - source_kmm (us-east-1)]]
- [[GlueDB - silver_kmn (us-east-1)]]
- [[SQL_KMM]]
- [[GlueJob - jdbc_to_bronze (us-east-1)]]
- [[Lambda - prd_ingestion_postgres_kmn (us-east-1)]]
