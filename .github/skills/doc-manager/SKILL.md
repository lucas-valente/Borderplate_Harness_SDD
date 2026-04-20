---
name: doc-manager
description: "Use when creating, editing, consulting, or maintaining documentation, planning, specs, governance, releases, daily execution, or manuals. Actions: create spec, update release, register ADR, update planner, create daily note, update kanban, maintain governance, consult documentation, answer questions about product state. Triggers: documentacao, spec, especificacao, release, ADR, decisao, planner, nota diaria, kanban, governanca, manual, mapa de riscos, dependencias, planejamento, execucao diaria, revisao semanal, plano operacional."
---

# Doc Manager

Skill para criar, editar, consultar e manter toda documentação do projeto sem perder sincronização entre camadas.

## Responsabilidades

- ✅ Criar e revisar specs com SDD completa
- ✅ Atualizar release ativa
- ✅ Registrar decisões arquiteturais (ADRs)
- ✅ Manter Planner sincronizado
- ✅ Criar daily notes e kanban
- ✅ Manter governança (riscos, dependências)
- ✅ Consultar estado do produto
- ✅ Responder perguntas sobre planejamento e execução
- ✅ Garantir coerência entre camadas

## Quando Usar

### Criar

- [ ] Primeira spec de uma feature
- [ ] Primeira release do projeto
- [ ] ADR para decisão arquitetural importante
- [ ] Daily note para rastreamento operacional
- [ ] Template para novo tipo de artefato

### Editar

- [ ] Spec existente com mudança de requisito
- [ ] Release ativa com mudança de escopo
- [ ] Planner com mudança de prioridade
- [ ] Governança com novo risco/dependência
- [ ] Daily note ou kanban com progresso

### Consultar

- [ ] "Qual o status atual da feature X?"
- [ ] "Quais os REQ-* dessa spec?"
- [ ] "Qual foi a decisão sobre Y?"
- [ ] "Qual o risco de Z?"
- [ ] "Quando entra a feature W?"

### Responder

- [ ] Questões sobre fonte de verdade
- [ ] Questões sobre dependências
- [ ] Questões sobre status de execução
- [ ] Questões sobre decisões fechadas

---

## Workflow Doc Manager

### Quando criar spec nova

1. Use template: `Documentacao_[NomeDoProjeto]/04-planejamento-do-produto/02-templates/template-spec-sdd.md`
2. Preencha `## Requisitos` com `REQ-001`, `REQ-002`, etc.
3. Atualize frontmatter com `requisitos: [REQ-001, ...]`
4. Registre no Planner: adicione link na tabela de features
5. Registre em governança se houver novo risco/dependência

**Validação**:
- [ ] Todos os `REQ-*` têm critério mínimo?
- [ ] Frontmatter `requisitos:` lista todos?
- [ ] Spec aparece no Planner?

### Quando criar workstream novo

1. Use template: `Documentacao_[NomeDoProjeto]/06-planejamento-tecnico-do-desenvolvimento/02-workstreams-tecnicos/template-workstream-sdd.md`
2. Link spec de origem
3. Preencha `## Coverage Matrix` com todos os `REQ-*`
4. Nenhum `REQ-*` pode estar omitido (PENDENTE é ok)

**Validação**:
- [ ] Coverage Matrix presente?
- [ ] Todos os REQ-* cobertos?
- [ ] Nenhum MISSING?

### Quando fechar uma entrega

1. Update `Documentacao_[NomeDoProjeto]/05-execucao-diaria-do-desenvolvimento/` com REQ-* linkage
2. Registre em daily note: "cobre REQ-001, REQ-002, REQ-003"
3. Se mudar status de execução, update release e planner
4. Se regressão ou blocker, registre em governança

**Validação**:
- [ ] Daily note registrada?
- [ ] REQ-* linkados?
- [ ] Riscos/dependências atualizadas?

### Quando registrar decisão

1. Crie arquivo: `Documentacao_[NomeDoProjeto]/04-planejamento-do-produto/07-governanca/decisoes/ADR-NNN-titulo.md`
2. Siga formato: contexto → decisão → rationale → consequências
3. Coloque link em governança / mapa de dependências
4. Se afeta release, atualize spec/planner

**Validação**:
- [ ] ADR referencia spec ou release?
- [ ] Rationale é clara?
- [ ] Consequências mapeadas?

---

## Perguntas Frequentes

### "Qual é a fonte de verdade para X?"

Consulte a seção "Fontes de Verdade" no skill `workspace-documentation-manager`.

**Ordem de consulta**:
1. Release ativa (se existe feature nela)
2. Planner (para prioridade e status)
3. Spec (para requisitos funcionales)
4. Governança (para riscos/dependências)
5. Workstream (para design técnico)
6. Daily notes (para status operacional)

### "Como sei se uma spec está pronta?"

Checklist de pronto:
- [ ] Seção `## Requisitos` preenchida com `REQ-001+`
- [ ] Todos os `REQ-*` têm critério mínimo
- [ ] Frontmatter `requisitos:` atualizado
- [ ] Spec aparece no Planner
- [ ] Sem dependencies blocker em Gov

### "Como sei se um workstream está pronto?"

Checklist de pronto:
- [ ] Coverage Matrix presente
- [ ] Todos os `REQ-*` da spec aparecem na matrix
- [ ] Nenhum `REQ-*` omitido (PENDENTE é ok, MISSING não)
- [ ] Contratos definidos (payloads, endpoints, etc.)
- [ ] Decomposição técnica clara

### "Como faço daily standup com essa estrutura?"

1. Leia última daily note
2. Identifique REQ-* em progresso
3. Registre done items com REQ-* linkage
4. Registre blockers em governança se houver
5. Atualize planner se prioridade mudou

---

## Formato Rápido

### Spec mínima

```markdown
---
requisitos: [REQ-001, REQ-002]
---

## Requisitos

| ID | Tipo | Descrição | Critério mínimo |
|----|------|-----------|-----------------|
| REQ-001 | funcional | O que fazer | Como validar |
```

### Workstream mínimo

```markdown
## Coverage Matrix

| REQ-ID | Descrição | Cobertura | Artefato |
|--------|-----------|-----------|----------|
| REQ-001 | Descrição | Endpoint POST | src/controller.ts |
```

### Daily note mínima

```markdown
- [x] Feature X — REQ-001, REQ-002
- [ ] Feature Y — REQ-003 (60% done)
```

---

## Convenções Rápidas

| Item | Padrão |
|------|--------|
| Spec | `NN-feature-nome-versao.md` |
| Workstream | `ws-nome-versao.md` |
| Release | `release-X.Y.Z-nome.md` |
| REQ-ID | `REQ-001`, `REQ-002` (sequencial por spec) |
| ADR | `ADR-NNN-titulo.md` |
| Daily note | `YYYY-MM-DD.md` em `04-daily-notes/` |

---

## Guardrails

❌ **NUNCA**:
- Deixar spec sem `## Requisitos` formal
- Deixar workstream sem `## Coverage Matrix`
- Omitir `REQ-*` de cobertura (PENDENTE é ok)
- Atualizar apenas um espelho quando mudança afeta camadas
- Criar dependência ou risco sem registrar em Gov

✅ **SEMPRE**:
- Começar pela release quando mudar escopo
- Sincronizar Planner quando spec entra/sai
- Linkar daily notes a REQ-* quando entregar
- Validar cobertura antes de marcar workstream ready
- Manter README/guias sincronizados com realidade

---

**Última atualização**: 2026-04-20
