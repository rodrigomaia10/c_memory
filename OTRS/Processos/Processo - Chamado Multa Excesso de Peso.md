---
tipo: otrs-processo
tags: [otrs, otrs/processo, estado/active]
atualizado: 2026-10-23
fonte: snapshot do repo otrs (ZZZProcessManagement.pm / ZZZACL.pm)
entity: Process-ad2e5a5f9ef57a1025737cf457e8a46d
estado: Active
---

# Processo - Chamado Multa Excesso de Peso

**Chamado Multa Excesso de Peso** — estado **Active** · criado 2022-01-21 10:15:52 · alterado 2022-01-21 15:49:56

Hub: [[Hub - OTRS Processos]] · [[Hub - OTRS]] · [[otrs]]

Início: **1.Abertura Chamado Multa Excesso de Peso** → diálogo [[Dialog - Formulario Multa Excesso de Peso]]

## Fluxo
```mermaid
flowchart LR
  A500726c0["2.Atendimento Societário Multa Excesso Peso"]
  A08d003a1["1.Abertura Chamado Multa Excesso de Peso"]
  style A08d003a1 stroke-width:3px
  A08d003a1 -->|"Envia Fila>> Societario Multa Excesso de Peso"| A500726c0
```

## Atividades e diálogos
- **1.Abertura Chamado Multa Excesso de Peso** (início): [[Dialog - Formulario Multa Excesso de Peso]]
- **2.Atendimento Societário Multa Excesso Peso**: [[Dialog - Formulario Multa Excesso de Peso]]

## Transições
- **Envia Fila>> Societario Multa Excesso de Peso**: 1.Abertura Chamado Multa Excesso de Peso → 2.Atendimento Societário Multa Excesso Peso
  - Condição: (and: [[DF - CteDB]] Regexp `.`; [[DF - Placa]] Regexp `.`)
  - Ação *Atribui Fila>> Societario Multa Excesso de Peso* — TicketQueueSet: Fila [[Fila - CRC]]
  - Ação *Atribui>>Servico Processo: Chamado Multa Excesso de Peso* — TicketServiceSet: Serviço [[Servico - Processo- Chamado Multa Excesso de Peso]]
  - Ação *Atribui>>Titulo Processo: Chamado Multa Excesso de Peso* — TicketTitleSet: Title=`Placa: <OTRS_TICKET_DynamicField_CtePlaca> | CT-e :<OTRS_TICKET_DynamicField_CteNumero> | Cliente : <OTRS_TICKET_DynamicField_CteNomePagador>`

## ACLs que se aplicam (diretas ou por diálogo)
- nenhuma

> Fonte: snapshot do repo (espelho da prod); fila/serviço aparecem como nomes nas ações.
