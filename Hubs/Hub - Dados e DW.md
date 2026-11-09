---
tipo: hub
dominio: dados
tags: [hub, dominio/dados]
atualizado: 2026-10-16
---
# Hub - Dados e DW

Dados e DW — pipeline Bronze/Silver/Gold, Power BI e orquestração.

Raiz: [[Cootravale]]

## Projetos
- [[airflow-app]] — Diagnóstico do Airflow de produção via Chrome (scheduler parado, 2026-10-28).
- [[api_powerbi_shell]] — Versão em shell das rotinas de API do Power BI.
- [[api-powerbi]] — Scripts Python/PowerShell para extrair metadados e datasets do Power BI (token, XMLA, ADOMD).
- [[Apolo11]] — Migração de BI/DW da Cootravale: views Athena, Power BI, conciliação multi-KMM, contratos, crédito, torre de controle.
- [[PowerBIClaudio]] — workspace Power BI por área, relatório de migração e governança
- [[Arquitetura Projeto Dados]] — Guia de boas práticas Power BI e visualizador de diagramas.
- [[curso_dbt]] — Material do curso de dbt (zips de exemplo).
- [[datalake_glue_hml_manual]] — SQLs de dimensões (dim_*) para carga manual em HML do datalake.
- [[dw_aso]] — Repositório oficial do Data Warehouse Cootravale (Bronze→Silver com Glue, Airflow e Spark; branches main/hml).
- [[dw-aso]] — Variante de trabalho do DW-ASO: queries Athena, glue_catalog_local, lambdas e simulador local.
- [[leverpro]] — Acesso AWS restrito (política IAM "lever pro"): Athena/Glue/S3 só em lancamentos (bronze) e ponte_lancamento_documento_carga (gold).
- [[hml-airflow-docker]] — Airflow + dbt em Docker para homologação local.
- [[pbi-mcp-server]] — MCP server customizado para ler/editar relatórios e modelos semânticos .pbip locais.
- [[pbi-tools]] — Binário pbi-tools para extrair/compilar projetos Power BI.
- [[SQL_KMM]] — SQLs das fontes KMM multi-empresa.
- [[LSTM_Autoencoder]] — Protótipo PyTorch de detecção de anomalias em métricas operacionais (Airflow/gateway/EC2).

## Infra na AWS
- [[Hub - AWS]] — mapa da conta AWS. Projetos de pipeline, orquestração, Lambda e IaC migraram para [[Hub - AWS Glue]] · [[Hub - AWS Monitoramento e Custo]] · [[Hub - AWS Lambda]].
