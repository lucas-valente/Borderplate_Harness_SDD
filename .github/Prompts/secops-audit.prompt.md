---
description: "Run a full SecOps security audit: SAST, dependency scan, code-level control review, and documentation coherence. Returns PASS/FAIL with prioritized remediation."
mode: "agent"
tools: [read, search, execute, todo]
---

# SecOps Audit

Run security audit for: **${{context}}**

## Scope Resolution

- If `${{context}}` lists specific files or a feature name, audit only those files (scoped audit)
- If `${{context}}` is `full` or empty, audit all project source directories

## Audit Pipeline

### Step 1 — SAST (Static Analysis)
- Resolve Semgrep executable (prefer `semgrep` from PATH)
- Run on target files:
  ```bash
  semgrep --config=p/owasp-top-ten --config=p/nodejs --config=p/typescript --config=p/react <target_files_or_dirs>
  ```
- Install if needed: `pip install semgrep`
- Classify findings by severity: `CRITICAL`, `HIGH`, `MEDIUM`, `LOW`
- `CRITICAL`/`HIGH` block PASS

### Step 2 — Dependency Scan (SCA)
- Run `npm audit --audit-level=moderate` (or equivalent for your package manager)
- `CRITICAL`/`HIGH` CVEs block PASS
- `MEDIUM`/`LOW` listed but do not block

### Step 3 — Code-Level Security Controls
Review the following in scoped files:

#### 3a — Data Isolation
- Every database query must scope by user/organization/tenant as appropriate
- No cross-boundary data leaks in services, controllers, or frontend state

#### 3b — Auth & Authorization
- Protected routes have proper guards/middleware
- No unauthenticated access to sensitive endpoints
- Token handling follows secure patterns (httpOnly cookies, no localStorage for refresh tokens)

#### 3c — Input Validation
- All user-facing endpoints validate input (Zod, class-validator, DTOs, or equivalent)
- No raw unvalidated body/query usage
- File uploads have type/size restrictions

#### 3d — Secrets & Crypto
- No hardcoded secrets, API keys, or tokens in source code
- Environment variables used for all sensitive config
- Passwords hashed with proper algorithm and cost factor
- JWT secrets are strong and not shared across environments

#### 3e — HTTP Hardening
- Security headers enabled (Helmet or equivalent)
- CORS configured with explicit origins (no `*` in production)
- Rate limiting on auth endpoints

#### 3f — Logging & Audit Trail
- Sensitive data (passwords, tokens, PII) never logged
- Auth events logged with user/tenant context
- No `console.log` with sensitive payloads in production code

### Step 4 — Documentation Coherence
- Read security-related technical docs in `Documentacao_[NomeDoProjeto]/01-documentacao-tecnica/`
- Check if implemented security controls match documented controls
- Flag any divergence between code and documentation

### Step 5 — Risk Assessment Against Plan
- Read active release and governance risks
- If scoped to a feature, read its spec
- Compare planned security requirements vs actual implementation

### Step 6 — Final Verdict

Return:
- `SECURITY AUDIT: PASS`
- `SECURITY AUDIT: PASS WITH RISKS`
- `SECURITY AUDIT: FAIL`

Always include:
1. SAST summary (CRITICAL / HIGH / MEDIUM / LOW)
2. Dependency scan summary
3. Code-level controls verdict per dimension
4. Documentation coherence verdict
5. Prioritized corrective actions with file references
