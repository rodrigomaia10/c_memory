---
tipo: aws-tags
tags: [aws, governanca]
atualizado: 2026-10-22
fonte: aws-cli (conta 152774997921)
---
# AWS - Tags

Hub: [[Hub - AWS]] · [[AWS - Achados]]

## Chaves em uso (EC2)
- `Backup`: 13 instâncias
- `Role`: 2 instâncias
- `managed-by`: 2 instâncias
- `Projeto`: 2 instâncias
- `DbHostname`: 1 instâncias

- `Backup=Sim` marca instâncias no plano de backup (DLM).
- `managed-by=terraform` + `Projeto=BI`: recursos geridos por [[IaC]].
- `Role`/`DbHostname`: us-east-1 stage.

## EC2 sem nenhuma tag além de Name
- [[EC2 - vpn-test-ping]]
- [[EC2 - Srv_AD02]]
- [[EC2 - srv-hm-portalccs]]
- [[EC2 - srv-prod-ocs NAO LIGAR]]
- [[EC2 - VM-Backup-Rodopar]]
- [[EC2 - srv-prod-databases]]

## Outros recursos
- Lambdas, Glue jobs, buckets S3 e ALBs: praticamente **sem tags** (ver cada nó). Sugestão: padronizar `Projeto`, `Ambiente`, `Dono`, `Backup`, `CentroCusto`.
