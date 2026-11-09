---
tipo: aws-ec2
tags: [aws, aws/ec2, regiao/sa-east-1, estado/running, awstag/backup-sim, awstag/managed-by-terraform, awstag/projeto-bi]
instance_id: i-033b8a37c75cb7a08
regiao: sa-east-1
tipo_instancia: t3.medium
estado: running
atualizado: 2026-10-22
fonte: aws-cli + ssm + cloudwatch + sg (conta 152774997921)
---
# EC2 - srv-prod-bitbucketrunner

**Runner do Bitbucket Pipelines (CI/CD) — host que também responde como `airflow.ctv.aws`/`api-cootravale`.**

Hub: [[Hub - AWS Computação]] · [[AWS - Mapa]] · [[AWS - EC2 (índice)]] · [[AWS - Dependências entre servidores]]

## O que faz e como sabemos
- Tags `managed-by=terraform`, `Projeto=BI`; EIP nomeada "airflow"; DNS `airflow.ctv.aws` → este IP.
- O SG de [[EC2 - srv-hm-portalccs]] libera SSH apenas de `172.31.48.69` (este host) e o de [[EC2 - srv-prod-rpasmartshare]] libera 80/443/all para o mesmo IP.

## Com o que se liga
- Faz deploy por SSH em [[EC2 - srv-hm-portalccs]] (homologação do portal).
- Acessa o SmartShare em [[EC2 - srv-prod-rpasmartshare]] (regra dedicada para este IP).
- Pipelines dos repositórios [[airflow-prod-dags]] / [[dw_aso]] (Bitbucket `ctv-ti`).

## Quem pode acessar (security groups)
- `internal-network` all ← 172.31.0.0/16
- `icestechnology-access` tcp/1433-1433 ← cootravale-jobs-sg(sg)

## SG compartilhados
- [[SG - icestechnology-access]]
- [[SG - internal-network]]

## Uso real (CloudWatch, 14 dias)
- CPU média **2.57%**, pico 66.65% · rede entrada 81 KB/s / saída 44 KB/s (média)

## Plataforma
- Ubuntu 22.04 — host `ip-172-31-48-69.sa-east-1.compute.internal` · tipo `t3.medium` · estado **running** · lançada 2026-03-16
- VPC [[VPC - cootravale-01]] · IP privado `172.31.48.69` · IP público: sim
- Instance profile: [[IAM - profile-S3-EC2]] · tags AWS: {"Backup": "Sim", "Name": "srv-prod-bitbucketrunner", "managed-by": "terraform", "Projeto": "BI"}

## Achados
- Pacotes antigos (Ubuntu 22.04, awscli 1.22). Servidor com IP público.

## Projetos relacionados
- [[runner airflow]]
- [[airflow-prod-dags]]
- [[IaC]]
- [[api-cootravale]]

> Evidência: inventário SSM (parcial — pacotes Linux truncados em 50), regras de SG, métricas CloudWatch, README/scripts dos projetos locais. Itens marcados "inferido" não foram confirmados.
