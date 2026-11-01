# ADR-001 — Separação em camadas e monólito modular

**Status:** PROPOSTO, aguardando validação do Grupo 14.

## Contexto
O QuimiPort exige documentação de domínio, regras de negócio, arquitetura e qualidade. O projeto deve poder evoluir sem criar dependência excessiva de framework ou banco de dados.

## Decisão
Adotar como **proposta** uma arquitetura modular em TypeScript estrito com:
- `domain` — entidades, VOs, agregados, regras e erros;
- `application` — casos de uso e contratos/ports;
- `infrastructure` — persistência e integrações futuras;
- `interfaces` — API, CLI e interface web/móvel futuras.

## Benefícios
Testabilidade, encapsulamento de regras, baixo acoplamento e evolução incremental.

## Custos
Mais estrutura e conceitos a explicar; evitar abstrações prematuras.

## Alternativas
MVC simples (viável, porém com risco de misturar regras e camadas); microsserviços imediatos (complexidade injustificada para a Fase 01).

## Revisão
Reconsiderar quando houver requisitos reais de implementação, volume ou novas orientações da FIAP.
