# Central do Workspace — [NomeDoProjeto]

> Substitua `[NomeDoProjeto]` pelo nome real do projeto em todos os arquivos.

**Boilerplate baseado em:** Borderplate Harness + SDD v1.0

## Objetivo

[Descreva o objetivo principal do projeto aqui]

## O que é este workspace

Este workspace é a camada oficial de documentação, planejamento, governança e execução operacional do projeto **[NomeDoProjeto]**.

## Estrutura

```
Documentacao_[NomeDoProjeto]/
├── 01-documentacao-tecnica/        — Arquitetura, módulos, integrações, regras de sistema
├── 02-documentacao-executiva/      — Visão executiva, roadmap, posicionamento
├── 03-documentacao-oficial-do-sistema/ — Documentação funcional consolidada
├── 04-planejamento-do-produto/     — Release, backlog, specs, governança
├── 05-execucao-diaria-do-desenvolvimento/ — Nota diária, kanban, planos operacionais
├── 06-planejamento-tecnico-do-desenvolvimento/ — Workstreams, decisões técnicas, riscos
└── Manual/                         — Manual do usuário final
```

## Fontes de Verdade por Camada

| Atividade | Fonte principal |
|-----------|----------------|
| O que entra em escopo | `04-planejamento-do-produto/06-releases/01-ativas/` |
| Priorização e roadmap | `04-planejamento-do-produto/Planner.md` |
| Especificações funcionais | `04-planejamento-do-produto/03-especificacoes/` |
| Governança (riscos, ADRs) | `04-planejamento-do-produto/07-governanca/` |
| Desenho técnico | `06-planejamento-tecnico-do-desenvolvimento/` |
| Execução do dia/semana | `05-execucao-diaria-do-desenvolvimento/` |

## Padrão SDD (Sistema de Documentação Descritiva)

- Spec → `## Requisitos` com `REQ-001`, `REQ-002`...
- Workstream → `## Coverage Matrix` mapeando REQ → artefato técnico
- Auditoria → `/audit-against-plan` verifica toda a cadeia

## Regra Central

Um requisito sem REQ-ID rastreável pode ser esquecido.
Um workstream sem Coverage Matrix pode divergir silenciosamente.
Uma entrega sem auditoria não tem garantia de aderência.

## Comecar

### 1. Primeira Release

1. Defina a release ativa em `04-planejamento-do-produto/06-releases/01-ativas/`
2. Use o template: `04-planejamento-do-produto/06-releases/template-release.md`
3. Atualize o `04-planejamento-do-produto/Planner.md`

### 2. Primeira Feature

1. Crie a spec em `04-planejamento-do-produto/03-especificacoes/`
2. Use o template: `04-planejamento-do-produto/02-templates/template-spec-sdd.md`
3. Preencha `## Requisitos` com `REQ-001`, `REQ-002`, etc.

### 3. Primeiro Workstream

1. Crie o workstream em `06-planejamento-tecnico-do-desenvolvimento/02-workstreams-tecnicos/`
2. Use o template de plano técnico em `.github/docs/plan-template.md`
3. Adicione `## Coverage Matrix` ligando cada `REQ-*`

### 4. Governanca

Abra `04-planejamento-do-produto/07-governanca/` e registre:

- Dependencias iniciais
- Riscos tecnicos
- Decisoes arquiteturais

## Checklist de Setup

- [ ] Release ativa criada
- [ ] Planner personalizado com projeto
- [ ] Primeira spec com `## Requisitos`
- [ ] Primeiro workstream com `## Coverage Matrix`
- [ ] Governanca inicial registrada
- [ ] `.github/copilot-instructions.md` adaptado

---

**Última atualização:** [DATA]
**Owner:** [RESPONSAVEL]

**Inicializado em:** [DATA]
**Time:** [TIME]
**Contact:** [EMAIL]
