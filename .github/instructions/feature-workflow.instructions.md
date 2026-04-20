---
description: "Use when implementing new features or working on the main development branch. Enforces the mandatory 6-step feature implementation workflow."
applyTo: "src/**"
---

# Feature Implementation Workflow

Every new feature MUST follow this strict 6-step pipeline, one feature at a time:

## Steps

1. **Planning** — Review requirements from the active release document in `Documentacao_[NomeDoProjeto]/04-planejamento-do-produto/06-releases/01-ativas/` and the relevant spec in `Documentacao_[NomeDoProjeto]/04-planejamento-do-produto/03-especificacoes/`. Search for the matching technical workstream in `Documentacao_[NomeDoProjeto]/06-planejamento-tecnico-do-desenvolvimento/02-workstreams-tecnicos/`. If it exists, use the `## Coverage Matrix` and workstream as the implementation source of truth. If it does not exist and the feature is non-trivial (cross-module changes, schema changes, multiple endpoints, critical flow), stop and create the technical planning first using `/technical-planning`. If the feature is small/simple, proceed from the spec. Define exact scope: schema changes, migrations, services, controllers, DTOs, frontend components.

2. **Implementation** — Write code following the appropriate order for your stack (schema → service → controller → frontend). Validate with the project build command after each significant change. NEVER use `npx tsc --noEmit` as the sole validation.

3. **Review** — Review all changed files. Check for: missing data-scoping (user/tenant isolation), input validation gaps, missing auth guards, error handling at system boundaries.

4. **Fix** — Fix any issues found during review. Re-validate with build.

5. **Browser QA** — Test the feature in the browser using Chrome DevTools or the QA agent. Verify UI renders correctly, API calls succeed, and data flows end-to-end. Map results back to `REQ-*` IDs.

6. **Documentation** — Create or update user manuals in `Documentacao_[NomeDoProjeto]/Manual/` and official system docs in `Documentacao_[NomeDoProjeto]/03-documentacao-oficial-do-sistema/` for any feature that changes user-facing behavior.

7. **Commit and Push** — Commit with a descriptive message using conventional commits (e.g., `feat: add filter to schedule view`). Push to origin.

## Rules

- Product scope comes from `Documentacao_[NomeDoProjeto]/04-planejamento-do-produto`
- Implementation decomposition comes from `Documentacao_[NomeDoProjeto]/06-planejamento-tecnico-do-desenvolvimento` when a workstream exists
- ONE feature at a time — never start the next before completing the current pipeline
- NEVER edit files via shell redirection or PowerShell encoding-unsafe commands — always use editor tools
- ALWAYS use the project build command for validation, never just the TypeScript compiler
- Every `REQ-*` in the spec must have a corresponding test result before the feature is closed

## Customize Per Project

Update the following in this file after cloning the boilerplate:
- Build commands (e.g., `cd API && npm run build`)
- Migration strategy (e.g., Prisma, Flyway, manual SQL)
- Tech stack-specific review checklist items
