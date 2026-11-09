---
tipo: otrs-dialog
tags: [otrs, otrs/dialog]
atualizado: 2026-10-23
fonte: snapshot do repo otrs (ZZZProcessManagement.pm / ZZZACL.pm)
entity: ActivityDialog-31530c3cd24925fb400dc24f9fc9248d
---

# Dialog - Formulário Frete Devolução

**Formulário Frete Devolução** · interface AgentInterface, CustomerInterface · permissão `rw` · botão "Criar Chamado"

Hub: [[Hub - OTRS Processos]] · [[Hub - OTRS]]

> Formulário Frete Devolução

## Usado em processos
- [[Processo - Chamado Diária na Devolução]] (Active)
- [[Processo - Chamado Frete Devolução]] (Active)
- [[Processo - Chamado Reembolso de Imposto Fiscal]] (Active)
- [[Processo - Reembolso Circuitos]] (Inactive)

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
- [[DF - PagoTransportador]] — Display 1
- [[DF - CteValor]] — Display 1
- [[DF - ManifestoData]] — Display 1
- [[DF - CteOcorrencia]] — Display 1
- `Article` — Display 1
- [[DF - AnexoCTENF]] — Display 2
- [[DF - CteDACTECarimbadoAssinado]] — Display 1
- [[DF - CteClienteTipoNestle]] — Display 1

## ACLs que miram este diálogo
- [[ACL - 2- Mostra Campos Chamado]]
