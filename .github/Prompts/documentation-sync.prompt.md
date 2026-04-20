---
description: "Sync documentation after code or planning changes. Updates product planning (04), technical planning (06), and daily execution (05) only when impacted."
mode: "agent"
tools: [read, edit, search, todo]
---

# Documentation Sync Pipeline

Synchronize documentation for this change context: **${{change_context}}**

## Goal

Ensure documentation stays coherent across:

- `Documentacao_[NomeDoProjeto]/04-planejamento-do-produto/`
- `Documentacao_[NomeDoProjeto]/05-execucao-diaria-do-desenvolvimento/`
- `Documentacao_[NomeDoProjeto]/06-planejamento-tecnico-do-desenvolvimento/`
- `Documentacao_[NomeDoProjeto]/Manual/`
- `Documentacao_[NomeDoProjeto]/03-documentacao-oficial-do-sistema/`

## Pipeline

### Step 1 — Read Change Context
- Read `${{change_context}}` and identify what changed (scope, rule, dependency, risk, priority, implementation design, validation strategy, rollout, operational status)
- Read active release
- Read planner

### Step 2 — Classify Impact Type
Classify the change as one or more:
- Product scope/governance impact (`04`)
- Technical implementation impact (`06`)
- Operational execution impact (`05`)
- User-facing behavior impact (`Manual` and `03-documentacao-oficial-do-sistema`)

### Step 3 — Update `04` (when applicable)
Update only impacted files:
- Release ativa
- Planner
- Spec funcional da frente
- Governança (mapa de dependências/riscos, registro de decisões, ADRs)

### Step 4 — Update `06` (when applicable)
Update only impacted files:
- Visão técnica por release
- Workstream técnico (including `## Coverage Matrix` if REQ coverage changed)
- Decisões técnicas
- Contratos e matrizes
- Riscos técnicos
- Validação e rollout

### Step 5 — Update `05` (when applicable)
Update operational artifacts only if already execution-ready:
- Kanban operacional diário
- Daily notes
- Revisões semanais
- Planos operacionais

### Step 6 — Update Manual/Doc Oficial (when applicable)
If user-facing behavior changed, update:
- `Documentacao_[NomeDoProjeto]/Manual/`
- `Documentacao_[NomeDoProjeto]/03-documentacao-oficial-do-sistema/`

### Step 7 — Coherence Confirmation
Return a summary of:
- Files updated
- Files that were checked but not updated (and why)
- Any remaining gaps that need manual attention

## Rules
- Never update `05` for changes that are still in planning
- Never update Manual without confirming the user-facing behavior actually changed
- Never update `04` for changes that are purely technical (no scope/priority/risk impact)
- Mark todos completed as each step finishes
