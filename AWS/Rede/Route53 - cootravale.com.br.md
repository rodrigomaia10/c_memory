---
tipo: aws-route53
tags: [aws, aws/route53, zona/pública]
atualizado: 2026-10-22
fonte: aws-cli (conta 152774997921)
---
# Route53 - cootravale.com.br

Hub: [[Hub - AWS Rede e Segurança]] · [[AWS - Rede]]

- Zona pública · 86 registros
- Domínio principal; maioria dos hosts aponta para [[ALB - cootravale]].
- Detalhe dos hosts e destinos em [[AWS - Rede]].

## Destinos
- ALBs: [[ALB - cootravale]] · [[ALB - cootravale-internal]]
- EC2: [[EC2 - srv-prod-bitbucketrunner]] · [[EC2 - srv-prod-wazuh]] · [[EC2 - stage-apps]] · [[EC2 - spark-server_old]]
- Hosts fora do mapa: [[Hub - AWS Hosts e Sites]] (on-premises, Locaweb, parceiros)
