---
description: "Create the full technical planning for a feature from its product spec: workstream, contracts, risks, validation plan. Use when a spec is approved and needs technical decomposition before implementation."
agent: plan
mode: "agent"
tools: [read, edit, search, todo]
---

# Technical Planning Pipeline

Create the complete technical planning for the spec at: **${{spec_path}}**

## Pipeline

### Step 1 — Context Reading
- Read the spec file at: `${{spec_path}}`
- Read the active release in `Documentacao_[NomeDoProjeto]/04-planejamento-do-produto/06-releases/01-ativas/`
- Read governance: `Documentacao_[NomeDoProjeto]/04-planejamento-do-produto/07-governanca/`
- Read existing workstreams in `Documentacao_[NomeDoProjeto]/06-planejamento-tecnico-do-desenvolvimento/02-workstreams-tecnicos/`
- Read the data schema (e.g., `prisma/schema.prisma` or ORM models)
- Read relevant existing services, controllers, and data access layers
- Create a todo list with all planning tasks

### Step 2 — Identify Location
- From the spec and release, determine the correct folder for the workstream within `Documentacao_[NomeDoProjeto]/06-planejamento-tecnico-do-desenvolvimento/02-workstreams-tecnicos/`
- Use waves or phases if your project uses them, otherwise create directly in the workstreams folder

### Step 3 — Create Technical Workstream
Create the workstream markdown file using `.github/docs/plan-template.md` as base, with these sections:

1. **Objetivo** — what this workstream delivers technically
2. **Spec de origem** — link to the product spec
3. **Escopo técnico** — what changes in backend, frontend, database
4. **Modelo de dados** — schema changes (new models, fields, relations)
5. **Endpoints** — new or modified API endpoints (method, path, auth, payload, response)
6. **Contratos e payloads** — request/response shapes for each endpoint
7. **Frontend** — new pages, components, hooks, API calls
8. **Dependências técnicas** — what must exist before this can start
9. **Riscos técnicos** — what can go wrong during implementation
10. **Coverage Matrix** — maps every `REQ-*` from spec to implementation artifact
11. **Decomposição em tarefas** — ordered task list ready for execution
12. **Critérios de pronto** — when is this workstream technically done

### Step 4 — Update Supporting Artifacts
If the analysis revealed relevant items, create or update:
- **Contracts/matrices** in `Documentacao_[NomeDoProjeto]/06-planejamento-tecnico-do-desenvolvimento/04-modelos-contratos-e-matrizes/`
- **Technical risks** in `Documentacao_[NomeDoProjeto]/06-planejamento-tecnico-do-desenvolvimento/05-riscos-tecnicos-e-dependencias/`
- **Validation plan** in `Documentacao_[NomeDoProjeto]/06-planejamento-tecnico-do-desenvolvimento/06-planos-de-validacao-e-rollout/`

### Step 5 — Coherence Check
Check and update if the technical planning changed anything upstream:
- Does the release need an update? (scope, priority, dependency)
- Does the Planner need to reflect a new dependency?
- Does governance need a new risk or decision?
- Is this feature ready for daily execution (kanban)?

## Rules
- Follow the skill `technical-planning-manager` for all decisions
- NEVER create a workstream without reading the spec first
- NEVER skip the coherence check (Step 5)
- NEVER create a workstream without a `## Coverage Matrix`
- Mark todos completed as each step finishes
