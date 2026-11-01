# 01 — Entendimento do domínio

**Base:** enunciado, pp. 2–4. **Status:** proposta de interpretação para revisão do grupo.

## Problema
O registro manual/descentralizado de cargas químicas prejudica consulta, rastreabilidade, acompanhamento de status, controle documental e verificação de condições para movimentação. O **QuimiPort** documentará a solução proposta nesse contexto portuário inspirado no Porto de Santos.

## Perfis e objetivos (exemplos do enunciado)
| Ator | Atuação proposta |
|---|---|
| Operador portuário | Registrar e acompanhar cargas |
| Responsável técnico | Acompanhar verificações e decisões técnicas |
| Analista de documentação | Conferir documentos exigidos |
| Analista de qualidade | Solicitar e registrar inspeções |
| Gestor operacional | Acompanhar status, bloqueios e histórico |
| Administrador | Administrar cadastros e acessos futuros |

A definição exata de permissões é **proposta**, não uma matriz obrigatória do PDF.

## Dados e processos
Informações: produto químico, situação ativo/inativo, classe de risco, quantidade com unidade, responsável técnico, documentos obrigatórios, inspeção, área de armazenamento opcional, status, decisão de bloqueio/liberação e histórico.

Fluxo de negócio proposto:
1. Cadastrar produto com nome e classificação de risco.
2. Registrar carga vinculada a **produto ativo**, com quantidade positiva e responsável.
3. Vincular e validar documentação obrigatória.
4. Registrar inspeções quando cabíveis.
5. Bloquear ou liberar conforme condições e registrar decisão.
6. Consultar status e histórico, respeitando regras de transição.

## Riscos e restrições
- Dados ou documentos faltantes devem impedir liberação.
- Carga bloqueada não pode ser movimentada; cancelada não é liberável.
- O status deve ter histórico auditável e mudanças autorizadas.
- **Uso acadêmico:** não utilizar protótipo ou regras ilustrativas como autorização real para movimentação de produtos perigosos. Exigências regulatórias específicas não foram definidas no PDF.

## Evolução
Na **Fase 01**, são exigidos domínio, DDD, documentação arquitetural, diagramas, planejamento da qualidade, repo Git e vídeo. API, persistência e interface podem ser construídas nas próximas fases conforme novos requisitos.
