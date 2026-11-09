---
tipo: otrs-dialog
tags: [otrs, otrs/dialog]
atualizado: 2026-10-23
fonte: snapshot do repo otrs (ZZZProcessManagement.pm / ZZZACL.pm)
entity: ActivityDialog-380e90623264f051b87cf8a72e538865
---

# Dialog - Formulario Recibo de Descarga

**Formulario Recibo de Descarga** · interface AgentInterface, CustomerInterface · permissão `rw` · botão "Criar Chamado"

Hub: [[Hub - OTRS Processos]] · [[Hub - OTRS]]

> Formulario Recibo de Descarga

## Usado em processos
- [[Processo - Chamado Recibo de Descarga]] (Active)

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
- [[DF - CteSenhaMarfrig]] — Display 1
- `Article` — Display 2
- [[DF - CteDACTENestle]] — Display 1
- [[DF - CteAnexoReciboDescarga]] — Display 1
- [[DF - AnexoComprovanteEntrega]] — Display 1
- [[DF - CteClienteTipoNestle]] — Display 1
- [[DF - ViagemSeara]] — Display 1

## ACLs que miram este diálogo
- [[ACL - 1- Esconde Anexo Recibo Descarga]]
- [[ACL - 1- Esconde Nota Débito MARFRIG DIÁRIA AO DESCARREGAR]]
- [[ACL - 1- Esconde Senha Marfrig HelpDeskTransportador]]
- [[ACL - 2 - Mostra Anexo Comprovante de Entrega - Recibo de Descarga]]
- [[ACL - 2- Mostra Anexo Recibo de Descarga]]
- [[ACL - 2- Mostra Anexo Recibo de Descarga(copiar)1]]
- [[ACL - 2- Mostra Campos Chamado]]
- [[ACL - 2- Mostra NotaDébito Marfrig Processo - DIÁRIA AO DESCARREGAR]]
- [[ACL - 2- Mostra Senha Marfrig Processo - Recibo de Descarga nao obrigatorio]]
