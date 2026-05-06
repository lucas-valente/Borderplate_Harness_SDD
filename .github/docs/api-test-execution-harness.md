# Domain Test Execution Harness (Generic)

## Purpose

Define canonical parsing and execution rules for domain test planning, implementation, and audit.

Use this harness to keep prompts, agents, and instructions aligned even when domain plan formats evolve.

## Canonical Sources

Use these sources in order when available:

1. domain test index (`00-indice.md`)
2. technical inventory (`00-inventario-tecnico-*.md`)
3. parallel execution plan (`00-plano-execucao-paralela-*.md`)
4. integration execution plan (`00-plano-integracao-*.md`)
5. Coverage control snapshot (`arquivos-para-coverage-control.md`)
6. Numbered domain plans (`01..NN`)

## Domain Plan Parsing

A modern domain plan should expose at least:

- domain snapshot/status;
- mapped productive files;
- expected unit/integration/e2e scope;
- acceptance checklist;
- current gaps;
- session execution report.

### Planned Files Source

Primary source should be a mapped files table (for example `Arquivos produtivos mapeados do dominio`).

Fallback for legacy plans can be a simpler list such as `Arquivos de codigo a testar`.

## Compatibility Rules

If both modern and legacy sections coexist, do not fail parsing.

- Prefer modern mapped-file sections for planned scope.
- Keep legacy sections synchronized when updates are required.

## Mandatory Gates

Always apply:

- per-file coverage gate (`85/65` rule from instructions);
- happy/sad/edge scenario evidence for changed listed files;
- checklist validation based on real command evidence;
- explicit file-state report for all planned files.

## File-State Status Values

Allowed status values:

- `PASS`
- `PASS CURRENT SCOPE`
- `PARTIAL`
- `PENDING`
- `N/A`
- `EXCEPTION`
- `BLOCKED`

## Session Write-Back

When writing back in a domain plan:

1. update the session report section;
2. keep mapped file status aligned with latest evidence;
3. reflect unresolved gaps with next action;
4. avoid claiming whole-domain completion when only a recorte passed.

## Execution Boundaries

- Prefer targeted commands over full-suite commands.
- Do not run full unit/integration/e2e suites unless explicitly authorized.
- Use build commands only when needed for test setup integrity, not as a replacement for test evidence.
