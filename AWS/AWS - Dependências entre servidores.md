---
tipo: aws-mapa
tags: [aws, mapa, dependencias]
atualizado: 2026-10-22
---
# AWS - Dependências entre servidores

Quem usa quem, deduzido de security groups, DNS, ALB, conexões Glue e README dos projetos. Hub: [[Hub - AWS Computação]] · [[AWS - Mapa]]

```mermaid
flowchart LR
  ALB[ALB cootravale] --> PCCS[portalccs]
  ALB --> OTRS[otrsapp]
  ALB --> SMS[rpasmartshare]
  ALB --> HM[hm-portalccs]
  ALB2[ALB star] --> PCCS
  ALBI[ALB interno] --> AF[airflow]
  AF -->|metadata 5432| PG[(postgresql: Postgres+MySQL)]
  OTRS -->|MySQL 3306| PG
  OTRS -->|LDAP| DC[dc01 / AD02]
  OTRS -->|1433| JOBS[cootravalejobs SQL Server + gateway PBI]
  JOBS -->|5432| PG
  JOBS -->|1433| SMS
  RUN[bitbucketrunner] -->|SSH deploy| HM
  RUN -->|80/443| SMS
  AF -->|80/443| SMS
  GLUE[Glue us-east-1] -->|JDBC 1433| JOBS
  GLUE -->|JDBC 3306| PG
  WZ[wazuh] -.agentes.- JOBS
  WZ -.agentes.- SMS
  WZ -.agentes.- OL[omnilink]
  ZBX[Zabbix on-prem] -.10050.- JOBS
  PBI[Power BI] --> JOBS
```

## Pontos únicos de falha
- [[EC2 - srv-prod-postgresql]]: Airflow prod + OTRS.
- [[EC2 - srv-prod-dc01]]: único AD ativo ([[EC2 - Srv_AD02]] parado).
- [[EC2 - srv-prod-portalccs]]: ~9 aplicativos públicos em 1 instância.
- [[EC2 - srv-prod-cootravalejobs]]: SQL Server + gateway Power BI + jobs.

## Saturação
- [[EC2 - srv-prod-rpasmartshare]] CPU 76% média; [[EC2 - srv-prod-postgresql]] 47%.
