---
tipo: otrs-acl
tags: [otrs, otrs/acl]
atualizado: 2026-10-23
fonte: snapshot do repo otrs (ZZZProcessManagement.pm / ZZZACL.pm)
---

# ACL - 5- Mostra Catalogo de Serviços Cootravale x Edukar

Hub: [[Hub - OTRS ACLs]] · [[Hub - OTRS]] · ordem de execução: alfabética pelo nome, a última que casa por campo vence.

Criada 2021-02-11 09:36:06 (rodrigo.maia) · alterada 2025-07-17 11:01:38 (samuel.euzebio) · comentário: Mostra serviços cootravale para escritório Contábil. Edukar · StopAfterMatch=0

## Quando se aplica (Properties)
- CustomerUser.Group_rw: `EDUKAR`

## Efeito
- PossibleAdd Ticket.Service: [[Servico - Contas a Pagar › Dúvida de Usuário - CAP › Lançamentos - Documentos]], [[Servico - Contas a Pagar › Ajustes › Correção de Lançamentos]], [[Servico - Societário › Ajustes › Correção de Lançamentos]], [[Servico - RH › Dúvidas › Lançamentos - Documentos]], [[Servico - RH › Ajustes › Correção de Lançamentos]], [[Servico - RH › Folha › Arquivo de Integração]], [[Servico - Suprimentos › Dúvidas › Lançamentos - Documentos]], [[Servico - Controladoria › Rodopar › Criação de Relatório]], [[Servico - Controladoria › Dúvidas › Lançamentos Contábeis]], [[Servico - TI]], [[Servico - Contas a Pagar]], [[Servico - Societário]], [[Servico - RH]], [[Servico - Suprimentos]], [[Servico - Contas a Pagar › Dúvida de Usuário - CAP]], [[Servico - Contas a Pagar › Ajustes]], [[Servico - Societário › Ajustes]], [[Servico - TI › Sistemas e Portais]], [[Servico - RH › Dúvidas]], [[Servico - RH › Ajustes]], [[Servico - Suprimentos › Dúvidas]], [[Servico - Controladoria]], [[Servico - Controladoria › Rodopar]], [[Servico - Controladoria › Dúvidas]], [[Servico - Societário › Dúvidas e Orientações]], [[Servico - Societário › Dúvidas e Orientações › Lançamentos - Documentos]], [[Servico - TI › Sistemas e Portais › Rodopar]], [[Servico - TI › Sistemas e Portais › Rodopar › Falha Sistema Rodopar]], [[Servico - RH › Folha]], [[Servico - Suprimentos › Ajustes › Correção de Lançamentos]], [[Servico - Suprimentos › Ajustes]], [[Servico - Suporte Operações › Dúvidas › Lançamentos - Documentos]], [[Servico - Suporte Operações]], [[Servico - Suporte Operações › Dúvidas]], [[Servico - Controladoria › Rodopar › Solicitação de Melhoria]], [[Servico - Controladoria › Rodopar › Ajuste de Relatório]], [[Servico - Controladoria › Rodopar › Cadastro de Usuário]], [[Servico - Controladoria › Dúvidas › Parâmetros Financeiros]], [[Servico - Controladoria › Ajustes › Correção de Lançamentos]], [[Servico - Controladoria › Ajustes]]
