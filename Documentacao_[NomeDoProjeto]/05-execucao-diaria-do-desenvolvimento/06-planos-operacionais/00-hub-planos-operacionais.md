# Hub dos planos operacionais - execucao

## Papel desta area

Esta pasta existe para concentrar os planos operacionais rastreaveis de execucao, sem misturar:

1. backlog macro do produto;
2. nota diaria;
3. revisao semanal;
4. plano de rollout de uma release especifica.

## O que entra aqui

- planos operacionais por release;
- trilhas de execucao ate PRD;
- cortes operacionais;
- ondas de implementacao;
- checklists de estabilizacao e rollout.

## O que nao entra aqui

- regras de escopo da release, que continuam em `Documentacao_[NomeDoProjeto]/04-planejamento-do-produto`;
- agenda do dia, que continua em `Documentacao_[NomeDoProjeto]/05-execucao-diaria-do-desenvolvimento/04-daily-notes`;
- quadro operacional curto, que continua no planner diario;
- backlog futuro macro do produto.

## Navegacao

- Hub da execucao diaria: [[Documentacao_[NomeDoProjeto]/05-execucao-diaria-do-desenvolvimento/00-hub-execucao-diaria]]
- Release ativa: [[Documentacao_[NomeDoProjeto]/04-planejamento-do-produto/06-releases/template-release]]
- Pasta de planos ativos: [[Documentacao_[NomeDoProjeto]/05-execucao-diaria-do-desenvolvimento/06-planos-operacionais/01-releases-ativas]]

## Estrutura sugerida

```text
06-planos-operacionais
|- 00-hub-planos-operacionais.md
|- 01-releases-ativas
`- 02-arquivados
```

## Regra pratica

1. cada release ativa pode ter no maximo um plano operacional principal;
2. o plano operacional deve apontar para a release e para a revisao semanal;
3. se surgir uma nova release ativa, ela ganha sua propria nota nesta pasta;
4. quando a release fechar, o plano pode ser movido para `02-arquivados`.
