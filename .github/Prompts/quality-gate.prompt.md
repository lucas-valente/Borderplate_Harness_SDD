---
description: "Run a unified delivery quality gate: build, architecture checks, and documentation coherence checks before completion."
mode: "agent"
tools: [read, search, execute, todo]
---

# Quality Gate

Run quality gate for: **${{context}}**

When the change touches auth, permissions, data boundaries, payments, uploads, webhooks, secrets, or HTTP security configuration, treat the security phase below as the official SecOps path.

## Gate Checklist

### Step 1 — Build Validation (Mandatory)
- Run build command for each app in the project (e.g., `npm run build`)
- If any build fails, stop and return blocking errors

### Step 2 — Security Audit
- For sensitive changes, execute this step with the same rigor required by `.github/Agents/security-review.agent.md`
- Use `.github/Prompts/secops-audit.prompt.md` as the security review procedure
- Run SAST scanner on changed files (Semgrep recommended: `semgrep --config=p/owasp-top-ten`)
- Block on any `HIGH` or `CRITICAL` findings
- `MEDIUM` findings must be listed but do not block
- Run dependency vulnerability audit (`npm audit` or equivalent)
- Block on `HIGH` or `CRITICAL` dependency vulnerabilities
- For sensitive flows, confirm code-level controls:
  - data scoping
  - auth guards / RBAC
  - boundary validation
  - secrets / token safety
  - headers, CORS, rate limiting, upload protection

### Step 3 — Implementation Quality Checks
- Confirm data scoping where applicable
- Confirm input validation for input boundaries
- Confirm auth guards/roles where route protection is required
- Confirm error messages are clear for user-facing failures

### Step 4 — Planning Coherence Checks
- Confirm feature aligns with spec in `Documentacao_[NomeDoProjeto]/04-planejamento-do-produto/03-especificacoes/`
- If non-trivial, confirm workstream exists/updated in `Documentacao_[NomeDoProjeto]/06-planejamento-tecnico-do-desenvolvimento/02-workstreams-tecnicos/`
- Confirm workstream `## Coverage Matrix` covers all `REQ-*` from spec
- If change touched scope/priority/risk/dependency, confirm `04` updates were made

### Step 5 — Documentation Coverage Check
- If user-facing behavior changed, confirm updates in:
  - `Documentacao_[NomeDoProjeto]/Manual/`
  - `Documentacao_[NomeDoProjeto]/03-documentacao-oficial-do-sistema/`
- If implementation design/contracts/validation/rollout changed, confirm updates in `06`

### Step 6 — Gate Result
- Return `QUALITY GATE: PASS` only when all mandatory checks pass
- Otherwise return `QUALITY GATE: FAIL` with objective blockers and exact file paths
- Include SAST findings summary (HIGH/CRITICAL count)
- Include dependency audit summary (HIGH/CRITICAL count)
- If the change was security-sensitive, include: `SECURITY AUDIT: PASS | PASS WITH RISKS | FAIL`

## Rules
- Never bypass build validation
- Never mark PASS with unresolved HIGH/CRITICAL findings
- Never mark PASS with unresolved blockers
- Never close a sensitive delivery without completing the SecOps review path
