# Instruções — [PROJETO]

Customize este arquivo com instruções específicas do seu projeto.

## Padrão SDD

Este projeto usa Sistema de Documentação Descritiva (SDD):

- Spec → Workstream → Execução → Auditoria
- Cada requisito tem ID único: `REQ-001`, `REQ-002`
- Coverage Matrix em cada workstream mapeia REQ → implementação

**Fontes de verdade**:
- Release ativa: `Documentacao_[NomeDoProjeto]/04-planejamento-do-produto/06-releases/01-ativas/`
- Specs: `Documentacao_[NomeDoProjeto]/04-planejamento-do-produto/03-especificacoes/`
- Workstreams: `Documentacao_[NomeDoProjeto]/06-planejamento-tecnico-do-desenvolvimento/02-workstreams-tecnicos/`
- Execução: `Documentacao_[NomeDoProjeto]/05-execucao-diaria-do-desenvolvimento/`

## Skills

- `sdd-traceability-manager` — Garantir rastreabilidade SDD
- `workspace-documentation-manager` — Sincronizar camadas
- `doc-manager` — Manutenção de documentação

## Convenções

### Arquivos

- Specs: `NN-feature-nome-versao.md` em `Documentacao_[NomeDoProjeto]/04-planejamento-do-produto/03-especificacoes/`
- Workstreams: `ws-nome-versao.md` em `Documentacao_[NomeDoProjeto]/06-planejamento-tecnico-do-desenvolvimento/02-workstreams-tecnicos/`
- Releases: `release-X.Y.Z-nome.md` em `Documentacao_[NomeDoProjeto]/04-planejamento-do-produto/06-releases/01-ativas/`

### Requisitos

- ID formato: `REQ-001`, `REQ-002`... (sequencial por spec)
- Tipos: `funcional`, `técnico`, `segurança`, `dados`, `ui`
- Nunca renumerar após publicação

### Workflows

1. **Primeira feature**: Crie spec com `## Requisitos` → workstream com `## Coverage Matrix`
2. **Aprovar spec**: Validator: (a) todos REQ-* com critério mínimo? (b) frontmatter `requisitos:` atualizado?
3. **Aprovar workstream**: Validator: (a) Coverage Matrix presente? (b) nenhum REQ-* omitido?
4. **Auditar entrega**: Use prompt `/audit-against-plan` — valida spec + workstream com presença de Coverage Matrix

## Repositório

[Adicione informações do seu repo aqui: URL, branch strategy, build commands, etc.]

### Build

```bash
cd [projeto]
npm run build
```

### Test

```bash
npm test
```

### Deploy

[Adicione instruções de deploy aqui]

---

**Última atualização**: 2026-04-20  
**Owner**: [NOME]
