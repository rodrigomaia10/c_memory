---
tipo: aws-ec2
tags: [aws, aws/ec2, regiao/sa-east-1, estado/running, awstag/backup-sim]
instance_id: i-0e4f0b7a5a9f34179
regiao: sa-east-1
tipo_instancia: t3.xlarge
estado: running
atualizado: 2026-10-22
fonte: aws-cli + ssm + cloudwatch + sg (conta 152774997921)
---
# EC2 - srv-prod-airflow

**Airflow 3.1.7 de produção: orquestra Lambdas e jobs Glue (jdbc→bronze→silver→gold).**

Hub: [[Hub - AWS Computação]] · [[AWS - Mapa]] · [[AWS - EC2 (índice)]] · [[AWS - Dependências entre servidores]]

## O que faz e como sabemos
- README de [[airflow-prod-dags]]; atrás do ALB interno [[ALB - cootravale-internal]] (`airflow-prod.cootravale.com.br`, TG `srv-prod-airflow-tg:8080`).
- Role `EC2AirflowProdRole` com acesso a S3/Glue/Lambda; metadata DB em [[EC2 - srv-prod-postgresql]].

## Com o que se liga
- Dispara jobs de [[AWS - Glue Jobs]] e Lambdas de ingestão ([[AWS - Lambdas (índice)]]) em us-east-1 via peering.
- Banco de metadados: [[EC2 - srv-prod-postgresql]] (5432).
- Acessa [[EC2 - srv-prod-rpasmartshare]] (80/443 liberados para o SG airflow) — DAGs que consomem o SmartShare.

## Quem pode acessar (security groups)
- `srv-prod-airflow` tcp/8080-8080 ← default(sg)
- `srv-prod-airflow` tcp/22-22 ← (origem não listada: prefix list/IPv6)

## Uso real (CloudWatch, 14 dias)
- CPU média **11.69%**, pico 17.77% · rede entrada 1.90 MB/s / saída 2.10 MB/s (média)

## Plataforma
- Amazon Linux 2023 — host `ip-192-168-168-69.sa-east-1.compute.internal` · tipo `t3.xlarge` · estado **running** · lançada 2026-02-18
- VPC [[VPC - cootravale-02]] · IP privado `192.168.168.69` · IP público: não
- Instance profile: [[IAM - EC2AirflowProdRole]] · tags AWS: {"Name": "srv-prod-airflow", "Backup": "Sim"}

## Achados
- Sem acesso SSH liberado (só 8080 do ALB); gestão só por SSM.

## Projetos relacionados
- [[airflow-prod-dags]]
- [[runner airflow]]
- [[datalake-glue]]

> Evidência: inventário SSM (parcial — pacotes Linux truncados em 50), regras de SG, métricas CloudWatch, README/scripts dos projetos locais. Itens marcados "inferido" não foram confirmados.
