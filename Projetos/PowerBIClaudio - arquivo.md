---
tipo: arquivo
projeto: PowerBIClaudio
tags: [arquivo, dominio/dados]
criado: 2026-10-21
---
# PowerBIClaudio — arquivo (histórico completo)

Cópia integral, sem edição, de "Decisões e planos" e "Log de sessões" do nó [[PowerBIClaudio]] até 2026-10-21. Só acrescentar, nunca apagar.

## Decisões e planos
- 2026-10-16 — Pasta migrada de `C:\PowerBIClaudio` para `C:\project\PowerBIClaudio`; pastas de memória do Claude renomeadas para `C--project-PowerBIClaudio*`.

- 2026-10-16 — BI financeiro (`14 - Controladoria/Financeiro.pbip`): gap de KPIs mapeado contra artigo bobpost. Próximo: bloco só-DAX (fluxo de caixa, MoM/YoY/YTD, ciclo financeiro, concentração); caixa e DRE dependem de checar Athena (saldo bancário, plano de contas).

- 2026-10-16 — Plano aprovado: fase 1 só-DAX no Financeiro.pbip (aguarda usuário abrir o .pbip no Desktop); fase 2 DRE/caixa histórico via `source_kmm.datalake_contab_*` (plano_de_contas + saldo_mes) e views gold. Detalhes na memory `projeto_bi_financeiro_gap_kpis.md`.

- 2026-10-16 — Fase 1 do BI financeiro feita: 32 medidas DAX em `TituloReceber` (fluxo de caixa, ciclo financeiro, concentração, MoM/YoY/YTD), validadas. "Resultado de Caixa" não é caixa real (entradas só AR, saídas = todo o pago). Pendente: salvar .pbip, página "5 números", fase 2. Dica: `pbi_connect` precisa de `report_path` do .pbip.

- 2026-10-16 — Página "Os 5 números" do Financeiro.pbip gerada em rascunho (scratchpad); só entra no projeto com o Desktop fechado e salvo, para o save não apagar a página. Passos na memory `projeto_bi_financeiro_gap_kpis.md`.

- 2026-10-16 — Página "Os 5 números" copiada para `Financeiro.Report` (1ª página) e validada (`pbi_report_validate` com caminho `...Financeiro.Report\definition`). Falta conferência visual no Desktop; depois, fase 2 (DRE/caixa histórico).

- 2026-10-16 — Medidas conferidas após reabrir o .pbip; ciclo financeiro viesado em meses recentes (só títulos quitados). Aguardando conferência visual do usuário e decisão sobre ajuste do ciclo e fase 2.

- 2026-10-16 — Página "Os 5 números": multiRowCard cortava valores; refeita com cards simples (27 visuais), pendente de copiar com o Desktop fechado.

- 2026-10-16 — Missing_References na página "Os 5 números": medida de prazo de pagamento está em TituloPagar. Corrigido no rascunho; falta copiar com o Desktop fechado. Checar referências de campo contra os .tmdl antes de copiar páginas.

- 2026-10-16 — Fase 1 do BI financeiro concluída e aprovada (medidas + página "Os 5 números"). Próximo: ajuste do ciclo financeiro e fase 2 (DRE/caixa histórico/views gold).

- 2026-10-16 — Fase 2: criadas em `hml_gold` as views `vw_fato_contab_lancamento`, `vw_dim_plano_contas`, `vw_fato_dre_mensal`, `vw_fato_fluxo_caixa_contabil` (base `prd_bronze.kmm_listas_contab_lancamentos`). Limites: sem receita na contabilidade, dados só de mai/26, sem saldo bancário histórico. Ver memory `projeto_bi_financeiro_gap_kpis.md`.

- 2026-10-16 — Usuário tem DRE antigo ("INFORMAÇÕES GERENCIAIS-CTV-3729-CTV-3729", SVN/OneDrive) para localizar a receita contábil e validar a DRE; aguardando arquivo no projeto ou caminho exato. Não listar pastas de OneDrive sem pedido.

## Log de sessões
- 2026-10-16 — Análise de lacunas de KPI do Financeiro.pbip; nenhuma alteração no modelo ainda.
- 2026-10-16 — Migração para `C:\project` (3781 arquivos conferidos). Entradas antigas em `~/.claude.json` (`C:/PowerBIClaudio`) ficaram órfãs, sem efeito.
