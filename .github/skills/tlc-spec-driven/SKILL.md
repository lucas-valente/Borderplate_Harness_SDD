---
name: tlc-spec-driven
description: "Spec-driven planning and execution for this boilerplate: product planning in 04, technical planning in 06, and operational execution in 05."
license: CC-BY-4.0
metadata:
  author: Borderplate Harness SDD
  version: 1.0.0
---

# TLC Spec-Driven (Generic)

Adaptive pipeline for planning and execution driven by specification.

## Pipeline

```text
SPECIFY -> DESIGN -> TASKS -> EXECUTE
```

## Layer Mapping

- `SPECIFY` -> `Documentacao_[NomeDoProjeto]/04-planejamento-do-produto/`
- `DESIGN` + `TASKS` -> `Documentacao_[NomeDoProjeto]/06-planejamento-tecnico-do-desenvolvimento/`
- `EXECUTE` status reflection -> `Documentacao_[NomeDoProjeto]/05-execucao-diaria-do-desenvolvimento/`

## Depth Rule

Choose depth by complexity:

- small: quick mode
- medium: spec + execute
- large: spec + design + tasks + execute
- complex/high risk: spec + discuss + design + tasks + validate

## Source Of Truth Order

1. active release
2. planner
3. related spec
4. governance
5. technical workstream/design
6. operational execution artifacts

## Coherence Rules

1. do not create parallel source of truth outside official folders;
2. do not use `05` as replacement for release/planner/spec;
3. do not use `06` as replacement for functional spec;
4. if business scope changes, sync `release -> planner -> spec -> governance`;
5. if technical design changes, sync `06` and reflect execution impacts in `05`.

## Integration With Other Skills

- use `doc-manager` for doc-heavy sessions;
- use `technical-planning-manager` for workstream-level decomposition;
- use `workspace-documentation-manager` for multi-layer sync.

## Verification Chain

```text
1. Codebase reality
2. Project documentation
3. Contracts/matrices
4. Official external docs
5. Mark as uncertain when still unverified
```
