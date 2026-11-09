---
tipo: convencao
tags: [convencao]
atualizado: 2026-10-16
---
# Convenções de memória

- **Primária:** `~/.claude/projects/<projeto>/memory/` (arquivos `*.md` + índice `MEMORY.md`) — carregada automaticamente.
- **Secundária (este vault):** um nó por pasta de `C:\project` em `Projetos/<pasta>.md`.
- Nó novo: criar `Projetos/<pasta>.md` a partir do modelo abaixo e linkar no hub do domínio e em nós relacionados.
- Links `[[...]]` só para relações que fazem sentido (mesmo sistema, dependência, origem/destino de dados).
- **Estado atual** (3–8 linhas) e **Índice de tópicos** ficam no topo do nó; o hook SessionStart injeta os dois + 5 últimas linhas do Log. O resto é lido/buscado sob demanda.
- Log: uma linha por sessão relevante em "Log de sessões" (só ~5 no nó); decisões duráveis e vigentes em "Decisões e planos".
- **Arquivo:** o histórico resolvido/tentativas vai para `Projetos/<pasta> - arquivo.md` (linkado no nó). Só acrescentar, nunca apagar; o Índice aponta para lá.
- Rotina completa: skill `/salvar-memoria`.

## Modelo de nó
```
---
tipo: projeto
caminho: C:\project\<pasta>
dominio: dados|portal|agentes|legado|suporte|misc
tags: [projeto, dominio/<dominio>]
criado: AAAA-MM-DD
atualizado: AAAA-MM-DD
---
# <pasta>
<descrição>
Hub: [[Hub - ...]] · Raiz: [[Cootravale]]
## Relacionados
- Histórico completo: [[<pasta> - arquivo]]
## Estado atual
## Índice de tópicos
## Memória do projeto (Claude)
## Decisões e planos
## Log de sessões
```
- Hook `memoria.mjs`: sessão na raiz `C:\project` é tratada como não-projeto (sem nó próprio); subpastas seguem a regra de nó por pasta.
- Mapa da AWS: pasta `AWS/` (gerado por AWS CLI, hub [[Hub - AWS]]); não é pasta de `C:\project`, então não tem nó em `Projetos/`.
