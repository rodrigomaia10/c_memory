---
tipo: otrs-dialog
tags: [otrs, otrs/dialog]
atualizado: 2026-10-23
fonte: snapshot do repo otrs (ZZZProcessManagement.pm / ZZZACL.pm)
entity: ActivityDialog-189c08089f5763a841a9942228fafdf3
---

# Dialog - Formulario Deslocamento

**Formulario Deslocamento** · interface AgentInterface, CustomerInterface · permissão `rw` · botão "Criar Chamado"

Hub: [[Hub - OTRS Processos]] · [[Hub - OTRS]]

> Formulario Deslocamento

## Usado em processos
- [[Processo - Chamado de Deslocamento]] (Active)

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
- [[DF - CteOcorrencia]] — Display 1
- [[DF - CteNotaDebitoMarfrig]] — Display 1
- [[DF - CteNumeroRegistroBRF]] — Display 1
- [[DF - CteCETBRF]] — Display 1
- [[DF - CteSenhaBRF]] — Display 1
- `Article` — Display 2
- [[DF - CteClienteTipoNestle]] — Display 1

## ACLs que miram este diálogo
- [[ACL - 1- Esconde Nota Débito MARFRIG DIÁRIA AO DESCARREGAR]]
- [[ACL - 1- Esconde Numero Registro BRF  DIÁRIA AO DESCARREGAR]]
- [[ACL - 1- EscondeCteSenhaBRF Deslocamento]]
- [[ACL - 2- Mostra Campos Chamado]]
- [[ACL - 2- Mostra CteSenhaBRF Processo - DESLOCAMENTO]]
- [[ACL - 2- Mostra NotaDébito Marfrig Processo - DIÁRIA AO DESCARREGAR]]
- [[ACL - 2- Mostra Numero Registro BRF Processo - DIÁRIA AO DESCARREGAR]]
