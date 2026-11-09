---
tipo: aws-ec2
tags: [aws, aws/ec2, regiao/sa-east-1, estado/running, awstag/backup-sim]
instance_id: i-0a491f110a291b9e9
regiao: sa-east-1
tipo_instancia: t3.large
estado: running
atualizado: 2026-10-22
fonte: aws-cli + ssm + cloudwatch + sg (conta 152774997921)
---
# EC2 - srv-prod-rpasmartshare

**SmartShare + RPA (Selbetti): Windows com IIS, SQL Server 2022, RPA Studio e SmartSigner — assinatura/distribuição de documentos e robôs.**

Hub: [[Hub - AWS Computação]] · [[AWS - Mapa]] · [[AWS - EC2 (índice)]] · [[AWS - Dependências entre servidores]]

## O que faz e como sabemos
- SSM: `RPA.ctv.br`, Windows Server 2022; software: SmartShare, RPA Studio, SmartSigner Agent, SQL Server 2022, IIS URL Rewrite, Zabbix Agent, Bitdefender, OCS Inventory Agent, Wazuh Agent.
- SG `cootravale-smartshare-sg`: "Sistema SmartShare e RPA mantido pela Selbetti"; ALB host `smartshare.cootravale.com.br`.

## Com o que se liga
- Recebe 80/443 do [[EC2 - srv-prod-bitbucketrunner]] e do SG do Airflow (integrações).
- SQL Server 1433 acessado por [[EC2 - srv-prod-cootravalejobs]] e por `srv01-db-sg`.
- Bucket [[S3 - rpa-selbetti]].
- Target groups do ALB: `cootravale-smartshare-tg`:80 (healthy) → [[ALB - cootravale]]

## Quem pode acessar (security groups)
- `cootravale-smartshare-sg` tcp/80-80 ← 0.0.0.0/0, 172.31.48.69/32, cootravale-airflow-sg(sg)
- `cootravale-smartshare-sg` tcp/1433-1433 ← 172.31.50.108/32, cootravale-srv01-db-sg(sg), cootravale-jobs-sg(sg)
- `cootravale-smartshare-sg` all ← 18.231.132.93/32, 172.31.48.69/32, 192.168.168.0/24
- `cootravale-smartshare-sg` tcp/443-443 ← 0.0.0.0/0, 172.31.48.69/32, cootravale-airflow-sg(sg)
- `cootravale-smartshare-sg` tcp/10050-10050 ← 192.168.1.0/24
- `cootravale-smartshare-sg` icmp/-1--1 ← 192.168.1.0/24
- `cootravale-smartshare-sg` tcp/3389-3389 ← (origem não listada: prefix list/IPv6)
- `cootravale-smartshare-sg` tcp/445-445 ← cootravale-jobs-sg(sg)
- `icestechnology-access` tcp/1433-1433 ← cootravale-jobs-sg(sg)

## SG compartilhados
- [[SG - icestechnology-access]]

## Uso real (CloudWatch, 14 dias)
- CPU média **76.36%**, pico 100.0% · rede entrada 150 KB/s / saída 122 KB/s (média)

## Plataforma
- Microsoft Windows Server 2022 Datacenter 10.0.20348 — host `RPA.ctv.br` · tipo `t3.large` · estado **running** · lançada 2023-03-20
- VPC [[VPC - cootravale-01]] · IP privado `172.31.30.38` · IP público: sim
- Instance profile: [[IAM - AmazonSSMRoleForInstancesQuickSetup]] · tags AWS: {"Backup": "Sim", "Name": "srv-prod-rpasmartshare"}
- Monitorada por [[Host - Zabbix (on-premises)]] (porta 10050 liberada para 192.168.1.0/24) e/ou Wazuh quando listado acima.

## Achados
- **CPU média 76% (pico 100%) em 14 dias**: instância saturada (t3.large) — risco de lentidão do RPA.

> Evidência: inventário SSM (parcial — pacotes Linux truncados em 50), regras de SG, métricas CloudWatch, README/scripts dos projetos locais. Itens marcados "inferido" não foram confirmados.
