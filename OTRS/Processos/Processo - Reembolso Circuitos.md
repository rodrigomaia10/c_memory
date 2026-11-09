---
tipo: otrs-processo
tags: [otrs, otrs/processo, estado/inactive]
atualizado: 2026-10-23
fonte: snapshot do repo otrs (ZZZProcessManagement.pm / ZZZACL.pm)
entity: Process-dde05dc9069dfdb1669e3cc8cab0ac04
estado: Inactive
---

# Processo - Reembolso Circuitos

**Reembolso Circuitos** — estado **Inactive** · criado 2022-05-04 08:42:36 · alterado 2023-10-30 08:44:03

Hub: [[Hub - OTRS Processos]] · [[Hub - OTRS]] · [[otrs]]

Início: **Reembolso Circuitos** → diálogo [[Dialog - Abre Chamado Reembolso Circuitos]]

## Fluxo
```mermaid
flowchart LR
  A474ff927["Atendimento CRC"]
  A2de84273["Reembolso Circuitos"]
  A19151257["2. Atendimento Contas Receber Frete Devolução"]
  style A2de84273 stroke-width:3px
  A2de84273 -->|"Envia Fila CRC"| A474ff927
  A2de84273 -->|"Envia Fila>> Contas Receber"| A19151257
```

## Atividades e diálogos
- **2. Atendimento Contas Receber Frete Devolução**: [[Dialog - Formulário Frete Devolução]]
- **Atendimento CRC**: —
- **Reembolso Circuitos** (início): [[Dialog - Abre Chamado Reembolso Circuitos]]

## Transições
- **Envia Fila CRC**: Reembolso Circuitos → Atendimento CRC
  - Condição: (and: [[DF - CTeReembolsoCircuitos]] Regexp `.`)
  - Ação *Envia Fila>> Societario* — TicketQueueSet: Fila [[Fila - CRC]]
  - Ação *Serviço Reembolso Circuitos CRC* — TicketServiceSet: Serviço [[Servico - Processo- Reembolso Circuitos]]
- **Envia Fila>> Contas Receber**: Reembolso Circuitos → 2. Atendimento Contas Receber Frete Devolução
  - Condição: (and: [[DF - CteClienteTipoNestle]] String `NESTLE`; [[DF - CteDB]] Regexp `.`; [[DF - CtePlaca]] Regexp `.`)

## ACLs que se aplicam (diretas ou por diálogo)
- [[ACL - 2- Mostra Campos Chamado]]

> Fonte: snapshot do repo (espelho da prod); fila/serviço aparecem como nomes nas ações.
