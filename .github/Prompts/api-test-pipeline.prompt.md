---
description: "Implement domain-based automated tests from official planning artifacts: context, fixtures, unit/integration/e2e tests, coverage evidence, and file-state reporting."
agent: "api-test"
argument-hint: "Caminho do plano de testes (bootstrap, integracao, ou dominio 01..NN)"
tools: [read, search, edit, execute, agent, todo, web]
---

# Domain Test Pipeline

Execute the domain test implementation workflow for: **${{test_plan_path}}**

Alias operacional em pt-BR: tratar `/api-teste-pipeline` como `/api-test-pipeline`.

Template generico: use este prompt para qualquer modulo de servico (API, backend, worker, gateway, jobs), nao para implementacao funcional de produto.

Harness reference: `.github/docs/api-test-execution-harness.md`.

## Input Modes

1. `00-plano-execucao-paralela-testes-por-dominio.md` (ou equivalente) -> bootstrap mode (fixtures/helpers/mocks/parallelism rules).
2. `00-plano-integracao-testes-por-dominio.md` (ou equivalente) -> integration-front mode (select next pending domain).
3. `01..NN-*.md` -> domain implementation mode.

## Pipeline

### Step 1 - Context and Source of Truth

- Read `${{test_plan_path}}`.
- Read related workstream/validation artifacts under:
  `Documentacao_[NomeDoProjeto]/06-planejamento-tecnico-do-desenvolvimento/`.
- Read `.github/docs/api-test-execution-harness.md`.
- Resolve target module path and test stack from project files.
- Read module manifest/config (for example: package.json, pyproject.toml, pom.xml, go.mod) and test configs.
- Apply skill `.github/skills/api-test-planning-by-domain/SKILL.md`.
- Apply `.github/instructions/api-test-coverage-gate.instructions.md` as hard gate.

### Step 2 - Map Existing Code and Tests

- Map target productive files from the selected domain plan.
- Inspect existing tests in the target module test directory.
- Build initial file-state report for all planned files.
- Identify current gaps and classify scope (`in scope`, `out of scope`, `blocked`).

### Step 3 - Implement Tests

- Add/update focused tests under the target module test directory.
- Prefer reusable fixtures and deterministic mocks.
- Cover unit + integration first; add e2e when plan requires.
- Keep provider calls mocked in mandatory suites.

### Step 4 - Validate

- Run targeted test commands for changed/impacted scope.
- Run targeted coverage for changed listed code files.
- Verify per-file thresholds (`85/85/85/65`).
- Validate happy/sad/edge evidence.

### Step 5 - Quality Review

- Check isolation/permission assertions when applicable.
- Check critical negative-path assertions in protected flows.
- Ensure checklist items reflect passing command evidence.

### Step 6 - Sync Documentation

- Update session execution evidence in the selected domain plan.
- Update file-state report with coverage and scenario evidence.
- Keep unresolved gaps visible with next action.

### Step 7 - Audit Handoff

- Delegate to `@api-test-audit` before declaring completion.
- If audit returns blockers, run remediation loop and re-audit.
- Close only when audit verdict is `PASS` or explicit blocked/out-of-scope exception is documented.

## Rules

- One domain/recorte at a time.
- Do not alter product behavior in this prompt unless explicitly requested.
- Do not use full-suite commands unless user explicitly authorizes.
- Do not use compilation-only checks as a substitute for test evidence.
