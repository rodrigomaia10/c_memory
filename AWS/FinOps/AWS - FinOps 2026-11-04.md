---
tipo: aws-finops
tags: [aws, custo, finops]
data: 2026-11-04
---
# AWS - FinOps 2026-11-04

Hub: [[Hub - AWS Operação]] · [[AWS - Achados]]

- Custo 30d: US$ 4419 (anterior US$ 4418)
- Economia potencial identificada: **US$ 992/mes** em 34 achados
- Relatorio completo: `C:\project\aws-finops\reports\2026-11-04.html`

## Top oportunidades
- **Snapshots** - 36 snapshots >90d (4103 GB, sa-east-1) - ~US$ 279/mes (baixa)
- **NAT** - NAT Gateway custa US$ 413/30d - ~US$ 124/mes (baixa)
- **Rightsizing** - srv-prod-wazuh (c4.xlarge) CPU media 1.1% / pico 7% em 14d - ~US$ 113/mes (media)
- **EBS solto** - vol-0597146d8ecbd20e3 400 GB gp3 (sa-east-1) sem uso desde 2025-02-12 - ~US$ 61/mes (alta)
- **Parada** - VM-Backup-Rodopar (sa-east-1) parada, EBS 440 GB - ~US$ 54/mes (alta)
- **Rightsizing** - srv-prod-databases (t3.large) CPU media 1.2% / pico 21% em 14d - ~US$ 49/mes (media)
- **HML 24x7** - srv-hm-portalccs (t3.medium) HML/teste ligada 24x7 - ~US$ 32/mes (media)
- **Parada** - Srv_AD02 (sa-east-1) parada, EBS 205 GB - ~US$ 31/mes (alta)
- **EBS gp2** - 9 volumes gp2 -> gp3 - ~US$ 27/mes (alta)
- **Rotina com falha** - Glue 'bronze_to_silver' falhou 80/167 execucoes (~US$ 47) - ~US$ 22/mes (media)
- **S3** - cootravale-infrabi-logs 1325 GB Standard sem lifecycle - ~US$ 21/mes (media)
- **EBS solto** - vol-0a067d450728b71af 250 GB gp3 (us-east-1) sem uso desde 2023-08-17 - ~US$ 20/mes (alta)
- **EBS solto** - vol-0d497372c756631d5 100 GB gp2 (sa-east-1) sem uso desde 2023-04-13 - ~US$ 19/mes (alta)
- **EIP** - 5 Elastic IPs sem associacao - ~US$ 18/mes (alta)
- **HML 24x7** - stage-apps (t4g.medium) HML/teste ligada 24x7 - ~US$ 16/mes (media)
