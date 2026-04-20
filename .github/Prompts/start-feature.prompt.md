---
description: "Orchestrate end-to-end feature delivery with agent handoffs: planning -> implementation -> quality gate -> documentation sync. Use for non-trivial features."
mode: "agent"
tools: [read, edit, search, execute, agent, todo, chrome-devtoo/*]
---

# Start Feature Orchestration

Run the complete delivery workflow for: **${{spec_path}}**

## Orchestration Flow

### Step 1 — Planning Handoff
- Read the spec at `${{spec_path}}`
- Check if a technical workstream already exists in `Documentacao_[NomeDoProjeto]/06-planejamento-tecnico-do-desenvolvimento/02-workstreams-tecnicos/`
- If no workstream exists and feature is non-trivial, handoff to planning using `/technical-planning ${{spec_path}}`
- If workstream exists, proceed directly

### Step 2 — Implementation Handoff
- Execute implementation using `/feature-pipeline ${{spec_path}}`

### Step 3 — Quality Gate Handoff
- Execute quality gate using `/quality-gate ${{spec_path}}`
- If gate fails, fix issues and re-run `/quality-gate ${{spec_path}}`

### Step 4 — Documentation Sync Handoff
- Build a concise change context from what was implemented
- Execute `/documentation-sync <change_context>`

### Step 5 — Delivery Summary
- Report: planned artifacts, implemented artifacts, validations, and documentation updates
- Confirm coherence across `04`, `05`, `06`

## Rules
- Never skip quality gate
- Never close delivery without documentation sync
- For trivial, low-impact changes, you may replace full sync with `/documentation-quick-sync <change_context>`
