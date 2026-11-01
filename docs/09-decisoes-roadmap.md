# 09 — Decisões arquiteturais e roadmap

## Decisões propostas
| ADR | Decisão | Por quê? | Trade-off |
|---|---|---|---|
| ADR-001 | Domínio, aplicação, infraestrutura e interfaces separados | Regras isoladas e testáveis | Mais estrutura documental |
| ADR-002 | TypeScript estrito | Contratos claros e erros detectáveis | Exige boas convenções |
| ADR-003 | CargaQuimica como Aggregate Root | Protege liberação, bloqueio, inspeção e histórico | Agregado requer limites bem definidos |
| ADR-004 | Monólito modular inicial | Evita complexidade distribuída desnecessária | Pode exigir divisão futura |
| ADR-005 | Repositórios por interfaces/ports | Banco substituível sem afetar domínio | Abstrações a manter |

Todas as decisões precisam de revisão coletiva. [ADR-001 detalhado](decisoes/ADR-001-camadas.md).

## Responsabilidades e baixo acoplamento
O domínio conserva invariantes; application orquestra casos de uso e políticas; infrastructure implementa repositórios e serviços externos; interfaces expõe API e UI. A direção de dependências evita domínio conhecer HTTP/SQL.

## Evolução planejada (não cronograma oficial)
- **Fase 01:** proposta do domínio, DDD, casos, regras, arquitetura, 2 diagramas obrigatórios, plano de qualidade, TypeScript, repositório, vídeo.
- **Etapas seguintes:** criar lógica e API, persistência, frontend e testes; então avaliar mobile, CI/CD e nuvem conforme conteúdo e novos enunciados.
- **Microsserviços:** apenas com justificativa técnica (contextos realmente independentes, escala, implantação separada).
- **Segurança futura:** identidade/perfis, validação de documentos, trilha de auditoria, gestão de segredos. Não tratar projeto acadêmico como certificação operacional.
