---
tipo: otrs-acl
tags: [otrs, otrs/acl]
atualizado: 2026-10-23
fonte: snapshot do repo otrs (ZZZProcessManagement.pm / ZZZACL.pm)
---

# ACL - 3- Esconde Servicos RH para não Gestores

Hub: [[Hub - OTRS ACLs]] · [[Hub - OTRS]] · ordem de execução: alfabética pelo nome, a última que casa por campo vence.

Criada 2021-07-26 11:16:01 (samuel.euzebio) · alterada 2021-08-30 18:12:00 (samuel.euzebio) · comentário: 3- Esconde Servicos RH para não Gestores · StopAfterMatch=0

## Quando se aplica (Properties)
- CustomerUser.Group_rw: `Usuários Clientes Geral`

## Efeito
- PossibleNot Ticket.Service: [[Servico - RH › Rescisão › Rescisão de Contrato - Desligamento por Parte da Cooperativa]], [[Servico - RH › Rescisão › Rescisão de Contrato - Desligamento por Parte do Colaborador]], [[Servico - RH › Rescisão › Rescisão de Contrato - Simulação de Rescisão]], [[Servico - RH › Rescisão]], [[Servico - RH › Férias]], [[Servico - RH › Medidas Disciplinares]], [[Servico - RH › Remuneração e Movimentação - Cargo-Setor-Unidade-Centro de Custos]], [[Servico - RH › Recrutamento e Seleção]], [[Servico - RH › Remuneração]], [[Servico - RH › Treinamento]]
