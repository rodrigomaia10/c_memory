---
tipo: arquivo
projeto: Hermes
tags: [arquivo, projeto/hermes]
criado: 2026-11-06
---
# Hermes — arquivo

Histórico resolvido/superado do nó [[Hermes]]. Só acrescentar, nunca apagar.

## Estado antigo do 9router/config (superado em 2026-10-28, ver estado ATUAL no nó)
- Localizado em 2026-10-28: container `hermes-agent` no app-ti, :8090, código em `~/hermes-docker`; SSH `cootrati`, senha na env var `app-ti` (User).
- Config inicial: provider openai-api → Ollama llama3.1:8b; `custom_providers` OllamaDoMaia; MCP `cooperado`.
- 9router do PC (http://10.80.9.165:20128/v1, modelo `maia`): auth OK, mas provedores falhavam (combo `mimo-auto`, groq 404, gemini-cli 403, mistral 403, deepseek 402). Substituído pelo 9router no app-ti.
- 9router movido para o app-ti (container `9router`, :20128, interno `http://9router:20128/v1`), inicialmente vazio; painel com senha via `INITIAL_PASSWORD`.
- Hermes ficou sem responder: config.yaml reescrito às 17:14 para provider openrouter/`ollama/minimax-m2.5` sem chave (401); resolvido apontando para `custom:9router`.

## Log antigo
- 2026-10-28 — Senha do painel 9router (servidor) definida; diagnosticado config.yaml com provider openrouter sem chave.
- 2026-10-28 — 9router subido como serviço Docker no app-ti (v0.5.112, vazio).
- 2026-10-28 — Chave do 9router gravada e testada: auth OK, modelos falham por erros dos provedores.
- 2026-10-28 — 9router (PC, :20128) inserido no config.yaml do Hermes com backup; aguardando chave.
- 2026-10-28 — Lida a config (Ollama + MCP cooperado); skill ssh-app-ti ganhou armadilhas de quoting/BOM.
- 2026-10-28 — Localizado o Hermes no app-ti via SSH; criada skill `ssh-app-ti`.
