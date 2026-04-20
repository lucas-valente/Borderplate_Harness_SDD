---
description: "Quick sync for small documentation updates with low structural impact. Use after minor code/UI/wording changes that do not alter release scope."
mode: "agent"
tools: [read, edit, search, todo]
---

# Documentation Quick Sync

Apply a fast documentation sync for: **${{change_context}}**

## Scope

Use this prompt only for low-impact changes, such as:
- text/label/UI wording adjustments
- minor behavior clarifications
- small endpoint field adjustments without structural dependency changes
- status updates in execution artifacts

## Pipeline

### Step 1 — Check Eligibility
- Read `${{change_context}}`
- If change affects scope, priority, dependency, risk, rollout strategy, or technical architecture, stop and use `/documentation-sync`

### Step 2 — Update Minimal Impacted Files
- Update only directly impacted files in:
  - `Documentacao_[NomeDoProjeto]/Manual/`
  - `Documentacao_[NomeDoProjeto]/03-documentacao-oficial-do-sistema/`
  - `Documentacao_[NomeDoProjeto]/05-execucao-diaria-do-desenvolvimento/` (kanban, daily notes)

### Step 3 — Consistency Check
- Confirm no updates are required in:
  - `Documentacao_[NomeDoProjeto]/04-planejamento-do-produto/`
  - `Documentacao_[NomeDoProjeto]/06-planejamento-tecnico-do-desenvolvimento/`
- If required, stop and switch to `/documentation-sync`

## Rules
- Keep edits concise and objective
- Do not create new planning artifacts for low-impact changes
- Mark todos completed as each step finishes
