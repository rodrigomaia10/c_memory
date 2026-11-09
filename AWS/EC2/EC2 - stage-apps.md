---
tipo: aws-ec2
tags: [aws, aws/ec2, regiao/us-east-1, estado/running, awstag/role-stage-apps]
instance_id: i-04bb88b22f0e4f514
regiao: us-east-1
tipo_instancia: t4g.medium
estado: running
atualizado: 2026-10-22
fonte: aws-cli + ssm + cloudwatch + sg (conta 152774997921)
---
# EC2 - stage-apps

**Ambiente de stage de aplicações (Ubuntu 24.04 arm64): HTTP/HTTPS público e wildcard `*.stage-apps.cootravale.com.br`.**

Hub: [[Hub - AWS Computação]] · [[AWS - Mapa]] · [[AWS - EC2 (índice)]] · [[AWS - Dependências entre servidores]]

## O que faz e como sabemos
- SG `ec2-stage-apps` 80/443; Route 53 `*.stage-apps`; role de deploy `stage-apps-deployer` e bucket [[S3 - cootravale-stage-apps-releases]].

## Com o que se liga
- Usa o Postgres [[EC2 - postgres01]] (porta 5432 só para este SG).

## Quem pode acessar (security groups)
- `ec2-stage-apps` tcp/80-80 ← 0.0.0.0/0
- `ec2-stage-apps` udp/443-443 ← 0.0.0.0/0
- `ec2-stage-apps` tcp/443-443 ← 0.0.0.0/0

## Uso real (CloudWatch, 14 dias)
- CPU média **2.11%**, pico 48.62% · rede entrada 37 KB/s / saída 19 KB/s (média)

## Plataforma
- SO: ubuntu/images/hvm-ssd-gp3/ubuntu-noble-24.04-arm64-server-20260610 · tipo `t4g.medium` · estado **running** · lançada 2026-09-15
- VPC [[VPC - cootravale-prod-us-east]] · IP privado `172.20.252.178` · IP público: sim
- Instance profile: [[IAM - ec2-stage-apps]] · tags AWS: {"Role": "stage-apps", "Name": "stage-apps"}

## Achados
- Único host público de us-east-1; está fora do datalake.

## Projetos relacionados
- [[IaC]]

> Evidência: inventário SSM (parcial — pacotes Linux truncados em 50), regras de SG, métricas CloudWatch, README/scripts dos projetos locais. Itens marcados "inferido" não foram confirmados.
