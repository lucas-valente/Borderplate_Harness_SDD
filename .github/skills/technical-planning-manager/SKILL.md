---
name: technical-planning-manager
description: "Use when creating, revising, or maintaining technical development planning workstreams. Actions: create technical workstream, update technical release view, register technical decisions, maintain contracts and matrices, map technical dependencies and risks, define validation and rollout plans, and sync product planning and daily execution when technical planning changes scope, priority, risk, dependency, or operational focus. Triggers: planejamento técnico, plano técnico, workstream técnico, contrato, matriz, payload, fluxo técnico, risco técnico, rollout, validação técnica, smoke, regressão, implementação."
---

# Technical Planning Manager — Planejamento Técnico do Desenvolvimento

Skill para criar, revisar e manter o planejamento técnico de desenvolvimento, garantindo coerência entre:

1. `Documentacao_[NomeDoProjeto]/04-planejamento-do-produto`
2. `Documentacao_[NomeDoProjeto]/05-execucao-diaria-do-desenvolvimento`
3. `Documentacao_[NomeDoProjeto]/06-planejamento-tecnico-do-desenvolvimento`

> Customize os caminhos abaixo com o nome real do projeto após clonar o boilerplate.

## Mapa da Pasta `06`

```
Documentacao_[NomeDoProjeto]/06-planejamento-tecnico-do-desenvolvimento/
├── 01-visao-tecnica-por-release/
├── 02-workstreams-tecnicos/
├── 03-decisoes-tecnicas/
├── 04-modelos-contratos-e-matrizes/
├── 05-riscos-tecnicos-e-dependencias/
└── 06-planos-de-validacao-e-rollout/
```

## Quando Usar

### Obrigatório

- Quando uma frente sair da spec funcional e virar desenho de implementação
- Quando surgir workstream técnico novo
- Quando detalhar contratos, payloads, matrizes, fluxos, validação ou rollout
- Quando uma decisão técnica alterar dependências, riscos, ordem de execução ou corte de release

### Recomendado

- Antes de iniciar implementação de feature relevante
- Ao quebrar uma onda/fase em trilhas backend/frontend/dados
- Ao transformar uma spec funcional em backlog técnico executável

### Não Usar

- Para tarefas puramente de código sem impacto no planejamento técnico
- Para atualizações apenas de status diário sem mudança de desenho técnico

## Fontes de Verdade (ordem de prioridade)

| Camada | Documento |
|--------|-----------|
| Release ativa | `Documentacao_[NomeDoProjeto]/04-planejamento-do-produto/06-releases/01-ativas/` |
| Planner | `Documentacao_[NomeDoProjeto]/04-planejamento-do-produto/Planner.md` |
| Spec funcional | `Documentacao_[NomeDoProjeto]/04-planejamento-do-produto/03-especificacoes/` |
| Governança | `Documentacao_[NomeDoProjeto]/04-planejamento-do-produto/07-governanca/` |
| Workstreams | `Documentacao_[NomeDoProjeto]/06-planejamento-tecnico-do-desenvolvimento/02-workstreams-tecnicos/` |
| Decisões técnicas | `Documentacao_[NomeDoProjeto]/06-planejamento-tecnico-do-desenvolvimento/03-decisoes-tecnicas/` |
| Contratos e matrizes | `Documentacao_[NomeDoProjeto]/06-planejamento-tecnico-do-desenvolvimento/04-modelos-contratos-e-matrizes/` |
| Riscos técnicos | `Documentacao_[NomeDoProjeto]/06-planejamento-tecnico-do-desenvolvimento/05-riscos-tecnicos-e-dependencias/` |
| Validação e rollout | `Documentacao_[NomeDoProjeto]/06-planejamento-tecnico-do-desenvolvimento/06-planos-de-validacao-e-rollout/` |
| Execução diária | `Documentacao_[NomeDoProjeto]/05-execucao-diaria-do-desenvolvimento/` |

## Regra Central

Planejamento técnico **nunca** deve atualizar apenas a pasta `06`.

Quando planejamento técnico mudar escopo, prioridade, risco, dependência ou foco operacional, atualizar **também**:

1. Release ativa (em `04`)
2. Planner (em `04`)
3. Spec da frente (em `04`) se o desenho técnico revelar gap funcional
4. Governança (em `04`) se surgir novo risco ou decisão
5. Kanban / daily notes (em `05`) quando virar trabalho da semana

## Workflow de Planejamento Técnico

### Para nova frente

1. Ler spec funcional + release ativa + governança
2. Identificar localização do workstream em `06/02-workstreams-tecnicos/`
3. Criar workstream usando `.github/docs/plan-template.md` como base
4. Preencher obrigatoriamente:
   - Spec de origem (link)
   - Escopo técnico (backend, frontend, dados)
   - Coverage Matrix (todos os `REQ-*` da spec)
   - Contratos de endpoints/API
   - Decomposição em tarefas ordenadas
   - Critérios de pronto
5. Atualizar artefatos de apoio (contratos, riscos, validação) se necessário
6. Verificar e atualizar coerência em `04` e `05`

### Para revisão de workstream existente

1. Ler versão atual + spec + release
2. Identificar o que mudou (escopo, contrato, risco, etc.)
3. Atualizar Coverage Matrix se `REQ-*` mudaram
4. Propagar mudanças relevantes para `04` e `05`

## Qualidade do Workstream

Um workstream está pronto para execução quando:
- [ ] Spec de origem linkada
- [ ] Coverage Matrix com todos os `REQ-*` da spec (PENDENTE é ok, MISSING não)
- [ ] Contratos definidos (endpoints, request/response)
- [ ] Decomposição técnica clara e ordenada
- [ ] Riscos técnicos identificados com mitigação
- [ ] Plano de validação definido (testes unitários, integração, smoke)
- [ ] Critérios de pronto explícitos

## Critérios de Decisão Técnica

Quando uma decisão técnica for tomada durante o planejamento:

1. Registrar em `06/03-decisoes-tecnicas/ADR-NNN-titulo.md`
2. Se mudar escopo/prioridade/risco de produto → atualizar `04`
3. Se mudar dependência entre workstreams → atualizar `04/07-governanca/`
4. Se mudar estratégia de validação/rollout → atualizar `06/06-planos-de-validacao-e-rollout/`
