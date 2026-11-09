---
tipo: aws-achados
tags: [aws, custo, governanca]
atualizado: 2026-10-22
fonte: aws-cli (conta 152774997921)
---
# AWS - Achados

Hub: [[Hub - AWS]] · [[AWS - Tags]]

## Custo / limpeza
- **9 volumes EBS soltos** (1108 GB): `vol-0a067d450728b71af` 250GB (us-east-1), `vol-084c8f58a821af340` 100GB (sa-east-1), `vol-0597146d8ecbd20e3` 400GB (sa-east-1), `vol-011720e0a911b6033` 100GB (sa-east-1), `vol-07f605087fc88270d` 50GB (sa-east-1), `vol-07cdc644e3f4e2c72` 8GB (sa-east-1), `vol-0ad4c98862ed7add5` 50GB (sa-east-1), `vol-0a93bec1886452769` 50GB (sa-east-1), `vol-0d497372c756631d5` 100GB (sa-east-1)
- EC2 paradas (ainda pagam EBS): [[EC2 - vpn-test-ping]], [[EC2 - Srv_AD02]], [[EC2 - srv-prod-syspass NÃO LIGAR]], [[EC2 - spark-server_old]], [[EC2 - srv-prod-ocs NAO LIGAR]], [[EC2 - VM-Backup-Rodopar]]
- EIPs sem associação (várias em sa-east-1 e 3 em us-east-1): cobrança por IP ocioso.
- Log groups >1 GB sem retenção definida (CloudTrail 17 GB, VPNLogs 5 GB, `/aws-glue/jobs/error` 14 GB, Airflow DAGProcessing 1 GB) — [[AWS - Monitoramento]]
- Ambientes MWAA/EMR/AppStream removidos mas roles/log groups remanescentes ([[AWS - IAM]])

## Saúde / inconsistências
- TGs `unhealthy`: cootravale-hml-torreportobelo, cootravale-ocs-tg (aponta IP 172.31.10.35, não a instância srv-prod-ocs), integciot-pub
- TGs sem targets: portal-coop, cootravale-portal-tg, mcp-call-tool, mcp-langfuse, airflow-hml-tg — regras do [[ALB - cootravale]] `api.*` e `airflow-hml.*` encaminham para TGs vazias
- VPN nstech: um túnel DOWN nas duas regiões (sem redundância)
- **Nenhum alarme CloudWatch** configurado
- [[EC2 - srv-prod-postgresql]] hospeda **Postgres (Airflow metadata) e MySQL (OTRS)** — ponto único de falha
- SG `icestechnology-access` anexado à maioria das EC2 (parceiro); vários `launch-wizard-*` genéricos
- Lambdas/Glue/S3 sem tags ([[AWS - Tags]]); Lambda env vars guardam credenciais em texto (test_jdbc_connection, get_incremental_tables, teste_con_sqlserver) → mover para Secrets Manager

## Achados da análise de servidores (SG + métricas)
- [[EC2 - srv-prod-dc01]]: SG libera TODO tráfego para 0.0.0.0/0
- [[EC2 - VM-Backup-Rodopar]]: RDP/80/443 abertos para 0.0.0.0/0 (parada)
- [[EC2 - srv-prod-omnilink]]: porta 12100 pública; SQL Server 2012 / Windows 2016
- [[EC2 - srv-prod-rpasmartshare]]: CPU média 76% (saturada)
- [[EC2 - Srv_AD02]] parado: AD sem redundância
- [[EC2 - srv-prod-databases]]: sem tags, sem uso, sem dono
- [[EC2 - srv-prod-portalcoop]]: ativa sem target group
- Ver [[AWS - Dependências entre servidores]]

## Achados da análise de servidores (SG + métricas)
- [[EC2 - srv-prod-dc01]]: SG libera TODO tráfego para 0.0.0.0/0
- [[EC2 - VM-Backup-Rodopar]]: RDP/80/443 abertos para 0.0.0.0/0 (parada)
- [[EC2 - srv-prod-omnilink]]: porta 12100 pública; SQL Server 2012 / Windows 2016
- [[EC2 - srv-prod-rpasmartshare]]: CPU média 76% (saturada)
- [[EC2 - Srv_AD02]] parado: AD sem redundância
- [[EC2 - srv-prod-databases]]: sem tags, sem uso, sem dono
- [[EC2 - srv-prod-portalcoop]]: ativa sem target group
- Ver [[AWS - Dependências entre servidores]]

## Lambdas (invocações 30d)
- `API_OTRS` é a única em uso (206 invocações); as outras 12 estão sem execução (ver [[AWS - Lambdas (índice)]])
- Lambdas de ingestão `prd_ingestion_*` substituídas pelo Glue `jdbc_to_bronze`; podem ser removidas (liberam ENIs na VPC)
- 3 Lambdas guardam credenciais SQL Server/Postgres em texto nas variáveis de ambiente (`get_incremental_tables`, `test_jdbc_connection`, `teste_con_sqlserver`)
- `presign-canhotos` nunca foi invocada; `CloudDog-SSO-ProviderCreator` em python3.7
