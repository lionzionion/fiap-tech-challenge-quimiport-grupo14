# 04 — Regras de negócio (RB01–RB12)

Regras extraídas dos exemplos **esperados** nas pp. 7–8 do enunciado; códigos e localização futura são propostas do grupo.

| ID | Regra | Camada futura | Evidência de teste planejado |
|---|---|---|---|
| RB01 | Não registrar carga sem produto associado | Aplicação/agregado | Produto ausente recusado |
| RB02 | Não registrar carga com produto inativo | Caso de uso registro | Inativo recusado |
| RB03 | Não registrar carga sem classificação de risco | VO/agregado | Risco vazio recusado |
| RB04 | Não liberar carga sem documentação obrigatória | Domínio/política | Documento pendente bloqueia |
| RB05 | Carga bloqueada não pode ser movimentada | Domínio | Movimentação recusada |
| RB06 | Carga cancelada não pode ser liberada | Domínio/status | Liberação recusada |
| RB07 | Carga em inspeção não finaliza antes de liberação | Domínio/status | Finalização recusada |
| RB08 | Produto deve ter nome | Entidade produto | Nome vazio recusado |
| RB09 | Produto deve ter classe de risco | Entidade/VO | Risco ausente recusado |
| RB10 | Produto inativo não entra em novas cargas | Caso de uso registro | Rejeição do vínculo |
| RB11 | Quantidade da carga maior que zero | VO quantidade | 0/negativo recusados |
| RB12 | Toda carga deve informar responsável técnico | Agregado/aplicação | Responsável vazio recusado |

**Regra de integridade geral:** erro de validação não pode produzir liberação, mudança parcial de status ou histórico falso. A classificação e documentação específicas de cargas perigosas reais dependerão de requisitos técnicos e legais validados em trabalho futuro.
