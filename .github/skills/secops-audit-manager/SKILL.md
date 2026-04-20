---
name: secops-audit-manager
description: "Use when performing end-to-end security audits. Actions: run SAST and dependency scans, inspect auth/permissions/data isolation, verify crypto/secrets/config hardening, check security documentation coherence, and return PASS/FAIL with prioritized remediation. Triggers: secops, segurança, security audit, auditoria de segurança, hardening, pentest prep, vulnerabilidade, OWASP, semgrep, npm audit, compliance, risco de segurança."
---

# SecOps Audit Manager

Skill para auditoria de segurança ponta a ponta em código, configuração e coerência técnica/documental.

## Quando Usar

### Obrigatório

- Antes de fechar release importante ou Go-Live
- Após feature crítica de autenticação, permissão, pagamento, dados sensíveis, upload, webhook
- Quando houver incidente de segurança ou suspeita de vulnerabilidade

### Recomendado

- Antes de PR de módulo sensível
- Em revisões semanais de risco técnico
- Antes de auditoria externa / pentest

### Não Usar

- Mudanças triviais de texto sem impacto técnico

## Fontes de Verdade (ordem)

1. Release ativa em `Documentacao_[NomeDoProjeto]/04-planejamento-do-produto/06-releases/01-ativas/`
2. Specs em `Documentacao_[NomeDoProjeto]/04-planejamento-do-produto/03-especificacoes/`
3. Governança em `Documentacao_[NomeDoProjeto]/04-planejamento-do-produto/07-governanca/`
4. Workstreams em `Documentacao_[NomeDoProjeto]/06-planejamento-tecnico-do-desenvolvimento/02-workstreams-tecnicos/`
5. Docs técnicas de auth/permissões em `Documentacao_[NomeDoProjeto]/01-documentacao-tecnica/`
6. Código fonte do projeto

## Pipeline de Auditoria SecOps

1. Definir escopo (`changed_files` ou full scan)
2. Rodar SAST (`semgrep --config=p/owasp-top-ten` ou equivalente)
3. Rodar dependência SCA (`npm audit` ou equivalente)
4. Revisar controles críticos no código:
   - isolamento de dados (user/tenant scoping)
   - auth guards e RBAC
   - validação de entrada (Zod, class-validator, DTOs, ou equivalente)
   - proteção de segredos e criptografia
   - rate-limit, headers, CORS, upload safety
5. Revisar aderência ao plano técnico e riscos em `04` e `06`
6. Emitir veredito com evidências rastreáveis

## Criticidades

- `CRITICAL`/`HIGH`: bloqueiam PASS
- `MEDIUM`: não bloqueiam, mas exigem plano de mitigação
- `LOW`: backlog com prioridade definida

## Critérios de FAIL

- Qualquer `CRITICAL` ou `HIGH` sem mitigação aprovada
- Falha de isolamento de dados (cross-user ou cross-tenant leak)
- Falha de autorização em fluxo protegido
- Exposição de segredo/chave/token em código ou log
- Divergência relevante entre implementação de segurança e plano técnico sem update documental

## Critérios de PASS

- Zero `CRITICAL/HIGH` em SAST e dependências
- Controles críticos confirmados
- Riscos residuais documentados com owner e prazo

## Formato de Saída

- `SECURITY AUDIT: PASS` | `SECURITY AUDIT: PASS WITH RISKS` | `SECURITY AUDIT: FAIL`
- Achados por severidade (CRITICAL / HIGH / MEDIUM / LOW)
- Controles críticos revisados (OK / FAIL / N/A)
- Coerência documental (OK / GAP / N/A)
- Ações corretivas priorizadas com referência de arquivo

## Personalização Por Projeto

Após clonar o boilerplate, adicione neste arquivo:
- Stack de segurança específica (ex: NestJS guards, Spring Security, etc.)
- Padrões de auditoria específicos do domínio (ex: PCI-DSS, LGPD, HIPAA)
- Ferramentas adicionais de scan específicas do projeto
