# Borderplate Harness SDD

Boilerplate para iniciar projetos com desenvolvimento guiado por IA, documentacao estruturada e fluxo SDD (Spec-Driven Development) com rastreabilidade de requisitos ponta a ponta.

## Visao Geral

Este repositorio entrega uma base pronta para times que querem:

- Planejar por release com specs formais
- Executar com workstreams tecnicos rastreaveis
- Orquestrar agentes, prompts e instrucoes no `.github/` de forma agnostica de IA (Claude, Cursor, Antigravity, Copilot e similares)
- Manter documentacao viva sem perder coerencia entre produto, tecnica e execucao diaria

Toda a documentacao principal fica em:

`Documentacao_[NomeDoProjeto]/`

Este harness e agnostico de plataforma de IA: voce pode operar o mesmo fluxo com diferentes agentes e IDEs, mantendo a mesma estrutura SDD e as mesmas regras de governanca.

## Oque vem Pronto

| Planejamento de Produto | Planejamento Tecnico |
|---|---|
| Release ativa, Planner, Specs, Governanca | Workstreams, Contratos, Matrizes, Riscos, Validacao |
| `04-planejamento-do-produto/` | `06-planejamento-tecnico-do-desenvolvimento/` |

| Execucao Diaria | Automacao IA |
|---|---|
| Kanban, Daily Notes, Planos operacionais | Agents, Prompts, Instructions, Skills, Workflow CI integraveis com qualquer IA |
| `05-execucao-diaria-do-desenvolvimento/` | `.github/` |

## Estrutura do Repositorio

```text
Borderplate_Harness_SDD/
|- .github/
|  |- Agents/
|  |- Prompts/
|  |- instructions/
|  |- skills/
|  |- docs/
|  |- workflows/
|  `- copilot-instructions.md
|- Documentacao_[NomeDoProjeto]/
|  |- 00-central-do-workspace.md
|  |- 01-documentacao-tecnica/
|  |- 02-documentacao-executiva/
|  |- 03-documentacao-oficial-do-sistema/
|  |- 04-planejamento-do-produto/
|  |- 05-execucao-diaria-do-desenvolvimento/
|  |- 06-planejamento-tecnico-do-desenvolvimento/
|  `- Manual/
`- README.md
```

## Comece em 7 Passos

1. Clone o repositorio.
2. Renomeie `Documentacao_[NomeDoProjeto]` para o nome real do projeto.
3. Edite `Documentacao_[NomeDoProjeto]/00-central-do-workspace.md` (fonte unica de verdade do workspace).
4. Crie a release ativa em `04-planejamento-do-produto/06-releases/01-ativas/`.
5. Crie a primeira spec com `REQ-001`, `REQ-002` em `03-especificacoes/`.
6. Crie o primeiro workstream com `Coverage Matrix` em `06/02-workstreams-tecnicos/`.
7. Ajuste `.github/copilot-instructions.md` e os prompts para o stack do projeto.

## Mini Tutorial: Dependencias dos Prompts (Semgrep e afins)

Alguns prompts, principalmente de seguranca (ex: `/secops-audit`, `/quality-gate`), dependem de ferramentas locais instaladas.

### 1) Semgrep (SAST)

Use uma das opcoes abaixo:

#### Windows (PowerShell)

```bash
python -m pip install --upgrade pip
pip install semgrep
semgrep --version
```

#### macOS (Homebrew)

```bash
brew install semgrep
semgrep --version
```

#### Linux (pip)

```bash
python3 -m pip install --upgrade pip
pip3 install semgrep
semgrep --version
```

Scan rapido de exemplo:

```bash
semgrep --config=p/owasp-top-ten .
```

### 2) Auditoria de dependencias (SCA)

Para projetos Node.js:

```bash
npm install
npm audit --omit=dev
```

Para projetos Python:

```bash
pip install pip-audit
pip-audit
```

### 3) Segredos vazados (recomendado)

Opcional, mas recomendado em repositorio publico:

```bash
# Exemplo com gitleaks (ajuste conforme seu SO)
gitleaks version
gitleaks detect --source .
```

### 4) Configuracao minima no projeto

Se seu projeto for Node.js, adicione scripts no `package.json` para padronizar os prompts:

```json
{
	"scripts": {
		"security:scan": "semgrep --config=p/owasp-top-ten .",
		"security:deps": "npm audit --omit=dev"
	}
}
```

Depois disso, os prompts podem chamar comandos previsiveis (`npm run security:scan` e `npm run security:deps`) com menos ajuste manual.

### 5) Checklist rapido de validacao

- [ ] `semgrep --version` responde sem erro
- [ ] scan semgrep roda no repositorio
- [ ] auditoria de dependencias roda sem quebrar ambiente
- [ ] comandos estao documentados no README do projeto final

## Fluxo SDD (Spec -> Workstream -> Execucao -> Auditoria)

### 1) Spec

- Define requisitos com IDs unicos (`REQ-*`)
- Define escopo, aceite, riscos e fora de escopo

### 2) Workstream tecnico

- Mapeia todos os `REQ-*` em `Coverage Matrix`
- Define contratos, tarefas, riscos tecnicos e validacao

### 3) Execucao

- Implementacao guiada por `/feature-pipeline`
- QA e quality gate antes de consolidar entrega

### 4) Auditoria

- `/audit-against-plan` compara planejado vs implementado
- Emite `PASS`, `PASS WITH DEVIATIONS` ou `FAIL`

## Kit IA pronto em `.github/`

### Agents

- `plan.agent.md`
- `QA.agent.md`
- `security-review.agent.md`
- `security-review-fix.agent.md`
- `consultor.agent.md`
- `api-test.agent.md` (template opcional para testes por dominio em modulo de servico)
- `api-test-audit.agent.md` (template opcional para auditoria de testes por dominio)

### Prompts-chave

- `/start-feature`
- `/technical-planning`
- `/feature-pipeline`
- `/api-test-pipeline` (template opcional para testes por dominio)
- `/api-test-quality-audit` (template opcional para auditoria de testes por dominio)
- `/quality-gate`
- `/audit-against-plan`
- `/documentation-sync`
- `/documentation-quick-sync`
- `/secops-audit`

Todos os prompts podem ser executados por diferentes copilotos/agentes. Se um provider nao suportar um comando exato, basta mapear o atalho equivalente mantendo o mesmo contrato de entrada/saida.

### Instructions

- `feature-workflow.instructions.md`
- `secops-review.instructions.md`
- `frontend-guidance.instructions.md`
- `api-test-coverage-gate.instructions.md`

### Skills

- `sdd-traceability-manager`
- `workspace-documentation-manager`
- `doc-manager`
- `technical-planning-manager`
- `implementation-audit-manager`
- `secops-audit-manager`
- `frontend-guidance`
- `database-mcp-manager`
- `tlc-spec-driven`
- `api-test-planning-by-domain`
- `caveman`

### Docs de suporte em `.github/docs/`

- `plan-template.md`
- `mcp-workflow-blueprint.md`
- `api-test-execution-harness.md`

### Workflows CI de exemplo em `.github/workflows/`

- `validate-pr-source.yml`
- `api-unit-full-suite.yml`
- `api-integration-suite.yml`
- `api-e2e-suite.yml`
- `semgrep-security.yml`

## Convencoes importantes

- Um requisito sem `REQ-ID` nao entra no fluxo oficial.
- Um workstream sem `Coverage Matrix` esta incompleto.
- Mudanca de escopo/prioridade/risco: atualize `release -> planner -> spec -> governanca`.
- Mudanca de desenho tecnico/contrato/rollout: atualize tambem a pasta `06` na mesma sessao.

## Para quem este boilerplate foi feito

- Times de produto + engenharia que querem rastreabilidade real
- Projetos multi-modulo que sofrem com desalinhamento entre planejamento e codigo
- Equipes que usam Copilot/agentes e precisam de guardrails claros

Tambem serve para times multi-ferramenta (ex: parte do time em Cursor, parte em Claude, parte em Copilot), porque o padrao de trabalho fica na documentacao e nao em um vendor especifico.

## Roadmap sugerido para adocao

1. Pilotar em 1 feature end-to-end.
2. Medir lead time e retrabalho.
3. Expandir para toda a release.
4. Tornar `audit-against-plan` um gate de entrega.

## Contribuicao

Contribuicoes sao bem-vindas. Para mudancas grandes, abra uma issue descrevendo:

- Problema atual
- Proposta de melhoria
- Impacto esperado no fluxo SDD

## Licenca

Defina a licenca do projeto (ex: MIT) antes da publicacao oficial.
