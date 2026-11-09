---
tipo: aws-ec2
tags: [aws, aws/ec2, regiao/sa-east-1, estado/stopped]
instance_id: i-064e8d13ab5891006
regiao: sa-east-1
tipo_instancia: t3.medium
estado: stopped
atualizado: 2026-10-22
fonte: aws-cli + ssm + cloudwatch + sg (conta 152774997921)
---
# EC2 - VM-Backup-Rodopar

**VM de backup do ERP Rodopar (parada): disco de 400 GB standard.**

Hub: [[Hub - AWS Computação]] · [[AWS - Mapa]] · [[AWS - EC2 (índice)]] · [[AWS - Dependências entre servidores]]

## O que faz e como sabemos
- Bucket [[S3 - vm-backup-rodopar]]; PBI script marca Rodopar como legado.

## Com o que se liga
- Guarda cópias do legado Rodopar ([[Hub - Legado]]).

## Quem pode acessar (security groups)
- `launch-wizard-7` tcp/80-80 ← 0.0.0.0/0
- `launch-wizard-7` tcp/443-443 ← 0.0.0.0/0
- `launch-wizard-7` tcp/3389-3389 ← 0.0.0.0/0

## Uso real (CloudWatch, 14 dias)
- Parada (sem métricas)

## Plataforma
- SO: AMI não encontrada (sem acesso/removida) · tipo `t3.medium` · estado **stopped** · lançada 2025-02-17
- VPC [[VPC - cootravale-01]] · IP privado `172.31.28.166` · IP público: não
- Instance profile: `—` ([[AWS - IAM]]) · tags AWS: {"Name": "VM-Backup-Rodopar"}

## Achados
- **SG com 3389 (RDP), 80 e 443 abertos para 0.0.0.0/0** — mesmo parada, não ligar sem fechar.

> Evidência: inventário SSM (parcial — pacotes Linux truncados em 50), regras de SG, métricas CloudWatch, README/scripts dos projetos locais. Itens marcados "inferido" não foram confirmados.
