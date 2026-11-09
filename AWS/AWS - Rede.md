---
tipo: aws-rede
tags: [aws, aws/vpc, aws/route53]
atualizado: 2026-10-22
fonte: aws-cli (conta 152774997921)
---
# AWS - Rede

Hub: [[Hub - AWS]] · [[AWS - Mapa]]

## VPCs
| VPC | Região | CIDR | Uso |
|---|---|---|---|
| cootravale-01 (`vpc-0035d739545a5b962`, default) | sa-east-1 | 172.31.0.0/16 | Servidores legado/portal/OTRS ([[AWS - EC2 (índice)]]) |
| cootravale-02 (`vpc-00b4c0dd1d14c8eb3`) | sa-east-1 | 192.168.168.0/24 | Airflow prod, DC01, OCS ([[EC2 - srv-prod-airflow]]) |
| cootravale-prod-us-east (`vpc-0f65f8acd8195e4bb`) | us-east-1 | 172.20.252.0/22 | Lambdas de ingestão, Glue, stage ([[AWS - Lambdas (índice)]]) |

## Peering (todos ativos)
- us-east-1 ↔ cootravale-01 · us-east-1 ↔ cootravale-02 · cootravale-01 ↔ cootravale-02

## VPN
| Nome | Região | Túneis |
|---|---|---|
| nstech-us-east-1 | us-east-1 | 1 UP / 1 DOWN — origem dos dados KMM/multitms ([[datalake-glue]]) |
| nstech-sa-east-1 | sa-east-1 | 1 UP / 1 DOWN |
| cootravale-embratel-vpn, NewVPC-Embratel | sa-east-1 | UP |
| cootravale-italine-vgw, NewVPC-Italaine | sa-east-1 | UP |

## NAT
- us-east-1: 1 NAT (cootravale-prod-us-east) · sa-east-1: 2 NATs (cootravale-01 e -02)

## Load balancers
- [[ALB - cootravale]] (público, ~20 hosts) · [[ALB - star-cotravale]] (público, APIPASS/portal-coop) · [[ALB - cootravale-internal]] (Airflow)

## Route 53
- Zonas: `cootravale.com.br` (86 registros), `cootravale.coop.br` (18), `ctv.aws` (privada, 10)
- Hosts → ALB cootravale: api, appcootravale, chamados, otrs, cooperadoshomologa, homologanovo, inventory, integradorciot, portalccs(+homologa), smartshare, syspass, termoantt, torreportobelo (+hml), crm, www, apex, cooperados.cootravale.coop.br
- airflow-prod → ALB interno · airflow.* / api-cootravale.* → [[EC2 - srv-prod-bitbucketrunner]] · wazuh → [[EC2 - srv-prod-wazuh]] · spark → [[EC2 - spark-server_old]] · `*.stage-apps` → [[EC2 - stage-apps]]
- Zona privada `ctv.aws`: airflow, airflow-hml, spark, spark-hml, wazuh, postgres01 ([[EC2 - postgres01]]), otrs.db ([[EC2 - srv-prod-postgresql]]), srv01.sqlserver.jobs ([[EC2 - srv-prod-cootravalejobs]])
- Registros para IPs 189.42.20.x / 170.82.194.x = infra on-premises; mysql01-07 = Locaweb (legado, [[Hub - Legado]]).
- Também: [[proxy-nginx]], [[Portal]].
