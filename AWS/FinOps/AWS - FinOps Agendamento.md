---
tipo: aws-rotina
tags: [aws, finops, agendamento, rotina]
atualizado: 2026-10-22
---
# AWS - FinOps Agendamento

Hub: [[Hub - AWS Operação]] · Projeto: [[aws-finops]] · Achados: [[AWS - Achados]]

Como a rotina semanal de custo da AWS é disparada e o que ela faz de ponta a ponta.

## Quando roda
- **Segunda-feira às 09:00** (horário local), no **Agendador de Tarefas do Windows**.
- Tarefa: `\AWS FinOps Semanal`. Executa `C:\project\aws-finops\run_semanal.bat`, que chama `python finops_semanal.py` e grava o log em `reports\ultima_execucao.log`.
- Roda como o usuário `rodrigo.maia`, **só com a sessão do Windows aberta** (logon interativo).
- O PC fica desligado sábado e domingo. A opção **StartWhenAvailable** está ligada: se o PC estiver desligado às 09:00, a tarefa roda assim que ele ligar. Funciona também na bateria.
- Ver ou editar: `taskschd.msc` (Biblioteca do Agendador de Tarefas, raiz) ou `schtasks /Query /TN "AWS FinOps Semanal"`.
- Não há job no Claude Code: o cron do Claude é só da sessão e expira em 7 dias, por isso foi removido.

## O que acontece em cada execução
1. Autentica na conta `152774997921` pelo perfil `userprod` do AWS CLI. Sempre com `--output json`, porque o config do usuário tem `output=parquet`.
2. **Custo:** Cost Explorer, últimos 30 dias contra os 30 anteriores, por serviço, mais o detalhe do "EC2 - Other".
3. **EC2** (sa-east-1 e us-east-1): estado, tipo, preço on-demand (Pricing API, com cache), CPU média e pico de 14 dias, disco, falta de tags.
4. **HML/teste:** instâncias e jobs com nome hml, hm, homolog, stage, stg, teste, test, dev, sandbox, old ou poc (com limite de palavra, para não casar `postgresql` nem `gold`).
5. **Armazenamento:** EBS solto, migração gp2 para gp3, snapshots com mais de 90 dias, IPs elásticos sem associação, NAT Gateway.
6. **Glue:** execuções, falhas e DPU-horas de 30 dias por job; o custo é calibrado com o valor real da fatura do Glue.
7. **Logs e S3:** log groups acima de 100 MB e sua retenção; buckets por tamanho e presença de lifecycle; ALBs com todos os target groups vazios.
8. Calcula os **achados** (categoria, ação, economia estimada por mês, confiança) e compara com a execução anterior.

## Saídas
- `C:\project\aws-finops\reports\AAAA-MM-DD.html` (relatório completo) e `.json` (dados; base do comparativo semanal).
- Nota resumida no vault: `AWS/FinOps/AWS - FinOps AAAA-MM-DD.md`.
- Duração: cerca de 8 minutos na primeira execução (varredura do S3 pesa); as seguintes aproveitam o cache de preços em `price_cache.json`.

## O que NÃO é automático
- **Dashboard do time** (https://claude.ai/artifact/Kjve4WkXSi8N39a6ao2hbd): não se atualiza sozinho. Depois da execução, pedir ao Claude "atualiza o dashboard". Ele roda `exporta_artefato.py`, envia os 7 JSON e atualiza os datasets.
- Ações de redução (desligar, apagar, redimensionar): o script só lê, nada é alterado na AWS.

## Limites conhecidos
- Memória das EC2 não é medida (sem CloudWatch Agent): o rightsizing usa só CPU.
- Agendas do Airflow não são lidas; rotinas diárias são inferidas pelo histórico do Glue.
- Savings Plans (~US$ 360 por 30 dias) cobre compute: desligar EC2 coberta só baixa a fatura acima do compromisso.
- Se o PC ficar desligado a semana toda, a execução fica pendente até ligar.

## Como mexer
- Mudar horário ou dia: `schtasks /Create /TN "AWS FinOps Semanal" /TR "C:\project\aws-finops\run_semanal.bat" /SC WEEKLY /D MON /ST 09:00 /F`.
- Rodar na hora: `schtasks /Run /TN "AWS FinOps Semanal"` ou `python C:\project\aws-finops\finops_semanal.py`.
- Verificar falha: ler `reports\ultima_execucao.log`.
