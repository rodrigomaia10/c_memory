---
tipo: aws-ec2
tags: [aws, aws/ec2, regiao/sa-east-1, estado/stopped]
instance_id: i-078da820516dda007
regiao: sa-east-1
tipo_instancia: t3.medium
estado: stopped
atualizado: 2026-10-22
fonte: aws-cli + ssm + cloudwatch + sg (conta 152774997921)
---
# EC2 - srv-prod-ocs NAO LIGAR

**OCS Inventory (parada, "NAO LIGAR"): inventário de ativos.**

Hub: [[Hub - AWS Computação]] · [[AWS - Mapa]] · [[AWS - EC2 (índice)]] · [[AWS - Dependências entre servidores]]

## O que faz e como sabemos
- SG sem regras; ALB `inventory.cootravale.com.br` aponta para o IP 172.31.10.35 (não é esta instância).

## Com o que se liga
- Agentes OCS ainda instalados em [[EC2 - srv-prod-rpasmartshare]].

## Quem pode acessar (security groups)
- `SG-SRV-OCS` all ← (origem não listada: prefix list/IPv6)

## Uso real (CloudWatch, 14 dias)
- Parada (sem métricas)

## Plataforma
- SO: ubuntu/images/hvm-ssd-gp3/ubuntu-noble-24.04-amd64-server-20250115 · tipo `t3.medium` · estado **stopped** · lançada 2025-10-16
- VPC [[VPC - cootravale-02]] · IP privado `192.168.168.70` · IP público: não
- Instance profile: `—` ([[AWS - IAM]]) · tags AWS: {"Name": "srv-prod-ocs NAO LIGAR"}

## Achados
- ALB aponta para IP fantasma (unhealthy); limpar o target group.

> Evidência: inventário SSM (parcial — pacotes Linux truncados em 50), regras de SG, métricas CloudWatch, README/scripts dos projetos locais. Itens marcados "inferido" não foram confirmados.
