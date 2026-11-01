# 02 — Domain-Driven Design

**Exigido:** entidades, objetos de valor (VO), agregados, casos de uso, regras de negócio e linguagem ubíqua (enunciado pp. 4–6). A modelagem a seguir é **proposta**.

## Linguagem ubíqua
| Termo | Definição |
|---|---|
| Produto Químico | Cadastro com nome, classificação de risco e atividade |
| Carga Química | Unidade registrada com produto, quantidade, responsável, documentos e status |
| Classificação de Risco | Identificação da categoria de risco, obrigatória |
| Documento de Carga | Evidência documental associada à carga |
| Inspeção | Verificação técnica com situação e resultado |
| Responsável Técnico | Profissional identificado para a carga |
| Liberação | Decisão que permite operação após validações |
| Bloqueio | Impedimento de movimentação |
| Histórico | Registro cronológico de mudanças e decisões |

## Entidades e atributos propostos
| Entidade | Responsabilidade | Atributos principais | Regras / relação |
|---|---|---|---|
| **ProdutoQuimico** | Manter cadastro | id, nome, classeRisco, ativo | Nome/risco obrigatórios; inativo não vincula nova carga; 1:N cargas |
| **CargaQuimica** | Controlar ciclo de vida | id, produtoId, quantidade, risco, responsavelId, status, historico | Raiz de agregado; documentação, inspeção e estados protegidos |
| **ResponsavelTecnico** | Identificar agente técnico | id, nome, identificacao | Obrigatório na carga; 1:N cargas |
| **DocumentoCarga** | Controlar evidência | id, tipo, situacao, validade | Pertence à carga; obrigatório validado antes de liberar |
| **Inspecao** | Registrar controle | id, data, resultado, situacao | Pertence à carga; restringe finalização |
| **AreaArmazenamento** | Representar local | id, nome, restricoes | Associação opcional; compatibilidade futura |

## Objetos de valor
- `ClassificacaoRisco`: valor não vazio e padronizado; **não supor taxonomia normativa**.
- `QuantidadeCarga`: número finito maior que zero e unidade.
- `StatusCarga`: valor pertencente ao conjunto de estados acordado.
- `IdentificadorCarga`: identificador único não vazio.
- `SituacaoDocumento`: exemplo de estados PENDENTE, VALIDO, INVALIDO.

## Agregado principal
`CargaQuimica` é a **Aggregate Root** proposta: conserva invariantes de produto, quantidade, responsável, documentos, inspeções, transições e histórico. `ProdutoQuimico` é cadastro próprio, referenciado por ID e consultado no caso de uso para impedir vínculo de produto inativo.

## Bounded contexts candidatos
**Catálogo Químico**, **Operações de Carga** e **Conformidade/Documentação**. A separação física em serviços não é necessária nesta fase.

Casos de uso: [03](03-casos-de-uso.md). Regras: [04](04-regras-negocio.md).
