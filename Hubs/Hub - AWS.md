---
tipo: hub
tags: [hub, dominio/aws]
atualizado: 2026-10-22
fonte: aws-cli (conta 152774997921)
---
# Hub - AWS

Mapa da conta AWS 152774997921 (regiões us-east-1 e sa-east-1), gerado via AWS CLI em 2026-10-22. Regenerar quando a infra mudar.

Raiz: [[Cootravale]] · Domínios relacionados: [[Hub - Dados e DW]] · [[Hub - Portal e APIs]] · [[Hub - Suporte OTRS]]

## Categorias
- [[Hub - AWS Dados]] · [[Hub - AWS Computação]] · [[Hub - AWS Rede e Segurança]] · [[Hub - AWS Operação]] · [[Hub - AWS Hosts e Sites]]

## Hubs por serviço
- Dados: [[Hub - AWS S3]] · [[Hub - AWS Glue]] · [[Hub - AWS Athena e SageMaker]]
- Computação: [[Hub - AWS EC2]] · [[Hub - AWS Lambda]]
- Rede e segurança: [[Hub - AWS Rede]] · [[Hub - AWS IAM e Acesso]]
- Operação: [[Hub - AWS Monitoramento e Custo]]

## Visão geral
- [[AWS - Mapa]] — diagrama e navegação · [[AWS - Dependências entre servidores]] · [[AWS - Achados]]

## Log
- 2026-10-22 — mapa inicial gerado via AWS CLI (21 EC2, 13 Lambdas, 27 GlueDBs, 3 ALBs); achados em [[AWS - Achados]].
- 2026-10-22 — sub-hubs (Computação, Dados, Rede e Segurança, Operação) + nós de 42 Glue jobs, 46 buckets, 6 VPNs, 3 zonas Route53, Transfer, SageMaker, SNS.
- 2026-10-22 — EC2 reescritas com função/evidência/dependências (SSM, SG, CloudWatch, READMEs); nó AWS - Dependências entre servidores; corrigido: srv-prod-postgresql hospeda Postgres Airflow + MySQL OTRS.
- 2026-10-22 — Lambdas reescritas com gatilho/uso/ligações: só API_OTRS ativa (206 inv/30d); ingestão prd_ingestion_* legada, substituída por Glue jdbc_to_bronze via Airflow; diagrama do datalake corrigido.
- 2026-10-22 — grafo conectado: 29 nós de hosts/sites fora da AWS (on-premises, Locaweb, fontes Nstech, referências sem instância), 3 VPCs, 3 SGs compartilhados, 13 roles IAM; jobs/DBs/VPNs/ALBs/Route53 ligados entre si.
- 2026-10-23 — hubs por serviço (S3, Glue, Athena/SageMaker, EC2, Lambda, Rede, IAM, Monitoramento/Custo); hubs de categoria viraram índices.
- 2026-10-23 — projetos de AWS migraram do Hub - Dados e DW para os hubs de serviço (Glue, Lambda, Monitoramento e Custo); linhas repetidas substituídas pela versão com descrição.
