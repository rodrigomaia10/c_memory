---
tipo: aws-ec2
tags: [aws, aws/ec2, regiao/sa-east-1, estado/running, awstag/backup-sim]
instance_id: i-050b88d0c9b9228cb
regiao: sa-east-1
tipo_instancia: t4g.xlarge
estado: running
atualizado: 2026-10-22
fonte: aws-cli + ssm + cloudwatch + sg (conta 152774997921)
---
# EC2 - srv-prod-otrsapp

**Aplicação OTRS/Znuny (chamados): Apache 80/443 atrás do [[ALB - cootravale]].**

Hub: [[Hub - AWS Computação]] · [[AWS - Mapa]] · [[AWS - EC2 (índice)]] · [[AWS - Dependências entre servidores]]

## O que faz e como sabemos
- ALB: hosts `chamados`, `otrs`, `chamadoshml`, `otrshml` → TG `cootravale-otrs-tg`.
- SG `otrs-app-sg`: SSH só de um IP fixo; 3306 aceita [[EC2 - srv-prod-cootravalejobs]]; LDAP (389) liberado no SG do AD.

## Com o que se liga
- Banco MySQL em [[EC2 - srv-prod-postgresql]] (otrs.db.ctv.aws).
- Autentica no AD via LDAP: [[EC2 - Srv_AD02]] / [[EC2 - srv-prod-dc01]].
- Consulta a API [[Lambda - API_OTRS (us-east-1)]] (placas via Athena) pelos formulários.
- Acessa SQL Server 1433 em [[EC2 - srv-prod-cootravalejobs]] (portalCooperado).
- Target groups do ALB: `cootravale-otrs-tg`:80 (healthy) → [[ALB - cootravale]]

## Quem pode acessar (security groups)
- `otrs-app-sg` tcp/80-80 ← 0.0.0.0/0
- `otrs-app-sg` all ← 192.168.168.0/24
- `otrs-app-sg` tcp/22-22 ← 187.101.172.22/32
- `otrs-app-sg` tcp/3306-3306 ← cootravale-jobs-sg(sg), cootravale-srv01-db-sg(sg)
- `otrs-app-sg` icmp/-1--1 ← 192.168.1.0/24, 10.90.0.0/24, 10.50.0.0/24
- `otrs-app-sg` tcp/10050-10050 ← 192.168.1.0/24
- `otrs-app-sg` tcp/443-443 ← 0.0.0.0/0
- `icestechnology-access` tcp/1433-1433 ← cootravale-jobs-sg(sg)

## SG compartilhados
- [[SG - icestechnology-access]]

## Uso real (CloudWatch, 14 dias)
- CPU média **5.83%**, pico 52.74% · rede entrada 5.33 MB/s / saída 987 KB/s (média)

## Plataforma
- SO: ubuntu/images/hvm-ssd/ubuntu-focal-20.04-arm64-server-20220419 · tipo `t4g.xlarge` · estado **running** · lançada 2026-09-03
- VPC [[VPC - cootravale-01]] · IP privado `172.31.3.170` · IP público: sim
- Instance profile: `—` ([[AWS - IAM]]) · tags AWS: {"Backup": "Sim", "Name": "srv-prod-otrsapp"}
- Monitorada por [[Host - Zabbix (on-premises)]] (porta 10050 liberada para 192.168.1.0/24) e/ou Wazuh quando listado acima.

## Achados
- Maior tráfego de entrada da frota (~5 MB/s médio). Ubuntu 20.04 (fim de suporte padrão).

## Projetos relacionados
- [[otrs]]
- [[API_Lambda]]

> Evidência: inventário SSM (parcial — pacotes Linux truncados em 50), regras de SG, métricas CloudWatch, README/scripts dos projetos locais. Itens marcados "inferido" não foram confirmados.
