---
description: "Use when changing sensitive code paths such as auth, permissions, data boundaries, payments, uploads, webhooks, secrets, or HTTP security configuration. Enforces SecOps review before completion."
applyTo: "**/src/**"
---

# SecOps Review Guardrail

When working on security-sensitive code, you MUST activate the SecOps audit workflow before considering the task complete.

## Trigger Conditions

Apply this instruction whenever the change touches any of the following:

- authentication, sessions, JWT, password, reset password, login
- authorization, guards, roles, RBAC, permissions
- data isolation, user/tenant scoping, cross-boundary access
- payments, financial operations, checkout, webhooks
- file upload, storage, import/export, external integrations
- secrets, tokens, API keys, encryption, hashing
- CORS, headers, rate limiting, cookies, CSP, security middleware

## Mandatory Actions

1. Read `.github/skills/secops-audit-manager/SKILL.md`
2. Apply `.github/Prompts/secops-audit.prompt.md` when the change is non-trivial or touches a protected flow
3. Review the relevant technical docs before concluding:
   - `Documentacao_[NomeDoProjeto]/01-documentacao-tecnica/` (auth/permissions and quality/observability docs)
   - relevant spec/workstream when the change belongs to a planned feature
4. Verify, at minimum:
   - data isolation is preserved (user/tenant scoping)
   - protected routes have proper guards/middleware
   - inputs are validated at boundaries
   - secrets are not exposed in source code or logs
   - HTTP security settings are not weakened unintentionally
5. Before completion, run the appropriate validation path:
   - `/secops-audit <context>` for a focused or full security audit
   - `/quality-gate <context>` when the change is part of feature delivery

## Blocking Rules

- Never treat a sensitive change as complete only because the build passed
- Never approve a change with unresolved `CRITICAL` or `HIGH` security findings
- Never approve a protected flow without checking auth, validation, and data boundaries
- Never leave a code/doc divergence in security behavior unexplained

## Scope Discipline

- Use the SecOps audit workflow for security-sensitive work
- Do not run the full audit for trivial text-only or non-technical changes
- Keep the final result objective: `PASS`, `PASS WITH RISKS`, or `FAIL`
