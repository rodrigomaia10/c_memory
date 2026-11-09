---
tipo: aws-ec2
tags: [aws, aws/ec2, regiao/us-east-1, estado/running, awstag/role-postgres]
instance_id: i-0bb71d01a338ff088
regiao: us-east-1
tipo_instancia: t4g.small
estado: running
atualizado: 2026-10-22
fonte: aws-cli + ssm + cloudwatch + sg (conta 152774997921)
---
# EC2 - postgres01

**Postgres do ambiente stage (Ubuntu 26.04 arm64).**

Hub: [[Hub - AWS Computação]] · [[AWS - Mapa]] · [[AWS - EC2 (índice)]] · [[AWS - Dependências entre servidores]]

## O que faz e como sabemos
- SG `postgres-stage-sg`: 5432 só da VPC us-east-1 e de [[EC2 - stage-apps]]; DNS `postgres01.ctv.aws`; tag `DbHostname`.

## Com o que se liga
- Banco do [[EC2 - stage-apps]]; as Lambdas de teste (VPC us-east-1) com `POSTGRES_HOST` podem usá-lo (não confirmado).

## Quem pode acessar (security groups)
- `postgres-stage-sg` tcp/5432-5432 ← 172.20.252.0/22, ec2-stage-apps(sg)

## Uso real (CloudWatch, 14 dias)
- CPU média **1.11%**, pico 28.37% · rede entrada 19 KB/s / saída 18 KB/s (média)

## Plataforma
- SO: ubuntu/images/hvm-ssd-gp3/ubuntu-resolute-26.04-arm64-server-20260604 · tipo `t4g.small` · estado **running** · lançada 2026-09-14
- VPC [[VPC - cootravale-prod-us-east]] · IP privado `172.20.252.90` · IP público: não
- Instance profile: [[IAM - ec2-postgres-banco]] · tags AWS: {"DbHostname": "postgres01.ctv.aws", "Role": "Postgres", "Name": "postgres01"}

## Achados
- Ubuntu 26.04 é versão não-LTS/recente — conferir suporte.

> Evidência: inventário SSM (parcial — pacotes Linux truncados em 50), regras de SG, métricas CloudWatch, README/scripts dos projetos locais. Itens marcados "inferido" não foram confirmados.
