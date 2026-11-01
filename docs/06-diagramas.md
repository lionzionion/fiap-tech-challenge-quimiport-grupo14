# 06 — Diagramas técnicos

**Obrigatórios conforme enunciado p. 8:** diagrama de domínio (agregados/entidades) **e** fluxo de status da carga. Diagramas adicionais são opcionais. Os estados e transições são uma **proposta**, a aprovar pelo Grupo 14.

## A. Obrigatório — Diagrama de domínio

~~~mermaid
classDiagram
  class CargaQuimica {
    <<AggregateRoot>>
    +id
    +produtoId
    +quantidade
    +classificacaoRisco
    +responsavelTecnicoId
    +status
    +liberar()
    +bloquear()
    +atualizarStatus()
  }
  class ProdutoQuimico {
    +id
    +nome
    +classeRisco
    +ativo
  }
  class ResponsavelTecnico {
    +id
    +nome
    +identificacao
  }
  class DocumentoCarga {
    +id
    +tipo
    +situacao
  }
  class Inspecao {
    +id
    +resultado
    +situacao
  }
  class AreaArmazenamento {
    +id
    +nome
  }
  CargaQuimica --> ProdutoQuimico : referencia
  CargaQuimica --> ResponsavelTecnico : referencia
  CargaQuimica "1" *-- "0..*" DocumentoCarga : contem
  CargaQuimica "1" *-- "0..*" Inspecao : contem
  CargaQuimica --> AreaArmazenamento : opcional
~~~

Objetos de valor no agregado: `ClassificacaoRisco`, `QuantidadeCarga`, `StatusCarga` e `IdentificadorCarga`. Ver [DDD](02-modelagem-ddd.md).

## B. Obrigatório — Fluxo de status (proposto)

~~~mermaid
stateDiagram-v2
  [*] --> REGISTRADA
  REGISTRADA --> AGUARDANDO_DOCUMENTACAO
  AGUARDANDO_DOCUMENTACAO --> EM_ANALISE : conferir docs
  EM_ANALISE --> EM_INSPECAO : solicitar
  EM_INSPECAO --> LIBERADA : aprovada e docs validos
  EM_ANALISE --> LIBERADA : docs validos e sem inspecao pendente
  REGISTRADA --> BLOQUEADA
  EM_ANALISE --> BLOQUEADA
  EM_INSPECAO --> BLOQUEADA
  AGUARDANDO_DOCUMENTACAO --> BLOQUEADA
  BLOQUEADA --> EM_ANALISE : saneamento e reavaliacao
  LIBERADA --> EM_MOVIMENTACAO : autorizada
  EM_MOVIMENTACAO --> FINALIZADA
  REGISTRADA --> CANCELADA
  AGUARDANDO_DOCUMENTACAO --> CANCELADA
  EM_ANALISE --> CANCELADA
  CANCELADA --> [*]
  FINALIZADA --> [*]
~~~

**Guardas:** documentação obrigatória válida antes de liberar; carga **bloqueada não movimenta**; **cancelada não libera**; carga **em inspeção não finaliza sem antes ser liberada**. Transições de desbloqueio/cancelamento e necessidade de inspeção em cada situação são propostas, não definições do PDF.

## C. Opcional — Contexto
~~~mermaid
flowchart LR
  OP[Operador] --> SYS[QuimiPort]
  RT[Responsavel tecnico] --> SYS
  DOC[Analista documental] --> SYS
  QA[Analista qualidade] --> SYS
  G[Gestor] --> SYS
  SYS -. integracao futura .-> DB[(Banco)]
~~~
