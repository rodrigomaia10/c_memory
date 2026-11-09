---
tipo: otrs-processo
tags: [otrs, otrs/processo, estado/inactive]
atualizado: 2026-10-23
fonte: snapshot do repo otrs (ZZZProcessManagement.pm / ZZZACL.pm)
entity: Process-edc94ee47d6af17bd958cf47bd0a50f4
estado: Inactive
---

# Processo - Reembolso de Despesa Conselheiros(copiar)

**Reembolso de Despesa Conselheiros(copiar)** — estado **Inactive** · criado 2022-07-28 17:32:24 · alterado 2022-07-28 17:32:24

Hub: [[Hub - OTRS Processos]] · [[Hub - OTRS]] · [[otrs]]

Início: **Abrir chamado Reembolso despesas** → diálogo [[Dialog - Formulário Reembolso Despesas Conselheiros]]

## Fluxo
```mermaid
flowchart LR
  A32ecdaac["FechaChamadoReembolsoDespesa"]
  Af719c203["Abrir chamado Reembolso despesas"]
  style Af719c203 stroke-width:3px
  Af719c203 -->|"EnviaFilaCRCReembolso"| A32ecdaac
```

## Atividades e diálogos
- **Abrir chamado Reembolso despesas** (início): [[Dialog - Formulário Reembolso Despesas Conselheiros]]
- **FechaChamadoReembolsoDespesa**: [[Dialog - Encerrar Demanda]] · [[Dialog - Termina]]

## Transições
- **EnviaFilaCRCReembolso**: Abrir chamado Reembolso despesas → FechaChamadoReembolsoDespesa
  - Condição: (and: [[DF - NomeCooperadoReembolso]] Regexp `.`)
  - Ação *Atribuir fila CRC* — TicketQueueSet: Fila [[Fila - CRC]]

## ACLs que se aplicam (diretas ou por diálogo)
- nenhuma

> Fonte: snapshot do repo (espelho da prod); fila/serviço aparecem como nomes nas ações.
