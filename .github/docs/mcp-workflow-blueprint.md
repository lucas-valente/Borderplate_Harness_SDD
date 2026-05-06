# MCP Workflow Blueprint

## Objetivo

Integrar MCP servers nos workflows de planejamento, implementação, QA e documentação para reduzir coleta manual de contexto e aumentar consistência.

## Roadmap de Prioridade

### P0 — Usar e formalizar imediatamente

- **Chrome DevTools MCP**
  - Usar no Passo 5 de `/feature-pipeline` (QA com browser)
  - Usar em `/quality-gate` para verificação com browser quando aplicável
  - Checks mínimos: console errors, network failures, happy path evidence

### P1 — Integrações de alto impacto

- **GitHub MCP** (issues / comments / projects)
  - Extrair requisitos direto de issues + comentários durante planejamento
  - Linkar spec/workstream/PR em um fluxo único

- **Database read-only MCP** (ex: Postgres, MySQL, etc.)
  - Validar pressupostos de dados durante planejamento e QA
  - Suportar investigações sem scripts ad-hoc

### P2 — Integrações de médio impacto

- **Docs MCP** (wiki interna, se disponível)
  - Extrair políticas e contratos externos durante planejamento

- **Observabilidade MCP** (logs/métricas, se disponível)
  - Fechar loop de feedback de produção em atualizações de planejamento e decisões de risco

## Mapping por Prompt

| Prompt | MCP Recomendado |
|--------|----------------|
| `/technical-planning` | GitHub MCP (issue context) |
| `/feature-pipeline` | Chrome DevTools MCP (QA step) |
| `/api-test-pipeline` | Database MCP (validacao de dados), GitHub MCP (contexto de mudancas) |
| `/api-test-quality-audit` | Database MCP (reconciliacao de evidencias), GitHub MCP (rastreio de arquivos alterados) |
| `/quality-gate` | Chrome DevTools MCP (opcional) |
| `/documentation-sync` | - |
| `/audit-against-plan` | Database MCP (validação de dados) |
| `/secops-audit` | - |

## Regras de Governança

- MCP é aditivo — nunca substitui a fonte de verdade em `Documentacao_[NomeDoProjeto]/`
- Qualquer decisão derivada de MCP **deve** ser refletida nos artefatos documentais oficiais
- Manter uso de MCP auditável em devlogs / delivery summaries

## Critérios de Sucesso

- Menos retrabalho pós-implementação
- Ciclo de planejamento mais rápido
- Menos docs faltando por feature entregue
- Menos regressões de QA após merge

## Personalização

Após clonar o boilerplate, ajuste este arquivo com:
- MCP servers disponíveis no projeto
- Priorização específica do stack (ex: PostgreSQL, MongoDB, Azure DevOps, Linear, etc.)
- Critérios de verificação específicos do domínio
