---
tipo: otrs-acl
tags: [otrs, otrs/acl]
atualizado: 2026-10-23
fonte: snapshot do repo otrs (ZZZProcessManagement.pm / ZZZACL.pm)
---

# ACL - 5 - Mostra serviço RH para Gestores

Hub: [[Hub - OTRS ACLs]] · [[Hub - OTRS]] · ordem de execução: alfabética pelo nome, a última que casa por campo vence.

Criada 2021-07-26 11:55:24 (samuel.euzebio) · alterada 2021-08-30 18:11:43 (samuel.euzebio) · comentário: 5 - Mostra serviço RH para Gestores · StopAfterMatch=0

## Quando se aplica (Properties)
- CustomerUser.Group_rw: `Gestores Cliente RH`

## Efeito
- PossibleAdd Ticket.Service: [[Servico - RH › Rescisão]], [[Servico - RH › Rescisão › Rescisão de Contrato - Desligamento por Parte da Cooperativa]], [[Servico - RH › Rescisão › Rescisão de Contrato - Desligamento por Parte do Colaborador]], [[Servico - RH › Rescisão › Rescisão de Contrato - Simulação de Rescisão]], [[Servico - RH › Férias]], [[Servico - RH › Férias › Férias - Agendamento de férias]], [[Servico - RH › Férias › Férias - Cancelamento de Férias]], [[Servico - RH › Férias › Férias - Relátorio de Férias]], [[Servico - RH › Medidas Disciplinares]], [[Servico - RH › Medidas Disciplinares › Medidas Disciplinares - Advertência]], [[Servico - RH › Medidas Disciplinares › Medidas Disciplinares - Suspensão]], [[Servico - RH › Recrutamento e Seleção]], [[Servico - RH › Recrutamento e Seleção › Recrutamento e Seleção - Contratação-Substituíção Gestão]], [[Servico - RH › Recrutamento e Seleção › Recrutamento e Seleção - Contratação-Substituíção]], [[Servico - RH › Recrutamento e Seleção › Recrutamento e Seleção - Recrutamento Interno]], [[Servico - RH › Remuneração e Movimentação - Cargo-Setor-Unidade-Centro de Custos]], [[Servico - RH › Remuneração]], [[Servico - RH › Treinamento]]
