---
name: Feature - [NOME]
release: "0.0.1"
versao: "1.0"
data-criacao: "2026-04-20"
data-ultima-revisao: "2026-04-20"
status: "rascunho"
owner: "[NOME DO OWNER]"
requisitos: [REQ-001, REQ-002, REQ-003]
---

# Feature: [NOME DESCRITIVO]

## Contexto

**Problema**: O que exatamente está quebrado ou falta?

**Oportunidade**: Por que isso importa agora?

**Impacto esperado**: Como o produto ou negócio muda?

## Ajuste Proposto

**O que muda**: Descrição clara do que será entregue.

**Escopo funcional**:
- Ponto 1
- Ponto 2
- Ponto 3

**Fora de escopo** (o que deliberadamente NÃO entra):
- Coisa que poderia entrar mas fica para depois

## Requisitos

| ID | Tipo | Descrição | Critério mínimo |
|----|------|-----------|-----------------|
| REQ-001 | funcional | [O que o sistema deve fazer] | [Como validar que está pronto] |
| REQ-002 | segurança | [Restrição, controle de acesso] | [Checklist mínimo] |
| REQ-003 | dados | [Persistência, modelo] | [Como validar integridade] |

### Regras de negócio

- **RN-001**: [Regra que governa comportamento]
- **RN-002**: [Outra regra crítica]

## Casos de Uso

### Caso 1: [Nome do cenário]

**Ator**: [Quem faz isso]

**Pré-condição**: [Estado inicial]

**Fluxo principal**:
1. Ator faz X
2. Sistema faz Y
3. Sistema retorna Z

**Fluxo alternativo**: [Se algo der errado]

**Pós-condição**: [Estado final esperado]

---

### Caso 2: [Outro cenário]

[Mesmo formato acima]

## Dependências

- Spec: [Outra spec ou feature que precisa estar pronta]
- Integ: [Sistema externo que precisa estar preparado]
- Dados: [Migração, seed ou estrutura que precisa existir]

## Riscos

| Risco | Impacto | Mitigação |
|-------|---------|-----------|
| [Risco A] | Alto/Médio/Baixo | [Como reduzir] |
| [Risco B] | Alto/Médio/Baixo | [Como reduzir] |

## Decisões Fechadas

- **[Decisão 1]**: Por quê essa escolha e não a alternativa?
- **[Decisão 2]**: Justificativa técnica ou de produto

## Critérios de Aceite

- [ ] Todos os `REQ-*` foram implementados conforme critério mínimo
- [ ] Coverage Matrix no workstream cobre 100% dos REQ-IDs
- [ ] Não há `REQ-*` omitidos (PENDENTE é aceitável, ausência não)
- [ ] Testes de regressão passam
- [ ] Documentação atualizada

## Observações

[Qualquer coisa que não se encaixa nas seções acima mas é importante saber]

---

**Revisor**: [NOME]  
**Data de aprovação**: [DATA, se já aprovado]
