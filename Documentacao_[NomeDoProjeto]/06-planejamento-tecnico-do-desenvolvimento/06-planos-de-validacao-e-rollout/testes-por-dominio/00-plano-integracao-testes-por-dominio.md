# Plano de Integracao - Testes por Dominio

## Objetivo

Definir ordem de integracao dos dominios e controle de handoff entre execucoes.

## Ordem sugerida

1. P0 (seguranca, integridade de dados, fluxos criticos)
2. P1 (operacao core e fluxos regulares)
3. P2 (automacoes e expansao de regressao)

## Quadro de status

| Dominio | Prioridade | Responsavel | Status | Proxima acao |
|---|---|---|---|---|
| 01-dominio-critico-a | P0 | [NOME] | PENDENTE | Abrir plano de dominio |
| 02-dominio-critico-b | P0 | [NOME] | PENDENTE | Abrir plano de dominio |
| 03-dominio-operacional-c | P1 | [NOME] | PENDENTE | Abrir plano de dominio |

## Regras

- Nao iniciar novo dominio sem registrar status do anterior.
- Se houver bloqueio cross-dominio, registrar no risco tecnico.
- Toda conclusao deve passar por auditoria de qualidade de testes.
