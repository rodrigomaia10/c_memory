---
tipo: aws-alb
tags: [aws, aws/alb, regiao/sa-east-1]
esquema: internet-facing
atualizado: 2026-10-22
fonte: aws-cli (conta 152774997921)
---
# ALB - star-cotravale

Hub: [[Hub - AWS]] · [[AWS - Mapa]] · Rede: [[AWS - Rede]] · [[VPC - cootravale-01]] · DNS: [[Route53 - cootravale.com.br]] · [[Route53 - cootravale.coop.br]]

- Esquema: **internet-facing** · tipo application · VPC cootravale-01
- DNS: `star-cotravale-1034824001.sa-east-1.elb.amazonaws.com`
- Route 53: ver [[AWS - Rede]] (registros apontam para este ALB)

## Regras (listener → destino)
| Porta | Prio | Condição | Ação |
|---|---|---|---|
| 80/HTTP | 2 | path-pattern: /apipass/* | fwd:apipass |
| 80/HTTP | default | (default) | redirect |
| 443/HTTPS | 1 | path-pattern: /apipass, /apipass/*; host-header: portalccs.cootravale.com.br | fwd:apipass |
| 443/HTTPS | default | (default) | fwd:portal-coop |

## Target groups usados
- `apipass` (:5000) → [[EC2 - srv-prod-portalccs]] :4500 (healthy)
- `portal-coop` (:80) → **sem targets**

## Relacionados
- APIPASS (`/apipass/*` em portalccs.cootravale.com.br) · [[Portal]]
