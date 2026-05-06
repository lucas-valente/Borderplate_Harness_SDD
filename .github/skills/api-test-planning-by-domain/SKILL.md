---
name: api-test-planning-by-domain
description: "Use when planning automated test coverage by domain. Triggers: testes por dominio, matrix, relatorio por arquivo, unit, integracao, e2e, contrato, quality gate."
argument-hint: "Objetivo do planejamento de testes por dominio"
---

# Test Planning By Domain

Create a technical planning package for test execution by domain, without implementing production features.

## Outcome

Expected artifacts:

1. Module inventory and baseline test map.
2. Domain taxonomy with priority (P0/P1/P2).
3. Matrix: domain -> productive files -> test type.
4. Execution plan (parallel + integration order).
5. One domain plan per area (`01..NN`).
6. Risk record and quality gates.

## Required Context

Read before planning:

1. active release in `Documentacao_[NomeDoProjeto]/04-planejamento-do-produto/06-releases/01-ativas/`
2. planner in `Documentacao_[NomeDoProjeto]/04-planejamento-do-produto/`
3. related spec(s)
4. governance files in `04-planejamento-do-produto/07-governanca/`
5. technical planning hub in `06-planejamento-tecnico-do-desenvolvimento/`
6. related technical workstreams
7. target module model/contracts/configs
8. module test/runtime configs
9. `.github/docs/api-test-execution-harness.md`

## Procedure

### 1. Frame Scope

Define if planning is for:

- full module;
- release slice;
- one domain;
- quality-gate remediation.

### 2. Inventory Module Surface

Map at least:

- productive files in target source directories;
- core components/classes/functions by architecture style;
- data model/contracts/integration boundaries when applicable;
- existing unit/integration/e2e tests;
- setup fixtures and mocks.

### 3. Build Domain Taxonomy

Group files into business/technical domains and assign priority:

- `P0`: security/data-integrity/critical operations;
- `P1`: core CRUD and daily operations;
- `P2`: automation/support/regression breadth.

### 4. Define Required Test Types

For each domain, classify planned evidence:

- unit
- integration
- e2e
- contract/integration
- regression
- security/permission/isolation

### 5. Define Execution Gates

Every numbered domain plan (`01..NN`) must include:

- per-file coverage gate for changed listed files:
  - statements `85%+`
  - functions `85%+`
  - lines `85%+`
  - branches `65%+`
- mandatory happy/sad/edge scenario coverage.
- checklist rules for unit/integration/e2e.

### 6. File-State Reporting Standard

Require a file-state report listing all planned code files in each domain plan.

Recommended columns:

- code file;
- area/recorte;
- scope status;
- test evidence by type;
- per-file coverage;
- happy/sad/edge evidence;
- final state;
- next action.

### 7. Quality Validation

Before closing planning:

- verify every productive file is mapped or explicitly out-of-scope;
- verify P0 domains are scheduled first;
- verify acceptance criteria are testable;
- verify harness compatibility for new vs legacy sections.

## Completion Response

Return:

1. created/updated planning files;
2. final domain order;
3. quality gates applied;
4. known risks and next decisions.
