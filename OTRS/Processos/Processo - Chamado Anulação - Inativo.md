---
tipo: otrs-processo
tags: [otrs, otrs/processo, estado/inactive]
atualizado: 2026-10-23
fonte: snapshot do repo otrs (ZZZProcessManagement.pm / ZZZACL.pm)
entity: Process-daf4f0a0be940199427572f084496e73
estado: Inactive
---

# Processo - Chamado Anulação - Inativo

**Chamado Anulação - Inativo** — estado **Inactive** · criado 2020-11-23 14:32:00 · alterado 2022-01-12 10:42:05

Hub: [[Hub - OTRS Processos]] · [[Hub - OTRS]] · [[otrs]]

Início: **Processo exemplo** → diálogo [[Dialog - Formulário Anulação]]

## Fluxo
```mermaid
flowchart LR
  A66b3cc4f["Processo exemplo"]
  Aa9eb3bc6["3.1 Fecha Chamado Societario Divergencia Valor do Frete"]
  style A66b3cc4f stroke-width:3px
  A66b3cc4f -->|"Envia Fila>> Societario"| Aa9eb3bc6
```

## Atividades e diálogos
- **3.1 Fecha Chamado Societario Divergencia Valor do Frete**: [[Dialog - Formulário Anulação]]
- **Processo exemplo** (início): [[Dialog - Formulário Anulação]]

## Transições
- **Envia Fila>> Societario**: Processo exemplo → 3.1 Fecha Chamado Societario Divergencia Valor do Frete
  - Condição: (and: [[DF - CteClienteTipoNestle]] String `NAONESTLE`; [[DF - CteDB]] Regexp `.`; [[DF - CtePlaca]] Regexp `.`)
  - Ação *Atribuir>>Tabela: Anulação* — DynamicFieldSet: <OTRS_TICKET_DynamicField_TabelaAnulacao>=`testado`

## ACLs que se aplicam (diretas ou por diálogo)
- nenhuma

> Fonte: snapshot do repo (espelho da prod); fila/serviço aparecem como nomes nas ações.
