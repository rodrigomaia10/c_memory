---
tipo: aws-host
tags: [aws, aws/hosts, inferido]
atualizado: 2026-10-22
fonte: aws-cli + route53 + sg + projetos locais (conta 152774997921)
---
# Host - srv01 (on-premises)

Servidor de banco legado `srv01` (nome sugere SQL Server/ERP; SG `cootravale-srv01-db-sg` acessa MySQL do OTRS e SQL Server do SmartShare; log group RDS `srv01-db`). Inferido.

Hub: [[Hub - AWS Hosts e Sites]] · [[AWS - Rede]]

- Endereço: `189.42.20.186 (DNS srv01)`
- Site/provedor: [[Site - Embratel (on-premises)]]
- Registro DNS em [[Route53 - cootravale.com.br]]

## Ligações
- [[EC2 - srv-prod-otrsapp]]
- [[EC2 - srv-prod-rpasmartshare]]
- [[EC2 - srv-prod-postgresql]]
