---
name: implementation-audit-manager
description: "Use when auditing implemented features against original planning artifacts (spec/workstream/release) after development. Actions: compare planned vs delivered scope, detect missing/divergent requirements, verify architecture/security/data consistency, and produce PASS/FAIL with corrective actions. Triggers: auditoria, audit, aderência ao plano, comparação plano vs implementação, gap analysis, pós-implementação, validação contra spec, validar entrega."
---

# Implementation Audit Manager

Skill para auditar se a implementação entregue está aderente ao plano original de produto e técnico.

## Quando Usar

### Obrigatório

- Após execução de `/feature-pipeline` em feature não trivial
- Antes de fechamento final de entrega quando houver dependências/riscos relevantes
- Quando houver suspeita de desvio entre o que foi planejado e o que foi entregue

### Recomendado

- Antes de abrir PR final
- Após correções pós-QA

### Não Usar

- Mudanças triviais de texto/label sem impacto funcional

## Fontes de Verdade (ordem)

1. Spec funcional em `Documentacao_[NomeDoProjeto]/04-planejamento-do-produto/03-especificacoes/`
2. Workstream técnico em `Documentacao_[NomeDoProjeto]/06-planejamento-tecnico-do-desenvolvimento/02-workstreams-tecnicos/`
3. Release ativa em `Documentacao_[NomeDoProjeto]/04-planejamento-do-produto/06-releases/01-ativas/`
4. Governança em `Documentacao_[NomeDoProjeto]/04-planejamento-do-produto/07-governanca/`
5. Evidência de implementação no código fonte do projeto

## Fluxo de Auditoria

1. Ler spec e extrair todos os `REQ-*` da tabela `## Requisitos`
   - Se spec não tiver tabela, inferir requisitos das seções funcionais e atribuir `REQ-T001...` temporários
2. Ler workstream e verificar `## Coverage Matrix`
   - Se workstream existe mas não tem Coverage Matrix → isso é um gap auditável
3. Mapear evidência de implementação por requisito
4. Classificar cada requisito: `OK`, `PARTIAL`, `MISSING`, `DIVERGENT`
5. Validar impacto técnico (isolamento de dados, validação, contratos, riscos)
6. Confirmar cobertura documental em `04`, `05`, `06`, `Manual`, `03-documentacao-oficial-do-sistema`
7. Emitir veredito final com plano de ação

## Critérios de Bloqueio (FAIL)

- Requisito crítico de fluxo principal classificado como `MISSING`
- `REQ-*` presente na spec mas ausente da `## Coverage Matrix` do workstream quando workstream existe
- Divergência de contrato/API sem atualização de plano técnico/documentação
- Falha estrutural de segurança/isolamento de dados em área impactada

## Critérios de Aprovação

- Todos os requisitos críticos em `OK`
- Desvios não críticos com ação corretiva clara podem resultar em `PASS WITH DEVIATIONS`
- Evidências rastreáveis por arquivo

## Evidência de Dados

Quando a conclusão depender de dados persistidos, usar MCP PostgreSQL (`mcp_postgres_query`) ou equivalente antes de fechar o parecer, se disponível.

## Formato de Saída

```
AUDIT RESULT: PASS | PASS WITH DEVIATIONS | FAIL

Coverage Matrix:
| REQ-ID | Tipo | Descrição | Status | Evidência |
|--------|------|-----------|--------|-----------|
| REQ-001 | ... | ... | OK | src/... |

Summary: X/Y OK, Z PARTIAL, W MISSING, V DIVERGENT

Findings:
1. [MISSING] REQ-003 — ...
2. [DIVERGENT] REQ-005 — ...

Corrective Actions:
1. ...
2. ...

Rerun Required: /feature-pipeline | /quality-gate | /documentation-sync
```
