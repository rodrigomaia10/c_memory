---
tipo: aws-ec2
tags: [aws, aws/ec2, regiao/sa-east-1, estado/stopped]
instance_id: i-0ebe4de43de14a012
regiao: sa-east-1
tipo_instancia: t4g.nano
estado: stopped
atualizado: 2026-10-22
fonte: aws-cli + ssm + cloudwatch + sg (conta 152774997921)
---
# EC2 - vpn-test-ping

**Instância de teste de conectividade VPN (só ICMP) — parada.**

Hub: [[Hub - AWS Computação]] · [[AWS - Mapa]] · [[AWS - EC2 (índice)]] · [[AWS - Dependências entre servidores]]

## O que faz e como sabemos
- SG `cootravale-ping-sg`: apenas ICMP.

## Com o que se liga
- Usada para testar [[AWS - Rede]] (VPNs).

## Quem pode acessar (security groups)
- `cootravale-ping-sg` icmpv6/-1--1 ← (origem não listada: prefix list/IPv6)
- `cootravale-ping-sg` icmp/-1--1 ← 0.0.0.0/0

## Uso real (CloudWatch, 14 dias)
- Parada (sem métricas)

## Plataforma
- SO: ubuntu/images/hvm-ssd/ubuntu-focal-20.04-arm64-server-20211129 · tipo `t4g.nano` · estado **stopped** · lançada 2022-04-28
- VPC [[VPC - cootravale-01]] · IP privado `172.31.36.210` · IP público: não
- Instance profile: [[IAM - AmazonSSMRoleForInstancesQuickSetup]] · tags AWS: {"Name": "vpn-test-ping"}

## Achados
- Pode ser removida.

> Evidência: inventário SSM (parcial — pacotes Linux truncados em 50), regras de SG, métricas CloudWatch, README/scripts dos projetos locais. Itens marcados "inferido" não foram confirmados.
