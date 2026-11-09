---
tipo: aws-ec2
tags: [aws, aws/ec2, regiao/sa-east-1, estado/running, awstag/backup-sim]
instance_id: i-05cfa9f120bcaffcf
regiao: sa-east-1
tipo_instancia: t3.large
estado: running
atualizado: 2026-10-22
fonte: aws-cli + ssm + cloudwatch + sg (conta 152774997921)
---
# EC2 - srv-prod-portalcoop

**Portal do cooperado (produção): Apache com `adcli`, hostname `porta-coop`.**

Hub: [[Hub - AWS Computação]] · [[AWS - Mapa]] · [[AWS - EC2 (índice)]] · [[AWS - Dependências entre servidores]]

## O que faz e como sabemos
- SG `launch-wizard-1` compartilhado com portalccs (8181 público, MySQL 3306 de IP externo).
- Sem target group ativo no ALB (`cootravale-portal-tg` e `portal-coop` estão vazios).

## Com o que se liga
- Irmão de [[EC2 - srv-prod-portalccs]]; recebe tráfego do [[ALB - star-cotravale]] só se o TG `portal-coop` for religado (hoje sem targets).

## Quem pode acessar (security groups)
- `icestechnology-access` tcp/1433-1433 ← cootravale-jobs-sg(sg)
- `launch-wizard-1` tcp/0-65535 ← default(sg)
- `launch-wizard-1` all ← 192.168.168.0/24, STAR.contravale-lb(sg), cootravale-lb-sg(sg)
- `launch-wizard-1` tcp/22-22 ← 172.31.0.0/16
- `launch-wizard-1` tcp/8181-8181 ← 0.0.0.0/0
- `launch-wizard-1` tcp/3306-3306 ← 3.212.10.26/32
- `launch-wizard-1` tcp/10050-10050 ← 192.168.1.203/32
- `launch-wizard-1` icmp/-1--1 ← 192.168.1.0/24

## SG compartilhados
- [[SG - icestechnology-access]]
- [[SG - launch-wizard-1]]

## Uso real (CloudWatch, 14 dias)
- CPU média **2.16%**, pico 53.61% · rede entrada 49 KB/s / saída 22 KB/s (média)

## Plataforma
- Ubuntu 22.04 — host `porta-coop` · tipo `t3.large` · estado **running** · lançada 2023-09-13
- VPC [[VPC - cootravale-01]] · IP privado `172.31.2.247` · IP público: sim
- Instance profile: [[IAM - AmazonSSMRoleForInstancesQuickSetup]] · tags AWS: {"Backup": "Sim", "Name": "srv-prod-portalcoop"}
- Monitorada por [[Host - Zabbix (on-premises)]] (porta 10050 liberada para 192.168.1.0/24) e/ou Wazuh quando listado acima.

## Achados
- Instância rodando sem target group — confirmar se ainda é usada (rede ~50 KB/s).

## Projetos relacionados
- [[Portal]]

> Evidência: inventário SSM (parcial — pacotes Linux truncados em 50), regras de SG, métricas CloudWatch, README/scripts dos projetos locais. Itens marcados "inferido" não foram confirmados.
