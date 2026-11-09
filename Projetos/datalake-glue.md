---
tipo: projeto
caminho: C:\project\datalake-glue
dominio: dados
tags: [projeto, dominio/dados]
criado: 2026-10-16
atualizado: 2026-10-16
---
# datalake-glue

Pipeline Medallion (Bronze→Silver→Gold) em AWS Glue/S3, consumido via Athena pelo Power BI. Pipelines no Bitbucket.

Hub: [[Hub - Dados e DW]] · Raiz: [[Cootravale]]

## Relacionados
- [[PowerBIClaudio]] — relatórios consumidores via Athena
- [[datalake_glue_hml_manual]] — SQLs de dimensões usados em HML manual
- [[dw_aso]] — camada de modelagem do DW
- [[airflow-prod-dags]] — orquestração
- [[Monitoramento_Gateway_job_cootravale]] — checagem de freshness e qualidade dos jobs
- [[Apolo11]] — views e painéis consumidores
- [[S3 - Datalake]] · [[AWS - Glue Jobs]] · [[AWS - Athena]] — mapa AWS real (buckets, databases parquet, jobs)

## Memória do projeto (Claude)
Pasta: `C:/Users/rodrigo.maia/.claude/projects/C--project-datalake-glue/memory`
- aging-dias-em-aberto-bigint-vs-int — erro fato_aging, fix na silver

## Estado atual
- `silver/aging.sql` editado (CAST INT em DIAS_EM_ABERTO), sem commit. Próximo: reexecutar silver aging em hml, checar parquets mistos na pasta, depois deploy.

## Índice de tópicos
- Erro fato_aging INT64 vs int → Log 2026-11-05 + armadilha na skill etl-datalake-glue-padroes

## Decisões e planos
- `date_diff` do Spark é BIGINT: castar para INT na silver quando o catálogo diz int.

## Log de sessões
- 2026-11-05 — `.claude/` fora do git por preferência do usuário (`git rm --cached`, deleção staged, sem commit).
- 2026-11-05 — fato_aging falhou (DIAS_EM_ABERTO int vs INT64 no parquet da silver aging); corrigido com CAST INT em silver/aging.sql, pendente rerun em hml.
- 2026-11-09 — Remote `github` (rodrigomaia10/datalake-glue) adicionado; push de `main` rejeitado (GitHub tem histórico próprio de 2 commits/5 arquivos, sem base comum). Pendente: force push `main:main` ou merge unrelated-histories, após confirmar repo privado. Ver [[otrs]].
