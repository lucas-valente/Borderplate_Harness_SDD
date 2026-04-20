---
name: Release - [VERSÃO]
versao: "0.0.1"
data-inicio: "2026-04-20"
data-target-prd: "2026-05-01"
status: "planejada"
---

# Release 0.0.1 — [NOME DESCRITIVO]

## Objetivo

[Descreva a meta principal desta release em 1-2 frases]

## Escopo Aprovado

### P1 — Crítico (deve sair)

- [ ] Feature 1
- [ ] Feature 2
- [ ] Feature 3

### P2 — Alto (entra se ritmo estiver saudável)

- [ ] Feature 4
- [ ] Feature 5

### P3 — Médio (last mile, se sobrar slot)

- [ ] Feature 6
- [ ] Feature 7

### Fora de Escopo (explicitamente descartado)

- ❌ Coisa que poderia entrar em outra release
- ❌ Outra coisa que fica para depois

## Dependências Críticas

| Dependência | Impacto | Status |
|-------------|--------|--------|
| [Sistema externo A] | Blocker se não estiver pronto | 🟡 Em progresso |
| [Integração B] | Blocker se não estiver pronto | 🟢 Pronto |
| [Dados migrados C] | Blocker se não for seedado | 🟡 Em progresso |

## Timeline

| Milestone | Data | Responsável |
|-----------|------|-------------|
| Specs finalizadas | 2026-04-22 | [NOME] |
| Workstreams aprovados | 2026-04-23 | [NOME] |
| Implementação completa | 2026-04-28 | [TIME] |
| QA + Smoke tests | 2026-04-29 | [QA] |
| PRD | 2026-05-01 | [DEVOPS] |

## Governança

**Decisões fechadas**:
- [Decisão A]: Por quê?
- [Decisão B]: Por quê?

**Riscos registrados**:
- Veja `04-planejamento-do-produto/07-governanca/01-mapa-de-dependencias-e-riscos.md`

**ADRs**(Architecture Decision Records):
- Veja `04-planejamento-do-produto/07-governanca/decisoes/`

## Specs Ligadas

| Spec | Prioridade | Status |
|------|-----------|--------|
| [Spec 1](../../03-especificacoes/01-feature-x.md) | P1 | 🟡 Rascunho |
| [Spec 2](../../03-especificacoes/02-feature-y.md) | P1 | 🟢 Aprovada |

## Métricas de Sucesso

- [ ] Todas as P1 entregues com cobertura SDD 100%
- [ ] Coverage Matrix sem MISSING ou PENDING
- [ ] Testes de regressão passam
- [ ] Sem regressions em produção nos primeiros 7 dias

## Comunicação

- **Product Owner**: [NOME]
- **Tech Lead**: [NOME]
- **QA Lead**: [NOME]
- **DevOps**: [NOME]

---

**Criada em**: 2026-04-20  
**Última atualização**: 2026-04-20
