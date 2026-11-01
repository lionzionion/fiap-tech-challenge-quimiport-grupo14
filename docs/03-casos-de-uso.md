# 03 — Casos de uso planejados

**Base:** exemplos do enunciado pp. 6–7. Objetivo, ator, entrada, saída, regras e erros são descritos por caso.

| ID | Objetivo | Ator proposto | Entrada | Saída | Regras | Erros possíveis |
|---|---|---|---|---|---|---|
| UC01 | Cadastrar produto | Administrador | nome, risco | produto com ID | RB08–09 | nome/risco ausente, duplicado |
| UC02 | Inativar produto | Administrador | produtoId | produto inativo | RB10 | produto inexistente |
| UC03 | Registrar carga | Operador | produtoId, quantidade, risco, responsavelId | carga registrada | RB01–03,10–12 | produto inativo, quantidade inválida |
| UC04 | Validar documentos | Analista documental | cargaId, documentos | situação documental | RB04 | ausente/inválido |
| UC05 | Solicitar inspeção | Operador/qualidade | cargaId, motivo | inspeção registrada | RB07 | carga em estado incompatível |
| UC06 | Liberar carga | Técnico/gestor | cargaId, decisão | liberação/histórico | RB04,06–07 | documentos faltantes, cancelada |
| UC07 | Bloquear carga | Técnico/gestor | cargaId, motivo | bloqueio/histórico | RB05 | estado incompatível |
| UC08 | Atualizar status | Operador | cargaId, destino | novo estado | RB05–07 | transição inválida |
| UC09 | Cancelar carga | Gestor | cargaId, justificativa | cancelamento | RB06 | transição impossível |
| UC10 | Consultar por status | Operador/gestor | filtros/status | lista de cargas | visibilidade futura | filtro inválido |
| UC11 | Consultar histórico | Gestor/qualidade | cargaId | eventos da carga | rastreabilidade | não encontrada |

**UC06, fluxo detalhado:** confirmar carga válida → verificar documentação obrigatória → verificar inspeção e estado → registrar decisão de liberação e histórico → devolver resultado. Se houver documento pendente, bloqueio, cancelamento ou inspeção pendente, **não mudar o estado**; retornar erro de domínio. Atores e contratos são propostas a validar em reunião.
