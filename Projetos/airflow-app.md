---
tipo: projeto
caminho: C:\project\airflow-app
dominio: dados
tags: [projeto, dominio/dados]
criado: 2026-10-28
atualizado: 2026-10-28
---
# airflow-app

Pasta de trabalho (vazia de código) usada para diagnosticar o Airflow de produção via Chrome (https://airflow-prod.cootravale.com.br).

Hub: [[Hub - Dados e DW]] · Raiz: [[Cootravale]]

## Relacionados
- [[airflow-prod-dags]] — DAGs de produção que rodam nesse Airflow (EC2 srv-prod-airflow)
- [[datalake-glue]] — jobs Glue disparados pela DAG `prd_carga_diaria_split_fluxo_datalake`
- Histórico completo: [[airflow-app - arquivo]]

## Estado atual
- 2026-10-28: scheduler do Airflow prod unhealthy; run manual de `prd_carga_diaria_split_fluxo_datalake` presa em queued; runs agendados faltando desde 27/10 04:00 UTC.
- Pendente: infra reiniciar o scheduler (e ler o log para a causa raiz); depois backfill dos runs perdidos (27/10 14:00 e 19:00 UTC, 28/10) se necessário.
- Não foi alterado nada no Airflow (só leitura).
- Regra fixa: toda parada no Airflow → avisar o CRC (envia e-mail a colaboradores e cooperados).
- Usuário está sem acesso ao servidor; plano: Reboot da EC2 (ou SSM Session Manager para reiniciar só o scheduler). Verificar antes que o Airflow sobe no boot.

## Índice de tópicos
- Scheduler parado / DAG não executa → skill `airflow-dag-nao-executa` + Decisões e planos (2026-10-28)
- Comunicação de paradas → CRC (Decisões e planos)

## Memória do projeto (Claude)
- airflow-prod-scheduler-parado-2026-10-28.md
- airflow-parada-avisar-crc.md
- Skill de projeto: `.claude/skills/airflow-dag-nao-executa`

## Decisões e planos
- Run queued + sem logs + gap nos runs agendados = olhar a Saúde (Agendador) na home antes do código da DAG.
- Toda parada no Airflow exige avisar o CRC, que notifica colaboradores e cooperados por e-mail (skill `airflow-dag-nao-executa`).

## Log de sessões
- 2026-10-28 — Diagnóstico via Chrome: scheduler unhealthy explica run manual queued; recomendado reiniciar scheduler + backfill.
- 2026-10-28 — Usuário sem acesso ao server; orientado a usar Reboot (não Stop/Start) ou SSM; checar Agendador verde depois.
- 2026-10-28 — Regra: parada no Airflow → avisar o CRC (e-mail a colaboradores e cooperados).
