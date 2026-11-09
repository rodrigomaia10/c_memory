---
tipo: aws-ec2
tags: [aws, aws/ec2, regiao/sa-east-1, estado/running, awstag/backup-sim]
instance_id: i-0754a71f9eeecd8fe
regiao: sa-east-1
tipo_instancia: c4.xlarge
estado: running
atualizado: 2026-10-22
fonte: aws-cli + ssm + cloudwatch + sg (conta 152774997921)
---
# EC2 - srv-prod-omnilink

**Servidor Omnilink (rastreamento/telemetria, inferido): Windows 2016 com SQL Server 2012 e aplicação em 12100/tcp.**

Hub: [[Hub - AWS Computação]] · [[AWS - Mapa]] · [[AWS - EC2 (índice)]] · [[AWS - Dependências entre servidores]]

## O que faz e como sabemos
- SSM: `OMNILINK.ctv.br`, Windows Server 2016; software: SQL Server 2012, Carsybde, Macro Recorder, Disk Savvy, Zabbix Agent, Wazuh Agent.
- SG `launch-wizard-3`: porta 12100 aberta para 0.0.0.0/0; backups no bucket [[S3 - bkpomnilink]].

## Com o que se liga
- Backup em [[S3 - bkpomnilink]]. Sem outros vínculos detectados.

## Quem pode acessar (security groups)
- `icestechnology-access` tcp/1433-1433 ← cootravale-jobs-sg(sg)
- `launch-wizard-3` all ← 192.168.168.0/24
- `launch-wizard-3` tcp/12100-12100 ← 0.0.0.0/0
- `launch-wizard-3` icmp/-1--1 ← 192.168.1.203/32
- `launch-wizard-3` tcp/10050-10050 ← 192.168.1.203/32
- `launch-wizard-3` tcp/3389-3389 ← (origem não listada: prefix list/IPv6)

## SG compartilhados
- [[SG - icestechnology-access]]

## Uso real (CloudWatch, 14 dias)
- CPU média **4.6%**, pico 32.94% · rede entrada 75 KB/s / saída 40 KB/s (média)

## Plataforma
- Microsoft Windows Server 2016 Datacenter 10.0.14393 — host `OMNILINK.ctv.br` · tipo `c4.xlarge` · estado **running** · lançada 2025-07-08
- VPC [[VPC - cootravale-01]] · IP privado `172.31.4.118` · IP público: sim
- Instance profile: [[IAM - AmazonSSMRoleForInstancesQuickSetup]] · tags AWS: {"Name": "srv-prod-omnilink", "Backup": "Sim"}
- Monitorada por [[Host - Zabbix (on-premises)]] (porta 10050 liberada para 192.168.1.0/24) e/ou Wazuh quando listado acima.

## Achados
- SQL Server 2012 e Windows 2016 fora de suporte; porta 12100 pública — revisar exposição.

> Evidência: inventário SSM (parcial — pacotes Linux truncados em 50), regras de SG, métricas CloudWatch, README/scripts dos projetos locais. Itens marcados "inferido" não foram confirmados.
