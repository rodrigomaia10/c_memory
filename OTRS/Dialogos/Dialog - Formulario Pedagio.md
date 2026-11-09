---
tipo: otrs-dialog
tags: [otrs, otrs/dialog]
atualizado: 2026-10-23
fonte: snapshot do repo otrs (ZZZProcessManagement.pm / ZZZACL.pm)
entity: ActivityDialog-1706111e7d5f598897f915110342d1f0
---

# Dialog - Formulario Pedagio

**Formulario Pedagio** · interface AgentInterface, CustomerInterface · permissão `rw` · botão "Criar Chamado"

Hub: [[Hub - OTRS Processos]] · [[Hub - OTRS]]

> Formulario Pedagio

## Usado em processos
- [[Processo - Chamado Pedágio]] (Active)

## Campos (Display: 0 oculto · 1 mostra · 2 obrigatório)
- `CustomerID` — Display 2
- [[DF - Placa]] — Display 2
- [[DF - CteDB]] — Display 2
- [[DF - CteFilial]] — Display 1
- [[DF - CteFilialNome]] — Display 1
- [[DF - CteNumero]] — Display 1
- [[DF - CteSerie]] — Display 1
- [[DF - CtePlaca]] — Display 1
- [[DF - CteCnpjPagador]] — Display 1
- [[DF - CteNomePagador]] — Display 1
- [[DF - CteDataEmissao]] — Display 1
- [[DF - ManifestoNumero]] — Display 1
- [[DF - ManifestoData]] — Display 1
- `Article` — Display 2
- [[DF - CteClienteTipoNestle]] — Display 1

## ACLs que miram este diálogo
- [[ACL - 2- Mostra Campos Chamado]]
