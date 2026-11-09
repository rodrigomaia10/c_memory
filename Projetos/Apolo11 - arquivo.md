---
tipo: arquivo
projeto: Apolo11
tags: [arquivo, dominio/dados]
criado: 2026-10-21
---
# Apolo11 — arquivo (histórico completo)

Cópia integral, sem edição, de "Decisões e planos" e "Log de sessões" do nó [[Apolo11]] até 2026-10-21. O nó mantém só estado atual, índice e decisões vigentes. Só acrescentar, nunca apagar.

## Decisões e planos
<!-- /salvar-memoria acrescenta aqui decisões duráveis -->
- 2026-10-19 — Contabilidade KMM no Athena: usar `prd_bronze.kmm_listas_contab_lancamentos_incremental` deduplicada (a tabela sem _incremental tem só 1 item por lançamento). Bate com o DRE (INFORMAÇÕES GERENCIAIS.pbip). Chaves CT-e/contrato/fatura validadas; view de ligação pendente de autorização.

## Log de sessões
<!-- /salvar-memoria acrescenta linhas "- AAAA-MM-DD — resumo" -->
- 2026-10-19 — DRE contábil: view vw_fato_dre_contabil criada; script build_dre_contabil.py pronto (tabela DreContabil + página, status do que não bate vs DRE); aguarda usuário fechar o Financeiro.
- 2026-10-19 — View vw_fato_ligacao_contabil aplicada e validada; Financeiro ganhou LigacaoContabil, 9 medidas e a página 'Conferência contábil'.
- 2026-10-19 — View vw_fato_ligacao_contabil escrita (SQL+script), execução pendente do usuário; NF: dedup por contabilizacao_id, chave número+CNPJ.
- 2026-10-19 — Validada a ligação documentos↔contabilidade lendo o BI DRE e o Athena; ver [[PowerBIClaudio]].

- 2026-10-20 — Margem de frete por cliente alta: Custo Operacional ignora linhas NDA/ND/OST (~3,7-4,2 mi/mes de custo de contrato fora de INTEGRADO). Proposta de incluir na medida do Financeiro aguarda ok do usuario.

- 2026-10-20 — Custo de Frete do Financeiro passou a incluir linhas NDA/ND/OST; margem de frete empresa 17-20% (KLABIN set 14%). Falta ajustar textos que citam 26-28%.

- 2026-10-20 — Margem por cliente passa a ter margem apos impostos + linha 'nao ligado a cliente' que fecha com o DRE (script v3 aplicado, falta validar no Desktop). Etapa 2 (ligar anulados/repasse na view) aguarda ok.

- 2026-10-20 — Textos do memorando e da Diretoria alinhados a margem apos impostos (frete ~19%, apos impostos ~14%, DRE ~9%). Falta conferencia visual e decisao da etapa 2 (view).

- 2026-10-20 — Margem por cliente consolidada na pagina Curva operacional x financeiro, com quadro 'o que nao entra' (exato pelas contas do DRE no modelo, fecha -5,16 mi = nao ligado a cliente). Usuario ve versao publicada no navegador (antiga): precisa republicar. Falta salvar o Desktop.

- 2026-10-20 — Avaliada evolucao para Balanco Patrimonial (material PDD Financas): falta saldo de abertura 30/04 e lancamentos manuais; plano em 4 fases aguardando decisao.

- 2026-10-20 — Criado MCP multi-datalake (Postgres datalake do KMM, user scope, somente leitura) para buscar saldo de abertura, balancete e lancamentos manuais; usar em sessao nova.

- 2026-10-20 — MCP multi-datalake conectado: lancamentos manuais (PERMITE_EDITAR=1) e historico desde 2020 existem no Postgres datalake; tabelas de saldo vazias; proximo passo = acumular itens e testar Ativo = Passivo + PL.

- 2026-10-20 — Decisao: balanco adiado (sem saldo); lancamentos passam a vir do Postgres datalake (so 2026+, com manuais). Destino (PBI direto x Athena) aguarda escolha; consulta de custo da extracao ainda pesada.

- 2026-10-20 — De-para Postgres datalake x Athena em montagem (1.734 objetos; so 103 em prd_bronze) para pedir ao fornecedor o que falta; Postgres nao permite criar view/tabela.

- 2026-10-20 — De-para do escopo gerado (depara_kmm_athena_escopo.csv, 101 linhas) para pedir ao fornecedor; etapa 2 da margem depende de tabelas que vem vazias para o usuario de leitura.

- 2026-10-20 — Curva so ate o DRE (sem balanco): bastam contab_lancamento, _it e plano_contas do Postgres; validando soma de set/26 contra Athena/DRE.

- 2026-10-21 — Gerado kmm_contab_sources.json (5 tabelas contab do Postgres) no modelo kmm do datalake-glue para o usuario subir ao bronze; depois views gold e troca do DreContabil.

- 2026-10-21 — JSON de carga atualizado (27 tabelas: contab + impostos/repasse + vazias); falta secret novo do banco datalake (colunas maiusculas) e confirmar corte de data; hml_bronze kmm_contab_lancamento* apontam para bucket do fornecedor (dropar so a definicao).

- 2026-10-21 — Levantado o que dropar: 16 definicoes em hml_bronze (externas no bucket do fornecedor), nada no S3; 12 tabelas vazias confirmadas vazias tambem no lake do fornecedor -> sugerido JSON enxuto de 15.

- 2026-10-21 — Job jdbc_to_bronze: 1a carga incremental usa dt_inicial do JSON (evita full); tabelas finais kmm_<schema>_<tabela> sem colisao; drop das 16 antigas do hml virou so limpeza.

- 2026-10-21 — Carga bronze falhou em tabela vazia (tabela sem colunas); JSON enxuto de 15 entradas + guard rdd.isEmpty(); limpar tabelas sem colunas criadas e reexecutar.

- 2026-10-21 — Postgres->hml_bronze validado: MC com manuais = DRE (9,51/10,16/10,21%). Nova vw_fato_dre_contabil pronta com backup; aguardando o usuario rodar o script (bloqueado pelo classificador), depois trocar DreContabil no Financeiro.

- 2026-10-21 — View v2 aplicada, mas origem vazia: origem vem de contabilizacao_agrupamento (nova tabela no JSON, 16 entradas); apos carregar, reaplicar view, comparar e so entao trocar DreContabil.

## Log movido do nó em 2026-10-22
- 2026-10-21 — Levantado o que dropar: 16 definicoes em hml_bronze (externas no bucket do fornecedor), nada no S3; 12 tabelas vazias confirmadas vazias tambem no lake do fornecedor -> sugerido JSON enxuto de 15.
- 2026-10-21 — Job jdbc_to_bronze: 1a carga incremental usa dt_inicial do JSON (evita full); tabelas finais kmm_<schema>_<tabela> sem colisao; drop das 16 antigas do hml virou so limpeza.
- 2026-10-21 — Carga bronze falhou em tabela vazia (tabela sem colunas); JSON enxuto de 15 entradas + guard rdd.isEmpty(); limpar tabelas sem colunas criadas e reexecutar.
- 2026-10-21 — Postgres->hml_bronze validado: MC com manuais = DRE (9,51/10,16/10,21%). Nova vw_fato_dre_contabil pronta com backup.
- 2026-10-21 — View v2 aplicada, mas origem vazia: origem vem de contabilizacao_agrupamento (nova tabela no JSON); apos carregar, reaplicar view e comparar.
- 2026-10-21 — View v2 com origem funcionando; '(sem origem)' (-6,342 mi, 1,96% itens) = lancamentos sem agrupamento no Postgres (manuais), legitimo.
- 2026-10-21 — Manuais = rotinas contabeis (reclassificacoes ~0, folha -3,5, financeiras -1,5, provisoes); nao afetam margem por cliente. DreContabil do Desktop antiga (refresh via XMLA nao pega).
- 2026-10-21 — Postgres tem 2026 completo; MC jan-set fecha com o DRE (com manuais). Financeiro passa a jan-set.
- 2026-10-21 — Financeiro/Diretoria: MC da empresa estendida a jan-set; Margem por cliente e documentos seguem jul-set ate atualizar vw_fato_ligacao_contabil.
- 2026-10-21 — MC jan-set fecha com o DRE no modelo. Documentos/LigacaoContabil com carga parcial (janela da carga diaria): Atualizar tudo fora das janelas.
