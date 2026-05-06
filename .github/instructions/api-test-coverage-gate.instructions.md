---
description: "Use when implementing, reviewing, or completing domain-based automated tests. Enforces per-file coverage gates, scenario coverage, and mandatory file-state reporting."
applyTo: "api/**, API/**, backend/**, server/**, services/**, src/**, test/**, tests/**, .github/Prompts/api-test-pipeline.prompt.md, .github/Prompts/api-test-quality-audit.prompt.md, .github/Agents/api-test.agent.md, .github/Agents/api-test-audit.agent.md, .github/skills/api-test-planning-by-domain/**"
---

# Domain Test Coverage Gate

Apply this gate whenever the task is test implementation or audit by domain.

## Per-File Coverage Thresholds

Every changed code file listed in the selected domain plan must reach:

- statements: `85%+`
- functions: `85%+`
- lines: `85%+`
- branches: `65%+`

Global coverage passing is not enough.

## Mandatory Scenario Coverage

For every changed listed file, tests must include evidence for:

- happy path;
- sad path;
- edge case.

Do not close the task with superficial line execution only.

## Mandatory File-State Report

Every domain run must include a file-state report that lists all planned code files from the domain plan, not only changed files.

Recommended columns:

- code file;
- area/recorte;
- current-session scope (`CHANGED`, `DIRECTLY IMPACTED`, `PLANNED BUT NOT TOUCHED`, `N/A`, `EXCEPTION`);
- unit, integration, e2e, contract/API evidence;
- security/permission/isolation evidence when applicable;
- coverage (statements/branches/functions/lines);
- happy/sad/edge evidence;
- status (`PASS`, `PASS CURRENT SCOPE`, `PARTIAL`, `PENDING`, `N/A`, `EXCEPTION`, `BLOCKED`);
- next action.

## Checklist Gate

Before closing a domain, validate checklist evidence:

- unit checkbox only after passing unit command;
- integration checkbox only after passing integration command;
- e2e checkbox only after passing e2e command.

Unchecked required items block completion.

## Completion Rule

A domain can be declared complete only when:

- per-file coverage thresholds pass for all changed listed files;
- happy/sad/edge coverage exists for changed listed files;
- mandatory checklist evidence is valid;
- file-state report is complete and honest about whole-domain vs recorte status.

If in-scope blockers remain, return `FAIL` or `PASS WITH GAPS`, not `PASS`.
