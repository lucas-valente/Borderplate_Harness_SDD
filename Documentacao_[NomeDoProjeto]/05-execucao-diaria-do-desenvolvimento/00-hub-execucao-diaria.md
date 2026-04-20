# Hub da execucao diaria - [PROJETO]

## Papel desta area

Esta pasta concentra a execucao diaria do trabalho, e nao o planejamento estrutural do produto.

Ela existe para organizar:

- o que sera feito hoje;
- blocos de foco no dia;
- prioridades operacionais da semana;
- revisao curta do que andou e do que travou.

## Regra de separacao de responsabilidades

### O que continua em `Documentacao_[NomeDoProjeto]/04-planejamento-do-produto`

- roadmap;
- releases;
- backlog;
- especificacoes;
- governanca;
- decisoes;
- dependencias estruturais.

### O que entra em `Documentacao_[NomeDoProjeto]/05-execucao-diaria-do-desenvolvimento`

- nota diaria;
- blocos do dia no Day Planner;
- tarefas do dia;
- revisao semanal;
- registro operacional curto de execucao.

## Navegacao principal

- Planejamento do produto: [[Documentacao_[NomeDoProjeto]/04-planejamento-do-produto/Planner]]
- Release ativa: [[Documentacao_[NomeDoProjeto]/04-planejamento-do-produto/06-releases/template-release]]
- Guia da execucao diaria: [[Documentacao_[NomeDoProjeto]/05-execucao-diaria-do-desenvolvimento/01-guia-da-execucao-diaria]]
- Setup Tasks + Day Planner: [[Documentacao_[NomeDoProjeto]/05-execucao-diaria-do-desenvolvimento/02-setup-tasks-e-day-planner]]
- Planner diario (kanban operacional): [[Documentacao_[NomeDoProjeto]/05-execucao-diaria-do-desenvolvimento/Planner diario]]
- Hub dos planos operacionais: [[Documentacao_[NomeDoProjeto]/05-execucao-diaria-do-desenvolvimento/06-planos-operacionais/00-hub-planos-operacionais]]
- Guia do kanban operacional: [[Documentacao_[NomeDoProjeto]/05-execucao-diaria-do-desenvolvimento/03a-guia-do-kanban-operacional]]
- Templates: [[Documentacao_[NomeDoProjeto]/05-execucao-diaria-do-desenvolvimento/03-templates/Template - Nota Diaria de Desenvolvimento]]

## Estrutura desta pasta

```text
05-execucao-diaria-do-desenvolvimento
|- 00-hub-execucao-diaria.md
|- 01-guia-da-execucao-diaria.md
|- 02-setup-tasks-e-day-planner.md
|- Planner diario.md
|- 03a-guia-do-kanban-operacional.md
|- 03-templates
|- 04-daily-notes
|- 05-revisoes-semanais
`- 06-planos-operacionais
   |- 00-hub-planos-operacionais.md
   |- 01-releases-ativas
   `- 02-arquivados
```

## Fluxo recomendado

1. definir o que entrou no backlog e na release em `Documentacao_[NomeDoProjeto]/04-planejamento-do-produto`;
2. puxar da release apenas o que vai ser atacado agora;
3. organizar o dia na nota diaria;
4. usar o Day Planner para blocos de foco;
5. usar o Tasks para acompanhar execucao e reagendamentos;
6. no fim da semana, consolidar a leitura em revisao semanal curta.
