---
tipo: otrs-dialog
tags: [otrs, otrs/dialog]
atualizado: 2026-10-23
fonte: snapshot do repo otrs (ZZZProcessManagement.pm / ZZZACL.pm)
entity: ActivityDialog-b63401ae0715ef538233f7be338af8b7
---

# Dialog - Formulario Diária Troca de Nota

**Formulario Diária Troca de Nota** · interface AgentInterface, CustomerInterface · permissão `rw` · botão "Criar Chamado"

Hub: [[Hub - OTRS Processos]] · [[Hub - OTRS]]

> Formulario Diária Troca de Nota

## Usado em processos
- [[Processo - Chamado Diária Troca de Nota]] (Active)

## Campos (Display: 0 oculto · 1 mostra · 2 obrigatório)
- `CustomerID` — Display 2
- [[DF - CteOcorrencia]] — Display 2
- [[DF - Placa]] — Display 2
- [[DF - CteDB]] — Display 2
- [[DF - NotaFiscalTroca]] — Display 2
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
- [[DF - CteSenhaMarfrig]] — Display 1
- [[DF - CteCETBRF]] — Display 1
- [[DF - CteAnexoPosicaoRastreador]] — Display 1
- [[DF - CteDACTECarimbadoAssinado]] — Display 1
- [[DF - CteAnexoCETBRF]] — Display 1
- [[DF - CteClienteTipoNestle]] — Display 1
- [[DF - ViagemSeara]] — Display 1
- `Article` — Display 2

## ACLs que miram este diálogo
- [[ACL - 1- Esconde CET BRF HelpDeskTransportador]]
- [[ACL - 2- Mostra Campos Chamado]]
- [[ACL - 2- Mostra Senha Marfrig Processos - DIÁRIA]]
