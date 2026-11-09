---
tipo: otrs-processo
tags: [otrs, otrs/processo, estado/active]
atualizado: 2026-10-23
fonte: snapshot do repo otrs (ZZZProcessManagement.pm / ZZZACL.pm)
entity: Process-65ea47102f723f5359a2e6b3b9bdd3f6
estado: Active
---

# Processo - Chamado Pesquisa Novo Cavalo

**Chamado Pesquisa Novo Cavalo** — estado **Active** · criado 2021-04-07 15:19:34 · alterado 2026-09-03 09:53:53

Hub: [[Hub - OTRS Processos]] · [[Hub - OTRS]] · [[otrs]]

Início: **1.Abertura Chamado Pesquisa Cavalo** → diálogo [[Dialog - Formulario Pesquisa Cavalo (5b65d9)]]

## Fluxo
```mermaid
flowchart LR
  A985f85ca["1.Abertura Chamado Pesquisa Cavalo"]
  A2e7e7ebf["3.1 Fecha Chamado Societario Pesquisa Cavalo"]
  A1fe9a0a5["3.Atendimento Societário Pesquisa Cavalo"]
  style A985f85ca stroke-width:3px
  A985f85ca -->|"Envia Fila>> Gestao de Frota Pesquisa Cavalo"| A1fe9a0a5
  A1fe9a0a5 -->|"Fecha Chamado >> Societario Pesquisa Motorista"| A2e7e7ebf
```

## Atividades e diálogos
- **1.Abertura Chamado Pesquisa Cavalo** (início): [[Dialog - Formulario Pesquisa Cavalo (5b65d9)]]
- **3.1 Fecha Chamado Societario Pesquisa Cavalo**: [[Dialog - Formulario Pesquisa Cavalo (5b65d9)]]
- **3.Atendimento Societário Pesquisa Cavalo**: [[Dialog - Formulario Pesquisa Cavalo (5b65d9)]] · [[Dialog - Controle Atendimento Processo (aadcb8)]]

## Transições
- **Envia Fila>> Gestao de Frota Pesquisa Cavalo**: 1.Abertura Chamado Pesquisa Cavalo → 3.Atendimento Societário Pesquisa Cavalo
  - Condição: (and: [[DF - PesqCavalo]] Regexp `.`)
  - Ação *Atribuir fila CRC* — TicketQueueSet: Fila [[Fila - CRC]]
  - Ação *Atribui>>Titulo Processo Pesquisa Cavalo* — TicketTitleSet: Title=`Pesquisa Cavalo : <OTRS_TICKET_DynamicField_PesqCavalo> | Carreta : <OTRS_TICKET_DynamicField_PesqCavaloPlacaCarreta>`
  - Ação *Atribui>>Servico Processo: Chamado Pesquisa Novo Cavalo* — TicketServiceSet: Serviço [[Servico - Processo- Chamado Pesquisa Novo Cavalo]]
- **Fecha Chamado >> Societario Pesquisa Motorista**: 3.Atendimento Societário Pesquisa Cavalo → 3.1 Fecha Chamado Societario Pesquisa Cavalo
  - Condição: (and: [[DF - CteControleAtividades]] String `Finalizar Atendimento Societario`)
  - Ação *Muda Estado Chamado >> Fechado* — TicketStateSet: StateID=`2`

## ACLs que se aplicam (diretas ou por diálogo)
- nenhuma

> Fonte: snapshot do repo (espelho da prod); fila/serviço aparecem como nomes nas ações.
