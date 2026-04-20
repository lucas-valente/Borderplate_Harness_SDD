---
description: "Audit implementation against original plan/spec/workstream. Produces PASS/FAIL with objective gaps and exact file references."
mode: "agent"
tools: [read, search, execute, todo, chrome-devtoo/*]
---

# Audit Against Plan

Audit the delivered implementation against the original planning artifacts for: **${{context}}**

## Required Inputs

- `spec_path`: path to functional spec in `Documentacao_[NomeDoProjeto]/04-planejamento-do-produto/03-especificacoes/`
- `workstream_path` (if exists): path to technical workstream in `Documentacao_[NomeDoProjeto]/06-planejamento-tecnico-do-desenvolvimento/02-workstreams-tecnicos/`
- `changed_files` (optional but recommended): list of changed files

## Audit Pipeline

### Step 1 — Load Baseline Plan
- Read spec at `${{spec_path}}`
- Read active release in `Documentacao_[NomeDoProjeto]/04-planejamento-do-produto/06-releases/01-ativas/`
- Read governance dependencies/risks in `Documentacao_[NomeDoProjeto]/04-planejamento-do-produto/07-governanca/`
- If `${{workstream_path}}` exists, read it as technical baseline, including `## Coverage Matrix` when present

### Step 2 — Load Delivery Evidence
- Inspect changed implementation files and documentation updates (`04`, `05`, `06`, `Manual`, `03-documentacao-oficial-do-sistema`)
- Run build checks when applicable (customize per project stack)

### Step 3 — Requirement Coverage Audit

1. Extract all `REQ-*` IDs from the `## Requisitos` table in the spec.
   - If spec predates the `REQ-*` standard (no table present), infer requirements from sections and assign temporary IDs `REQ-T001`, `REQ-T002`... for audit purposes only.
   - If `${{workstream_path}}` exists and has `## Coverage Matrix`, verify that every `REQ-*` from the spec appears in the workstream matrix before evaluating implementation evidence.
2. For each `REQ-ID`, classify:
   - `OK` — implemented as planned
   - `PARTIAL` — implemented with gaps
   - `MISSING` — not implemented
   - `DIVERGENT` — implemented differently from plan
3. Output a coverage matrix:

| REQ-ID | Tipo | Descrição resumida | Status | Evidência / Arquivo |
|--------|------|--------------------|--------|---------------------|
| REQ-001 | ... | ... | OK \| PARTIAL \| MISSING \| DIVERGENT | path/file.ts#L10 |

Audit dimensions per requirement:
- Functional scope
- Technical planning coverage in workstream (`## Coverage Matrix`)
- Data model
- Endpoints/contracts/payloads
- Frontend flow/components
- Security/auth/validation
- Documentation coherence (`04`, `05`, `06`)

### Step 4 — Risk and Data Consistency Checks
- If divergence touches persisted data, require database evidence before concluding (use MCP if available)
- If divergence impacts user-visible behavior, verify documentation coverage in `Manual` and `03-documentacao-oficial-do-sistema`

### Step 5 — Final Verdict
Return one of:
- `AUDIT RESULT: PASS`
- `AUDIT RESULT: PASS WITH DEVIATIONS`
- `AUDIT RESULT: FAIL`

Automatic FAIL conditions:
- Any `MISSING` item on critical flow (auth, key data operation)
- Any `REQ-*` present in the spec but absent from the workstream `## Coverage Matrix`, when a workstream exists
- More than 30% of `REQ-*` IDs classified as `MISSING` or `DIVERGENT`
- Build fails during Step 2

Always include:
1. Coverage matrix summary (total / OK / PARTIAL / MISSING / DIVERGENT counts)
2. Objective findings with exact file paths
3. Missing items (if any)
4. Required corrective actions in execution order
5. Whether re-run of `/feature-pipeline`, `/quality-gate`, and `/documentation-sync` is needed

## Rules

- Never approve without reading the original plan artifacts
- Never approve if workstream `## Coverage Matrix` is missing when workstream exists
- Never approve with unresolved `MISSING` on critical flow
