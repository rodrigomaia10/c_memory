---
tipo: aws-host
tags: [aws, aws/hosts, confirmado-por-dns]
atualizado: 2026-10-22
fonte: aws-cli + route53 + sg + projetos locais (conta 152774997921)
---
# Host - Zabbix (on-premises)

Zabbix on-premises: SGs liberam a porta 10050 (agente) e ICMP para a rede 192.168.1.0/24 em quase todas as EC2.

Hub: [[Hub - AWS Hosts e Sites]] · [[AWS - Rede]]

- Endereço: `192.168.1.0/24 (porta 10050)`
- Site/provedor: [[Site - Embratel (on-premises)]]

## Ligações
- [[EC2 - srv-prod-otrsapp]]
- [[EC2 - srv-prod-cootravalejobs]]
- [[EC2 - srv-prod-rpasmartshare]]
- [[EC2 - srv-prod-omnilink]]
- [[EC2 - srv-prod-portalccs]]
- [[EC2 - srv-hm-portalccs]]
- [[EC2 - srv-prod-portalcoop]]
- [[EC2 - Srv_AD02]]
