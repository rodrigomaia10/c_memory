---
tipo: aws-sg
tags: [aws, aws/sg, seguranca]
atualizado: 2026-10-22
fonte: aws-cli + route53 + sg + projetos locais (conta 152774997921)
---
# SG - icestechnology-access

incomming traffic from icestech environment

Hub: [[Hub - AWS Rede e Segurança]] · [[AWS - Rede]]

- `sg-07c5ff07fff3aa3e6` · 9 instâncias · 1 regras de entrada

## Instâncias que usam
- [[EC2 - srv-prod-bitbucketrunner]]
- [[EC2 - srv-prod-cootravalejobs]]
- [[EC2 - srv-prod-omnilink]]
- [[EC2 - srv-prod-otrsapp]]
- [[EC2 - srv-prod-portalccs]]
- [[EC2 - srv-prod-portalcoop]]
- [[EC2 - srv-prod-rpasmartshare]]
- [[EC2 - srv-prod-syspass NÃO LIGAR]]
- [[EC2 - srv-prod-wazuh]]

## Nota
SG de parceiro ("incoming traffic from icestech environment") anexado à maioria das EC2; libera 1433 a partir de `cootravale-jobs-sg` ([[EC2 - srv-prod-cootravalejobs]]). Revisar necessidade.
