---
tipo: aws-ec2
tags: [aws, aws/ec2, regiao/sa-east-1, estado/running, awstag/backup-sim]
instance_id: i-0acdf03fbfdbfd7a7
regiao: sa-east-1
tipo_instancia: t3.large
estado: running
atualizado: 2026-10-22
fonte: aws-cli + ssm + cloudwatch + sg (conta 152774997921)
---
# EC2 - srv-prod-portalccs

**Portal CCS de produção (Apache + vários apps Node/PHP em portas distintas) — front de `portalccs`, site institucional, CRM, torre Porto Belo, termo ANTT, integrador CIOT, app cooperado, APIPASS.**

Hub: [[Hub - AWS Computação]] · [[AWS - Mapa]] · [[AWS - EC2 (índice)]] · [[AWS - Dependências entre servidores]]

## O que faz e como sabemos
- 9 target groups apontam para esta instância ([[ALB - cootravale]] e [[ALB - star-cotravale]]): portas 80, 81 (nginx), 3000, 3002, 3003, 3010, 3020, 4500, 7070.
- Apache2 instalado; `adcli` (integração com AD); Alloy + CloudWatch Agent.

## Com o que se liga
- Lê SQL Server de [[EC2 - srv-prod-cootravalejobs]] (1433) e dados do datalake via APIs.
- Recebe deploy/uso do nginx descrito em [[proxy-nginx]].
- Par homologação: [[EC2 - srv-hm-portalccs]].
- Target groups do ALB: `apipass`:4500 (healthy) → [[ALB - star-cotravale]]; `cootravale-crm-tg`:7070 (healthy) → [[ALB - cootravale]]; `cootravale-portal-ccs-nginx-tg`:81 (healthy) → [[ALB - cootravale]]; `cootravale-portal-ccs-tg`:80 (healthy) → [[ALB - cootravale]]; `cootravale-torreportobelo`:3000 (healthy) → [[ALB - cootravale]]; `site-cootravale`:3003 (healthy) → [[ALB - cootravale]]; `srv-prod-portalccs-appcoot-pub`:3020 (healthy) → [[ALB - cootravale]]; `srv-prod-portalccs-integciot-pub`:3010 (unhealthy) → [[ALB - cootravale]]; `srv-prod-portalccs-termoantt-pub`:3002 (healthy) → [[ALB - cootravale]]; `teste`:5000 (unused) → 

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
- CPU média **6.46%**, pico 58.23% · rede entrada 993 KB/s / saída 491 KB/s (média)

## Plataforma
- Ubuntu 22.04 — host `ip-172-31-23-226.sa-east-1.compute.internal` · tipo `t3.large` · estado **running** · lançada 2023-03-31
- VPC [[VPC - cootravale-01]] · IP privado `172.31.23.226` · IP público: sim
- Instance profile: [[IAM - AmazonSSMRoleForInstancesQuickSetup]] · tags AWS: {"Backup": "Sim", "Name": "srv-prod-portalccs"}
- Monitorada por [[Host - Zabbix (on-premises)]] (porta 10050 liberada para 192.168.1.0/24) e/ou Wazuh quando listado acima.

## Achados
- Concentra a maioria dos aplicativos públicos: instância única (t3.large) para ~9 serviços; TG integciot-pub unhealthy.

## Projetos relacionados
- [[Portal]]
- [[proxy-nginx]]
- [[PortalPHP5.3]]

> Evidência: inventário SSM (parcial — pacotes Linux truncados em 50), regras de SG, métricas CloudWatch, README/scripts dos projetos locais. Itens marcados "inferido" não foram confirmados.
