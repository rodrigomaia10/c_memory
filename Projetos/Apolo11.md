---
tipo: projeto
caminho: C:\project\Apolo11
dominio: dados
tags: [projeto, dominio/dados]
criado: 2026-10-16
atualizado: 2026-10-30
---
# Apolo11

Migração de BI/DW da Cootravale: views Athena, Power BI, conciliação multi-KMM, contratos, crédito, torre de controle.

Hub: [[Hub - Dados e DW]] · Raiz: [[Cootravale]]

- Histórico completo: [[Apolo11 - arquivo]]

## Relacionados
- [[PowerBIClaudio]] — workspace dos relatórios Power BI migrados
- [[dw_aso]] — repositório do DW (Bronze→Silver) que alimenta as views
- [[datalake-glue]] — pipeline Glue/Athena consumido pelos painéis
- [[airflow-prod-dags]] — DAGs de produção que cargam o datalake
- [[SQL_KMM]] — SQLs das fontes KMM usadas nas migrações
- [[pbi-mcp-server]] — MCP usado para editar os .pbip
- [[Arquitetura Projeto Dados]] — guia de boas práticas Power BI

## Estado atual
<!-- /salvar-memoria mantém esta seção curta (3–8 linhas); o hook injeta no início da sessão. -->
- **Camada dim/fato contábil (2026-10-22)**: por pedido do usuário, scripts no padrão do `datalake-glue` (`sqls/gold/*.sql`, Spark SQL, `{env}_bronze`/`{env}_gold`, membro `-1`, `sk_`; sem prefixo `vw_`; tabelas físicas via job `silver_to_gold`). Staging em `C:\project\Apolo11\gold_contab\` (`sqls/gold/` com `dim_conta`, `dim_origem_contabil`, `dim_centro_custo`, `dim_conta_dre`, `dim_linha_dre`, `fato_contab_item`, `fato_dre_contabil` + `gold_sources_contab.json`), gerados por `gerar_sql_gold_contab.py`. **Nada copiado ao repo nem executado**: falta ok para copiar ao repo, subir ao S3 e rodar em hml; depois validar `fato_dre_contabil` x v2 (diferença zero) e trocar o `DreContabil` no BI. Staging em medalhão (2026-10-23): 7 tabelas silver (`silver_kmm_contab_*`, `kmm_centro_custo`, `kmm_fiscal_documento_contab`) + 8 gold lendo só silver/gold (gold não lê bronze); JSONs `silver_sources_contab.json` e `gold_sources_contab.json`. **Plano aprovado (2026-10-22): DRE analítico por carga** — elo determinístico `agrupamento_id` (receita set/26 43,87 mi liga 100%), linha 'não alocado' para fechar com `fato_dre_contabil`; **Laya descartado pelo usuário** (ganho marginal; ver [[laya]]). Elo cobre 92–96% da receita 3.1.1.01 jan–set. Plano: `~/.claude/plans/estrutuirar-as-views-em-jaunty-kay.md`. Segurança: senha Postgres em texto puro em `C:\project\laya\sqljev_lib.py`.
- **Validação DRE view x prd (2026-10-26)**: `prd_gold.fato_dre_contabil` + dims JÁ EXISTEM no Athena (prd_gold: dim_conta, dim_conta_dre, dim_linha_dre, dim_centro_custo, dim_origem_contabil, fato_contab_item, fato_contab_documento, fato_dre_contabil) e batem com `hml_gold.vw_fato_dre_contabil` (diferença 0 por mês e em 15.582 chaves mês+conta+origem+centro). Não comparados: atributos de dim_conta (classificacao/nivel), `fato_contab_item` x `vw_fato_contab_lancamento`, ligação contábil. O Financeiro.pbip lê 7 tabelas de `hml_gold`; só o `DreContabil` tem equivalente no prd (títulos/baixa/custo/ligação/conciliação não). Pendente: ok do usuário para cópia do BI com DreContabil → prd e comparar o resto.
- **DRE por documento/carga (2026-10-26)**: grão fica no documento, cargas operacionais (`no_painel='SIM'`) como LISTA, sem rateio; custo de contrato liga por agrupamento→`kmm_contrato_contrato_transp` (chave = `numero_documento`). Rascunho `gold_contab/sqls/gold/fato_dre_documento.sql` (não executado; depende de `fato_conciliacao_multi_kmm` só em hml_gold; contratos só desde 18/05). `solicitacao_carga_id` do `fato_contab_documento` é 100% nulo.
- **BIs PRD (2026-10-28)**: `Financeiro PRD.pbip` (só DreContabil em prd). `INFORMAÇÕES GERENCIAIS PRD.pbip`: f_lancamentos com atualização incremental (3 anos/2 meses), Excel 2024/25 + Athena 2026+ (expressão `Athena2026`), carga e `Grupo pessoas tratado` via Athena, RLS (`_DRE E GESTORES_Email` corte DataCorte; `Contabilidade` corte DataValidacao), `kmm_prod` só em d_Filial (troca por Athena aguarda ok). Aberto: erro de privacidade no serviço (testar `Athena2026`), privacidade das planilhas SharePoint, teste "Exibir como". Detalhe: memory `project_gerencial_prd_incremental_rls.md`.
- **Margem por cliente** (Curva operacional x financeiro): consolidada, com quadro "o que não entra"; usuário vê versão antiga publicada → precisa republicar e salvar o Desktop. Etapa 2 (ligar anulados/repasse na view) depende de tabelas vazias para o usuário de leitura e aguarda ok.
- **Balanço Patrimonial**: adiado; `contab_saldos*` vazias → pedir saldo de abertura/balancete 31/12/2025 ao fornecedor; `vw_fato_contab_item` já serve de base (fase final estacionada).
- **De-para Postgres x Athena** gerado (`depara_kmm_athena_escopo.csv`, 101 linhas) para pedir ao fornecedor o que falta.

## Índice de tópicos (onde achar o antigo)
- Contabilidade KMM no Athena (`_incremental` deduplicada, chaves CT-e/contrato/fatura) → Decisões abaixo
- Ligação documentos↔contabilidade (`vw_fato_ligacao_contabil`, página "Conferência contábil") → [[Apolo11 - arquivo]] (2026-10-19) e [[PowerBIClaudio]]
- Margem de frete / Custo Operacional com NDA/ND/OST, margem após impostos, textos do memorando → [[Apolo11 - arquivo]] (2026-10-20)
- MCP multi-datalake (Postgres KMM, somente leitura) → [[Apolo11 - arquivo]] (2026-10-20)
- Job `jdbc_to_bronze`, JSON `kmm_contab_sources.json`, tabelas vazias, 16 definições a dropar no hml_bronze → [[Apolo11 - arquivo]] (2026-10-21); pipeline em [[datalake-glue]]
- Preferências de trabalho (views no Athena, prd_ sobre hml_, salvar o Desktop antes de fechar) → memory do projeto (lista abaixo)
- Laya/sqljev e DRE analítico por carga (elo agrupamento_id, resíduo e manuais) → memory `reference_laya_sqljev_uso.md` e [[laya]]

## Memória do projeto (Claude)
Pasta: `C:/Users/rodrigo.maia/.claude/projects/C--project-Apolo11/memory`
- `feedback_athena_views_over_pbi_workarounds.md` — User prefers filtering in an Athena view per-dashboard rather than working around filter issues inside Power BI
- `feedback_generic_reusable_skills.md` — User wants process/harness documentation written as generic, reusable skills — not tied to one specific report's table/measure names
- `feedback_no_new_dw_tables.md` — Never create new tables/views in the Athena DW itself during a PBI migration unless explicitly asked
- `feedback_pbi_desktop_save_before_close.md` — Always get the user to save (Ctrl+S) in Power BI Desktop before asking them to close/reopen it — unsaved model changes made via XMLA are lost
- `feedback_prd_over_hml_schema.md` — Never source a Power BI table from hml_ schema when a prd_ equivalent exists in the Athena DW
- `project_ccpagar_conta_corrente_migration.md` — Migration of the 'Conta Corrente CCPAGAR' Power BI report from ODBC/kmm_prod to Athena
- `project_conciliacao_multi_kmm_workflow.md` — How hml_gold.fato_conciliacao_multi_kmm is rebuilt/versioned (vNN CTAS + SET LOCATION) and the data pitfalls found 2026-10-05; runbook is atualizar_conciliacao_multi_kmm.md
- `project_contratos_multitms_kmm_migration.md` — In-progress migration/rebuild of the \"Contratos MultiTMS e KMM.pbip\" reconciliation report
- `project_credito_migration_status.md` — Status of the \"Análise Exposição de Crédito\" Power BI migration to Athena and its git setup, as of 2026-08-12
- `project_ligacao_contabil_documentos.md` — Ligação CT-e/contrato/fatura x contabilidade KMM: usar `_incremental` deduplicada; chaves e cobertura validadas em set/26; view pendente
- `project_gerencial_prd_incremental_rls.md` — Estado do INFORMAÇÕES GERENCIAIS PRD (incremental, RLS, Athena, pendências de publicação)
- `project_pipeline_monitoring_agent.md` — Status of the Airflow/Glue/Athena/Power BI monitoring agent project (Fase 1 = alert-only via Telegram)
- `project_torre_controle_migration.md` — Status of the Central Torre de Controle PBI migration from legacy SQL Server/Azure SQL to Athena prd_gold
- `reference_data_pipeline_architecture.md` — Locations and log tables for the Cootravale data pipeline (Airflow EC2 -> Glue -> Athena -> Power BI governance)
- `reference_rovo_atlassian_scope.md` — The Rovo/Atlassian MCP server available in this project only covers Jira and Confluence, not Bitbucket
- `reference_source_kmm_schema_not_queryable.md` — The Athena schema source_kmm is catalogued (~1641 tables, datalake_<schema>_<table> naming) but SELECTs against it fail
- `reference_torre_controle_docs.md` — Where to find the DW architecture doc and ER diagram for the \"Central Torre de Controle\" Power BI


## Decisões e planos
<!-- Só decisões duráveis e vigentes; o resolvido/narrativa vai para [[Apolo11 - arquivo]] (copiar, nunca apagar). -->
- **Contabilidade KMM no Athena (2026-10-19):** usar `prd_bronze.kmm_listas_contab_lancamentos_incremental` deduplicada (a sem `_incremental` tem só 1 item por lançamento). Bate com o DRE (INFORMAÇÕES GERENCIAIS.pbip). Chaves CT-e/contrato/fatura validadas.
- **Custo de Frete do Financeiro (2026-10-20):** passou a incluir linhas NDA/ND/OST (antes ignoradas, ~3,7–4,2 mi/mês); margem de frete empresa 17–20%; após impostos ~14%; DRE ~9%.
- **Fonte dos lançamentos (2026-10-20):** vêm do Postgres datalake (só 2026+, com manuais, `PERMITE_EDITAR=1`); Postgres não permite criar view/tabela. Carga: `jdbc_to_bronze` com 1ª carga incremental usando `dt_inicial` do JSON; tabelas finais `kmm_<schema>_<tabela>`; JSON enxuto de 15+ entradas e guard `rdd.isEmpty()` (tabela sem colunas quebra a carga).
- **Estrutura dim/fato (2026-10-22):** tabelas gold físicas pelo padrão do repo `datalake-glue` (usuário pediu; supera 'só views'); `fato_contab_item` = base única de DRE e Balanço; `dim_conta_dre`/`dim_linha_dre` viram SQL com VALUES (dono: controladoria); v3 mantém colunas da v2 + chaves; aceite = diferença zero contra a v2 (jan-set) e ROB/ROL/margem de set/26 (43.995.688,64 / 41.074.177,15 / 4.677.995,60).

## Log de sessões
<!-- Só as últimas entradas; log completo em [[Apolo11 - arquivo]]. -->
- 2026-10-21 — Modelo atualizado e conferido (curva e MC jan-set ok); quadro 'fora da margem' corrigido (conferência 0, total -4,753 mi). Falta Ctrl+S e pendentes.
- 2026-10-21 — Margem mensal por cliente oscila por desencontro de datas (caso BEM BRASIL); recomendado aviso + acumulado; correção na conciliação v55 aguarda ok.
- 2026-10-21 (encerramento) — Plano de retirar a foto do DRE (só parâmetro) memorizado; execução na próxima sessão com BI fechado e backup.
- 2026-10-22 — Avaliado Balanço (falta saldo de abertura; 3 fases) e aprovado plano de views dim/fato contábeis validadas contra o DRE; SQLs e aplicador gerados, backup da v2; aguarda ok para criar no Athena.
- 2026-10-22 — Avaliado Laya/sqljev: maior ganho é elo determinístico CT-e↔lançamento por agrupamento_id (sem Laya); Laya só no resíduo (~4,9 mi/mês) e manuais; plano de DRE analítico por carga aprovado; staging ganhou fato_contab_documento.
- 2026-10-22 — Decidido NÃO usar Laya; plano segue só com elo determinístico por agrupamento_id (cobertura 92–96% da receita 3.1.1.01 jan–set) e `fato_dre_carga` com 'não alocado'.
- 2026-10-23 — Staging refeito no modelo medalhão: limpeza (dedup/tipos) na silver, gold só modela; silver_sources_contab.json novo; nada copiado ao repo.
- 2026-10-26 — Dim/fato contábeis já em prd_gold; `fato_dre_contabil` (prd) = `vw_fato_dre_contabil` (hml): diferença 0 por mês e por 15.582 chaves. Cópia do BI p/ prd só faz sentido p/ DreContabil; aguarda ok.
- 2026-10-26 — Criado `Financeiro PRD.pbip` (cópia do Financeiro; só DreContabil em prd_gold); dois BIs mantidos p/ validação lado a lado.
- 2026-10-26 — Criado `INFORMAÇÕES GERENCIAIS PRD.pbip`: só Dados2026 (cadeia de f_lancamentos) vem do Athena prd; demais fontes iguais; aguarda refresh e comparação no Desktop.
- 2026-10-26 — Definido DRE por documento com lista de cargas operacionais (sem rateio) e custo de contrato por agrupamento; gerencial PRD enxugado (só Dados2026 do Athena); tudo aguardando teste no Desktop e ok para criar no Athena.
- 2026-10-26 — fato_dre_documento no gold_sources_contab.json (via gerador, que apaga a pasta); gerencial PRD: erro SINAL_LANCAMENTO/VALOR corrigido (colunas vazias antes da despivotagem), Desktop aberto sobrescreveu a edição -> fechar sem salvar antes de reabrir.
- 2026-10-26 — Gerencial PRD atualizou OK no Desktop: f_lancamentos 1.934.548 linhas, jan–dez/26, soma VALOR 4.235.351,39 = fato_dre_contabil (até out − nov/dez). Pendente: ajustes do BI (comparar com original, carga, trocar ODBC legado).
- 2026-10-26 — Carga no gerencial PRD: 4 colunas (lista de cargas operacionais, status) na consulta do Dados2026/f_lancamentos; custo de contrato jan–jun não liga (numero_documento nulo; ~−30 mi/mês fora); fallback lancto_id não aplicado, aguarda decisão. Falta refresh no Desktop (fechar sem salvar antes).
- 2026-10-26 — Conferido o prd_gold: dims e fatos contabeis existem (dim_conta/_dre/linha_dre/centro_custo/origem, fato_contab_item/documento, fato_dre_contabil); fato_dre_documento NAO existe (Entity Not Found) e fato_conciliacao_multi_kmm so em hml_gold; usuario disse ter subido o resto, aguardando nome/job.
- 2026-10-26 — Decisão: fato_dre_documento é opcional (carga do gerencial PRD vai direto na consulta do Dados2026); só fato_conciliacao_multi_kmm precisa ir p/ prd_gold p/ ficar 100% prd (hoje só hml, CTAS manual, fora de qualquer JSON). fato_dre_documento já está em datalake-glue/sources/gold_sources_contab.json (job falha em prd sem a conciliação). Catálogo prd ainda sem as duas.
- 2026-10-26 — fato_conciliacao_multi_kmm incluída no gerador/JSON gold (staging gold_contab) via conversão Trino→Spark; não testada, não copiada ao datalake-glue.
- 2026-10-26 — Job silver_to_gold_contab rodou em prd e falhou (sintaxe Trino na conciliação). Descoberta: carga do DRE não precisa da conciliação — CT-e via fato_operacional.cte e contrato via num_formulario→cft→carga (prd), cobre jan–out; aguarda ok para reescrever Dados2026/fato_dre_documento.
- 2026-10-26 — Conciliação removida do pipeline; carga do DRE 100% em prd (CT-e via fato_operacional.cte, contrato via num_formulario→cft→carga); fato_dre_documento reescrita e Dados2026 do gerencial PRD sem hml; falta fechar Desktop sem salvar, atualizar e rodar job.
- 2026-10-27 — Query descarga/pedágio (Multi x KMM): join por recibo=NUM_FORMULARIO dava 0 match (NUM_FORMULARIO é decimal(38,18); recibo era lista). Fix BIGINT + recibos em linhas casa 23.488/23.489 cargas, mas gera 371k linhas (PAM_NUMERO não é único); falta chave extra (placa/data/valor). Ver memory join-recibo-pam-numero-formulario.
- 2026-10-28 — Gerencial PRD: incremental em f_lancamentos, RLS (DataCorte/DataValidacao), carga+grupo via Athena (`Athena2026`); `kmm_prod` só em d_Filial; erro de privacidade no serviço segue aberto (teste local/serviço pendente).
- 2026-10-28 — Refresh no serviço falhou: coluna 'Centro custo' não encontrada (provável partição vazia em f_lancamentos); correção proposta aguarda ok e nome da partição; Chrome MCP não vê aba anônima.
- 2026-10-28 — Chrome MCP acessou o serviço: erro de privacidade resolvido, resta 'Centro custo' não encontrado (partição sem colunas ou cabeçalho do Excel); aguarda ok + Desktop fechado p/ blindar Base.
- 2026-10-28 — d_Filial: dim_filial/dim_centro_custo do prd_gold não cobrem (sem pessoa/CNPJ); proposta = bronze kmm_kss via Athena, aguarda ok.
- 2026-10-28 — Criada no staging dim_filial_organograma (+ silver kmm_pessoa/kmm_organograma) via gerador; d_Filial do PRD trocará p/ ela após o job rodar em prd.
- 2026-10-28 — dimensão renomeada dim_centro_custo_pessoa (grão centro x pessoa); Base vazia da f_lancamentos corrigida (aguarda teste); usuário roda job contab após a bronze.
- 2026-10-28 — d_Filial do PRD trocada p/ prd_gold.dim_centro_custo_pessoa (Athena); kmm_prod fora do PRD; aguarda teste no Desktop e refresh no serviço.
- 2026-10-28 — Teste no Desktop: modelo traz DRE Real 2026 normalmente; usuário relata visual sem medidas, aguarda print/detalhe (filtro, Desktop x serviço).
- 2026-10-28 — 2026 está completo no modelo; visual em branco provavelmente segmentador/cache; aguarda retorno do usuário.
- 2026-10-28 — RAZÃO ANALÍTICO em branco no Desktop mas modelo retorna dados (cargas e grupo ok); orientado salvar e reabrir o pbip.
- 2026-10-28 — Ao reabrir o PRD, f_lancamentos/d_Filial/d_tipoLanc2 ficaram NoData; aguarda confirmação da atualização e Ctrl+S; RangeStart do usuário 01/01/2024.
- 2026-10-28 — Carga só de set/26 por causa do RangeStart do arquivo; Athena tem 2026 inteiro e nada antes; orientado RangeStart=01/01/2024 e reatualizar f_lancamentos.
- 2026-10-28 — RangeStart do modelo continuava 01/09/2026 (alteração não aplicada via Fechar e aplicar); orientado cancelar, ajustar e aplicar.
- 2026-10-28 — Gerencial PRD: RangeStart=01/01/2024 aplicado; f_lancamentos 2024–26 carregada (5,67 mi linhas); aguardando Ctrl+S, detalhe do 'algo errado' e teste de refresh no serviço.
- 2026-10-28 — Gerencial PRD: RAZÃO ANALÍTICO vazio em 2026 por Tipo do lançamento=2 no Athena2026 (segmentador 'Normal'); correção via agrupamento_id_estorno proposta, aguarda ok e Desktop fechado.
- 2026-10-28 — Gerencial PRD: Athena2026 c12 corrigido (Estornado/Estorno/Normal); validar com RangeStart=01/01/2026 (recarga 2024+ leva ~2h); aguarda recarga do usuário.
- 2026-10-28 — Gerencial PRD: SQL do Athena2026 corrigido (espaço perdido) e validado no Athena; aguarda recarga com RangeStart=01/01/2026.
- 2026-10-28 — Gerencial PRD: Tipo do lançamento corrigido e validado no Desktop (2026 a partir de 05/2026); falta conferir visuais, publicar e testar refresh no serviço.
- 2026-10-28 — Gerencial PRD: RangeStart/End não editáveis no serviço (Pro); sem fechamento de mês na base (manual por tb_versao_liberacao/DataCorte); aguarda regra de fechamento do usuário.
- 2026-10-29 — Gerencial PRD: plano mes_status (indício de fechamento por date_update, DiasEstabilidade=5, página CONTROLE DE MESES) aprovado; aguarda Desktop fechado para aplicar.
- 2026-10-29 — Gerencial PRD: mes_status + página CONTROLE DE MESES aplicadas e validadas; f_lancamentos completa 2024–26; falta conferir visuais, publicar/testar serviço e RLS.
- 2026-10-29 — Gerencial PRD: razão jul/26 PRD x antigo (−2,4 mil) = CC '1001 - JUIZ DE FORA ' com espaço (trim); chave de cargas serie-numero colide entre emissores (incluir data_emissao); correções propostas aguardam ok e Desktop fechado.
- 2026-10-29 — Gerencial PRD: caso CT-e 7875 confirma colisão de chave de cargas; propostas A (ajuste temporário no BI) / B (só Athena: trim no silver + gold fato_contab_documento_carga); aguarda escolha.
- 2026-10-29 — Gerencial PRD: trim CC + chave de cargas com data aplicados no Athena2026; razão jul/ago/set conferido (jul +1,3 mil = 3 estornos retroativos que o antigo não tem); falta publicar/testar serviço/RLS.
- 2026-10-29 — Gerencial PRD: memorando para a Contabilidade criado (doc Docs) com 3 casos de estorno (R$ 1.307,56) e perguntas; aguarda decisão e exports de abril/junho.
- 2026-10-29 — Gerencial PRD: página MEMORANDO DRE no BI e doc de arquitetura (ingestão→BI) criados; falta publicar/serviço/RLS e decisão da Contabilidade.
- 2026-10-29 — Pipeline: plano de botão no BI → Lambda (URL) → Glue Workflow contab (opção A, sem Airflow); aguarda nomes dos jobs no Glue e do JSON do bronze contab. Detalhe: memory project_gatilho_pipeline_contab_lambda.md.
- 2026-10-29 — Pipeline: gatilho contab pronto em C:\project\Apolo11\gatilho_contab (workflow, Lambda, IAM); jobs prd conferidos; nada criado na AWS; aguarda ok p/ aplicar.

- 2026-10-29 — Atualização do BI PRD no serviço: 1ª carga ~29 min (normal, sem erro; Athena não é gargalo); aviso de ordenação em dPlanoContas NIVEL 2 pendente; ver memory project_gerencial_prd_incremental_rls.

- 2026-10-29 — 2ª atualização do BI PRD no serviço também completa (36 min, pós-republicação); teste da política incremental fica para a próxima sem republicar (conferir 2 consultas no Athena).

- 2026-10-29 — 3ª atualização do BI PRD (sem republicar): Athena mostra ano 2026 inteiro x4 + setembro x3; política incremental não está limitando a 2 meses; aguardando término.

- 2026-10-29 — Atualização do BI PRD no serviço caiu para 22 min (política incremental ajuda em parte); proposta pendente: trocar RangeStart/RangeEnd padrão para o mês atual e republicar; alternativa: agendar madrugada.

- 2026-10-29 — Explicado como cargas/grupo pagador são ligados no `Athena2026` (agrupamento_id→documento→fato_operacional por cte+data) e conferida `hml_gold.fato_conciliacao_multi_kmm` x BI (chave 100% igual; cargas iguais 96,4%; divergências = cancelados, transbordo e chave sem emissor). Melhor chave = `kmm_doc_id`; gold novo só com ok. Ver memory project_gerencial_prd_incremental_rls.

- 2026-10-29 — Classificados os 1.143 CT-e divergentes conciliação x BI: 453 regra de filtro (transbordo/repasse/cancelado), 669 ambiguidade comprovada de chave, 474 a verificar; `kmm_doc_id` corrigiria ~669 (0,23%). Próximo: amostrar os 474 antes de criar gold novo. Ver memory project_gerencial_prd_incremental_rls.

- 2026-10-30 — Investigados os 474 CT-e (conciliação parece incompleta, não o BI) e busca de emissor comum: não existe campo 1:1 entre fato_operacional e KMM; recomendado manter chave serie-numero+data e documentar margem ~0,2–0,4%. Aguarda: testar desempate por valor ou só documentar no memorando. Ver memory project_gerencial_prd_incremental_rls.

- 2026-10-30 — Desempate por valor (vlr_prest_servico x total_conhecimento) validado: resolve ambiguidade da chave CT-e (682/682 iguais à conciliação vs 64/682 atual), sem objeto novo no gold. Aguarda ok para aplicar no Athena2026 (Desktop fechado). Ver memory project_gerencial_prd_incremental_rls.

- 2026-10-30 — Proposta de tabela ponte lançamento×documento×carga (BI + app de DRE), gold lendo vw_fato_operacional_painel_filial (equivale ao filtro do Athena2026); fato_operacional não é alterada. Aguarda escolha gold x silver e ok para escrever/validar o SQL no staging. Ver memory project_gerencial_prd_incremental_rls.

- 2026-10-30 — Ponte `ponte_lancamento_documento_carga` (gold, lançamento×documento×carga, regra da vw do painel copiada, desempate por valor) escrita no staging e validada em prd (cobre 100% dos lançamentos; 99,83% igual à conciliação). Falta usuário copiar ao datalake-glue/deploy/rodar job; depois Athena2026 passa a ler a ponte. `prd_gold.fato_dre_documento` já existe (chave antiga). Ver memory project_gerencial_prd_incremental_rls.

- 2026-10-30 — Ponte processada em prd (1.363.131 linhas, igual ao teste). Versão nova do Athena2026 lendo a ponte validada (jul/26 zero diferença; fev/26 654 itens corrigidos pelo desempate e 120 viram SEM CARGA). Aguarda: decisão aceitar os 120 x placa e Desktop fechado para editar o expressions.tmdl. Ver memory project_gerencial_prd_incremental_rls.

- 2026-10-30 — Athena2026 do BI PRD trocado para ler `prd_gold.ponte_lancamento_documento_carga` (aplicado no expressions.tmdl, validado no Athena; Desktop não recarregado). Aguarda usuário recarregar f_lancamentos (RangeStart 01/10/2026) e salvar; depois publicar/testar serviço. Ver memory project_gerencial_prd_incremental_rls.
- 2026-10-30 — Conciliação Multi x KMM: erro = 1 carga por CT-e escolhida sem regra do painel (pega transbordo em 478 docs 2026). Correção proposta: flag do painel no ORDER BY do `rn` do doc_multi → v55 (SELECT de teste: 291.312/291.312 cargas na ponte). Aguarda ok do usuário para criar v55. Ver memory project_conciliacao_multi_kmm_workflow.
- 2026-10-30 — Conciliação v55 criada e ativa em hml_gold (carga escolhida pela regra do painel; 614 docs trocam de carga vs v54, +25.754 docs de outubro; rollback = v54). Aguarda usuário atualizar AnaliseDocumentos.pbip e conferir CT-e 100-50949/100-43780. Ver memory project_conciliacao_multi_kmm_workflow.
- 2026-10-30 — Financeiro PRD: DrePlano/DreLinhas/DreAjustesManuais (fixos) têm equivalente no Athena (dim_conta_dre, dim_linha_dre, itens sem origem; diferença zero); Ref do DreContabil fica como foto de auditoria. Aguarda ok + Desktop fechado para trocar por Odbc.Query. Ver memory project_dre_view_vs_prd_validation.
- 2026-10-30 — Financeiro PRD: DrePlano/DreLinhas/DreAjustesManuais trocados por Odbc.Query no Athena (backup bak_fin_prd_20261030; única diferença jul/26 R$ 10.500 em conta fora do DRE). Aguarda usuário abrir/atualizar/salvar. Ver memory project_dre_view_vs_prd_validation.
- 2026-10-30 — Incremental não se aplica ao DRE do Financeiro PRD (tabelas pequenas). Avaliação como diretor financeiro: BI serve p/ decisão, não p/ fechamento oficial; atualização diária ~06:00 recomendada. Aguarda se o usuário quer a lista de pendências p/ aceite. Ver memory project_dre_view_vs_prd_validation.
- 2026-10-30 — Memorando do Financeiro PRD atualizado (textos velhos corrigidos + nova página 4/4 com a lista do que falta para fechamento oficial). Aguarda usuário abrir, conferir layout e salvar. Orçado x realizado já existe no BI do DRE. Ver memory project_dre_view_vs_prd_validation.
- 2026-10-30 — Conferido Financeiro PRD no Desktop: DreAjustesManuais ok; DrePlano/DreLinhas/DreContabil vazias até Atualizar+salvar. Deduções do documento zeradas em jan–abr/26 (margem após impostos = bruta) a investigar; usuário relatou % pós-impostos maior, aguarda onde viu. Ver memory project_dre_view_vs_prd_validation.
- 2026-10-30 — Margem por cliente x DRE (set/26): diferença de R$ 1,02 mi vem sobretudo de seguros/outros custos operacionais (−763 mil), não de anulações (+79 mil). Explicada ao usuário (por cliente p/ comparar, DRE p/ resultado; sem rateio). Ver memory project_dre_view_vs_prd_validation.
- 2026-10-30 — Achado: LigacaoContabil (view hml antiga) sem contabilidade jan–abr/26 → margem após impostos = bruta nesses meses. Proposta: refazer via ponte + fato_contab_item (prd). Aguarda ok + Desktop fechado. Ver memory project_dre_view_vs_prd_validation.
- 2026-10-30 — LigacaoContabil do Financeiro PRD refeita sobre itens do Postgres (prd_gold + cod_participante→CNPJ): preenche jan–abr/26 (deduções ~R$ 2 mi/mês) e corrige maio/junho; mai–out iguais à view antiga. Aguarda usuário atualizar/salvar e conferir margem após impostos jan–abr. Financeiro.pbip foi sobrescrito com cópia do PRD. Ver memory project_dre_view_vs_prd_validation.
- 2026-10-30 — Log contábil antigo: sem dados antes de maio e com só 22% do custo de contrato de maio; jun–out igual ao Postgres. Aguarda usuário atualizar o Financeiro PRD (modelo aberto vazio) para conferir cobertura mês a mês e reescrever texto do memorando. Financeiro.pbip (cópia) tem a ligação antiga. Ver memory project_dre_view_vs_prd_validation.
- 2026-10-30 — Refresh completo do Financeiro leva horas; dados ficam no cache.abf do .pbip. Nova LigacaoContabil aplicada também no Financeiro.pbip (que tem os dados) com backup do cache; usuário atualiza só essa tabela e salva. Definir arquivo oficial (Financeiro.pbip x PRD). Ver memory project_dre_view_vs_prd_validation.
- 2026-10-30 — Decisão: BI Financeiro oficial = `Financeiro.pbip` (o `Financeiro PRD.pbip` fica parado, não apagado). Edições futuras em Financeiro.*. Ver memory project_financeiro_pbip_oficial.
- 2026-10-30 — Financeiro.pbip conferido após troca da LigacaoContabil: jan–abr com deduções (margem após impostos < frete), cobertura contábil jan–set 99,4–99,97%, out 75% (em andamento); memorando atualizado no Financeiro.Report. Pendente: usuário abrir/salvar; custo contábil < operacional (78–93%) não investigado. Ver memory project_financeiro_pbip_oficial.
- 2026-10-30 — Custo contábil x operacional explicado: ocorrências (~2,3 mi/mês), contratos sem linha no painel (3–4 mi/mês) e rateio; contábil por contrato ≈ frete operacional. Aguarda ok para pôr no memorando/conferência. Ver memory project_financeiro_pbip_oficial.
- 2026-10-30 — Ponte do custo contábil x operacional aplicada no Financeiro.pbip (2 medidas na LigacaoContabil, página nova "Ponte do custo", parágrafo no memorando 2/3); não testada no Desktop; aguarda usuário abrir/salvar e eu conferir o resíduo. Ver memory project_financeiro_pbip_oficial.
- 2026-10-30 — Ponte do custo conferida: resíduo mar/abr (−2,75/−3,86 mi) vem de contratos de docs NF não fiscais (R$ 2,8/3,2 mi); ~6,6 mil contratos/mês batem ao centavo. Aguarda decisão: separar 'fora do painel' em não fiscal x outros. Ver memory project_financeiro_pbip_oficial.
- 2026-10-30 — OST/NDA/ND sem documento no KMM têm receita no Multi (OST jan–abr ~R$ 15 mi; NDA ~R$ 5 mi/mês desde jun) e custo na contabilidade: é divergência TMS x KMM, hoje escondida como 'NAO APLICAVEL'. Proposta v56 da conciliação (aguarda ok) + Conferência no BI; Fiscal deve confirmar faturamento. Ver memory project_conciliacao_multi_kmm_workflow.
- 2026-10-30 — OST/NDA tratadas como exposição (aging: OST R$ 10,8 mi >180 dias; Klabin 5,95 mi) e risco de sujeira; 98% do custo OST já pago, sem duplicidade. NDA fica fora do painel mas dentro do custo operacional (decidir). Aguarda escolha: página OST/NDA, amostra p/ Operação ou decisão NDA. Ver memory project_financeiro_pbip_oficial.
- 2026-10-30 — ETL em prd p/ deploy da próxima semana: staging com silver item (+3 colunas), gold fato_dre_ajuste_manual (validado) e fato_ligacao_contabil (validada, depende da conciliação). Gerador agora preserva gold_contab_manual/. Faltam conciliação como gold, títulos/baixas/custo e trocar o BI. Ver memory project_dre_view_vs_prd_validation.
- 2026-10-30 — Conciliação como gold SQL: gerador gerar_conciliacao_gold.py traduz Trino→Spark; variante de teste igual ao original no Athena; falta registrar no JSON, títulos/baixas/custo e BI. Spark não testado localmente. Ver memory project_dre_view_vs_prd_validation.
- 2026-10-30 — PDF do Financeiro exportado do Desktop com valores borrados (PyMuPDF; script C:\project\Apolo11orrar_pdf.py) para mostrar à diretoria só a estrutura. Ver memory reference_pdf_borrar_valores.
- 2026-11-03 — Conciliação, ligação contábil e ajustes manuais copiados ao datalake-glue (sem commit; JSON gold_contab com 14 entradas, silver item +3 colunas). Job contab roda em sequência na ordem do JSON; não rodar a conciliação em hml. Falta: títulos/baixas/custo como gold e trocar o BI. Ver memory project_dre_view_vs_prd_validation.
- 2026-11-03 — jdbc_to_bronze_contab com margem de 1 dia no incremental (datalake-glue, sem commit). BI atual não lê nenhuma tabela _incremental (só as views antigas hml). Ver memory project_dre_view_vs_prd_validation.
- 2026-11-03 — Script de compactação do _incremental do bronze contab (última versão por chave + 30 dias de histórico, com dry-run e conferência) preparado no datalake-glue, sem commit; falta criar/agendar o job no Glue fora da carga diária. Ver memory project_dre_view_vs_prd_validation.
- 2026-11-03 — Decisão: contab no Airflow (novo DAG prd_carga_contab após o DAG principal + compactação semanal + refresh do PBI depois). Aguarda horário e ok p/ escrever os DAGs. Silver item corrigida no catálogo; falta rodar silver_to_gold_contab p/ criar ligação e ajustes. Ver memory project_gatilho_pipeline_contab_lambda e project_dre_view_vs_prd_validation.
- 2026-11-03 — Contab integrado na DAG prd_carga_diaria_split_fluxo_datalake (run_bronze_contab / run_silver_contab / run_gold_contab), editada localmente sem commit; comparar com a DAG online antes do push. Faltam DAG de compactação do _incremental e refresh do PBI. Ver memory project_gatilho_pipeline_contab_lambda.
- 2026-11-03 — Edição da DAG prd_carga_diaria_split_fluxo_datalake REVERTIDA (usuário não pediu); repo airflow limpo. Regra: não editar DAGs sem pedido explícito. Ver memory feedback_nao_editar_dags_sem_pedido.
- 2026-11-03 — A pedido, criada a DAG prd_carga_diaria_fluxo_contab_datalake (bronze→silver→gold→compactação, sem commit) e a definição do job Glue compacta_bronze_incremental_contab (JSON; job ainda não criado na AWS). bronze_to_silver_contab aponta p/ script em s3://.../temporary/. Ver memory project_gatilho_pipeline_contab_lambda.
- 2026-11-03 — compacta_bronze_incremental_contab reescrito no padrão dos jobs (tb_log_exec camada BRONZE, try/except por tabela); sem commit, não testado no Glue; falta push, criar o job e rodar a DAG em DRY_RUN. Ver memory project_dre_view_vs_prd_validation.
- 2026-11-03 — Criada a skill de projeto `etl-datalake-glue-padroes` (.claude/skills): padrões do ETL (nomes, JSON, SQL Spark, jobs Glue + tb_log_exec, Airflow, validação, armadilhas). Ver memory reference_skill_etl_datalake_glue_padroes.
- 2026-11-03 — Regra: skills/agents/roles ficam na raiz do repo alterado. Skill ETL movida p/ datalake-glue\.claude e skill de DAGs criada em airflow-prod-dags\.claude (sem commit); Apolo11 guarda só o índice repos-padroes-indice. Ver memory feedback_skills_na_raiz_do_repo.
- 2026-11-03 — CLAUDE.md curtos criados na raiz de datalake-glue e airflow-prod-dags (apontam para a skill do repo; sem commit). Ver memory feedback_skills_na_raiz_do_repo.
- 2026-11-03 — Regra do usuário: todo teste em hml, nunca em prd (skills ETL/Airflow, índice e CLAUDE.md atualizados). Conflito aberto: job gold contab em hml sobrescreve a tabela manual hml_gold.fato_conciliacao_multi_kmm. Ver memory feedback_testes_somente_em_hml.
- 2026-11-03 — Hook PreToolUse criado (escopo usuário) que bloqueia testes/alterações em prd (Glue, Athena DDL/DML, S3, Airflow, MCP) e libera SELECT e hml; disparo provado. Falha aberta; só controla ações do Claude. Ver memory feedback_testes_somente_em_hml. Testes das skills (3 pedidos com/sem skill) aguardam ok do usuário.
- 2026-11-03 — Testes da skill ETL (3 casos com/sem skill) disparados; CLAUDE.md e .claude/ no .gitignore dos repos datalake-glue e airflow-prod-dags (no datalake-glue já estavam commitados). Resultados pendentes. Ver memory reference_skill_etl_datalake_glue_padroes.
- 2026-11-03 — Testes da skill ETL, iteração 1: com skill 100% x sem 76,4%; ganho concentrado em converter view Trino→gold e no diagnóstico de SUCCEEDED sem tabela; viewer estático gerado, aguarda feedback do usuário. Ver memory reference_skill_etl_datalake_glue_padroes.
- 2026-11-04 — Gerencial PRD: corrigido RELATED na tabela DRE (MAXX/RELATEDTABLE); erro NIVEL 2 = conta 3110100020 sem Ordem Nivel 2 (21), pendente ajuste na planilha. Memory: project_gerencial_prd_erros_dre_nivel2.
- 2026-11-04 — Gerencial PRD: usuário deixou erro NIVEL 2 pendente; impacto da conta 3110100020 = 18 lanç. (R$ 8,7 mil), sem Código, fora do DRE.
