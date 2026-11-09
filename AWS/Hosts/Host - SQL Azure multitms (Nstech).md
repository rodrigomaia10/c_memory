---
tipo: aws-host
tags: [aws, aws/hosts, confirmado-por-dns]
atualizado: 2026-10-22
fonte: aws-cli + route53 + sg + projetos locais (conta 152774997921)
---
# Host - SQL Azure multitms (Nstech)

SQL Azure do multitms/TMS: origem de `silver_multi` e das tabelas multi. Acessado via VPN/rede `multitms-network`.

Hub: [[Hub - AWS Hosts e Sites]] · [[AWS - Rede]]

- Endereço: `sql-mg-nst-core-eus-prd-bi.database.windows.net:1433/sqldb-coot`
- Site/provedor: [[Site - Nstech (Azure)]]

## Ligações
- [[AWS - Glue Crawlers e Conexões]]
- [[GlueDB - source_multi_tms (us-east-1)]]
- [[GlueDB - silver_multi (us-east-1)]]
- [[GlueJob - jdbc_to_bronze (us-east-1)]]
- [[Lambda - prd_ingestion_sqlserver_tms (us-east-1)]]
