# Hub - Planos de Validacao e Rollout

## Objetivo

Centralizar planos tecnicos de validacao, cobertura e rollout.

## Estrutura recomendada

- `testes-por-dominio/`
- `testes-frontend/` (opcional)
- `testes-performance/` (opcional)
- `rollout/` (opcional)

## Regras

1. Toda mudanca de escopo de teste deve refletir na matriz e no risco tecnico.
2. Toda execucao por dominio deve manter relatorio por arquivo/estado.
3. Toda conclusao deve respeitar gate por arquivo e evidencia de cenarios.
