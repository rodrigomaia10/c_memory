---
tipo: aws-iam
tags: [aws, aws/iam]
atualizado: 2026-10-22
fonte: aws-cli (conta 152774997921)
---
# AWS - IAM (roles)

Hub: [[Hub - AWS]]

## Vínculos principais
- `GlueAthenaToMySQLRole` → jobs Glue Portal_*, Envio*, carga_* ([[AWS - Glue Jobs]])
- `GlueJobBronzeSilverCatalog` → jobs do pipeline medalhão ([[datalake-glue]])
- `CloudDog-SSO-LambdaExecutionRole-*` → Lambdas de ingestão **legadas/inativas** ([[AWS - Lambdas (índice)]])
- `API_OTRS-role-*` (5, só `wikqb9wy` em uso) → [[Lambda - API_OTRS (us-east-1)]]
- `EC2AirflowProdRole` → [[EC2 - srv-prod-airflow]] · `EC2CootravaleJobsRole` → [[EC2 - srv-prod-cootravalejobs]] · `profile-S3-EC2`/`role-S3-EC2` → bitbucketrunner e spark-server_old
- `AmazonSSMRoleForInstancesQuickSetup` → maioria das EC2 sa-east-1 (SSM)
- `ec2-stage-apps`, `stage-apps-deployer`, `ec2-postgres-banco` → stage us-east-1
- `TDSynnex-*`, `tdsynnex-*` → acesso do parceiro TD Synnex (CloudDog/FinOps)
- `GrafanaRole`, `grafana-cloudwatch-readonly` → Grafana lê CloudWatch
- `AWSServiceRoleForAmazonMWAA`, `AmazonMWAA-airflow-prod-*`, `AmazonEMR-*`, `AmazonAppStream*` → serviços antigos (sem ambiente ativo hoje)

Total de roles: 76. Usuário CLI: `rodrigo.maia@cootravale.com.br` (perfis `default`/`userprod`) e `leverpro`.
