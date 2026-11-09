---
tipo: projeto
tags: [aws, custo, finops]
atualizado: 2026-11-04
---
# aws-finops

Hub: [[Hub - AWS Operação]] · [[AWS - Achados]] · [[AWS - FinOps Agendamento]]

## Estado atual
Script `C:\project\aws-finops\finops_semanal.py`, agendado no Windows (seg 09:00). Relatório HTML + nota em `AWS/FinOps/`. Primeira execução: custo 30d US$ 1.492, economia potencial ~US$ 838/mês (33 achados).

Atualização 2026-11-04: rodado manualmente, 34 achados, economia ~US$ 992/mês (período 05/10–04/11). Dashboard do time atualizado com esses dados. Execução agendada de 03/11 aparentemente interrompida (`^C` no `ultima_execucao.log`): investigar `run_semanal.bat` se repetir.

## Decisões e planos
- Dashboard do time (artefato Dashboard): https://claude.ai/artifact/Kjve4WkXSi8N39a6ao2hbd. Dados são arquivos JSON fixos gerados por `exporta_artefato.py`; atualização manual (pedir ao Claude toda semana). Privado até compartilhar pelo botão Share.
- Cobre custo, EC2 ociosa/HML 24x7, EBS/EIP/NAT/snapshots, Glue (rotinas e falhas), logs sem retenção, S3 sem lifecycle.
- Lacunas: memória das EC2 (sem CWAgent), agendas do Airflow, desconto de Savings Plans por instância.

- Atualização semanal do dashboard: sempre reusar o mesmo artefato, via skill de projeto `atualizar-dashboard` (`aws-finops/.claude/skills/`). Memory: `dashboard-time-atualizacao`.

- Bug corrigido em 2026-11-04 no `finops_semanal.py`: `coleta_custo.por()` lia só `ResultsByTime[0]`, então janelas de 30 dias que cruzam meses subcontavam (relatório de 22/10 mostrou US$ 1,5 mil; o real era ~US$ 5,7 mil/mês). Agora soma todos os períodos. Relatórios anteriores a essa data têm total errado.
- Novo `coleta_historico()` (6 meses por serviço, Cost Explorer) grava `historico` no relatório; `exporta_artefato.py` gera o dataset `meses`.
- Decisão do usuário: montar um dashboard NOVO de evolução mensal (https://claude.ai/artifact/5irFM4stoDxSZAC3HDauE6, em construção) em vez de alterar o antigo (Kjve4WkXSi8N39a6ao2hbd, que ficou com dados pré-correção).

- Painel novo "Custo AWS por mês" (https://claude.ai/artifact/5irFM4stoDxSZAC3HDauE6) preenchido em 2026-11-04 com datasets de arquivo `meses`, `resumo`, `oportunidades` (página com calcs mensal/kpis/series/comparativo). Verificação automática `check` ainda não apareceu (depende de alguém abrir a página). Números pós-correção: 30d US$ 5.027, economia US$ 1.010/mês, 34 achados.

## Log
- 2026-11-04: painel novo de evolução mensal preenchido e publicado; script rerodado com a correção.
- 2026-11-04: corrigido bug de custo, adicionado histórico mensal, criado artefato novo de evolução mensal (a preencher após o script terminar).
- 2026-11-04: dashboard do time atualizado (7 datasets, mesmo artefato); criada a skill `atualizar-dashboard`. Primeiro envio saiu com dados de 22/10 porque não havia relatório novo; rodado `finops_semanal.py` e reenviado.
- 2026-10-22: criado e executado pela primeira vez.
- 2026-10-22: dashboard do time publicado; verificação automática `check` ainda não apareceu.
- 2026-10-22: agendamento no Windows ajustado para segunda 09:00 com catch-up; cron do Claude removido.
