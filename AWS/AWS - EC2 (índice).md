---
tipo: aws-indice
tags: [aws, aws/ec2]
atualizado: 2026-10-22
---
# AWS - EC2 (índice)

Hub: [[Hub - AWS Computação]] · [[AWS - Dependências entre servidores]]

| Instância | Região | Tipo | Estado | CPU média 14d | O que faz |
|---|---|---|---|---|---|
| [[EC2 - Srv_AD02]] | sa-east-1 | t3.medium | stopped | —% | Segundo controlador de domínio (parado) |
| [[EC2 - VM-Backup-Rodopar]] | sa-east-1 | t3.medium | stopped | —% | VM de backup do ERP Rodopar (parada) |
| [[EC2 - spark-server_old]] | sa-east-1 | t3.large | stopped | —% | Servidor Spark standalone antigo (parado) |
| [[EC2 - srv-hm-portalccs]] | sa-east-1 | t3.medium | running | 3.6% | Homologação do Portal CCS/cooperados (Apache) — hosts `*homologa*`, `homologanovo`, `hml.torreportobelo`. |
| [[EC2 - srv-prod-airflow]] | sa-east-1 | t3.xlarge | running | 11.69% | Airflow 3.1.7 de produção |
| [[EC2 - srv-prod-bitbucketrunner]] | sa-east-1 | t3.medium | running | 2.57% | Runner do Bitbucket Pipelines (CI/CD) — host que também responde como `airflow.ctv.aws`/`api-cootravale`. |
| [[EC2 - srv-prod-cootravalejobs]] | sa-east-1 | t3.xlarge | running | 15.82% | Servidor Windows de jobs/automação de BI |
| [[EC2 - srv-prod-databases]] | sa-east-1 | t3.large | running | 1.2% | Servidor de bancos sem função confirmada (Amazon Linux 2023 recente, SSH só). |
| [[EC2 - srv-prod-dc01]] | sa-east-1 | t3.medium | running | 13.33% | Controlador de domínio (DC01) + **sincronização Microsoft Entra ID (Azure AD Connect)** e Fortinet SSO Collect |
| [[EC2 - srv-prod-ocs NAO LIGAR]] | sa-east-1 | t3.medium | stopped | —% | OCS Inventory (parada, "NAO LIGAR") |
| [[EC2 - srv-prod-omnilink]] | sa-east-1 | c4.xlarge | running | 4.6% | Servidor Omnilink (rastreamento/telemetria, inferido) |
| [[EC2 - srv-prod-otrsapp]] | sa-east-1 | t4g.xlarge | running | 5.83% | Aplicação OTRS/Znuny (chamados) |
| [[EC2 - srv-prod-portalccs]] | sa-east-1 | t3.large | running | 6.46% | Portal CCS de produção (Apache + vários apps Node/PHP em portas distintas) — front de `portalccs`, site instit |
| [[EC2 - srv-prod-portalcoop]] | sa-east-1 | t3.large | running | 2.16% | Portal do cooperado (produção) |
| [[EC2 - srv-prod-postgresql]] | sa-east-1 | t3.large | running | 47.39% | Servidor de banco compartilhado |
| [[EC2 - srv-prod-rpasmartshare]] | sa-east-1 | t3.large | running | 76.36% | SmartShare + RPA (Selbetti) |
| [[EC2 - srv-prod-syspass NÃO LIGAR]] | sa-east-1 | t3.small | stopped | —% | SysPass (cofre de senhas, parado, "NÃO LIGAR"). |
| [[EC2 - srv-prod-wazuh]] | sa-east-1 | c4.xlarge | running | 1.11% | Servidor Wazuh (SIEM/EDR) |
| [[EC2 - vpn-test-ping]] | sa-east-1 | t4g.nano | stopped | —% | Instância de teste de conectividade VPN (só ICMP) — parada. |
| [[EC2 - postgres01]] | us-east-1 | t4g.small | running | 1.11% | Postgres do ambiente stage (Ubuntu 26.04 arm64). |
| [[EC2 - stage-apps]] | us-east-1 | t4g.medium | running | 2.11% | Ambiente de stage de aplicações (Ubuntu 24.04 arm64) |
