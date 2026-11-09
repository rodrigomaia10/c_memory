---
tipo: otrs-dialog
tags: [otrs, otrs/dialog]
atualizado: 2026-10-23
fonte: snapshot do repo otrs (ZZZProcessManagement.pm / ZZZACL.pm)
entity: ActivityDialog-2de93fb09d400f1d8d30efdc23d96d82
---

# Dialog - 1.1 Formulário Seguro de Vida

**1.1 Formulário Seguro de Vida** · interface AgentInterface, CustomerInterface · permissão `rw` · botão "Abrir Chamado"

Hub: [[Hub - OTRS Processos]] · [[Hub - OTRS]]

> 1.1 Formulário Seguro de Vida

## Usado em processos
- [[Processo - Chamado Seguro de Vida]] (Active)

## Campos (Display: 0 oculto · 1 mostra · 2 obrigatório)
- [[DF - NomeCooperado]] — Display 1
- [[DF - NomeAssegurado]] — Display 1
- [[DF - CPFAssegurado]] — Display 1
- [[DF - TipoAssegurado]] — Display 1
- [[DF - AnexoCnhAssegurado]] — Display 1
- `CustomerID` — Display 2
- `Article` — Display 1

## ACLs que miram este diálogo
- [[ACL - 11 - Esconde Campos Seguro de Vida]]
- [[ACL - 11 - Mostra Campos Seguro de Vida]]
