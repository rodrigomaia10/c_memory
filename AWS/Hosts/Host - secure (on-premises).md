---
tipo: aws-host
tags: [aws, aws/hosts, confirmado-por-dns]
atualizado: 2026-10-22
fonte: aws-cli + route53 + sg + projetos locais (conta 152774997921)
---
# Host - secure (on-premises)

FortiGate/ponta da VPN Embratel: o mesmo IP é o customer gateway `cootravale-embratel-cgw` e aparece liberado nos SGs de jobs e Spark.

Hub: [[Hub - AWS Hosts e Sites]] · [[AWS - Rede]]

- Endereço: `189.42.20.190 (DNS secure) = CGW Embratel`
- Site/provedor: [[Site - Embratel (on-premises)]]
- Registro DNS em [[Route53 - cootravale.com.br]]

## Ligações
- [[VPN - cootravale-embratel-vpn]]
- [[EC2 - srv-prod-cootravalejobs]]
- [[EC2 - spark-server_old]]
