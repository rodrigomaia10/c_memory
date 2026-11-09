---
tipo: aws-ec2
tags: [aws, aws/ec2, regiao/sa-east-1, estado/running]
instance_id: i-076f5886cd365461a
regiao: sa-east-1
tipo_instancia: t3.medium
estado: running
atualizado: 2026-10-22
fonte: aws-cli + ssm + cloudwatch + sg (conta 152774997921)
---
# EC2 - srv-hm-portalccs

**Homologação do Portal CCS/cooperados (Apache) — hosts `*homologa*`, `homologanovo`, `hml.torreportobelo`.**

Hub: [[Hub - AWS Computação]] · [[AWS - Mapa]] · [[AWS - EC2 (índice)]] · [[AWS - Dependências entre servidores]]

## O que faz e como sabemos
- ALB: `portalccshomologa`, `cooperadoshomologa`(8181) e `hml.torreportobelo`(3000, unhealthy).
- SSH só do runner [[EC2 - srv-prod-bitbucketrunner]].

## Com o que se liga
- Deploy vindo do [[EC2 - srv-prod-bitbucketrunner]].
- Conecta no Postgres de [[EC2 - srv-prod-postgresql]] (regra 5432 para este IP).
- Target groups do ALB: `cootravale-hml-torreportobelo`:3000 (unhealthy) → [[ALB - cootravale]]; `cootravale-portal-ccs-hom-8181`:8181 (healthy) → [[ALB - cootravale]]; `cootravale-portal-ccs-hom-tg`:80 (healthy) → [[ALB - cootravale]]

## Quem pode acessar (security groups)
- `launch-wizard-2` tcp/0-65535 ← 172.31.0.0/16
- `launch-wizard-2` tcp/2526-2526 ← launch-wizard-1(sg)
- `launch-wizard-2` all ← 192.168.168.0/24
- `launch-wizard-2` tcp/22-22 ← 172.31.48.69/32
- `launch-wizard-2` tcp/8181-8181 ← 0.0.0.0/0
- `launch-wizard-2` tcp/3306-3306 ← (origem não listada: prefix list/IPv6)
- `launch-wizard-2` tcp/10050-10050 ← 192.168.1.202/32
- `launch-wizard-2` icmp/-1--1 ← 192.168.1.0/24

## Uso real (CloudWatch, 14 dias)
- CPU média **3.6%**, pico 52.75% · rede entrada 46 KB/s / saída 47 KB/s (média)

## Plataforma
- Ubuntu 22.04 — host `ip-172-31-30-124.sa-east-1.compute.internal` · tipo `t3.medium` · estado **running** · lançada 2026-03-17
- VPC [[VPC - cootravale-01]] · IP privado `172.31.30.124` · IP público: sim
- Instance profile: [[IAM - AmazonSSMRoleForInstancesQuickSetup]] · tags AWS: {"Name": "srv-hm-portalccs"}
- Monitorada por [[Host - Zabbix (on-premises)]] (porta 10050 liberada para 192.168.1.0/24) e/ou Wazuh quando listado acima.

## Achados
- TG `cootravale-hml-torreportobelo` unhealthy.

## Projetos relacionados
- [[Portal]]

> Evidência: inventário SSM (parcial — pacotes Linux truncados em 50), regras de SG, métricas CloudWatch, README/scripts dos projetos locais. Itens marcados "inferido" não foram confirmados.
