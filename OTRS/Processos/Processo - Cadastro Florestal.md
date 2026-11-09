---
tipo: otrs-processo
tags: [otrs, otrs/processo, estado/inactive]
atualizado: 2026-10-23
fonte: snapshot do repo otrs (ZZZProcessManagement.pm / ZZZACL.pm)
entity: Process-7caae57895528905892e83852a93eb43
estado: Inactive
---

# Processo - Cadastro Florestal

**Cadastro Florestal** — estado **Inactive** · criado 2022-07-28 16:53:57 · alterado 2023-10-27 16:58:59

Hub: [[Hub - OTRS Processos]] · [[Hub - OTRS]] · [[otrs]]

Início: **Cadastro Florestal** → diálogo [[Dialog - Formulario de Cadastro de Motorista]]

## Fluxo
```mermaid
flowchart LR
  A961ea201["13 - Chamado Encerrado"]
  Aea5fbb0f["Cadastro Florestal"]
  style Aea5fbb0f stroke-width:3px
  Aea5fbb0f -->|"Envia Fila CRC"| A961ea201
```

## Atividades e diálogos
- **13 - Chamado Encerrado**: [[Dialog - Encerrar Demanda]]
- **Cadastro Florestal** (início): [[Dialog - Formulario de Cadastro de Motorista]]

## Transições
- **Envia Fila CRC**: Cadastro Florestal → 13 - Chamado Encerrado
  - Condição: (and: [[DF - CTeReembolsoCircuitos]] Regexp `.`)

## ACLs que se aplicam (diretas ou por diálogo)
- nenhuma

> Fonte: snapshot do repo (espelho da prod); fila/serviço aparecem como nomes nas ações.
