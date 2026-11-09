---
tipo: aws-ec2
tags: [aws, aws/ec2, regiao/sa-east-1, estado/running]
instance_id: i-0e414b931809e9a70
regiao: sa-east-1
tipo_instancia: t3.large
estado: running
atualizado: 2026-10-22
fonte: aws-cli + ssm + cloudwatch + sg (conta 152774997921)
---
# EC2 - srv-prod-databases

**Servidor de bancos sem função confirmada (Amazon Linux 2023 recente, SSH só).**

Hub: [[Hub - AWS Computação]] · [[AWS - Mapa]] · [[AWS - EC2 (índice)]] · [[AWS - Dependências entre servidores]]

## O que faz e como sabemos
- AMI de 2026-08; SG só com SSH; CPU média 1,2%; tráfego ~33 KB/s; sem tags e sem DNS nem TG associado.

## Com o que se liga
- Nenhum SG ou DNS de outro servidor aponta para ele.

## Quem pode acessar (security groups)
- `srv-prod-databases` tcp/22-22 ← (origem não listada: prefix list/IPv6)

## Uso real (CloudWatch, 14 dias)
- CPU média **1.2%**, pico 22.21% · rede entrada 33 KB/s / saída 2 KB/s (média)

## Plataforma
- Amazon Linux 2023 — host `ip-172-31-52-118.sa-east-1.compute.internal` · tipo `t3.large` · estado **running** · lançada 2026-09-22
- VPC [[VPC - cootravale-01]] · IP privado `172.31.52.118` · IP público: não
- Instance profile: `—` ([[AWS - IAM]]) · tags AWS: {"Name": "srv-prod-databases"}

## Achados
- **Sem uso aparente e sem dono**: perguntar à equipe de infra antes de desligar.

> Evidência: inventário SSM (parcial — pacotes Linux truncados em 50), regras de SG, métricas CloudWatch, README/scripts dos projetos locais. Itens marcados "inferido" não foram confirmados.
