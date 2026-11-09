---
tipo: aws-monitoramento
tags: [aws, aws/cloudwatch]
atualizado: 2026-10-22
fonte: aws-cli (conta 152774997921)
---
# AWS - Monitoramento

Hub: [[Hub - AWS]] · [[Monitoramento_Gateway_job_cootravale]] · [[AWS - Glue Jobs]]

## EventBridge (us-east-1)
- Regra `cootravale-glue-falhas-prod` (ENABLED): Glue Job State Change FAILED/TIMEOUT/ERROR para 13 jobs de produção (Portal_*, RLS, Saldo_realizado, jdbc_to_bronze, bronze_to_silver, silver_to_gold, Envio*). Descrição: monitoramento ASODB/Grafana. Log group `/aws/events/cootravale-glue-falhas`.

## SNS (sa-east-1)
- `COOTRAVALE_CloudWatch_Alarms_Topic`, `CloudDog-Directory-Monitor`
- **Nenhum alarme CloudWatch configurado** (us-east-1 e sa-east-1).

## Log groups relevantes
| Região    | Log group                                 | Bytes   |
| --------- | ----------------------------------------- | ------- |
| us-east-1 | `/aws-glue/jobs/error`                    | 14.1 GB |
| us-east-1 | `airflow-airflow-prod-us-e-DAGProcessing` | 1.2 GB  |
| sa-east-1 | `VPNLOgs`                                 | 5.2 GB  |
| sa-east-1 | `aws-cloudtrail-logs-cootravale`          | 17.4 GB |

Log groups grandes sem retenção definida custam armazenamento: revisar (ver [[AWS - Achados]]).
