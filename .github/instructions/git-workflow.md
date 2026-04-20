# Git Workflow — [PROJETO]

Padrões de commit, branching e merge para este projeto.

## Branches

```
main (production)
  ├── staging (pré-prod)
  │   ├── develop (integração)
  │   │   ├── feature/[nome]
  │   │   ├── bugfix/[nome]
  │   │   └── hotfix/[nome]
```

## Commits

### Padrão

```
<tipo>: <descrição curta>

<corpo detalhado - opcional>

Fixes: [Se aplicável]
```

### Tipos

- `feat`: Nova feature
- `fix`: Correção de bug
- `docs`: Mudança apenas em documentação
- `refactor`: Refatoração sem mudança de comportamento
- `test`: Adição ou atualização de testes
- `chore`: Build, deps, tooling

### Exemplos

```
feat: adicionar filtro de barbeiros na agenda

Implementa REQ-003, REQ-004 conforme spec 07-feature-agenda-filtro-0-0-1.md

Fixes: #123
```

```
docs: atualizar coverage matrix do workstream agenda

Todos os REQ-* agora têm cobertura técnica mapeada.
```

## Merge Commit Messages

**Regra**: Mensagem declarativa com prefixo `merge:`

```
merge: feat: adicionar filtro de barbeiros

Fecha todas as user stories relacionadas a agenda nesta release.
```

Nunca use:
- ❌ "Merge branch 'develop' into staging"
- ❌ "Merge pull request #123"

## Pull Requests

**Título**: Mesma convenção de commit

**Descrição**:
```markdown
## Descrição

O que muda?

## Requisitos cobertos

- REQ-001: [Descrição]
- REQ-002: [Descrição]

## Checklist

- [ ] Spec com `## Requisitos` atualizada
- [ ] Workstream com `## Coverage Matrix` atualizado
- [ ] Build `npm run build` passou
- [ ] Testes passam
- [ ] Sem regressions conhecidas
```

## Workflow de Release

1. **Feature branch** → `develop`
   ```bash
   git checkout develop
   git merge --no-ff feature/[nome] -m "merge: feat: ..."
   git push origin develop
   ```

2. **Develop** → `staging` (release candidate)
   ```bash
   git checkout staging
   git merge develop --no-ff -m "merge: feat: ..."
   git push origin staging
   ```

3. **Staging** → `main` (produção)
   ```bash
   git checkout main
   git merge staging --no-ff -m "merge: feat: ..."
   git tag release-X.Y.Z
   git push origin main --tags
   ```

---

**Versão**: 1.0  
**Última atualização**: 2026-04-20
