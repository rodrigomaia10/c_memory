---
tipo: projeto
caminho: C:\project\PowerBIClaudio
dominio: dados
tags: [projeto, dominio/dados]
criado: 2026-10-16
atualizado: 2026-11-09
---
# PowerBIClaudio

Workspace Power BI da Cootravale por área (Torre de Controle, Contas a Receber/Pagar, Comercial, RH, Controladoria, TI, Benefícios), com relatório de migração do BI e documentação do projeto de dados. Contém a subpasta `Cootravale Governança` (modelo de governança do tenant).

Hub: [[Hub - Dados e DW]] · Raiz: [[Cootravale]]

- Histórico completo: [[PowerBIClaudio - arquivo]]

## Relacionados
- [[Apolo11]] — migração dos dashboards para Athena/Data Lake (mesmo escopo)
- [[Arquitetura Projeto Dados]] — guia de boas práticas Power BI (cópia do .docx aqui)
- [[pbi-mcp-server]] — edita os .pbip desta pasta
- [[pbi-tools]] — extração/compilação de projetos
- [[api-powerbi]] — extração de metadados do tenant
- [[datalake-glue]] — fonte dos dados via Athena
- [[laya]] — MCP/dados auxiliares (migração pendente)

## Estado atual
- **Inventário TI (`3 - TI/Inventario Equipamentos.pbip`)**: origem trocada para o Excel no SharePoint (2026-11-09); falta abrir no Desktop, autenticar e validar; Email virou Unidade; "Total Pessoas" agora conta equipamentos.
<!-- /salvar-memoria mantém esta seção curta (3–8 linhas); o hook injeta no início da sessão. -->
- **Financeiro.pbip (`14 - Controladoria`)**: fase 1 concluída e aprovada (32 medidas DAX em `TituloReceber` + página "Os 5 números"). Pendente: ajuste do ciclo financeiro (viesado em meses recentes, só títulos quitados).
- **Fase 2 (DRE/caixa)**: views em `hml_gold` criadas (`vw_fato_contab_lancamento`, `vw_dim_plano_contas`, `vw_fato_dre_mensal`, `vw_fato_fluxo_caixa_contabil`); o trabalho seguinte (DRE contábil, ligação com contabilidade, margem por cliente) aconteceu em [[Apolo11]] — ver o Estado atual de lá.
- **Dica operacional:** copiar páginas para o `.Report` só com o Desktop fechado e salvo; checar referências de campo contra os `.tmdl` antes de copiar.

## Índice de tópicos (onde achar o antigo)
- Inventário TI: origem = Excel SharePoint `Inventário TI.xlsx` (aba NOTE E PC), mapeamento de colunas e normalização de SO → Log 2026-11-09
- Gap de KPIs do Financeiro e plano das fases → memory `projeto_bi_financeiro_gap_kpis.md`; narrativa em [[PowerBIClaudio - arquivo]] (2026-10-16)
- Página "Os 5 números" (multiRowCard cortava valores, Missing_References, medida em TituloPagar) → [[PowerBIClaudio - arquivo]] (2026-10-16)
- DRE antigo "INFORMAÇÕES GERENCIAIS-CTV-3729" (receita contábil) → [[PowerBIClaudio - arquivo]] (2026-10-16) e [[Apolo11]]
- Migração da pasta de `C:\PowerBIClaudio` → [[PowerBIClaudio - arquivo]] (2026-10-16)
- ADIANTAMENTO DE ABASTECIMENTO (QTD = litros, OBS Taxa = posto): litros não estão no DW; cruzar `hml_gold.fato_beneficios.num_docto` = `LANCTO_AGR_ID` de abastecimento (98,9% de match) → memory `reference_dw_adiantamento_abastecimento.md` (2026-10-29)

## Memória do projeto (Claude)
Pasta: `C:/Users/rodrigo.maia/.claude/projects/C--project-PowerBIClaudio/memory`
- `projeto_bi_financeiro_gap_kpis.md` — meta de KPIs do Financeiro.pbip e lacunas (caixa, fluxo, YoY, DRE, projeção)
- `reference_dw_adiantamento_abastecimento.md` — verificação no DW do pedido "adiantamento de abastecimento" (litros/posto)
- `projeto_inventario_equipamentos_ti.md` — tabela Equipamentos (inventário de TI) criada num modelo Power BI sem título

Subprojeto Governança: `C:/Users/rodrigo.maia/.claude/projects/C--project-PowerBIClaudio-Cootravale-Governan-a/memory`
- `projeto_migracao_dw_status.md` — números finais validados da migração dos dashboards para o Data Lake (35 escopo: 24 migrado / 3 híbrido / 1 validação / 1 dev / 6 legado)
- `cootravale_bi_governanca_modelo.md` — consulta DAX ao tenant PBI (Dim_Ativo, Fato_Fontes, Workspaces, Atualizacao_dataset) e pegadinhas de relacionamento
- `feedback_word_com_seguranca.md` — não matar WINWORD sem checar janela visível; .ps1 em ASCII puro


## Decisões e planos
<!-- Só decisões duráveis e vigentes; o resolvido/narrativa vai para [[PowerBIClaudio - arquivo]] (copiar, nunca apagar). -->
- **Fase 1 só-DAX** no Financeiro.pbip feita e aprovada; "Resultado de Caixa" não é caixa real (entradas só AR, saídas = todo o pago).
- **Fase 2** em `hml_gold` sobre `prd_bronze.kmm_listas_contab_lancamentos`; limites originais: sem receita na contabilidade, dados só de mai/26, sem saldo bancário histórico (superados em parte pelo trabalho em [[Apolo11]]).
- `pbi_connect` precisa de `report_path` do .pbip; `pbi_report_validate` usa o caminho `...Financeiro.Report\definition`. Não listar pastas de OneDrive sem pedido.

## Log de sessões
<!-- Só as últimas entradas; log completo em [[PowerBIClaudio - arquivo]]. -->
- 2026-10-29 — Adiantamento de abastecimento (QTD/posto): origem é `fato_beneficios` (taxa); litros via cruzamento num_docto=LANCTO_AGR_ID (98,9%); posto = `kss.pessoa.CLIENTE` via COD_PESSOA_POSTO (1, 3, 11, 270401); SQL editado em `datalake-glue/sqls/silver/silver_kmm_beneficios_lancamentos.sql` (PARTE 1; gold herda; validado em prd_bronze, granularidade igual); observacao = só o posto. Commit 7c00f65 já em main (pipeline copia p/ S3 prd); decisão: rodar em PRD. Job rodou em prd e deu HIVE_CURSOR_ERROR: catálogo da silver tem `quantidade` int, parquet novo é decimal. SQL local com CAST AS DOUBLE (não commitado); falta ajustar o tipo no catálogo prd, commit/push, rerodar silver→gold e conferir. 30/10: tabela silver dropada em prd; job manual falhou por `prd_gold.tb_log_job_exec` vazia (execution_id None, linha 45 de bronze_to_silver_manual.py) — gold manual purga o log no fim; decidido tirar a checagem de ciclo do job manual: `bronze_to_silver_manual.py` editado localmente (pula checagem se log vazio). Falta commit/push (script + SQL silver com CAST), rodar silver e gold manual em prd e conferir.
- 2026-10-16 — Análise de lacunas de KPI do Financeiro.pbip; nenhuma alteração no modelo ainda.
- 2026-10-16 — Migração para `C:\project` (3781 arquivos conferidos). Entradas antigas em `~/.claude.json` (`C:/PowerBIClaudio`) ficaram órfãs, sem efeito.

- 2026-11-05: fato_beneficios/adiantamento abastecimento: SQL silver commitado em datalake-glue (7c00f65, 894c23a); edição de scripts/bronze_to_silver_manual.py (execution_id nulo) perdida, refazer só se pedirem. Ver memory reference_dw_adiantamento_abastecimento.md

- 2026-11-05: prd_gold.fato_beneficios já tem litros/posto (9.239 linhas da taxa, 8.251 com litros); DW pronto, falta lado Power BI (Beneficios.SemanticModel). Ver memory reference_dw_adiantamento_abastecimento.md

- 2026-11-05 — Inventário de equipamentos (TI): tabela `Equipamentos` (31 linhas: Setor, Nome, Email, Equipamento, Processador, Memória, SO, Idade Processador) criada via `#table` no modelo "Sem título" aberto no Desktop (porta 52235), via `table_operations` Create (exige `columns` com `sourceColumn`). Não salvo em .pbip; falta decidir destino e visuais. Ver memory projeto_inventario_equipamentos_ti.md

- 2026-11-05 — Inventário TI virou projeto `3 - TI/Inventario Equipamentos.pbip` (modelo exportado via TMDL do Desktop aberto; página com 3 cartões, slicer Setor e tabela; medidas Total Pessoas, Em Windows 10, Com 4+ anos, Sem Equipamento Registrado). Não aberto/validado no Desktop; falta cor condicional por SO/idade. Conversão pbix→pbip: `pbi_connect` na porta, `pbi_database_export_tmdl` p/ `<nome>.SemanticModel/definition` + copiar `definition.pbism`; `pbi_report_create` cria pasta Report aninhada (mover a interna p/ cima); `.pbip` manual.

- 2026-11-05 — Skill de projeto criada: `.claude/skills/pbip-criar-relatorio` (report_path das tools pbi_* deve terminar em `/definition`; colunas gravadas como Measure; export TMDL). Inventário reparado (páginas movidas p/ definition/pages).

- 2026-11-05 — Regra: visual do Financeiro.pbip é o template de todos os BIs. Inventário TI refeito nesse padrão (`3 - TI/Inventario Equipamentos.pbip`, colunas Idade/Ano do processador); erro `UnsupportedProjectionIndexInSemanticQuery` → removidos sort e formatação condicional (pendente reintroduzir). Skill `pbip-criar-relatorio` com padrão + `gerador_pagina_exemplo.py`. Memory feedback_template_visual_bis.md

- 2026-11-05 — Inventário TI, ajustes de layout: rótulos de filtro 10pt branco, filtros azul `#1B3A66` com borda, cards com rótulos curtos (<=18 car.), sort/cond. format removidos. Pendente: usuário abrir o .pbip e confirmar topo/cards/erro de projeção; mover o .pbix antigo (estava aberto) para fora de `3 - TI`. Tudo na skill pbip-criar-relatorio.

- 2026-11-05: Saldo_realizado.py (datalake-glue) editado p/ litros/posto no bloco beneficio; falta commit, rodar job e comparar. Ver memory reference_dw_adiantamento_abastecimento.md
- 2026-11-09 — Inventário TI: origem trocada de dados embutidos (#table) para Excel no SharePoint (`Inventário TI.xlsx`, aba NOTE E PC, via Web.Contents/Excel.Workbook). Mapeamento: PATRIMONIO→Equipamento, COLABORADOR→Nome, UNIDADE→Unidade (substitui Email, que não existe no Excel), SO normalizado p/ W10/W11, setor com typos corrigidos. Linhas agora = equipamentos (254), não pessoas. Não validado no Desktop (pendente: abrir, autenticar SharePoint e atualizar).
