---
tipo: aws-ec2
tags: [aws, aws/ec2, regiao/sa-east-1, estado/running, awstag/backup-sim]
instance_id: i-0e3d160f229a44316
regiao: sa-east-1
tipo_instancia: t3.xlarge
estado: running
atualizado: 2026-10-22
fonte: aws-cli + ssm + cloudwatch + sg (conta 152774997921)
---
# EC2 - srv-prod-cootravalejobs

**Servidor Windows de jobs/automação de BI: SQL Server (portalCooperado), **gateway de dados on-premises do Power BI**, Power BI Desktop e ferramentas de carga.**

Hub: [[Hub - AWS Computação]] · [[AWS - Mapa]] · [[AWS - EC2 (índice)]] · [[AWS - Dependências entre servidores]]

## O que faz e como sabemos
- SSM: Windows Server 2022, hostname `cootravale-jobs.ctv.br`; software: SQL Server 2019, On-premises data gateway, Power BI Desktop, SSMS, DBeaver, Npgsql/psqlodbc/pgJDBC/MySQL Connector, Pontomais Collector, SDoc-E, AnyDesk, Wazuh Agent.
- Script do projeto api_powerbi_shell classifica `172.31.14.242` como `SQL_Express_local` (fonte de relatórios).
- Conexões Glue `sqlserver-cootravale-connection` e `Jdbc connection` apontam para `172.31.14.242:1433/portalCooperado`.

## Com o que se liga
- Fonte/destino dos jobs `Portal_*`/`Lista_Operacional` ([[AWS - Glue Jobs]]).
- Abre conexões para [[EC2 - srv-prod-postgresql]] (5432) e é aceito pelo MySQL do OTRS e pelo SQL Server do [[EC2 - srv-prod-rpasmartshare]].
- Alimenta relatórios do [[PowerBIClaudio]] via gateway.
- SG `cootravale-jobs-sg` referenciado por vários outros SGs (hub da rede).

## Quem pode acessar (security groups)
- `icestechnology-access` tcp/1433-1433 ← cootravale-jobs-sg(sg)
- `cootravale-jobs-sg` tcp/1433-1433 ← 172.31.0.0/16, 10.0.0.0/8, 192.168.168.0/24, 172.20.252.0/22, 172.35.0.0/16, 192.168.1.0/24, cootravale-jobs-sg(sg), glue-otrs-access(sg)
- `cootravale-jobs-sg` tcp/0-65535 ← 191.233.242.194/32, cootravale-jobs-sg(sg)
- `cootravale-jobs-sg` all ← 172.30.50.0/32, 192.168.168.0/24, 189.42.20.190/32, 172.35.0.0/16
- `cootravale-jobs-sg` tcp/21-21 ← 3.212.10.26/32, 20.84.72.154/32
- `cootravale-jobs-sg` tcp/50000-51000 ← 3.212.10.26/32, 20.84.72.154/32
- `cootravale-jobs-sg` tcp/10050-10050 ← 192.168.1.0/24
- `cootravale-jobs-sg` icmp/-1--1 ← 192.168.1.0/24
- `cootravale-jobs-sg` tcp/3389-3389 ← 192.168.1.0/24

## SG compartilhados
- [[SG - icestechnology-access]]

## Uso real (CloudWatch, 14 dias)
- CPU média **15.82%**, pico 100.0% · rede entrada 9.66 MB/s / saída 1.50 MB/s (média)

## Plataforma
- Microsoft Windows Server 2022 Datacenter 10.0.20348 — host `cootravale-jobs.ctv.br` · tipo `t3.xlarge` · estado **running** · lançada 2026-02-26
- VPC [[VPC - cootravale-01]] · IP privado `172.31.14.242` · IP público: sim
- Instance profile: [[IAM - EC2CootravaleJobsRole]] · tags AWS: {"Backup": "Sim", "Name": "srv-prod-cootravalejobs"}
- Monitorada por [[Host - Zabbix (on-premises)]] (porta 10050 liberada para 192.168.1.0/24) e/ou Wazuh quando listado acima.

## Achados
- Muito referenciado por outros SGs; CPU com picos de 100% e ~10 MB/s de entrada. SG com portas 0-65535 aberto para IPs externos específicos — revisar.

## Projetos relacionados
- [[Portal]]
- [[datalake-glue]]
- [[PowerBIClaudio]]
- [[api_powerbi_shell]]

> Evidência: inventário SSM (parcial — pacotes Linux truncados em 50), regras de SG, métricas CloudWatch, README/scripts dos projetos locais. Itens marcados "inferido" não foram confirmados.
