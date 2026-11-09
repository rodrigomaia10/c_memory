---
tipo: projeto
caminho: C:\project\Portal
dominio: portal
tags: [projeto, dominio/portal]
criado: 2026-10-16
atualizado: 2026-10-29
---
git # Portal

Portal do cooperado: backend portal-cooperado-api, cadastro de motorista e integração CAF.

## Estado atual
- Script `portal-cooperado-api/scripts/qa-drop-tables.js` pronto (impacto de excluir tabelas no front); testado só com `status_caf` e `car_tipo_operacao`.
- Script atualizado com baseline (antes/depois) e AVISO; smoke em homologação achou `verify_processing` 500 pré-existente (não é da tabela).
- Baseline antes.json gerado em homologação; falta passo 2 (usuário renomear status_caf e rodar com --baseline) e teste manual das telas Dashboard/DashboardCrc/Drivers/Opentech/Contacts.
- Pendência: usuário informar quais tabelas excluir e onde fica o front de cartilhas (não está nos fronts locais); rodar `--smoke` em QA.
- Tabelas não usadas (2026-10-29): relatório + roteiro em `portal-cooperado-api/docs/tabelas-nao-usadas.md` (40 podem dropar). Usuário vai renomear (`_bkpold_bkp1029`) e dropar se não houver problema. Pendente: `stats_reset` e dependências (pg_depend/FK/functions). Ver memory `bd-portal-acesso`.

## Índice de tópicos
- QA de exclusão de tabelas → skill de projeto `qa-drop-tables` (2026-10-22)
- Acesso ao BD do portal / tabelas não usadas → memory `bd-portal-acesso` (2026-10-29)

Hub: [[Hub - Portal e APIs]] · Raiz: [[Cootravale]]

## Relacionados
- [[PortalPHP5.3]] — portal legado em PHP 5.3
- [[api-cootravale]] — API associada
- [[proxy-nginx]] — proxy reverso
- [[otrs]] — chamados e CSS do portal do cliente
- [[EC2 - srv-prod-portalccs]] · [[EC2 - srv-prod-portalcoop]] · [[ALB - cootravale]] — infra AWS do portal

## Memória do projeto (Claude)
Pasta: `C:/Users/rodrigo.maia/.claude/projects/C--project-Portal-portal-portal-cooperado-api/memory`
- `qa-drop-tables-script.md` — script de QA de exclusão de tabelas
- `qa-drop-tables-restricoes.md` — nunca alterar BD; smoke só em QA; achados da homologação
- `bd-portal-acesso.md` — multi-datalake é o ERP; sem .env; resultado da análise de tabelas não usadas

## Decisões e planos
<!-- /salvar-memoria acrescenta aqui decisões duráveis -->

## Log de sessões
<!-- /salvar-memoria acrescenta linhas "- AAAA-MM-DD — resumo" -->
- 2026-10-22 — Criado script qa-drop-tables.js + skill de projeto para validar impacto no front ao excluir tabelas do BD.
- 2026-10-23 — Usuário reforçou: não alterar banco, smoke nunca em prd; smoke em homologação inconclusivo (404).
- 2026-10-23 — qa-drop-tables.js: baseline antes/depois, AVISO 401/403/404, allowlist de URL QA, QA_TOKEN.
- 2026-10-23 — Baseline do smoke gerado; usuário errou nome da tabela no passo 2 (smoke vazio). Explicado: análise estática = potencial de quebra, front só testando à mão.
- 2026-10-29 — Pedido de listar tabelas não usadas do BD do portal: multi-datalake é o ERP (sem tabelas do portal) e não há .env; aguardando lista de tabelas do usuário.
- 2026-10-29 — Análise estática das 110 tabelas do portal: 40 sem referência no código, 2 legadas só em functions não chamadas; falta confirmar com pg_stat_user_tables.
- 2026-10-29 — Gerado docs/tabelas-nao-usadas.md (40 podem dropar; demais a verificar) a partir das estatísticas do usuário.
- 2026-10-29 — Estatísticas corrigidas: leituras em branco = tabela sem índice (desconhecido); 40 candidatas têm 0 escritas; v3 recebe carga. Falta consulta com seq_scan/stats_reset.
- 2026-10-29 — Stats de leitura confirmam as 40 (seq_scan=2, 0 escritas, ~440 MB); roteiro de bkp/rename/drop no md; sufixo _bkpold_bkp1029; usuário renomeia primeiro.
