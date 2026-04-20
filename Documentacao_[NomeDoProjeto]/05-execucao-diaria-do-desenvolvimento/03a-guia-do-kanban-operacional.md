# Guia do kanban operacional - [PROJETO]

## Papel do quadro

O kanban operacional diario e a camada visual curta da execucao.

Ele conversa com:

- nota diaria;
- Tasks;
- Day Planner.

## Relacao com as outras camadas

### `Documentacao_[NomeDoProjeto]/04-planejamento-do-produto`

Define:

- o que tem prioridade;
- o que entra na release;
- o que precisa ser detalhado.

### `Documentacao_[NomeDoProjeto]/05-execucao-diaria-do-desenvolvimento/Planner diario.md`

Mostra:

- o que foi puxado para a semana;
- o que virou trabalho de hoje;
- o que esta em foco;
- o que travou;
- o que concluiu.

## Fluxo recomendado

1. puxar item do backlog macro;
2. colocar em Backlog da semana;
3. mover para Hoje quando entrar no dia;
4. mover para Em foco quando estiver sendo atacado;
5. mover para Bloqueado se travar;
6. mover para Concluido ao terminar.

## Regra de ouro

Se o item exigir:

- redefinicao de escopo;
- mudanca de prioridade estrutural;
- nova especificacao;

ele deve voltar para `Documentacao_[NomeDoProjeto]/04-planejamento-do-produto`, e nao ser resolvido apenas aqui.
