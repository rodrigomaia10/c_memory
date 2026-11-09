---
tipo: projeto
caminho: C:\project\laya
status: migrado
dominio: agentes
tags: [projeto, dominio/agentes]
criado: 2026-10-16
atualizado: 2026-10-16
---
# laya

Pasta `C:\project\laya` (migrada de `C:\laya` em 2026-10-16): `laya-mcp-server.exe`, `obsidian-mcp` (MCP do vault operacional), `obsidian_cootravale`, `cootra_graphos`, `pipeline`.

Hub: [[Hub - Agentes e MCP]] · Raiz: [[Cootravale]]

## Relacionados
- [[obsidian_vault]] — vault operacional servido pelo `obsidian-mcp`
- [[claude_memory]] — vault de memória do Claude (outro vault)
- [[mcp_server_tools_cootravale]] — outro MCP da Cootravale
- [[PowerBIClaudio]] — dados de Power BI consumidos via MCP

## Memória do projeto (Claude)
Ver `C:/Users/rodrigo.maia/.claude/projects/C--project-laya/memory` (`project_migracao_laya.md`).

## Decisões e planos
- Migração concluída em 2026-10-16: processos parados, pasta movida, `command`/`args` de laya-server e obsidian corrigidos em `~/.claude.json` (backup `.bak-20261016-091303`), memória renomeada para `C--project-laya`, `server.mjs` com caminhos `pipeline/` corrigidos. Reconexão dos MCPs ainda não testada (precisa reiniciar sessão).

## Log de sessões
- 2026-10-16 — Nó criado antes da migração.
- 2026-10-16 — Pasta migrada para C:\project\laya; MCPs reapontados; referências antigas só em otrs/teams.
- 2026-10-22 — Avaliado uso no contábil/DRE: Laya = motor de decisão tipada (texto), sqljev = jev() em SQL (DuckDB/Postgres, não Athena); onde aplicar e achados em [[Apolo11]]. Senha Postgres em texto puro em sqljev_lib.py; MCP laya-server não conectou.
- 2026-10-22 — Decidido não usar Laya no contábil/DRE (ganho marginal); projeto segue como estava.
