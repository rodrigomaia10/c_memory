---
tipo: otrs-dialog
tags: [otrs, otrs/dialog]
atualizado: 2026-10-23
fonte: snapshot do repo otrs (ZZZProcessManagement.pm / ZZZACL.pm)
entity: ActivityDialog-dc48d1afd0dbd7e535dcd41b26d3a29e
---

# Dialog - Formulario Divergencia Valor de Frete

**Formulario Divergencia Valor de Frete** · interface AgentInterface, CustomerInterface · permissão `rw` · botão "Criar Chamado"

Hub: [[Hub - OTRS Processos]] · [[Hub - OTRS]]

> Formulario Divergencia Valor de Frete

## Usado em processos
- [[Processo - Chamado Divergência Valor de Frete]] (Active)

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
- [[DF - PagoTransportador]] — Display 1
- [[DF - CteValor]] — Display 1
- `Article` — Display 2
- [[DF - CteAnexoPosicaoRastreador]] — Display 1
- [[DF - ViagemSeara]] — Display 1
- [[DF - CteClienteTipoNestle]] — Display 1

## ACLs que miram este diálogo
- [[ACL - 2- Mostra Campos Chamado]]
