# 🚀 SETUP — Primeira Feature

Siga este checklist para configurar o boilerplate para seu projeto novo.

## 1️⃣ Personalizar Projeto

### Editar `00-central-do-workspace.md`

```markdown
# [NOME DO PROJETO]

**Objetivo**: [O que é o projeto]
**Time**: [Quem lidera]
**Data de início**: [YYYY-MM-DD]
```

### Editar `04-planejamento-do-produto/Planner.md`

```markdown
# Planner — [NOME DO PROJETO]

Remova os placeholders e preencha com features reais da sua release.
```

---

## 2️⃣ Criar Primeira Release

1. Copie `04-planejamento-do-produto/06-releases/template-release.md`
2. Renomeie para: `release-X.Y.Z-nome-descritivo.md`
   - Exemplo: `release-0.0.1-primeira-grande-atualizacao.md`
3. Salve em: `04-planejamento-do-produto/06-releases/01-ativas/`
4. Preencha:
   - Objetivo
   - Escopo P1/P2/P3
   - Timeline
   - Dependências

---

## 3️⃣ Criar Primeira Spec

1. Copie `04-planejamento-do-produto/02-templates/template-spec-sdd.md`
2. Renomeie para: `NN-feature-nome-descritivo-1-0.md`
   - Exemplo: `01-feature-autenticacao-ldap-1-0.md`
3. Salve em: `04-planejamento-do-produto/03-especificacoes/`
4. Preencha:
   - Contexto (problema, oportunidade)
   - Ajuste proposto (o que muda)
   - `## Requisitos` com REQ-001, REQ-002, etc.
   - Regras de negócio
   - Casos de uso
   - Dependências
   - Riscos

**Validação**: Todos os `REQ-*` preenchidos? ✓

---

## 4️⃣ Criar Primeiro Workstream

1. Copie `06-planejamento-tecnico-do-desenvolvimento/02-workstreams-tecnicos/template-workstream-sdd.md`
2. Renomeie para: `ws-nome-descritivo-1-0.md`
   - Exemplo: `ws-autenticacao-ldap-1-0.md`
3. Salve em: `06-planejamento-tecnico-do-desenvolvimento/02-workstreams-tecnicos/`
4. Preencha:
   - Link para spec de origem
   - Desenho de implementação (arquitetura, layers, endpoints)
   - `## Coverage Matrix` mapeando cada REQ-* para implementação
   - Contratos (payloads de request/response)
   - Decomposição técnica (fases, tasks)
   - Plano de validação (testes, smoke)

**Validação**: Todos os REQ-* têm cobertura técnica (OK, PARTIAL, PENDING)? ✓

---

## 5️⃣ Registrar Governança

1. Abra `04-planejamento-do-produto/07-governanca/template-dependencias-riscos.md`
2. Salve como: `01-mapa-dependencias-riscos.md`
3. Registre:
   - Dependências estruturais (entre features)
   - Dependências externas (APIs, dados, infraestruturas)
   - Riscos técnicos
   - Riscos de produto
   - Decisões arquiteturais importantes

---

## 6️⃣ Atualizar `.github/`

### Editar `.github/copilot-instructions.md`

- Customize com informações do seu projeto
- Adicione links para seus repos
- Defina convenções específicas

### Revisar prompts e agents adicionados

- Ajuste `/api-test-pipeline` para o caminho real dos planos de teste do modulo-alvo
- Ajuste `/api-test-quality-audit` para os gates de qualidade aceitos pelo seu time
- Configure `api-test.agent.md` e `api-test-audit.agent.md` conforme stack real (Node, Python, Java, Go, etc.)

### Revisar instructions e skills adicionados

- Ajuste `frontend-guidance.instructions.md` para os diretórios reais do frontend
- Ajuste `api-test-coverage-gate.instructions.md` para os thresholds aceitos no projeto
- Revise os skills: `frontend-guidance`, `database-mcp-manager`, `tlc-spec-driven`, `api-test-planning-by-domain`, `caveman`

### Revisar workflows novos

- `api-unit-full-suite.yml`
- `api-integration-suite.yml`
- `api-e2e-suite.yml`
- `semgrep-security.yml`
- Ajuste branch strategy e scripts conforme a stack do projeto

### Editar `.github/instructions/git-workflow.md`

- Customize branch strategy se diferente
- Adicione comandos de build/test específicos
- Defina política de PRs

---

## 7️⃣ Iniciar Daily Execution

Quando a primeira frente começar a ser implementada:

1. Copie `05-execucao-diaria-do-desenvolvimento/template-daily-note.md`
2. Crie arquivo: `04-daily-notes/YYYY-MM-DD.md`
3. Registre progresso diário linkando `REQ-*`:
   ```markdown
   - [x] Implementado login LDAP — cobre REQ-001, REQ-002
   ```

---

## ✅ Validação Final

Seu harness está pronto quando:

- [ ] Projeto renomeado em `00-central-do-workspace.md`
- [ ] Release ativa criada e ligada no Planner
- [ ] Primeira spec com `## Requisitos` completa
- [ ] Primeiro workstream com `## Coverage Matrix` completo
- [ ] Governança com map de dependências e riscos
- [ ] `.github/` personalizado
- [ ] Daily notes ou kanban iniciados (quando execução começar)

---

## 🎯 Próximos Passos

1. **Semana 1**: Especificações finalizadas com SDD completa
2. **Semana 1-2**: Workstreams aprovados com Coverage Matrix 100%
3. **Semana 2+**: Desenvolvimento começando respeitando cobertura SDD

---

**Tempo estimado de setup**: 2-4 horas  
**Dependências**: Nenhuma (tudo aqui fornecido)

---

**Dúvidas?** Consulte [README.md](./README.md)
