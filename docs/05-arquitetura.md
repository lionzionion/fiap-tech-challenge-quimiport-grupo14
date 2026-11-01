# 05 — Arquitetura e organização

**Fonte:** enunciado p. 8. **Proposta:** monólito modular TypeScript, princípios de DDD, SOLID e arquitetura hexagonal em camadas. **A implementação é futura.**

~~~mermaid
flowchart TB
  I[Interfaces futuras: API, Web, Mobile] --> A[Application: casos de uso]
  A --> D[Domain: entidades, VOs, regras e agregados]
  A --> P[Ports: contratos]
  INF[Infrastructure: adaptadores] -. implementa .-> P
  INF --> DB[(Banco de dados futuro)]
~~~

## Responsabilidades
- **domain:** regras de produto e carga, Aggregate Root `CargaQuimica`, valores, estados e erros. Não importa banco nem framework.
- **application:** coordena casos de uso UC01–UC11, interfaces de repositório e autorizações futuras.
- **infrastructure:** adaptadores de persistência, logs e integrações técnicas futuras.
- **interfaces:** pontos de entrada (API/CLI/frontend/mobile), sem duplicar regras.

## Estrutura sugerida
~~~text
quimiport/
  README.md
  docs/
    01-dominio.md
    02-modelagem-ddd.md
    03-casos-de-uso.md
    04-regras-negocio.md
    05-arquitetura.md
    06-diagramas.md
    07-plano-qualidade.md
    ...
    decisoes/
  src/                   # futuro
    domain/
      entities/
      aggregates/
      value-objects/
      errors/
    application/
      use-cases/
      ports/
      dto/
    infrastructure/
      persistence/
      external/
    interfaces/
      http/
      web/
  tests/                 # futuro
    unit/
    integration/
    bdd/
~~~

## Dependências e evolução
Domínio independe de HTTP/UI/SQL; persistência é abstraída por **ports**. A solução inicia como proposta documental; API, dados, interface, cloud e eventualmente microsserviços serão considerados conforme as próximas fases e justificativas concretas.

Ver [ADR-001](decisoes/ADR-001-camadas.md).
