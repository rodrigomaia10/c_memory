---
tipo: aws-ec2
tags: [aws, aws/ec2, regiao/sa-east-1, estado/running, awstag/backup-sim]
instance_id: i-0832350b4ad4d5f5d
regiao: sa-east-1
tipo_instancia: c4.xlarge
estado: running
atualizado: 2026-10-22
fonte: aws-cli + ssm + cloudwatch + sg (conta 152774997921)
---
# EC2 - srv-prod-wazuh

**Servidor Wazuh (SIEM/EDR): recebe logs/alertas dos agentes.**

Hub: [[Hub - AWS Computação]] · [[AWS - Mapa]] · [[AWS - EC2 (índice)]] · [[AWS - Dependências entre servidores]]

## O que faz e como sabemos
- SG `cootravale-wazuh-sg`: portas 1514/1515 (agente) e 80; DNS `wazuh.cootravale.com.br` e `wazuh.ctv.aws`.
- Agente Wazuh instalado em [[EC2 - srv-prod-cootravalejobs]], [[EC2 - srv-prod-rpasmartshare]] e [[EC2 - srv-prod-omnilink]] (inventário SSM).

## Com o que se liga
- Recebe dados dos servidores Windows com agente Wazuh acima.

## Quem pode acessar (security groups)
- `internal-network` all ← 172.31.0.0/16
- `icestechnology-access` tcp/1433-1433 ← cootravale-jobs-sg(sg)
- `cootravale-wazuh-sg` tcp/80-80 ← (origem não listada: prefix list/IPv6)
- `cootravale-wazuh-sg` tcp/1515-1515 ← (origem não listada: prefix list/IPv6)
- `cootravale-wazuh-sg` all ← 192.168.168.0/24
- `cootravale-wazuh-sg` udp/1514-1514 ← (origem não listada: prefix list/IPv6)
- `cootravale-wazuh-sg` tcp/22-22 ← (origem não listada: prefix list/IPv6)
- `cootravale-wazuh-sg` tcp/1514-1514 ← (origem não listada: prefix list/IPv6)
- `cootravale-wazuh-sg` udp/1515-1515 ← (origem não listada: prefix list/IPv6)
- `cootravale-wazuh-sg` tcp/10050-10050 ← 192.168.1.0/24
- `cootravale-wazuh-sg` icmp/-1--1 ← 192.168.1.0/24
- `cootravale-wazuh-sg` tcp/443-443 ← 189.42.20.190/32, 170.82.194.185/32

## SG compartilhados
- [[SG - icestechnology-access]]
- [[SG - internal-network]]

## Uso real (CloudWatch, 14 dias)
- CPU média **1.11%**, pico 7.29% · rede entrada 2 KB/s / saída 0 KB/s (média)

## Plataforma
- SO: ubuntu/images/hvm-ssd/ubuntu-jammy-22.04-amd64-server-20230919 · tipo `c4.xlarge` · estado **running** · lançada 2025-10-16
- VPC [[VPC - cootravale-01]] · IP privado `172.31.1.139` · IP público: sim
- Instance profile: [[IAM - AmazonSSMRoleForInstancesQuickSetup]] · tags AWS: {"Name": "srv-prod-wazuh", "Backup": "Sim"}
- Monitorada por [[Host - Zabbix (on-premises)]] (porta 10050 liberada para 192.168.1.0/24) e/ou Wazuh quando listado acima.

## Achados
- Baixo uso (CPU 1%); SG compartilhado `internal-network` abre tudo na VPC.

> Evidência: inventário SSM (parcial — pacotes Linux truncados em 50), regras de SG, métricas CloudWatch, README/scripts dos projetos locais. Itens marcados "inferido" não foram confirmados.
