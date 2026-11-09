---
tipo: aws-ec2
tags: [aws, aws/ec2, regiao/sa-east-1, estado/running, awstag/backup-sim]
instance_id: i-0e661c0f3513a6cbd
regiao: sa-east-1
tipo_instancia: t3.medium
estado: running
atualizado: 2026-10-22
fonte: aws-cli + ssm + cloudwatch + sg (conta 152774997921)
---
# EC2 - srv-prod-dc01

**Controlador de domínio (DC01) + **sincronização Microsoft Entra ID (Azure AD Connect)** e Fortinet SSO Collector.**

Hub: [[Hub - AWS Computação]] · [[AWS - Mapa]] · [[AWS - EC2 (índice)]] · [[AWS - Dependências entre servidores]]

## O que faz e como sabemos
- SSM: `SRV-DC01.ctv.br`, Windows Server 2022; software: Entra Connect Sync, Entra Connect Health, Azure AD Connect Authentication Agent, Azure Connected Machine Agent, Fortinet SSO Collector Agent.

## Com o que se liga
- Autenticação LDAP usada por [[EC2 - srv-prod-otrsapp]], [[EC2 - srv-prod-cootravalejobs]] e [[EC2 - srv-prod-rpasmartshare]] (regra no SG do AD).
- Par: [[EC2 - Srv_AD02]] (parado).
- Monitorado por [[AWS - SNS]] `CloudDog-Directory-Monitor`.

## Quem pode acessar (security groups)
- `launch-wizard-5` all ← 0.0.0.0/0

## Uso real (CloudWatch, 14 dias)
- CPU média **13.33%**, pico 99.23% · rede entrada 946 KB/s / saída 4.72 MB/s (média)

## Plataforma
- Microsoft Windows Server 2022 Datacenter 10.0.20348 — host `SRV-DC01.ctv.br` · tipo `t3.medium` · estado **running** · lançada 2025-10-20
- VPC [[VPC - cootravale-02]] · IP privado `192.168.168.74` · IP público: não
- Instance profile: [[IAM - AmazonSSMRoleForInstancesQuickSetup]] · tags AWS: {"Name": "srv-prod-dc01", "Backup": "Sim"}

## Achados
- **SG `launch-wizard-5` libera TODO o tráfego para 0.0.0.0/0** (sem restrição); sem IP público, mas exposto a toda a rede interligada. Único AD ativo (AD02 parado).

> Evidência: inventário SSM (parcial — pacotes Linux truncados em 50), regras de SG, métricas CloudWatch, README/scripts dos projetos locais. Itens marcados "inferido" não foram confirmados.
