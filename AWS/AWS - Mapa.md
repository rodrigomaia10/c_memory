---
tipo: aws-mapa
tags: [aws, mapa]
atualizado: 2026-10-22
fonte: aws-cli (conta 152774997921)
---
# AWS - Mapa

Hub: [[Hub - AWS]]

```mermaid
flowchart TB
  subgraph Internet
    U[Usuários] --> R53[Route 53]
  end
  R53 --> ALB1[ALB cootravale]
  R53 --> ALB2[ALB star-cotravale]
  R53 --> ALB3[ALB internal]
  ALB1 --> PCCS[EC2 portalccs]
  ALB1 --> OTRS[EC2 otrsapp]
  ALB1 --> SMS[EC2 rpasmartshare]
  ALB1 --> HM[EC2 hm-portalccs]
  ALB2 --> PCCS
  ALB3 --> AF[EC2 srv-prod-airflow]
  OTRS --> MYSQL[(srv-prod-postgresql: MySQL OTRS + Postgres Airflow)]
  AF --> MYSQL
  subgraph us-east-1 Datalake
    GL[Glue jdbc_to_bronze] --> BR[S3 bronze parquet]
    BR --> SI[S3 silver]
    SI --> GO[S3 gold]
    GO --> ATH[Athena]
    EB[EventBridge falhas Glue]
  end
  AF -. dispara .-> GL
  VPN[VPN Nstech] --> GL
  ATH --> PBI[Power BI]
  APIO[Lambda API_OTRS] --> ATH
  OTRS --> APIO
```

## Navegação
- Dependências: [[AWS - Dependências entre servidores]]
- Dependências: [[AWS - Dependências entre servidores]]
- Computação: [[AWS - EC2 (índice)]] · [[AWS - Lambdas (índice)]]
- Dados (parquet): [[S3 - Datalake]] · [[AWS - Glue Jobs]] · [[AWS - Glue Crawlers e Conexões]] · [[AWS - Athena]] · [[AWS - S3 (índice)]]
- Rede: [[AWS - Rede]] · [[ALB - cootravale]] · [[ALB - star-cotravale]] · [[ALB - cootravale-internal]]
- Operação: [[AWS - Monitoramento]] · [[AWS - IAM]] · [[AWS - Tags]] · [[AWS - Achados]]
- Projetos mapeados: [[datalake-glue]] · [[airflow-prod-dags]] · [[API_Lambda]] · [[otrs]] · [[Portal]] · [[IaC]] · [[dw_aso]] · [[Apolo11]]
- Fora da AWS: [[Hub - AWS Hosts e Sites]] (on-premises, Locaweb, fontes Nstech, referências sem instância) · VPCs: [[VPC - cootravale-01]] · [[VPC - cootravale-02]] · [[VPC - cootravale-prod-us-east]]
