---
tipo: aws-ec2
tags: [aws, aws/ec2, regiao/sa-east-1, estado/running, awstag/backup-sim]
instance_id: i-0fa86f3d6b8fd079b
regiao: sa-east-1
tipo_instancia: t3.large
estado: running
atualizado: 2026-10-22
fonte: aws-cli + ssm + cloudwatch + sg (conta 152774997921)
---
# EC2 - srv-prod-postgresql

**Servidor de banco compartilhado: PostgreSQL (porta 5432) com o `airflow_db` (metadados do Airflow de produção) e MySQL (porta 3306) com o banco do OTRS.**

Hub: [[Hub - AWS Computação]] · [[AWS - Mapa]] · [[AWS - EC2 (índice)]] · [[AWS - Dependências entre servidores]]

## O que faz e como sabemos
- README do projeto [[airflow-prod-dags]]: host `172.31.28.247`, porta 5432, database `airflow_db`, usuário `airflow_user`.
- DNS `otrs.db.ctv.aws` e conexão Glue `Jdbc connection - otrs` (`jdbc:mysql://172.31.28.247:3306/otrs`) — [[AWS - Glue Crawlers e Conexões]].
- Security group: 5432 liberado para o SG do Airflow ([[EC2 - srv-prod-airflow]]), [[EC2 - srv-prod-cootravalejobs]], [[EC2 - srv-hm-portalccs]], [[EC2 - srv-prod-portalccs]], airflow-hml (172.31.50.108), a VPC 172.31.0.0/16, a sub-rede do datalake us-east-1 (172.20.252.0/26 — Lambdas/Glue) e um IP externo; 3306 liberado para [[EC2 - srv-prod-otrsapp]], a VPC e o SG `glue-otrs-access` (Glue).
- Log groups legados `/aws/rds/instance/otrs-db` e `srv01-db` indicam que os bancos já foram RDS e hoje rodam em EC2.

## Com o que se liga
- [[EC2 - srv-prod-airflow]] usa o Postgres daqui como metadata DB — se este host cair, o Airflow de produção para.
- [[EC2 - srv-prod-otrsapp]] usa o MySQL daqui — o OTRS para junto.
- O Glue lê o MySQL do OTRS por [[AWS - Glue Crawlers e Conexões]] (job `Athena to Otrs job`).

## Quem pode acessar (security groups)
- `launch-wizard-8` tcp/5432-5432 ← 3.212.10.26/32, 172.31.14.242/32, 172.31.30.124/32, 172.31.23.226/32, 172.31.50.108/32, 172.31.0.0/16, 172.20.252.0/26, srv-prod-airflow(sg)
- `launch-wizard-8` all ← (origem não listada: prefix list/IPv6)
- `launch-wizard-8` tcp/3306-3306 ← 172.31.3.170/32, 10.212.134.200/32, 172.31.0.0/16, 172.20.252.0/26, glue-otrs-access(sg)

## Uso real (CloudWatch, 14 dias)
- CPU média **47.39%**, pico 99.99% · rede entrada 4.55 MB/s / saída 7.72 MB/s (média)

## Plataforma
- Amazon Linux 2023 — host `ip-172-31-28-247.sa-east-1.compute.internal` · tipo `t3.large` · estado **running** · lançada 2026-09-23
- VPC [[VPC - cootravale-01]] · IP privado `172.31.28.247` · IP público: sim
- Instance profile: `—` ([[AWS - IAM]]) · tags AWS: {"Backup": "Sim", "Name": "srv-prod-postgresql"}

## Achados
- **Ponto único de falha**: Airflow prod + OTRS no mesmo servidor, CPU média 47% com picos de 100% nos últimos 14 dias. Candidato a separar/RDS. Nome da instância ("postgresql") esconde o MySQL.

## Projetos relacionados
- [[airflow-prod-dags]]
- [[otrs]]
- [[runner airflow]]

> Evidência: inventário SSM (parcial — pacotes Linux truncados em 50), regras de SG, métricas CloudWatch, README/scripts dos projetos locais. Itens marcados "inferido" não foram confirmados.
