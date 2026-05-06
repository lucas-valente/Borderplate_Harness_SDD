---
description: "Audit domain test delivery quality: planned files, file-state report, checklist evidence, per-file coverage gates, and acceptance status."
agent: "api-test-audit"
argument-hint: "Caminho do plano de dominio 01..NN ou ALL para dominios tocados na sessao"
tools: [read, search, execute, agent, todo]
---

# Domain Test Quality Audit

Audit domain test delivery for: **${{audit_scope}}**

This is an audit prompt. Do not implement tests or product code here.

Harness reference: `.github/docs/api-test-execution-harness.md`.

## Scope Modes

1. Domain mode: one selected plan (`01..NN`).
2. Session-wide mode: `ALL` for domains touched in current session.

## Audit Pipeline

### Step 1 - Resolve Scope

- Identify changed production/test files in current session.
- Identify impacted domain plan(s).
- Reject broad full-suite scope unless user explicitly requested.

### Step 2 - Extract Obligations

From each selected domain plan, extract:

- planned files;
- required test types (unit/integration/e2e/contract/security);
- acceptance checklist;
- current gaps;
- completion claim type (whole-domain vs recorte).

### Step 3 - Validate Evidence

- Verify test files and targeted command outcomes.
- Verify file-state report contains all planned files.
- Verify per-file coverage for changed listed files.
- Verify happy/sad/edge scenario evidence.
- Verify checklist status matches command evidence.

### Step 4 - Apply Gates

Fail if any of these occur:

- missing planned files in report;
- per-file coverage below `85/85/85/65`;
- missing happy/sad/edge evidence;
- required checklist item unchecked or invalid;
- unresolved in-scope blocker.

### Step 5 - Remediation Loop

- If blockers are actionable in scope, delegate back to `@api-test` with remediation payload.
- Re-audit updated evidence.
- Repeat up to 3 iterations in same run.

### Step 6 - Verdict

Return one verdict:

- `DOMAIN TEST QUALITY AUDIT: PASS`
- `DOMAIN TEST QUALITY AUDIT: PASS WITH GAPS`
- `DOMAIN TEST QUALITY AUDIT: FAIL`

## Output Format

```text
DOMAIN TEST QUALITY AUDIT: PASS | PASS WITH GAPS | FAIL
Scope: <domain|ALL>

Domain Summary:
- <domain>: PASS | PASS WITH GAPS | FAIL

Findings:
1. <severity> - <finding> - <file>

Required Corrective Actions:
1. <action>
```

## Rules

- Audit only session scope by default.
- Keep findings objective and traceable.
- Never approve a recorte as whole-domain complete.
- Do not run full unit/integration/e2e suites unless explicitly authorized.
