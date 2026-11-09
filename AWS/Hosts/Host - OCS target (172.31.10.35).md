---
tipo: aws-host
tags: [aws, aws/hosts, confirmado-por-dns]
atualizado: 2026-10-22
fonte: aws-cli + route53 + sg + projetos locais (conta 152774997921)
---
# Host - OCS target (172.31.10.35)

Alvo do target group `cootravale-ocs-tg` (unhealthy): o ALB envia `inventory.cootravale.com.br` para esse IP, que não é uma EC2 desta conta.

Hub: [[Hub - AWS Hosts e Sites]] · [[AWS - Rede]]

- Endereço: `172.31.10.35:80`

## Ligações
- [[ALB - cootravale]]
- [[EC2 - srv-prod-ocs NAO LIGAR]]
