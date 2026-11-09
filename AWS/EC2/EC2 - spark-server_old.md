---
tipo: aws-ec2
tags: [aws, aws/ec2, regiao/sa-east-1, estado/stopped, awstag/projeto-bi, awstag/backup-sim, awstag/managed-by-terraform]
instance_id: i-075f88f4fc86288b6
regiao: sa-east-1
tipo_instancia: t3.large
estado: stopped
atualizado: 2026-10-22
fonte: aws-cli + ssm + cloudwatch + sg (conta 152774997921)
---
# EC2 - spark-server_old

**Servidor Spark standalone antigo (parado): master 7077, UI 8080/4040 — usado pelo Airflow/runner antes do Glue.**

Hub: [[Hub - AWS Computação]] · [[AWS - Mapa]] · [[AWS - EC2 (índice)]] · [[AWS - Dependências entre servidores]]

## O que faz e como sabemos
- SG `cootravale-spark-sg`: 7077/8080/4040 liberados só para a sub-rede 172.31.48.0/24 (onde estão runner e airflow).
- DNS `spark.ctv.aws` e `spark.cootravale.com.br`; tags terraform/BI.

## Com o que se liga
- Era consumido pelo runner/airflow legado ([[EC2 - srv-prod-bitbucketrunner]]); substituído pelo pipeline [[AWS - Glue Jobs]].

## Quem pode acessar (security groups)
- `cootravale-spark-sg` tcp/4040-4040 ← 172.31.49.0/24, 172.31.48.0/24
- `cootravale-spark-sg` tcp/8080-8080 ← 172.31.48.0/24
- `cootravale-spark-sg` all ← 189.42.20.190/32, 192.168.168.0/24
- `cootravale-spark-sg` tcp/0-0 ← 170.82.194.185/32
- `cootravale-spark-sg` tcp/10050-10050 ← 0.0.0.0/0
- `cootravale-spark-sg` tcp/7077-7077 ← 172.31.48.0/24, 172.31.49.0/24

## Uso real (CloudWatch, 14 dias)
- Parada (sem métricas)

## Plataforma
- SO: ubuntu/images/hvm-ssd/ubuntu-jammy-22.04-amd64-server-20230325 · tipo `t3.large` · estado **stopped** · lançada 2023-04-07
- VPC [[VPC - cootravale-01]] · IP privado `172.31.48.16` · IP público: não
- Instance profile: [[IAM - profile-S3-EC2]] · tags AWS: {"Name": "spark-server_old", "Projeto": "BI", "Backup": "Sim", "managed-by": "terraform"}
- Monitorada por [[Host - Zabbix (on-premises)]] (porta 10050 liberada para 192.168.1.0/24) e/ou Wazuh quando listado acima.

## Achados
- Parado: custo só de EBS; avaliar remover junto com os registros DNS `spark*`.

## Projetos relacionados
- [[dw_aso]]
- [[datalake-glue]]
- [[IaC]]

> Evidência: inventário SSM (parcial — pacotes Linux truncados em 50), regras de SG, métricas CloudWatch, README/scripts dos projetos locais. Itens marcados "inferido" não foram confirmados.
