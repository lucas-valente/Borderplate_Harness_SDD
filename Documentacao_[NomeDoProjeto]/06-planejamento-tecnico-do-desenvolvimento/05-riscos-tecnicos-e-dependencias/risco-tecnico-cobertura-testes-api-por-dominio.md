# Risco Tecnico - Cobertura de Testes por Dominio

## Contexto

Registro de riscos tecnicos relacionados a cobertura de testes por dominio no modulo-alvo.

## Riscos

| ID | Risco | Impacto | Probabilidade | Mitigacao | Owner | Status |
|---|---|---|---|---|---|---|
| RT-TEST-001 | Falta de isolamento de dados entre suites | Alto | Media | Padronizar fixtures e reset de base por suite | [NOME] | ABERTO |
| RT-TEST-002 | Dependencias externas nao controladas em testes | Medio | Media | Congelar respostas, clocks e contratos de mock | [NOME] | ABERTO |
| RT-TEST-003 | Cobertura global mascarando arquivos criticos | Alto | Alta | Aplicar gate de cobertura por arquivo (85/65) | [NOME] | ABERTO |

## Dependencias

- Plano de execucao paralela de testes por dominio
- Matriz de cobertura por dominio
- Planos de dominio `01..NN`

## Gatilho de revisao

Revisar este arquivo quando houver:

1. novo bloqueio de teste cross-dominio;
2. falha recorrente no quality gate;
3. mudanca de estrategia de teste por tipo.
