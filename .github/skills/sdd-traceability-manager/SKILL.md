---
name: sdd-traceability-manager
description: "Use when creating or updating specs, workstreams, or audit artifacts. Enforces REQ-ID standard traceability: spec table → workstream coverage → audit matrix → kanban/daily-note linking. Triggers: criar spec, atualizar spec, novo requisito, rastreabilidade, req-id, cobertura de requisitos, audit matrix, SDD, spec driven, gaps de requisito, template de feature, workstream coverage."
---

# SDD Traceability Manager

Skill para garantir rastreabilidade formal de requisitos entre spec, workstream, execução diária e auditoria.

## Problema que resolve

O workflow de documentação tem rastreabilidade estrutural forte (artefatos se ligam entre si), mas sem IDs formais (`REQ-*`) não é possível produzir coverage matrices auditáveis.

## Quando Usar

### Obrigatório

- Ao criar ou revisar qualquer spec em `Documentacao_[NomeDoProjeto]/04-planejamento-do-produto/03-especificacoes/`
- Ao criar ou revisar qualquer workstream em `Documentacao_[NomeDoProjeto]/06-planejamento-tecnico-do-desenvolvimento/02-workstreams-tecnicos/`
- Antes de rodar `/audit-against-plan`

### Recomendado

- Ao fechar uma entrega e registrar no kanban ou nota diária
- Quando houver dúvida se todos os requisitos de uma spec foram cobertos pela implementação

### Não Usar

- Mudanças triviais (texto, label, typo) sem impacto em requisito funcional
- Atualizações de doc executiva ou roadmap sem spec associada

---

## Fontes de Verdade

| Camada | Arquivo |
|--------|---------|
| Template de spec | `Documentacao_[NomeDoProjeto]/04-planejamento-do-produto/02-templates/template-spec-sdd.md` |
| Specs ativas | `Documentacao_[NomeDoProjeto]/04-planejamento-do-produto/03-especificacoes/` |
| Workstreams técnicos | `Documentacao_[NomeDoProjeto]/06-planejamento-tecnico-do-desenvolvimento/02-workstreams-tecnicos/` |
| Audit prompt | `.github/Prompts/audit-against-plan.prompt.md` (se disponível) |

---

## Padrão REQ-ID

```
REQ-NNN   (3 dígitos, sequencial por spec, começa em 001)
```

### Tipos aceitos

| Tipo | Quando usar |
|------|-------------|
| `funcional` | Comportamento visível pelo usuário |
| `técnico` | Restrição ou decisão de implementação |
| `segurança` | Controle de acesso, validação |
| `dados` | Persistência, modelo, migração |
| `ui` | Layout, componente, fluxo de navegação |

### Regra de numeração

- IDs são sequenciais **por spec** — cada spec começa em `REQ-001`
- IDs nunca são reaproveitados ou renumerados após publicação da spec
- IDs temporários (`REQ-T001`, `REQ-T002`...) são válidos apenas em sessões de auditoria em specs legadas

---

## Pipeline de Traceabilidade

### Etapa 1 — Spec (camada `04`)

Ao criar ou revisar uma spec, preencha a seção `## Requisitos`:

```markdown
## Requisitos

| ID | Tipo | Descrição | Critério mínimo |
|----|------|-----------|-----------------|
| REQ-001 | funcional | <o que o sistema deve fazer> | <como validar que está pronto> |
| REQ-002 | segurança | <restrição de acesso ou validação> | <checklist mínimo> |
```

Regras:
- Toda regra de negócio, caso de uso e critério de aceite deve ter ao menos um `REQ-*` associado
- Não deixar `REQ-*` sem critério mínimo preenchido
- Atualizar o campo `requisitos:` no frontmatter da spec com a lista de IDs: `requisitos: [REQ-001, REQ-002]`

---

### Etapa 2 — Workstream Técnico (camada `06`)

Ao criar ou revisar um workstream, adicione a **Coverage Matrix** após a seção de origem:

```markdown
## Coverage Matrix

| REQ-ID | Descrição resumida | Cobertura técnica | Artefato |
|--------|--------------------|-------------------|---------|
| REQ-001 | <descrição> | Endpoint POST /recurso, guard X | `src/module/controller.ts` |
| REQ-002 | <descrição> | Validação DTO | `src/module/dto.ts` |
```

Regras:
- Todo `REQ-*` da spec deve aparecer na matrix do workstream
- Se um `REQ-*` não tiver cobertura técnica definida, marcar como `PENDENTE` — não omitir
- A coluna `Artefato` deve referenciar o arquivo de implementação planejado

---

### Etapa 3 — Execução Diária (camada `05`)

Ao registrar itens no kanban ou nota diária que concluem um requisito, referenciar o `REQ-*`:

```markdown
- [x] Implementado [funcionalidade] — cobre REQ-003, REQ-004
```

Não é obrigatório citar `REQ-*` em toda linha — apenas quando o item fecha ou avança diretamente um requisito.

---

### Etapa 4 — Auditoria (`/audit-against-plan`)

O prompt `audit-against-plan` agora **valida obrigatoriamente**:

- [ ] Tabela `## Requisitos` presente e preenchida na spec
- [ ] Tabela `## Coverage Matrix` presente no workstream com **todos** os `REQ-*` da spec
- [ ] Nenhum `REQ-*` omitido da Coverage Matrix (PENDENTE é aceitável, ausência não)
- [ ] Status de cobertura: OK | PARTIAL | MISSING | DIVERGENT

Para specs legadas sem tabela formal, o prompt infere IDs temporários `REQ-T001...`.

---

## Critérios de Qualidade

Uma spec está pronta para descer para `06` quando:
- [ ] Todos os requisitos têm `REQ-*` atribuído
- [ ] Todos os `REQ-*` têm critério mínimo preenchido
- [ ] Frontmatter `requisitos:` está atualizado

Um workstream está pronto para iniciar execução quando:
- [ ] Coverage matrix presente com todos os `REQ-*` da spec
- [ ] Sem `REQ-*` omitidos (PENDENTE é preferível a ausente)

Uma entrega está pronta para `/audit-against-plan` quando:
- [ ] Spec com tabela `REQ-*` disponível
- [ ] Changed files identificados
- [ ] Build passou em todas as aplicações

---

## Diagnóstico Rápido de Gaps

Se você não sabe o estado de rastreabilidade de uma spec:

```
1. Abra a spec em Documentacao_[NomeDoProjeto]/04-planejamento-do-produto/03-especificacoes/
2. Procure pela seção ## Requisitos
   - Presente e preenchida → rastreabilidade formal OK
   - Ausente → spec legada, aplicar IDs antes de descer para 06
3. Abra o workstream em Documentacao_[NomeDoProjeto]/06-planejamento-tecnico-do-desenvolvimento/02-workstreams-tecnicos/
4. Procure pela seção ## Coverage Matrix
   - Presente → cobertura técnica mapeada
   - Ausente → adicionar antes de iniciar execução
```

---

## Referência Rápida de Formato

### Spec (mínimo)
```markdown
## Requisitos

| ID | Tipo | Descrição | Critério mínimo |
|----|------|-----------|-----------------|
| REQ-001 | funcional | | |
```

### Workstream (mínimo)
```markdown
## Coverage Matrix

| REQ-ID | Descrição resumida | Cobertura técnica | Artefato |
|--------|--------------------|-------------------|---------|
| REQ-001 | | | |
```
