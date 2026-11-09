---
tipo: otrs-processo
tags: [otrs, otrs/processo, estado/inactive]
atualizado: 2026-10-23
fonte: snapshot do repo otrs (ZZZProcessManagement.pm / ZZZACL.pm)
entity: Process-414a68f941ab2def6682afc9d8bd8754
estado: Inactive
---

# Processo - Chamado para Cancelamentos LCD-Contrato-Extrato

**Chamado para Cancelamentos LCD/Contrato/Extrato** — estado **Inactive** · criado 2022-02-21 17:02:51 · alterado 2022-02-21 17:55:09

Hub: [[Hub - OTRS Processos]] · [[Hub - OTRS]] · [[otrs]]

Início: **Abertura de Chamado Cancelamentos** → diálogo (?)

## Fluxo
```mermaid
flowchart LR
  A42106595["Abertura de Chamado Cancelamentos"]
  Aeaf8243a["3.Atendimento Societário"]
  style A42106595 stroke-width:3px
  A42106595 -->|"Envia Fila>> Societario"| Aeaf8243a
```

## Atividades e diálogos
- **3.Atendimento Societário**: [[Dialog - Formulário Diária de Devolução]] · [[Dialog - Controle Atendimento Processo (aadcb8)]]
- **Abertura de Chamado Cancelamentos** (início): —

## Transições
- **Envia Fila>> Societario**: Abertura de Chamado Cancelamentos → 3.Atendimento Societário
  - Condição: (and: [[DF - CteClienteTipoNestle]] String `NAONESTLE`; [[DF - CteDB]] Regexp `.`; [[DF - CtePlaca]] Regexp `.`)

## ACLs que se aplicam (diretas ou por diálogo)
- nenhuma

> Fonte: snapshot do repo (espelho da prod); fila/serviço aparecem como nomes nas ações.
