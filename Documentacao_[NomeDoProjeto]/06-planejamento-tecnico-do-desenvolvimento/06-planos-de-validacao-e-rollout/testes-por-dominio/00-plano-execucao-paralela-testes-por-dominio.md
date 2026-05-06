# Plano de Execucao Paralela - Testes por Dominio

## Objetivo

Definir base para execucao paralela por dominio sem interferencia entre suites.

## Fase T0 (fundacao)

- [ ] padronizar setup de testes
- [ ] padronizar fixtures de autenticacao/permissao (quando aplicavel)
- [ ] padronizar fixtures de escopo de dados
- [ ] padronizar mocks de dependencias externas
- [ ] definir estrategia de isolamento para integracao/e2e
- [ ] definir comandos alvo por tipo (unit/integration/e2e/coverage)

## Regras de paralelismo

1. Suites unitarias podem rodar em paralelo.
2. Suites de integracao/e2e com estado compartilhado exigem isolamento explicito.
3. Mocks globais devem ser deterministicos para reduzir flakiness.

## Criterio de pronto (T0)

T0 esta concluido quando os itens acima estao validados com comandos reais.
