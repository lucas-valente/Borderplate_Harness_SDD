# Setup de Tasks + Day Planner - [PROJETO]

## Objetivo

Padronizar a camada de execucao diaria usando os plugins Tasks e Day Planner sem misturar essa rotina com o planejamento do produto.

## Estrutura recomendada

- pasta das notas diarias:
  - `Documentacao_[NomeDoProjeto]/05-execucao-diaria-do-desenvolvimento/04-daily-notes`
- pasta das revisoes semanais:
  - `Documentacao_[NomeDoProjeto]/05-execucao-diaria-do-desenvolvimento/05-revisoes-semanais`
- template da nota diaria:
  - `Documentacao_[NomeDoProjeto]/05-execucao-diaria-do-desenvolvimento/03-templates/Template - Nota Diaria de Desenvolvimento.md`
- template da revisao semanal:
  - `Documentacao_[NomeDoProjeto]/05-execucao-diaria-do-desenvolvimento/03-templates/Template - Revisao Semanal.md`

## Leitura recomendada de configuracao

### Daily Notes

Configurar para usar como base:

- pasta: `05-execucao-diaria-do-desenvolvimento/04-daily-notes`
- template: `05-execucao-diaria-do-desenvolvimento/03-templates/Template - Nota Diaria de Desenvolvimento`

### Tasks

Usar o plugin para:

- marcar tarefas do dia;
- reagendar com `scheduled`;
- puxar tarefas priorizadas para a nota diaria;
- manter historico simples do que foi concluido.

### Day Planner

Usar o plugin para:

- mostrar os blocos do dia da nota diaria;
- abrir timeline lateral;
- organizar sessoes de foco;
- enxergar o dia antes de comecar a execucao.

## Convencao sugerida para blocos

Dentro da nota diaria, usar o bloco:

```md
## Day Planner

- [ ] 09:00 - 10:30 Frente principal do dia
- [ ] 11:00 - 12:00 Ajustes e revisao
- [ ] 14:00 - 16:00 Desenvolvimento profundo
```

## Convencao sugerida para Tasks

Quando a tarefa exigir data, usar o Tasks com `scheduled`.

Exemplo:

```md
- [ ] Fechar detalhamento da frente X ⏳ 2026-04-20
```

Ou deixar a tarefa dentro da nota diaria quando ela for apenas operacional do dia.

## Regra de ouro

Tasks e Day Planner organizam execucao.

Eles nao substituem:

- release;
- backlog;
- especificacoes;
- governanca do planejamento.
