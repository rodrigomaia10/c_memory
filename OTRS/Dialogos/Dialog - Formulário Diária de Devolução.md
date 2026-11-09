---
tipo: otrs-dialog
tags: [otrs, otrs/dialog]
atualizado: 2026-10-23
fonte: snapshot do repo otrs (ZZZProcessManagement.pm / ZZZACL.pm)
entity: ActivityDialog-3026fd1b4532278e9a23993204d82d5b
---

# Dialog - Formulário Diária de Devolução

**Formulário Diária de Devolução** · interface AgentInterface, CustomerInterface · permissão `rw` · botão "Criar Chamado"

Hub: [[Hub - OTRS Processos]] · [[Hub - OTRS]]

> Formulário Diária de Devolução

## Usado em processos
- [[Processo - Chamado Diária ao Descarregar]] (Active)
- [[Processo - Chamado Diária na Devolução]] (Active)
- [[Processo - Chamado para Cancelamentos LCD-Contrato-Extrato]] (Inactive)

## Campos (Display: 0 oculto · 1 mostra · 2 obrigatório)
- `CustomerID` — Display 2
- [[DF - Placa]] — Display 1
- [[DF - CteDB]] — Display 1
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
- [[DF - CteNumeroRegistroBRF]] — Display 1
- [[DF - CteCETBRF]] — Display 1
- [[DF - CteSenhaMarfrig]] — Display 1
- [[DF - CtedDataHoraChegada]] — Display 1
- [[DF - CteDataHoraSaida]] — Display 1
- `Article` — Display 2
- [[DF - CteAnexoPosicaoRastreador]] — Display 1
- [[DF - CteDACTECarimbadoAssinado]] — Display 1
- [[DF - CteAnexoCETBRF]] — Display 1
- [[DF - CteClienteTipoNestle]] — Display 1
- [[DF - ViagemSeara]] — Display 1

## ACLs que miram este diálogo
- nenhuma direta
