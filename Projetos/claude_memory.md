---
tipo: projeto
caminho: C:\project\claude_memory
dominio: agentes
tags: [projeto, dominio/agentes]
criado: 2026-10-16
atualizado: 2026-10-21
---
# claude_memory

Este vault: memória secundária do Claude. Cada pasta de C:\project tem um nó em Projetos/.

Hub: [[Hub - Agentes e MCP]] · Raiz: [[Cootravale]]

## Relacionados
- [[obsidian_vault]] — vault operacional

## Estado atual
- Formato novo dos nós em vigor desde 2026-10-21 (Estado atual + Índice + arquivo; hook injeta o resumo). Migrados: [[otrs]], [[Apolo11]], [[PowerBIClaudio]]; os demais migram no próximo /salvar-memoria de cada projeto.
- Skills de procedimento são sempre de projeto; o hook avisa quando o projeto não tem `.claude/skills` e o /salvar-memoria cria. Próximo: conferir numa sessão nova se o resumo do hook chega ao contexto; usuário deve revisar o Estado atual do otrs e do Apolo11.

## Índice de tópicos (onde achar o antigo)
- Regras do formato → [[Convenções de memória]] e skill salvar-memoria (~/.claude/skills)
- Hook SessionStart/Stop/PreCompact → ~/.claude/hooks/memoria.mjs; decisão em Decisões abaixo
- Registro do vault no Obsidian (vault pai) → Decisões abaixo

## Memória do projeto (Claude)
Pasta: `C:/Users/rodrigo.maia/.claude/projects/C--project-claude-memory/memory`
- obsidian-vault-registro-e-vault-pai.md

## Decisões e planos
<!-- /salvar-memoria acrescenta aqui decisões duráveis -->
- Nunca registrar `C:project` como vault do Obsidian (vault pai causa erro de permissão em `venvib64`); cofres válidos: claude_memory e obsidian_vault. Restauração via `obsidian.json`.
- **Formato dos nós (2026-10-21):** hook injeta Estado atual, Índice e 5 últimas linhas do Log (máx. 4500 caracteres); sem Estado atual, fallback (nó pequeno inteiro, grande truncado). Histórico resolvido vai para `<pasta> - arquivo` (só acrescentar). Se o pedido citar algo fora do resumo, buscar no vault antes de agir (regra no CLAUDE.md global). Backups da migração em ~/.claude/state/*.bak.

## Log de sessões
<!-- /salvar-memoria acrescenta linhas "- AAAA-MM-DD — resumo" -->
- 2026-10-16 — Vault populado: 44 nós em Projetos/, 6 hubs, [[Cootravale]] e [[Convenções de memória]]. MCP obsidian deu `fetch failed`; escrita feita direto em disco.
- 2026-10-20 — Vault sumiu do Obsidian após mover pasta; reregistrado em obsidian.json e removido o vault pai C:\project (.obsidian renomeado).
- 2026-10-21 — Formato novo dos nós (Estado atual, Índice, arquivo) e hook que injeta o resumo; migrados otrs, Apolo11 e PowerBIClaudio; skill, Convenções e CLAUDE.md atualizados.
