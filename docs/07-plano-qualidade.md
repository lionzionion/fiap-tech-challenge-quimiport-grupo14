# 07 — Plano de qualidade de software

**Enunciado:** pp. 8–9. **Fase 01 exige o planejamento dos testes, não sua execução.**

## Priorização de riscos
1. **Crítico:** liberar carga sem documentos obrigatórios (RB04).
2. **Crítico:** movimentar carga bloqueada ou liberar cancelada (RB05/RB06).
3. **Crítico:** finalizar carga em inspeção antes de liberação (RB07).
4. **Alto:** registrar com produto inativo, sem classificação, quantidade positiva ou responsável (RB01–03, RB10–12).
5. **Alto:** cadastrar produto sem nome/classe de risco (RB08/RB09).

## Estratégia futura
| Teste | Objetivo | Abordagem proposta |
|---|---|---|
| Unitário | Validar entidades, VOs e regras isoladas | Vitest, sem banco/rede |
| Caso de uso | Testar fluxos positivos e erros | Mocks de repositório e geradores |
| Integração | Validar persistência e API quando existirem | Banco de testes e dados fictícios |
| BDD | Descrever comportamentos críticos | Gherkin, Given/When/Then |
| Regressão | Evitar retorno de falhas | Suíte automatizada em CI futura |
| Carga | Validar volume quando houver API | k6/Artillery opcional |

## Mocks e dados simulados
- ProdutoRepositoryFake com produto ativo, inativo e ausente.
- CargaRepositoryFake com carga registrada, bloqueada, cancelada e em inspeção.
- DocumentoRepositoryFake com conjunto completo, incompleto e vencido.
- ClockFake/IdGeneratorFake para testes determinísticos.
- **Nunca utilizar documentos reais, dados sensíveis ou credenciais.**

## Matriz de testes planejados
| ID | Cenário | Resultado esperado |
|---|---|---|
| T01 | Produto sem classe de risco | Impedir cadastro |
| T02 | Registrar carga de produto inativo | Recusar registro |
| T03 | Liberar sem documentação obrigatória | Manter bloqueada/não liberar |
| T04 | Movimentar carga bloqueada | Recusar movimentação |
| T05 | Liberar carga cancelada | Recusar liberação |
| T06 | Finalizar carga em inspeção, não liberada | Recusar finalização |
| T07 | Liberar carga com documentos e condições válidos | Permitir e registrar histórico |
| T08 | Quantidade igual a zero ou negativa | Recusar registro |
| T09 | Registro sem responsável técnico | Recusar |
| T10 | Transição de status inválida | Preservar estado anterior |

## Cenários BDD (propostos)
~~~gherkin
Funcionalidade: Liberacao de cargas quimicas

  Cenario: Documentacao obrigatoria incompleta
    Dado uma carga registrada com documentacao incompleta
    Quando for solicitada a liberacao
    Entao o sistema deve recusar a liberacao
    E o status anterior deve ser preservado

  Cenario: Liberacao com requisitos atendidos
    Dado uma carga de produto ativo e quantidade valida
    E um responsavel tecnico identificado
    E toda documentacao obrigatoria validada
    E nenhuma inspecao ou bloqueio pendente
    Quando for solicitada a liberacao
    Entao o sistema pode registrar a liberacao no historico
~~~

**Evidência da Fase 01:** estratégia, cenários, mocks e critérios, **não prints de testes não executados**.
