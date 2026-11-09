---
tipo: aws-finops
tags: [aws, custo, finops]
data: 2026-10-22
---
# AWS - FinOps 2026-10-22

Hub: [[Hub - AWS Operação]] · [[AWS - Achados]]

- Custo 30d: US$ 1492 (anterior US$ 1552)
- Economia potencial identificada: **US$ 838/mes** em 33 achados
- Relatorio completo: `C:\project\aws-finops\reports\2026-10-22.html`

## Top oportunidades
- **Snapshots** - 33 snapshots >90d (3603 GB, sa-east-1) - ~US$ 245/mes (baixa)
- **Rightsizing** - srv-prod-wazuh (c4.xlarge) CPU media 1.1% / pico 7% em 14d - ~US$ 113/mes (media)
- **EBS solto** - vol-0597146d8ecbd20e3 400 GB gp3 (sa-east-1) sem uso desde 2025-02-12 - ~US$ 61/mes (alta)
- **Parada** - VM-Backup-Rodopar (sa-east-1) parada, EBS 440 GB - ~US$ 54/mes (alta)
- **Rightsizing** - srv-prod-databases (t3.large) CPU media 1.2% / pico 22% em 14d - ~US$ 49/mes (media)
- **NAT** - NAT Gateway custa US$ 124/30d - ~US$ 37/mes (baixa)
- **HML 24x7** - srv-hm-portalccs (t3.medium) HML/teste ligada 24x7 - ~US$ 32/mes (media)
- **Parada** - Srv_AD02 (sa-east-1) parada, EBS 205 GB - ~US$ 31/mes (alta)
- **EBS gp2** - 9 volumes gp2 -> gp3 - ~US$ 27/mes (alta)
- **S3** - cootravale-infrabi-logs 1325 GB Standard sem lifecycle - ~US$ 21/mes (media)
- **EBS solto** - vol-0a067d450728b71af 250 GB gp3 (us-east-1) sem uso desde 2023-08-17 - ~US$ 20/mes (alta)
- **EBS solto** - vol-0d497372c756631d5 100 GB gp2 (sa-east-1) sem uso desde 2023-04-13 - ~US$ 19/mes (alta)
- **EIP** - 5 Elastic IPs sem associacao - ~US$ 18/mes (alta)
- **HML 24x7** - stage-apps (t4g.medium) HML/teste ligada 24x7 - ~US$ 16/mes (media)
- **EBS solto** - vol-084c8f58a821af340 100 GB gp3 (sa-east-1) sem uso desde 2026-03-17 - ~US$ 15/mes (alta)
