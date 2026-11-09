---
tipo: aws-ec2
tags: [aws, aws/ec2, regiao/sa-east-1, estado/stopped]
instance_id: i-09e80602b94f4d4e9
regiao: sa-east-1
tipo_instancia: t3.medium
estado: stopped
atualizado: 2026-10-22
fonte: aws-cli + ssm + cloudwatch + sg (conta 152774997921)
---
# EC2 - Srv_AD02

**Segundo controlador de domínio (parado): LDAP/Kerberos/DNS.**

Hub: [[Hub - AWS Computação]] · [[AWS - Mapa]] · [[AWS - EC2 (índice)]] · [[AWS - Dependências entre servidores]]

## O que faz e como sabemos
- SG `cootravale-ad-sg`: LDAP 389 aceita [[EC2 - srv-prod-otrsapp]], [[EC2 - srv-prod-cootravalejobs]], [[EC2 - srv-prod-rpasmartshare]]; EIP "AD".

## Com o que se liga
- Serviço de autenticação dos 3 servidores acima, hoje atendido só pelo [[EC2 - srv-prod-dc01]].

## Quem pode acessar (security groups)
- `cootravale-ad-sg` udp/464-464 ← (origem não listada: prefix list/IPv6)
- `cootravale-ad-sg` tcp/464-464 ← (origem não listada: prefix list/IPv6)
- `cootravale-ad-sg` tcp/49152-65535 ← (origem não listada: prefix list/IPv6)
- `cootravale-ad-sg` udp/389-389 ← (origem não listada: prefix list/IPv6)
- `cootravale-ad-sg` udp/53-53 ← (origem não listada: prefix list/IPv6)
- `cootravale-ad-sg` tcp/389-389 ← otrs-app-sg(sg), cootravale-jobs-sg(sg), cootravale-smartshare-sg(sg), launch-wizard-2(sg), cootravale-syspass-sg(sg), cootravale-portal-sg(sg), launch-wizard-1(sg)
- `cootravale-ad-sg` tcp/3389-3389 ← 192.168.1.0/24
- `cootravale-ad-sg` tcp/10050-10050 ← 192.168.1.0/24
- `cootravale-ad-sg` udp/123-123 ← (origem não listada: prefix list/IPv6)
- `cootravale-ad-sg` tcp/445-445 ← (origem não listada: prefix list/IPv6)
- `cootravale-ad-sg` icmp/-1--1 ← (origem não listada: prefix list/IPv6)
- `cootravale-ad-sg` tcp/3268-3268 ← (origem não listada: prefix list/IPv6)
- `cootravale-ad-sg` tcp/88-88 ← (origem não listada: prefix list/IPv6)
- `cootravale-ad-sg` all ← 192.168.168.0/24, AD-01-cootravale(sg)
- `cootravale-ad-sg` tcp/10051-10051 ← 192.168.1.0/24
- `cootravale-ad-sg` tcp/135-135 ← (origem não listada: prefix list/IPv6)
- `cootravale-ad-sg` tcp/636-636 ← (origem não listada: prefix list/IPv6)
- `cootravale-ad-sg` tcp/3269-3269 ← (origem não listada: prefix list/IPv6)
- `cootravale-ad-sg` tcp/53-53 ← (origem não listada: prefix list/IPv6)
- `cootravale-ad-sg` udp/88-88 ← (origem não listada: prefix list/IPv6)

## Uso real (CloudWatch, 14 dias)
- Parada (sem métricas)

## Plataforma
- SO: AMI não encontrada (sem acesso/removida) · tipo `t3.medium` · estado **stopped** · lançada 2024-09-25
- VPC [[VPC - cootravale-01]] · IP privado `172.31.4.71` · IP público: sim
- Instance profile: [[IAM - AmazonSSMRoleForInstancesQuickSetup]] · tags AWS: {"Name": "Srv_AD02"}
- Monitorada por [[Host - Zabbix (on-premises)]] (porta 10050 liberada para 192.168.1.0/24) e/ou Wazuh quando listado acima.

## Achados
- Parado: sem redundância de AD. Decidir religar ou remover (volume 200 GB).

> Evidência: inventário SSM (parcial — pacotes Linux truncados em 50), regras de SG, métricas CloudWatch, README/scripts dos projetos locais. Itens marcados "inferido" não foram confirmados.
