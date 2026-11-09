---
tipo: otrs-processo
tags: [otrs, otrs/processo, estado/inactive]
atualizado: 2026-10-23
fonte: snapshot do repo otrs (ZZZProcessManagement.pm / ZZZACL.pm)
entity: Process-217d3e9969ace767f68eaf779a4908c2
estado: Inactive
---

# Processo - Cadastro de Motorista

**Cadastro de Motorista** — estado **Inactive** · criado 2022-07-27 15:30:11 · alterado 2022-10-10 13:51:32

Hub: [[Hub - OTRS Processos]] · [[Hub - OTRS]] · [[otrs]]

Início: **Iniciar Cadastro de Motorista** → diálogo [[Dialog - Formulario de Cadastro de Motorista]]

## Fluxo
```mermaid
flowchart LR
  A1012e7fe["Iniciar Cadastro de Motorista"]
  Aa9576c91["Atende Chamado Cadastro Motorista"]
  style A1012e7fe stroke-width:3px
  A1012e7fe -->|"Envia Fila CRC"| Aa9576c91
```

## Atividades e diálogos
- **Atende Chamado Cadastro Motorista**: —
- **Iniciar Cadastro de Motorista** (início): [[Dialog - Formulario de Cadastro de Motorista]]

## Transições
- **Envia Fila CRC**: Iniciar Cadastro de Motorista → Atende Chamado Cadastro Motorista
  - Condição: (and: [[DF - CTeReembolsoCircuitos]] Regexp `.`)
  - Ação *Envia Fila>>CRC1* — TicketQueueSet: Fila [[Fila - CRC]]

## ACLs que se aplicam (diretas ou por diálogo)
- nenhuma

> Fonte: snapshot do repo (espelho da prod); fila/serviço aparecem como nomes nas ações.
