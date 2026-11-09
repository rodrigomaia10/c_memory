---
tipo: aws-ec2
tags: [aws, aws/ec2, regiao/sa-east-1, estado/stopped, awstag/backup-sim]
instance_id: i-0f4aa6d2377315ec8
regiao: sa-east-1
tipo_instancia: t3.small
estado: stopped
atualizado: 2026-10-22
fonte: aws-cli + ssm + cloudwatch + sg (conta 152774997921)
---
# EC2 - srv-prod-syspass NÃO LIGAR

**SysPass (cofre de senhas, parado, "NÃO LIGAR").**

Hub: [[Hub - AWS Computação]] · [[AWS - Mapa]] · [[AWS - EC2 (índice)]] · [[AWS - Dependências entre servidores]]

## O que faz e como sabemos
- ALB host `syspass.cootravale.com.br` → TG `cootravale-syspass-tg` (unused).

## Com o que se liga
- Era acessado via [[ALB - cootravale]].
- Target groups do ALB: `cootravale-syspass-tg`:80 (unused) → [[ALB - cootravale]]

## Quem pode acessar (security groups)
- `icestechnology-access` tcp/1433-1433 ← cootravale-jobs-sg(sg)
- `cootravale-syspass-sg` tcp/80-80 ← cootravale-lb-sg(sg)
- `cootravale-syspass-sg` tcp/1515-1515 ← (origem não listada: prefix list/IPv6)
- `cootravale-syspass-sg` all ← 192.168.168.0/24
- `cootravale-syspass-sg` udp/1514-1514 ← (origem não listada: prefix list/IPv6)
- `cootravale-syspass-sg` tcp/22-22 ← 187.75.92.145/32, 192.168.1.0/24
- `cootravale-syspass-sg` tcp/1514-1514 ← (origem não listada: prefix list/IPv6)
- `cootravale-syspass-sg` udp/1515-1515 ← (origem não listada: prefix list/IPv6)
- `cootravale-syspass-sg` tcp/443-443 ← (origem não listada: prefix list/IPv6)
- `cootravale-syspass-sg` icmp/-1--1 ← 192.168.1.0/24
- `cootravale-syspass-sg` tcp/10050-10050 ← 192.168.1.0/24

## SG compartilhados
- [[SG - icestechnology-access]]

## Uso real (CloudWatch, 14 dias)
- Parada (sem métricas)

## Plataforma
- SO: AMI não encontrada (sem acesso/removida) · tipo `t3.small` · estado **stopped** · lançada 2025-02-12
- VPC [[VPC - cootravale-01]] · IP privado `172.31.10.23` · IP público: não
- Instance profile: [[IAM - AmazonSSMRoleForInstancesQuickSetup]] · tags AWS: {"Name": "srv-prod-syspass N�O LIGAR", "Backup": "Sim"}
- Monitorada por [[Host - Zabbix (on-premises)]] (porta 10050 liberada para 192.168.1.0/24) e/ou Wazuh quando listado acima.

## Achados
- Cofre de senhas parado: confirmar onde as credenciais vivem hoje.

> Evidência: inventário SSM (parcial — pacotes Linux truncados em 50), regras de SG, métricas CloudWatch, README/scripts dos projetos locais. Itens marcados "inferido" não foram confirmados.
