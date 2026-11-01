# QuimiPort · Tech Challenge Fase 01 — Grupo 14

**Pós-Tech FIAP + Alura | Full Stack Development | Turma 10FSDT**

> **Status: documentação preliminar para revisão e aprovação coletiva.** Projeto acadêmico, não sistema apto a operar cargas químicas reais.

## Objetivo

Propor a arquitetura do **QuimiPort**, solução para gestão inicial de cargas químicas em operações portuárias inspiradas no Porto de Santos. O domínio envolve produtos químicos, cargas, classificação de risco, documentação obrigatória, responsável técnico, inspeções, status, bloqueio e liberação.

**Escopo oficial da Fase 01:** documentação técnica e arquitetural no GitHub **e vídeo de 5 a 10 minutos**. **Não é necessário entregar frontend, backend ou banco de dados funcionando** nesta fase.

**Importante:** o Tech Challenge vale **90% da nota de cada disciplina da fase**, conforme o enunciado. O **prazo não consta no PDF**: confirmar no portal da FIAP.

## Navegação pelo projeto

| Documento | Conteúdo |
|---|---|
| [01 — Entendimento do domínio](docs/01-dominio.md) | Problema, atores, processos, riscos e evolução |
| [02 — DDD](docs/02-modelagem-ddd.md) | Linguagem ubíqua, entidades, VOs e agregados |
| [03 — Casos de uso](docs/03-casos-de-uso.md) | Fluxos, atores, entradas, saídas e erros |
| [04 — Regras de negócio](docs/04-regras-negocio.md) | Regras RB01–RB12 e rastreabilidade |
| [05 — Arquitetura](docs/05-arquitetura.md) | Camadas, responsabilidades e pastas |
| [06 — Diagramas](docs/06-diagramas.md) | **Diagrama de domínio e fluxo de status obrigatórios** |
| [07 — Qualidade](docs/07-plano-qualidade.md) | Estratégia de testes futuros e cenários |
| [08 — JS/TypeScript](docs/08-javascript-typescript.md) | Tipos, contratos e decisões técnicas |
| [09 — Decisões e evolução](docs/09-decisoes-roadmap.md) | ADRs e roadmap |
| [10 — Backlog](docs/10-backlog.md) | 19 atividades propostas |
| [11 — Divisão da equipe](docs/11-divisao-equipe.md) | Frentes de trabalho e revisões |
| [12 — Plano de execução](docs/12-plano-execucao.md) | Sequência relativa, sem prazos inventados |
| [13 — Roteiro do vídeo](docs/13-roteiro-video.md) | Apresentação de 5 a 10 minutos |
| [14 — Checklist da entrega](docs/14-checklist-entrega.md) | Conferência com páginas do PDF |
| [ADR-001](docs/decisoes/ADR-001-camadas.md) | Justificativa da arquitetura |

## Modelo inicial proposto

**Agregado principal:** CargaQuimica. **Entidades candidatas:** ProdutoQuimico, DocumentoCarga, Inspecao, ResponsavelTecnico e AreaArmazenamento.

**Invariantes:** produto ativo, risco informado, quantidade positiva, responsável técnico definido; documentação obrigatória antes da liberação; carga bloqueada não movimenta; cancelada não libera; em inspeção não finaliza antes de liberação.

**Arquitetura sugerida:** monólito modular com \`domain\`, \`application\`, \`infrastructure\` e \`interfaces\`; TypeScript com tipagem estrita. O código funcional será tratado nas fases futuras, se exigido.

## Como colaborar

1. Ler os [requisitos e checklist](docs/14-checklist-entrega.md).
2. Consultar as [tarefas](docs/10-backlog.md) ou [Issues](../../issues).
3. Escolher uma atividade com a equipe; não se autoatribuir trabalho alheio.
4. Criar uma branch, atualizar documentação e abrir pull request.
5. Pedir revisão de outro integrante antes de integrar na \`main\`.
6. Preparar e conferir coletivamente o vídeo exigido.

**Fontes:** enunciado oficial \`10FSDT -Tech Challenge - Fase 1.pdf\` fornecido aos estudantes. Este repositório contém **textos originais elaborados para o grupo** e não republica o PDF institucional.

## Licença

Este repositório contém um arquivo [MIT LICENSE](LICENSE) criado por seu proprietário. A publicação de contribuições e a atribuição de autoria devem ser acordadas entre os integrantes. Materiais da FIAP e de terceiros preservam seus direitos.
