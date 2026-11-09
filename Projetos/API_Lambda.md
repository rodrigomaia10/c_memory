---
tipo: projeto
caminho: C:\project\API_Lambda
dominio: dados
tags: [projeto, dominio/dados]
criado: 2026-10-19
atualizado: 2026-10-19
---
# API_Lambda

Lambdas AWS expostas como API. Primeira: `API_OTRS` (us-east-1), consulta Athena por placa para o OTRS.

Hub: [[Hub - Dados e DW]] · Raiz: [[Cootravale]]

## Relacionados
- [[otrs]] — consumidor da API (formulários/portal OTRS)
- [[datalake-glue]] — origem das tabelas Athena (silver_kmn)
- [[Lambda - API_OTRS (us-east-1)]] · [[AWS - Lambdas (índice)]] — nó AWS da função

## Memória do projeto (Claude)
Pasta: `C:/Users/rodrigo.maia/.claude/projects/C--project-API-Lambda/memory`
- `project_api_otrs_lambda.md` — diagnóstico, tabelas e pendências da API_OTRS
- `reference_aws_cli_config_invalida.md` — config AWS inválida, regiões dos catálogos

## Decisões e planos
- API_OTRS: handler errado, código template, role sem Athena, timeout 3s, URL AWS_IAM. Query: `silver_kmn.veiculo_veiculo` → `agreg_termo_veiculo` → `agreg_termo` (us-east-1, workgroup `cootravale-s3-athena`). Código em `lambda_function.py`, não implantado. Pendente: método de autenticação do OTRS e placa de teste.

## Log de sessões
- 2026-10-19 — Diagnosticada a API_OTRS via CLI/Chrome, mapeadas as tabelas e escrito o código local; aguardando autorização para alterar a AWS.
- 2026-10-19 — Escrita a policy IAM mínima (policy_api_otrs.json); usuário cria/anexa na AWS. Pendente: autenticação do OTRS, placa de teste, ajustar handler/timeout.
- 2026-10-19 — Decidido: auth por header x-api-key (env var API_KEY) com Function URL NONE; policy anexada; usuário configura no console passo a passo (restam handler/timeout, código, env var, URL, teste).
- 2026-10-19 — Passos 1-3 concluídos e verificados (policy, handler/timeout/memória, código publicado). Faltam env var API_KEY, Function URL NONE e teste curl.
- 2026-10-19 — Env var API_KEY e Function URL NONE feitos; curl confirmou 401 sem chave; chave salva com "." extra sendo corrigida. Falta teste com placa real.
- 2026-10-19 — API testada OK (HTTP 200). Usuário migrando policy/query para prd_bronze + prd_gold.dim_cooperado; faltava liberar bucket bronze-us na policy. Pendente definir campos de saída.
- 2026-10-19 — lambda_function.py agora responde {response, placa, values[]} (antes resultados) p/ o campo Webservice do OTRS; pendente publicar na Lambda. Ver [[otrs]].
- 2026-10-19 — Lambda API_OTRS publicada pelo usuário com resposta {response, placa, values[]}; validada pelo OTRS (DF Webservice) com IUO2G67.
