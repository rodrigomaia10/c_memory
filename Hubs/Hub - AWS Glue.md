---
tipo: hub
tags: [hub, dominio/aws, aws/glue]
atualizado: 2026-10-23
fonte: aws-cli (conta 152774997921)
---
# Hub - AWS Glue

Databases do catálogo (parquet), jobs e crawlers/conexões.

Hub pai: [[Hub - AWS]] · Raiz: [[Cootravale]] · Categoria: [[Hub - AWS Dados]] · [[AWS - Glue Jobs]] · [[AWS - Glue Crawlers e Conexões]] · [[datalake-glue]] · [[S3 - Datalake]]

## Databases Glue (parquet)
- [[GlueDB - 3_gold (us-east-1)]]
- [[GlueDB - agings (sa-east-1)]]
- [[GlueDB - cootravale (sa-east-1)]]
- [[GlueDB - core_gold (us-east-1)]]
- [[GlueDB - default (us-east-1)]]
- [[GlueDB - faturamento (sa-east-1)]]
- [[GlueDB - gold (us-east-1)]]
- [[GlueDB - gold_tms (sa-east-1)]]
- [[GlueDB - hml_bronze (us-east-1)]]
- [[GlueDB - hml_gold (us-east-1)]]
- [[GlueDB - hml_silver (us-east-1)]]
- [[GlueDB - kmm (sa-east-1)]]
- [[GlueDB - mart_gold (us-east-1)]]
- [[GlueDB - multi (sa-east-1)]]
- [[GlueDB - portal_cooperado (sa-east-1)]]
- [[GlueDB - prd_bronze (us-east-1)]]
- [[GlueDB - prd_gold (us-east-1)]]
- [[GlueDB - prd_silver (us-east-1)]]
- [[GlueDB - sagemaker_sample_db (us-east-1)]]
- [[GlueDB - saldo_realizado (sa-east-1)]]
- [[GlueDB - silver_kmn (us-east-1)]]
- [[GlueDB - silver_multi (us-east-1)]]
- [[GlueDB - silver_tms (sa-east-1)]]
- [[GlueDB - source_kmm (us-east-1)]]
- [[GlueDB - source_multi_tms (us-east-1)]]
- [[GlueDB - taxa (sa-east-1)]]
- [[GlueDB - validation_db (us-east-1)]]

## Glue Jobs
### envio-relatorio
- [[GlueJob - Athena to Otrs job (sa-east-1)]]
- [[GlueJob - EnvioAlteracaoCooperadoCRC (us-east-1)]] (prod monitorado)
- [[GlueJob - EnvioAlteracaoValidarNotasFiscaisComercial (us-east-1)]]
- [[GlueJob - carga_terceiros_centro_custos (us-east-1)]]
- [[GlueJob - carga_terceiros_centro_custos-copy (us-east-1)]]
- [[GlueJob - envioRelatorioTaxasCooperado (us-east-1)]] (prod monitorado)

### carga-portal
- [[GlueJob - Lista_Operacional (sa-east-1)]]
- [[GlueJob - Portal_Adiantamento (us-east-1)]] (prod monitorado)
- [[GlueJob - Portal_Beneficios (us-east-1)]]
- [[GlueJob - Portal_Descarga_Pedagio (us-east-1)]] (prod monitorado)
- [[GlueJob - Portal_Fato_Operacional (us-east-1)]] (prod monitorado)
- [[GlueJob - Portal_Lista_Bloqueados (us-east-1)]] (prod monitorado)
- [[GlueJob - Portal_Lista_Bloqueados_KMM (us-east-1)]] (prod monitorado)
- [[GlueJob - Portal_Lista_Cooperados (us-east-1)]] (prod monitorado)
- [[GlueJob - Portal_Lista_Espelhamento (us-east-1)]]
- [[GlueJob - Portal_prazo_clientes (us-east-1)]]
- [[GlueJob - Saldo_realizado (us-east-1)]] (prod monitorado)

### rls
- [[GlueJob - RLS (us-east-1)]] (prod monitorado)

### teste
- [[GlueJob - Job-Teste-Final (sa-east-1)]]
- [[GlueJob - TEST_JOB_UPDATE_DATA (sa-east-1)]]
- [[GlueJob - airflow_teste (us-east-1)]]
- [[GlueJob - teste-absoluto (sa-east-1)]]
- [[GlueJob - teste-simples (sa-east-1)]]
- [[GlueJob - teste-spark-simples (sa-east-1)]]
- [[GlueJob - teste_conec (us-east-1)]]
- [[GlueJob - testes (us-east-1)]]
- [[GlueJob - testesqlserver (sa-east-1)]]

### pipeline-medalhao
- [[GlueJob - bronze_to_silver (us-east-1)]] (prod monitorado)
- [[GlueJob - bronze_to_silver_manual (us-east-1)]]
- [[GlueJob - jdbc_to_bronze (us-east-1)]] (prod monitorado)
- [[GlueJob - jdbc_to_bronze_full (us-east-1)]]
- [[GlueJob - jdbc_to_bronze_manual (us-east-1)]]
- [[GlueJob - jdbc_to_bronze_teste_split (us-east-1)]]
- [[GlueJob - parquet_bronze_to_silver_transform (sa-east-1)]]
- [[GlueJob - parquet_bronze_to_silver_transform (us-east-1)]]
- [[GlueJob - parquet_silver_to_gold_transform (us-east-1)]]
- [[GlueJob - silver_to_gold (us-east-1)]] (prod monitorado)
- [[GlueJob - silver_to_gold_manual (us-east-1)]]
- [[GlueJob - silver_to_silver_transform (us-east-1)]]

### validacao
- [[GlueJob - incremental_tables_validation_n2 (us-east-1)]]
- [[GlueJob - incremental_tables_validation_n3 (us-east-1)]]
- [[GlueJob - shell_incremental_tables_validation_n1 (us-east-1)]]

## Projetos
- [[datalake-glue]] — Pipeline Medallion (Bronze→Silver→Gold) em AWS Glue/S3, consumido via Athena pelo Power BI. Pipelines no Bitbucket.

## Relacionados
[[Hub - AWS S3]] · [[Hub - AWS Athena e SageMaker]] · [[airflow-prod-dags]] · [[IAM - GlueJobBronzeSilverCatalog]] · [[IAM - AWSGlueServiceRole-S3_consumer]]
