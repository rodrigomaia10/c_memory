---
tipo: otrs-dialog
tags: [otrs, otrs/dialog]
atualizado: 2026-10-23
fonte: snapshot do repo otrs (ZZZProcessManagement.pm / ZZZACL.pm)
entity: ActivityDialog-03bf516d8db4f8202abee65a8f24c5ac
---

# Dialog - Formulário Anulação

**Formulário Anulação** · interface AgentInterface, CustomerInterface · permissão `rw` · botão "Criar Chamado"

Hub: [[Hub - OTRS Processos]] · [[Hub - OTRS]]

> Formulário Anulação

## Usado em processos
- [[Processo - Chamado Anulação - Inativo]] (Inactive)
- [[Processo - Chamado Divergência Valor de Frete]] (Active)

## Campos (Display: 0 oculto · 1 mostra · 2 obrigatório)
- [[DF - TabelaAnulacao]] — Display 1
- [[DF - CteNomePagador]] — Display 1
- [[DF - TipoDocumento]] — Display 1
- [[DF - Filial]] — Display 1
- [[DF - CteSerie]] — Display 1
- [[DF - NumeroDocumento]] — Display 1
- [[DF - UnidadeNegocio]] — Display 1
- [[DF - ValorReceber]] — Display 1
- [[DF - CteDataEmissao]] — Display 1
- `CustomerID` — Display 2
- `Article` — Display 1

## ACLs que miram este diálogo
- nenhuma direta
