---
description: "Run the full 6-step feature implementation pipeline: planning, implementation, review, fix, QA testing, commit."
mode: "agent"
tools: [read, edit, search, execute, agent, todo, chrome-devtoo/*]
---

# Feature Pipeline

Execute the complete 6-step feature implementation workflow for the spec at: **${{spec_path}}**

## Pipeline

### Step 1 — Planning
- Read the spec file at the provided path: `${{spec_path}}`
- Read the active release in `Documentacao_[NomeDoProjeto]/04-planejamento-do-produto/06-releases/01-ativas/`
- Check governance for dependencies/risks in `Documentacao_[NomeDoProjeto]/04-planejamento-do-produto/07-governanca/`
- Search for an existing technical workstream in `Documentacao_[NomeDoProjeto]/06-planejamento-tecnico-do-desenvolvimento/02-workstreams-tecnicos/`
- If a matching workstream exists, read it — especially the `## Coverage Matrix` — and use it as the technical source of truth
- If no workstream exists and the feature is non-trivial (cross-module changes, schema changes, multiple endpoints, critical flow), stop and instruct the user to run `/technical-planning` first
- If no workstream exists and the feature is small/simple, proceed using the spec as the source of truth
- Read relevant existing code (services, controllers, schema, components)
- Create a todo list with all implementation tasks
- Define: schema changes, new endpoints, new services, frontend components

### Step 2 — Implementation
- Apply schema changes
- Create/update services, controllers, DTOs/validators, modules
- Create/update frontend components, pages, API calls
- Validate with `npm run build` (or project-appropriate build command) in all relevant apps

### Step 3 — Review
- Review all changed files for:
  - Missing data-scoping (multi-tenant or user-level isolation as appropriate)
  - Missing input validation
  - Missing auth guards/roles
  - Error handling at system boundaries
  - User-facing error messages should be clear

### Step 4 — Fix
- Fix all issues found in review
- Re-validate with build

### Step 5 — Browser QA
- Delegate to `@QA` agent to test the feature in the browser
- QA must validate: happy path, edge cases, data persistence, cross-module integrity
- QA must map each `REQ-*` to a test result
- Fix any bugs found, re-test until clean

### Step 6 — Commit and Push
- Stage all changes
- Commit with conventional message: `feat: {feature description}`
- Push to origin

## Rules
- Follow ALL rules from `.github/instructions/feature-workflow.instructions.md`
- Treat the spec as the product source of truth
- Treat the workstream as the implementation source of truth when it exists
- ONE feature at a time
- NEVER skip steps
- Mark todos completed as each step finishes
