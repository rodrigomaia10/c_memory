---
tipo: aws-glue
tags: [aws, aws/glue, parquet]
atualizado: 2026-10-22
fonte: aws-cli (conta 152774997921)
---
# AWS - Glue Jobs

Hub: [[Hub - AWS]] · Projeto: [[datalake-glue]] · [[dw_aso]] · [[airflow-prod-dags]] (orquestra) · [[datalake_glue_hml_manual]] (variantes *_manual)

Falhas dos jobs de produção viram evento em [[AWS - Monitoramento]] (regra EventBridge) → [[Monitoramento_Gateway_job_cootravale]].

## Envios / relatórios / cargas pontuais
| Job | Região | Tipo | Glue | Workers | Role | Conexão | Alterado |
|---|---|---|---|---|---|---|---|
| Athena to Otrs job | sa-east-1 | glueetl | 4.0 | G.1X 5 | GlueAthenaToMySQLRole | — | 2026-05-01 |
| EnvioAlteracaoCooperadoCRC | us-east-1 | glueetl | 5.1 | G.1X 10 | GlueAthenaToMySQLRole | — | 2026-09-14 |
| EnvioAlteracaoValidarNotasFiscaisComercial | us-east-1 | glueetl | 5.1 | G.1X 10 | GlueAthenaToMySQLRole | — | 2026-09-14 |
| carga_terceiros_centro_custos | us-east-1 | glueetl | 5.1 | G.1X 10 | GlueAthenaToMySQLRole | multitms-network | 2026-09-14 |
| carga_terceiros_centro_custos-copy | us-east-1 | glueetl | 5.1 | G.1X 10 | GlueAthenaToMySQLRole | multitms-network | 2026-09-14 |
| envioRelatorioTaxasCooperado | us-east-1 | glueetl | 5.1 | G.1X 10 | GlueAthenaToMySQLRole | — | 2026-09-14 |

## Cargas para o Portal (Athena → portal)
| Job | Região | Tipo | Glue | Workers | Role | Conexão | Alterado |
|---|---|---|---|---|---|---|---|
| Lista_Operacional | sa-east-1 | glueetl | 4.0 | G.1X 5 | GlueAthenaToMySQLRole | sqlserver-cootravale-connection | 2026-04-24 |
| Portal_Adiantamento | us-east-1 | glueetl | 5.1 | G.1X 10 | GlueAthenaToMySQLRole | multitms-network | 2026-09-14 |
| Portal_Beneficios | us-east-1 | glueetl | 5.1 | G.1X 10 | GlueAthenaToMySQLRole | Jdbc connection - multitms | 2026-10-20 |
| Portal_Descarga_Pedagio | us-east-1 | glueetl | 5.1 | G.1X 10 | GlueAthenaToMySQLRole | multitms-network | 2026-09-14 |
| Portal_Fato_Operacional | us-east-1 | glueetl | 5.1 | G.1X 10 | GlueAthenaToMySQLRole | multitms-network | 2026-10-05 |
| Portal_Lista_Bloqueados | us-east-1 | glueetl | 5.1 | G.1X 10 | GlueAthenaToMySQLRole | multitms-network | 2026-09-14 |
| Portal_Lista_Bloqueados_KMM | us-east-1 | glueetl | 5.1 | G.1X 10 | GlueAthenaToMySQLRole | multitms-network | 2026-09-14 |
| Portal_Lista_Cooperados | us-east-1 | glueetl | 5.1 | G.1X 10 | GlueAthenaToMySQLRole | Jdbc connection - multitms | 2026-10-20 |
| Portal_Lista_Espelhamento | us-east-1 | glueetl | 5.1 | G.1X 10 | GlueAthenaToMySQLRole | — | 2026-09-14 |
| Portal_prazo_clientes | us-east-1 | glueetl | 5.1 | G.1X 10 | GlueAthenaToMySQLRole | multitms-network | 2026-09-14 |
| Saldo_realizado | us-east-1 | glueetl | 5.1 | G.1X 10 | GlueAthenaToMySQLRole | multitms-network | 2026-09-24 |

## RLS (Power BI)
| Job | Região | Tipo | Glue | Workers | Role | Conexão | Alterado |
|---|---|---|---|---|---|---|---|
| RLS | us-east-1 | pythonshell | 3.0 |   | GlueJobBronzeSilverCatalog | — | 2026-09-17 |

## Testes e sandbox
| Job | Região | Tipo | Glue | Workers | Role | Conexão | Alterado |
|---|---|---|---|---|---|---|---|
| Job-Teste-Final | sa-east-1 | glueetl | 4.0 | G.1X 10 | GlueAthenaToMySQLRole | — | 2026-04-09 |
| TEST_JOB_UPDATE_DATA | sa-east-1 | glueetl | 4.0 | G.1X 2 | AWSGlueServiceRole-S3_consumer | — | 2025-06-26 |
| airflow_teste | us-east-1 | glueetl | 5.0 | G.1X 2 | GlueJobBronzeSilverCatalog | — | 2026-09-14 |
| teste-absoluto | sa-east-1 | pythonshell | 3.0 |   | GlueAthenaToMySQLRole | — | 2026-04-17 |
| teste-simples | sa-east-1 | glueetl | 4.0 | G.1X 10 | GlueAthenaToMySQLRole | — | 2026-04-09 |
| teste-spark-simples | sa-east-1 | glueetl | 5.0 | G.1X 2 | GlueAthenaToMySQLRole | — | 2026-04-17 |
| teste_conec | us-east-1 | glueetl | 5.0 | G.1X 2 | GlueJobBronzeSilverCatalog | — | 2026-09-14 |
| testes | us-east-1 | glueetl | 5.0 | G.1X 2 | GlueAthenaToMySQLRole | multitms-network | 2026-10-07 |
| testesqlserver | sa-east-1 | glueetl | 4.0 | G.1X 10 | GlueAthenaToMySQLRole | sqlserver-cootravale-connection | 2026-04-17 |

## Pipeline medalhão (bronze→silver→gold)
| Job | Região | Tipo | Glue | Workers | Role | Conexão | Alterado |
|---|---|---|---|---|---|---|---|
| bronze_to_silver | us-east-1 | glueetl | 5.0 | G.1X 3 | GlueJobBronzeSilverCatalog | — | 2026-10-03 |
| bronze_to_silver_manual | us-east-1 | glueetl | 5.0 | G.1X 3 | GlueJobBronzeSilverCatalog | — | 2026-10-15 |
| jdbc_to_bronze | us-east-1 | glueetl | 5.0 | G.1X 4 | GlueJobBronzeSilverCatalog | multitms-network | 2026-10-01 |
| jdbc_to_bronze_full | us-east-1 | glueetl | 5.0 | G.1X 4 | GlueJobBronzeSilverCatalog | multitms-network | 2026-09-30 |
| jdbc_to_bronze_manual | us-east-1 | glueetl | 5.0 | G.1X 4 | GlueJobBronzeSilverCatalog | multitms-network | 2026-10-21 |
| jdbc_to_bronze_teste_split | us-east-1 | glueetl | 5.0 | G.2X 3 | GlueJobBronzeSilverCatalog | multitms-network | 2026-09-14 |
| parquet_bronze_to_silver_transform | us-east-1 | glueetl | 5.0 | G.1X 3 | GlueJobBronzeSilverCatalog | Jdbc connection - multitms, Jdbc connection - kmm | 2026-09-14 |
| parquet_bronze_to_silver_transform | sa-east-1 | glueetl | 5.0 | G.1X 2 | GlueJobBronzeSilverCatalog | — | 2025-07-06 |
| parquet_silver_to_gold_transform | us-east-1 | glueetl | 5.0 | G.1X 3 | GlueJobBronzeSilverCatalog | — | 2026-09-14 |
| silver_to_gold | us-east-1 | glueetl | 5.0 | G.1X 3 | GlueJobBronzeSilverCatalog | — | 2026-09-14 |
| silver_to_gold_manual | us-east-1 | glueetl | 5.1 | G.1X 3 | GlueJobBronzeSilverCatalog | — | 2026-10-16 |
| silver_to_silver_transform | us-east-1 | glueetl | 5.0 | G.1X 3 | GlueJobBronzeSilverCatalog | — | 2026-09-14 |

## Validação de tabelas incrementais
| Job | Região | Tipo | Glue | Workers | Role | Conexão | Alterado |
|---|---|---|---|---|---|---|---|
| incremental_tables_validation_n2 | us-east-1 | glueetl | 5.1 | G.1X 2 | GlueJobBronzeSilverCatalog | multitms-network | 2026-06-07 |
| incremental_tables_validation_n3 | us-east-1 | glueetl | 5.0 | G.2X 3 | GlueJobBronzeSilverCatalog | multitms-network | 2026-09-14 |
| shell_incremental_tables_validation_n1 | us-east-1 | pythonshell | 3.0 |   | GlueJobBronzeSilverCatalog | multitms-network | 2026-06-07 |

Scripts: `s3://cootravale-glue/scripts/` e `s3://aws-glue-assets-152774997921-<região>/scripts/` ([[S3 - cootravale-glue]]). Nenhum job tem tags AWS.
