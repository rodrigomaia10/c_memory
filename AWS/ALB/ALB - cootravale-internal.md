---
tipo: aws-alb
tags: [aws, aws/alb, regiao/sa-east-1]
esquema: internal
atualizado: 2026-10-22
fonte: aws-cli (conta 152774997921)
---
# ALB - cootravale-internal

Hub: [[Hub - AWS]] · [[AWS - Mapa]] · Rede: [[AWS - Rede]] · [[VPC - cootravale-01]] · DNS: [[Route53 - cootravale.com.br]] · [[Route53 - cootravale.coop.br]]

- Esquema: **internal** · tipo application · VPC cootravale-01
- DNS: `internal-cootravale-internal-1009009701.sa-east-1.elb.amazonaws.com`
- Route 53: ver [[AWS - Rede]] (registros apontam para este ALB)

## Regras (listener → destino)
| Porta | Prio | Condição | Ação |
|---|---|---|---|
| 443/HTTPS | default | (default) | fwd:srv-prod-airflow-tg |
| 80/HTTP | default | (default) | redirect |

## Target groups usados
- `srv-prod-airflow-tg` (:8080) → [[EC2 - srv-prod-airflow]] (192.168.168.69) :8080 (healthy)

## Relacionados
- [[airflow-prod-dags]] · [[runner airflow]]
