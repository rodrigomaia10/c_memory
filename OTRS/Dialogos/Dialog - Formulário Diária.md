---
tipo: otrs-dialog
tags: [otrs, otrs/dialog]
atualizado: 2026-10-23
fonte: snapshot do repo otrs (ZZZProcessManagement.pm / ZZZACL.pm)
entity: ActivityDialog-b3ab90b93dfe94a87d5bfdeffc3cec0c
---

# Dialog - Formulário Diária

**Formulário Diária** · interface AgentInterface, CustomerInterface · permissão `rw` · botão "Criar Chamado"

Hub: [[Hub - OTRS Processos]] · [[Hub - OTRS]]

> Formulário Diária

## Usado em processos
- [[Processo - Chamado Diária ao Descarregar]] (Active)
- [[Processo - Chamado Diária na Devolução]] (Active)

## Campos (Display: 0 oculto · 1 mostra · 2 obrigatório)
- `CustomerID` — Display 2
- [[DF - Placa]] — Display 2
- [[DF - CteDB]] — Display 2
- [[DF - CteOcorrencia]] — Display 1
- [[DF - CteDACTECarimbadoAssinado]] — Display 1
- [[DF - CteAnexoPosicaoRastreador]] — Display 1
- [[DF - CteFilial]] — Display 3
- [[DF - CteFilialNome]] — Display 3
- [[DF - CteNumero]] — Display 1
- [[DF - CteSerie]] — Display 1
- [[DF - CtePlaca]] — Display 3
- [[DF - CteCnpjPagador]] — Display 1
- [[DF - CteNomePagador]] — Display 1
- [[DF - CteDataEmissao]] — Display 1
- [[DF - ManifestoNumero]] — Display 1
- [[DF - CteValor]] — Display 1
- [[DF - CteNumeroRegistroBRF]] — Display 1
- [[DF - CteCETBRF]] — Display 1
- [[DF - CteSenhaMarfrig]] — Display 1
- [[DF - CteDACTENestle]] — Display 1
- [[DF - CteAnexoCETBRF]] — Display 1
- [[DF - CteClienteTipoNestle]] — Display 1
- [[DF - ViagemSeara]] — Display 1
- `Article` — Display 2

## ACLs que miram este diálogo
- [[ACL - 1- Esconde Anexo Posicao Rastreador HelpDeskTransportador]]
- [[ACL - 1- Esconde CET BRF HelpDeskTransportador]]
- [[ACL - 1- Esconde Numero Registro BRF HelpDeskTransportador]]
- [[ACL - 1- Esconde Senha Marfrig HelpDeskTransportador]]
- [[ACL - 2- Mostra Anexo Posicao Rastreador Processo - DIÁRIA AO DESCARREGAR]]
- [[ACL - 2- Mostra Campos Chamado]]
- [[ACL - 2- Mostra Numero Registro BRF Processo - DIÁRIA AO DESCARREGAR]]
- [[ACL - 2- Mostra Senha Marfrig Processos - DIÁRIA]]
