---
tipo: projeto
caminho: C:\project\Hermes
dominio: agentes
tags: [projeto, dominio/agentes]
criado: 2026-10-16
atualizado: 2026-11-06
---
# Hermes

Pasta local vazia; o Hermes real roda no servidor **app-ti** (192.168.1.251).

Hub: [[Hub - Agentes e MCP]] · Raiz: [[Cootravale]]

## Estado atual
- Container `hermes-agent` no app-ti (192.168.1.251), :8090, código em `~/hermes-docker`; SSH `cootrati`, senha na env var Windows `app-ti` (User). Painel do 9router do servidor: senha via `INITIAL_PASSWORD` em `~/hermes-docker/.9router.env`.
- 2026-11-06: usuário quer configurar também a **chave do Claude (Anthropic)**; verificado que o Hermes tem provider `anthropic` e lê `ANTHROPIC_API_KEY` de `~/hermes-docker/data/.env` (hoje só há OPENAI_*). Opções A (padrão) / B (alternativa via `--provider anthropic`, recomendada) / C (chave no painel do 9router). Usuário escolheu **B**; chave via env var Windows `ANTHROPIC_KEY_HERMES` (nunca no chat). Valor criado veio inválido (sem o `s` inicial, com espaço) — nada gravado; aguardando recolar a chave. Ver memory `hermes-chave-claude-anthropic`.
- ATUAL: Hermes usa o 9router do servidor (`custom:9router`, `gcli/grok-4.7`, http://9router:20128/v1); `hermes -z` responde ok. Falta reiniciar `hermes-agent` (confirmar com o usuário) para o `serve` recarregar a config. Armadilha: `openai-api` é sobreposto pelo OPENAI_BASE_URL do compose.
- Plano (proposto): agente no Hermes que analisa chamado novo do OTRS e manda sugestão de resolução ao Teams — Znuny→Hermes→Power Automate→Teams (PA é nuvem, não alcança o Hermes interno). Vault OTRS é só mapa de configuração; fonte real = chamados fechados + FAQ. Aguarda respostas (FAQ? acesso aos chamados? LLM externo ok? fila TI primeiro?). Ver [[otrs]] e memory `plano-agente-otrs-analise-chamado`.
- MCP OTRS somente leitura criado e testado (`C:\project\Hermes\otrs_mcp\otrs_mcp.py`, cópia em `~/hermes-docker/app/`): banco 172.31.28.247 db otrs, usuário OTRSLeitura, 5 tools (FAQ, chamados similares, chamado, schema, select). REGISTRADO no Hermes em 2026-10-28 (pymysql em `app/vendor`, `mcp_servers.otrs` no config.yaml, restart feito; agente usou `faq_buscar` ok). Próximo: webhook Znuny→Hermes→Teams. Detalhes na memory `mcp-otrs-leitura`; usa o módulo FAQ (552 itens). Decisão pendente: LLM externa x local (LGPD).
- Serviço **otrs-faq** (sem LLM) no app-ti, porta 8095: webhook do Znuny (TicketCreate, filas TI::*) → índice BM25 da FAQ (366 artigos) + chamados fechados parecidos (por título) → card no Teams roteado por fila (TI::Infraestrutura/BI/Sistemas/demais, um fluxo Power Automate cada). Código `C:\project\Hermes\otrs_faq\` + core `otrs_mcp/otrs_core.py` (o MCP usa o mesmo core). Roda em modo teste; faltam URLs dos 4 fluxos do Teams, `OTRS_BASE_URL` e importar `FaqSugestao_HML.yml` no HML. Detalhes na memory `servico-otrs-faq`; relaciona com [[otrs]] (4 web services TeamsChat).
- Limites do Hermes: webhook só ativa agente (HMAC, plataforma desligada), entrega só em chats (sem Teams); por isso o `otrs-faq` fica fora do Hermes. Fase com LLM proposta: Znuny→otrs-faq(HMAC)→webhook Hermes→MCP→tool `postar_teams`→Power Automate→Teams. Propostas sem resposta: skill anti-alucinação + desativar `otrs_select`, tool `sugerir_chamado`, página `:8095/`. Detalhes na memory `plano-agente-otrs-analise-chamado`.
- Guardrails do agente OTRS (provisório, no `SOUL.md` do Hermes) + skill local `otrs-suporte-ti` + `otrs_select` excluída do MCP (tools.exclude). Hermes não filtra PII p/ o LLM; a máscara fica no código do MCP. Falta reiniciar `hermes-agent` (perguntado). Ver memory `mcp-otrs-leitura`.
- Pendente: `~/.pm2`, logs; decidir se traz o código para `C:\project\Hermes`.

## Índice de tópicos
- Onde roda / acesso → [[#Decisões e planos]] + skill de projeto `ssh-app-ti` (2026-10-28)
- Chave do Claude no Hermes → [[#Estado atual]] + memory `hermes-chave-claude-anthropic` (2026-11-06)
- Histórico do 9router/config e log antigo → [[Hermes - arquivo]] (2026-11-06)

## Relacionados
- [[agent_hermes]] — projeto irmão (também vazio localmente)
- [[otrs]] — agente de análise de chamados (Znuny→Hermes→Teams) reaproveita o webhook/Teams do OTRS

## Memória do projeto (Claude)
Pasta: `C:/Users/rodrigo.maia/.claude/projects/C--project-Hermes/memory`
- hermes-servidor-app-ti.md — onde roda e portas
- ssh-app-ti-via-env-var.md — como logar (armadilha do escopo User)
- hermes-chave-claude-anthropic.md — provider anthropic, ANTHROPIC_API_KEY, opções A/B/C

## Decisões e planos
- Hermes roda no app-ti (192.168.1.251), container `hermes-agent`, :8090. Acesso SSH `cootrati`, senha em env var `app-ti` (User). Só leitura no servidor até o usuário pedir alteração. Nunca gravar a senha.

## Log de sessões
- 2026-11-06 — Hermes passou a consultar o vault: criada skill `vault-conhecimento` + bloco no SOUL.md; teste mostrou chamadas `mcp_vault_*` no log. MCP lê a cópia local do servidor (sync de 30 min do PC), não o PC.
- 2026-11-06 — Vault MCP no ar (container recriado, 925 notas, tarefa agendada de 30 min no Windows). A recriação trouxe de volta o "Chat unavailable: 1": faltavam `ui-tui/` e `HERMES_NODE` (correções antigas feitas à mão na imagem de jul/2026); agora persistentes no compose (patches/, HERMES_NODE, patch sk-ant-svc, vault-data). Ver memory `hermes-recriar-container-persistencia`.
- 2026-11-06 — Vault MCP instalado no app-ti (chave restrita, envio de 925 notas ok, MCP testado por protocolo; compose e config.yaml alterados com backup). Falta: persistir o patch sk-ant-svc (bloqueado pelas permissões; usuário roda), recriar o hermes-agent (`docker compose up -d`), tarefa agendada no Windows e teste no Hermes.
- 2026-11-06 — Verificado: Hermes sem suporte nativo a Obsidian/`OBSIDIAN_VAULT_PATH`; vault sem Smart Connections (só plugins REST). Busca semântica via Ollama ficou como fase 2 opcional do MCP do vault; aguardando OK p/ iniciar a instalação da fase 1.
- 2026-11-06 — Vault MCP: escopo = vault inteiro; servidor não alcança o PC e o cron do Hermes não dispara (gateway parado) → PC envia via Agendador (`sync_vault.ps1` + `vault_receive.sh`, symlink `current`); scripts prontos em `vault_mcp/`, nada instalado; aguardando OK p/ chave SSH, servidor, compose e tarefa agendada.
- 2026-11-06 — Criado o MCP do vault Obsidian (`C:\project\Hermes\vault_mcp`, 4 tools só leitura, máscara de segredos), testado local em Projetos+Hubs; falta deploy no app-ti + sync + registro no config.yaml (pedir OK). Ver memory `mcp-vault-obsidian`.
- 2026-11-06 — Usuário perguntou como Hermes e o Claude do OTRS (módulo ZnunyAICopilot) conversam via MCP sem banco; proposta: MCP otrs via API REST do Znuny + nota interna via TicketUpdate; aguardando escolha (a: Copilot responde com FAQ / b: Hermes sugere no chamado). Ver memory `proposta-hermes-znuny-via-api` e [[otrs]].
- 2026-11-06 — Claude funcionando também no painel após o usuário reiniciar o hermes-agent (patch só vale após restart). Pendente: patch no Dockerfile, apagar variável Windows `ANTHROPIC_KEY_HERMES`.
- 2026-11-06 — Claude funcionando no Hermes: usuário aplicou o patch `sk-ant-svc` em `_is_oauth_token`; `--provider anthropic` e `custom:claude` respondem ok. Padrão segue 9router. Pendente: patch no Dockerfile, decidir Claude como padrão (restart), apagar variável Windows.
- 2026-11-06 — Causa raiz do 400 de crédito: Hermes trata a chave `sk-ant-svc` como OAuth e injeta o prompt "You are Claude Code", recusado pela Anthropic. Padrão restaurado p/ 9router. Patch em `_is_oauth_token` negado pelas permissões; aguardando usuário (autorizar patch, rodar sed, ou chave `sk-ant-api03`).
- 2026-11-06 — Provider `claude` (api.anthropic.com, anthropic_messages) adicionado em custom_providers; curl direto ok mas Hermes ainda recebe 400 de crédito (request_id no errors.log). Padrão do Hermes foi mudado no painel para anthropic/claude-sonnet-5 (quebrado); aguardando decisão de restaurar custom:9router/gcli/grok-4.7.
- 2026-11-06 — Chave do Claude (`sk-ant-svc-`) gravada em data/.env e válida direto na API, mas `--provider anthropic` falha no Hermes com "credit balance too low" (credencial vira exhausted); endpoint ok; proposta: custom_providers `claude` ou chave `sk-ant-api03`; aguardando OK do usuário.
- 2026-11-06 — Opção B escolhida p/ chave do Claude; variável `ANTHROPIC_KEY_HERMES` criada mas inválida (truncada); gravação no servidor abortada, aguardando nova chave.
- 2026-10-28 — Criado o serviço otrs-faq (sem LLM) no app-ti com roteamento por fila; testado em modo teste; aguardando URLs do Teams e importação do web service no HML.
- 2026-10-28 — Criado e testado no app-ti o MCP OTRS somente leitura (FAQ + chamados); registro no Hermes aguardando OK do usuário.
- 2026-10-28 — Análise do vault p/ agente OTRS no Hermes: proposta de arquitetura e MVP (fila TI); aguardando respostas do usuário.
- 2026-10-28 — Hermes apontado para o 9router do servidor com grok-4.7 (`custom:9router`); teste one-shot ok; restart do hermes-agent pendente.
- 2026-11-06 — Pedido para configurar chave do Claude no Hermes: levantado que há provider `anthropic` + `ANTHROPIC_API_KEY` em `data/.env`; propostas A/B/C; aguardando escolha, chave e erro do usuário.
