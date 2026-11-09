---
tipo: aws-alb
tags: [aws, aws/alb, regiao/sa-east-1]
esquema: internet-facing
atualizado: 2026-10-22
fonte: aws-cli (conta 152774997921)
---
# ALB - cootravale

Hub: [[Hub - AWS]] · [[AWS - Mapa]] · Rede: [[AWS - Rede]] · [[VPC - cootravale-01]] · DNS: [[Route53 - cootravale.com.br]] · [[Route53 - cootravale.coop.br]]

- Esquema: **internet-facing** · tipo application · VPC cootravale-01
- DNS: `cootravale-1452664283.sa-east-1.elb.amazonaws.com`
- Route 53: ver [[AWS - Rede]] (registros apontam para este ALB)

## Regras (listener → destino)
| Porta     | Prio    | Condição                                                                                                                  | Ação                                 |
| --------- | ------- | ------------------------------------------------------------------------------------------------------------------------- | ------------------------------------ |
| 443/HTTPS | 1       | host-header: api.cootravale.com.br                                                                                        | fwd:mcp-langfuse                     |
| 443/HTTPS | 2       | host-header: homologanovo.cootravale.com.br                                                                               | fwd:cootravale-portal-tg             |
| 443/HTTPS | 3       | host-header: homologa.cootravale.com.br                                                                                   | fwd:cootravale-portal-tg             |
| 443/HTTPS | 4       | host-header: otrshml.cootravale.com.br, otrs.cootravale.com.br, chamadoshml.cootravale.com.br, chamados.cootravale.com.br | fwd:cootravale-otrs-tg               |
| 443/HTTPS | 5       | host-header: smartshare.cootravale.com.br                                                                                 | fwd:cootravale-smartshare-tg         |
| 443/HTTPS | 6       | host-header: syspass.cootravale.com.br                                                                                    | fwd:cootravale-syspass-tg            |
| 443/HTTPS | 7       | host-header: portalccs.cootravale.com.br                                                                                  | fwd:cootravale-portal-ccs-nginx-tg   |
| 443/HTTPS | 8       | host-header: portalccshomologa.cootravale.com.br                                                                          | fwd:cootravale-portal-ccs-hom-tg     |
| 443/HTTPS | 10      | host-header: airflow-hml.cootravale.com.br                                                                                | fwd:mcp-langfuse                     |
| 443/HTTPS | 11      | host-header: cooperadoshomologa.cootravale.com.br                                                                         | fwd:cootravale-portal-ccs-hom-8181   |
| 443/HTTPS | 12      | host-header: cooperadosnovo.cootravale.com.br                                                                             | fwd:cootravale-portal-tg             |
| 443/HTTPS | 13      | host-header: airflow-hml.cootravale.com.br                                                                                | fwd:mcp-call-tool                    |
| 443/HTTPS | 14      | host-header: inventory.cootravale.com.br                                                                                  | fwd:cootravale-ocs-tg                |
| 443/HTTPS | 15      | host-header: hml.torreportobelo.cootravale.com.br                                                                         | fwd:cootravale-hml-torreportobelo    |
| 443/HTTPS | 16      | host-header: torreportobelo.cootravale.com.br                                                                             | fwd:cootravale-torreportobelo        |
| 443/HTTPS | 17      | host-header: cooperados.cootravale.coop.br                                                                                | fwd:cootravale-portal-ccs-tg         |
| 443/HTTPS | 18      | host-header: cootravale.coop.br, cootravale.com.br, www.cootravale.com.br, www.cootravale.coop.br                         | fwd:site-cootravale                  |
| 443/HTTPS | 19      | host-header: crm.cootravale.com.br                                                                                        | fwd:cootravale-crm-tg                |
| 443/HTTPS | 20      | host-header: termoantt.cootravale.com.br                                                                                  | fwd:srv-prod-portalccs-termoantt-pub |
| 443/HTTPS | 21      | host-header: integradorciot.cootravale.com.br                                                                             | fwd:srv-prod-portalccs-integciot-pub |
| 443/HTTPS | 22      | host-header: appcootravale.cootravale.com.br                                                                              | fwd:srv-prod-portalccs-appcoot-pub   |
| 443/HTTPS | default | (default)                                                                                                                 | fixed-response                       |
| 80/HTTP   | default | (default)                                                                                                                 | redirect                             |
| 8181/HTTP | default | (default)                                                                                                                 | redirect                             |

## Target groups usados
- `mcp-langfuse` (:80) → **sem targets**
- `cootravale-portal-tg` (:80) → **sem targets**
- `cootravale-otrs-tg` (:80) → [[EC2 - srv-prod-otrsapp]] :80 (healthy)
- `cootravale-smartshare-tg` (:80) → [[EC2 - srv-prod-rpasmartshare]] :80 (healthy)
- `cootravale-syspass-tg` (:80) → [[EC2 - srv-prod-syspass NÃO LIGAR]] :80 (unused)
- `cootravale-portal-ccs-nginx-tg` (:81) → [[EC2 - srv-prod-portalccs]] :81 (healthy)
- `cootravale-portal-ccs-hom-tg` (:80) → [[EC2 - srv-hm-portalccs]] :80 (healthy)
- `cootravale-portal-ccs-hom-8181` (:8181) → [[EC2 - srv-hm-portalccs]] :8181 (healthy)
- `mcp-call-tool` (:3000) → **sem targets**
- `cootravale-ocs-tg` (:80) → IP 172.31.10.35 (não é EC2 mapeada) :80 (unhealthy)
- `cootravale-hml-torreportobelo` (:3000) → [[EC2 - srv-hm-portalccs]] :3000 (unhealthy)
- `cootravale-torreportobelo` (:3000) → [[EC2 - srv-prod-portalccs]] :3000 (healthy)
- `cootravale-portal-ccs-tg` (:80) → [[EC2 - srv-prod-portalccs]] :80 (healthy)
- `site-cootravale` (:3003) → [[EC2 - srv-prod-portalccs]] :3003 (healthy)
- `cootravale-crm-tg` (:7070) → [[EC2 - srv-prod-portalccs]] :7070 (healthy)
- `srv-prod-portalccs-termoantt-pub` (:3002) → [[EC2 - srv-prod-portalccs]] :3002 (healthy)
- `srv-prod-portalccs-integciot-pub` (:3010) → [[EC2 - srv-prod-portalccs]] :3010 (unhealthy)
- `srv-prod-portalccs-appcoot-pub` (:3020) → [[EC2 - srv-prod-portalccs]] :3020 (healthy)

## Relacionados
- [[Portal]] · [[otrs]] · [[proxy-nginx]] · [[Hub - Agentes e MCP]] (TGs mcp-langfuse / mcp-call-tool sem targets)
