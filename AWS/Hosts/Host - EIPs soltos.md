---
tipo: aws-host
tags: [aws, aws/hosts, custo]
atualizado: 2026-10-22
fonte: aws-cli + route53 + sg + projetos locais (conta 152774997921)
---
# Host - EIPs soltos

IPs elásticos sem instância associada (cobrança ociosa). Vários apontam para IPs privados de instâncias que não existem mais — pistas de servidores antigos.

Hub: [[Hub - AWS Hosts e Sites]] · [[AWS - Achados]]

| Região | IP público | IP privado associado | Nome |
|---|---|---|---|
| us-east-1 | 100.48.170.106 | — | — |
| us-east-1 | 174.129.116.91 | 172.20.252.168 | — |
| us-east-1 | 18.213.203.33 | — | — |
| sa-east-1 | 18.229.30.170 | 192.168.168.139 | Nat gateway |
| sa-east-1 | 18.229.93.241 | 192.168.168.135 | spark |
| sa-east-1 | 18.231.103.115 | — | srv-prod-otrsapp |
| sa-east-1 | 52.67.111.69 | 172.31.27.3 | — |
| sa-east-1 | 52.67.66.31 | 172.31.15.192 | — |
| sa-east-1 | 54.20.30.48 | 172.31.46.171 | — |
| sa-east-1 | 54.207.194.87 | — | airflow-hml |
| sa-east-1 | 54.207.39.228 | 172.31.13.160 | — |
| sa-east-1 | 54.94.158.255 | — | srv-prod-cootravalejobs |
| sa-east-1 | 56.126.123.216 | 172.31.47.58 | — |
| sa-east-1 | 56.126.27.124 | 172.31.49.9 | — |
| sa-east-1 | 56.126.61.123 | 172.31.6.252 | — |

Relacionados: [[EC2 - srv-prod-otrsapp]] (EIP nomeada) · [[EC2 - srv-prod-cootravalejobs]] (EIP nomeada) · [[EC2 - spark-server_old]] · [[Host - airflow-hml (sem instância)]]
