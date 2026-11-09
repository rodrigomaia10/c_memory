---
tipo: otrs-dialog
tags: [otrs, otrs/dialog]
atualizado: 2026-10-23
fonte: snapshot do repo otrs (ZZZProcessManagement.pm / ZZZACL.pm)
entity: ActivityDialog-c358079ebd217f3b6bac5359d59ac82f
---

# Dialog - Formulario Diária em Posto Fiscal

**Formulario Diária em Posto Fiscal** · interface AgentInterface, CustomerInterface · permissão `rw` · botão "Criar Chamado"

Hub: [[Hub - OTRS Processos]] · [[Hub - OTRS]]

> Formulario Diária em Posto Fiscal

## Usado em processos
- [[Processo - Chamado Diária em Posto Fiscal]] (Active)

## Campos (Display: 0 oculto · 1 mostra · 2 obrigatório)
- `CustomerID` — Display 2
- [[DF - Placa]] — Display 2
- [[DF - CteDB]] — Display 2
- [[DF - CteOcorrencia]] — Display 2
- [[DF - CTePDF]] — Display 1
- [[DF - CteAnexoPosicaoRastreador]] — Display 1
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
- [[DF - OC]] — Display 1
- [[DF - CteCETBRF]] — Display 1
- [[DF - CteDACTECarimbadoAssinado]] — Display 1
- [[DF - CteAnexoCETBRF]] — Display 1
- [[DF - CteClienteTipoNestle]] — Display 1
- [[DF - ViagemSeara]] — Display 1
- `Article` — Display 2

## ACLs que miram este diálogo
- [[ACL - 1- Esconde CET BRF HelpDeskTransportador]]
- [[ACL - 2- Mostra Campos Chamado]]
