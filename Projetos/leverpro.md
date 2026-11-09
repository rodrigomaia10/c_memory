---
tipo: projeto
caminho: C:\project\leverpro
dominio: dados
tags: [projeto, dominio/dados]
criado: 2026-11-05
atualizado: 2026-11-05
---
# leverpro
Projeto com acesso AWS restrito via política IAM "lever pro" (Athena/Glue/S3, somente 2 tabelas).
Hub: [[Hub - Dados e DW]] · Raiz: [[Cootravale]]

## Relacionados
- [[Hub - AWS IAM e Acesso]] — a política "lever pro" é um acesso IAM restrito.
- [[Hub - AWS Athena e SageMaker]] — consultas via Athena, workgroup `primary`.

## Estado atual
- Política IAM "lever pro" (conta 152774997921, us-east-1) com 2 tabelas liberadas.
- JSON completo com o bucket gold entregue ao usuário; falta ele aplicar no IAM e validar com `SELECT ... LIMIT 10`.
- Se der AccessDenied no gold: checar KMS (`kms:Decrypt`) e o `Location` real da tabela.

## Índice de tópicos
- Política AWS lever pro (escopo, como incluir tabela) → seção Decisões e planos + memory `aws-politica-lever-pro` (2026-11-05)

## Memória do projeto (Claude)
- `aws-politica-lever-pro.md`

## Decisões e planos
- Acesso mínimo: só `prd_bronze.kmm_listas_contab_lancamentos` e `prd_gold.ponte_lancamento_documento_carga`.
- Resultados Athena em `cootravale-layer-bronze-us/athena_query_results/*`; sem escrita no bucket gold.
- Nova tabela = ARN Glue (table) + prefixo S3 (GetObject e s3:prefix do ListBucket); outro bucket exige GetBucketLocation/ListBucket próprios.

## Log de sessões
- 2026-11-05 — Mapeada a política "lever pro" e incluída a tabela gold `ponte_lancamento_documento_carga` (database `prd_gold` confirmado).
