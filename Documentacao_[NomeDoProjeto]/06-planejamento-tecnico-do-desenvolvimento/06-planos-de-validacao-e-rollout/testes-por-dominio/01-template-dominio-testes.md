# Template - Dominio de Testes

## Metadados

- Dominio: [NOME]
- Prioridade: P0 | P1 | P2
- Responsavel: [NOME]
- Status formal: ABERTO | ABERTO PARA INTEGRACAO | EM AUDITORIA | CONCLUIDO
- Atualizado em: YYYY-MM-DD

## Objetivo do dominio

Descreva o que deve ficar coberto neste dominio.

## Arquivos produtivos mapeados do dominio (cobertura completa)

| Arquivo | Tipo | Unitario (foco atual) | Integracao | E2E | Status coverage atual |
|---|---|---|---|---|---|
| [caminho/arquivo] | [tipo] | PRIORITARIO | OBRIGATORIO | OPCIONAL | FAIL |

## Criterios de aceite

- [ ] testes de unidade aplicaveis ao dominio passando
- [ ] testes de integracao aplicaveis ao dominio passando
- [ ] testes e2e aplicaveis ao dominio passando

## Lacunas atuais

- [ ] [descricao da lacuna 1]
- [ ] [descricao da lacuna 2]

## Relatorio de execucao da sessao

### Atualizacao em `YYYY-MM-DD`: [resumo curto]

### Estado validado no recorte de [recorte]:

- [evidencia objetiva]

### Relatorio por arquivo/estado (execucao dedicada de `YYYY-MM-DD`)

| Arquivo de codigo | Area/recorte | Escopo da sessao | Unit | Integracao | E2E | Contrato/Integracao | Seguranca/Isolamento | Coverage stmts/branches/functions/lines | Caminho feliz | Caminho triste | Edge cases | Estado | Proxima acao |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| [caminho/arquivo] | [recorte] | CHANGED | OK | OK | N/A | OK | OK | 90/70/90/90 | OK | OK | OK | PASS | - |
