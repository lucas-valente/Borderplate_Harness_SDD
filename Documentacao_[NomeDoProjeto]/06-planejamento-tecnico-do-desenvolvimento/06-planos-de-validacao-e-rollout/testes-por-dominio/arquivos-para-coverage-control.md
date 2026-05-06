# Arquivos para Coverage Control

## Objetivo

Consolidar arquivos produtivos que entram no controle de cobertura por dominio.

## Tabela base

| Dominio | Arquivo | Tipo | Obrigatorio no gate | Observacao |
|---|---|---|---|---|
| dominio-critico-a | [caminho/arquivo] | [tipo] | SIM | Atualizar |
| dominio-critico-b | [caminho/arquivo] | [tipo] | SIM | Atualizar |
| dominio-operacional-c | [caminho/arquivo] | [tipo] | SIM | Atualizar |

## Gate por arquivo alterado

- statements >= 85%
- functions >= 85%
- lines >= 85%
- branches >= 65%

## Regras

1. Arquivo alterado no dominio deve aparecer no relatorio de cobertura.
2. Arquivo ausente no output invalida o gate.
3. Cobertura global nao substitui cobertura por arquivo.
