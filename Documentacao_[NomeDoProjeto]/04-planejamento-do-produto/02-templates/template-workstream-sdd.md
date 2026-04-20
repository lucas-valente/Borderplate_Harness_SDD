---
titulo: "[nome-da-frente]"
release: "[X.Y.Z]"
spec_path: "Documentacao_[NomeDoProjeto]/04-planejamento-do-produto/03-especificacoes/..."
created_at: "YYYY-MM-DD"
updated_at: "YYYY-MM-DD"
owner: "[responsavel]"
status: "draft"
---

# Workstream: [Nome da Feature]

## Origem funcional

- **Release:** [X.Y.Z]
- **Spec:** [link para spec]
- **Decisões relacionadas:** [link para ADR se houver]

## Escopo técnico

- **Backend:** [módulos, endpoints, serviços afetados]
- **Frontend:** [páginas, componentes, rotas afetadas]
- **Dados:** [tabelas, migrations, queries afetadas]
- **Integrações:** [APIs externas, webhooks, queues]

## Coverage Matrix

> Obrigatório. Todos os REQ-* da spec devem aparecer aqui.
> Status: PENDENTE | EM ANDAMENTO | IMPLEMENTADO | N/A

| REQ-ID | Tipo | Descrição | Status | Artefato técnico |
|--------|------|-----------|--------|------------------|
| REQ-001 | funcional | ... | PENDENTE | - |
| REQ-002 | técnico | ... | PENDENTE | - |
| REQ-003 | segurança | ... | PENDENTE | - |

## Arquitetura e desenho técnico

> Fluxo técnico ponta a ponta, componentes afetados, tradeoffs considerados.

## Contratos e payloads

### [Endpoint 1]

```
[MÉTODO] /[path]
Headers: Authorization: Bearer <token>
Params: [...]
```

**Request:**
```json
{
  "campo": "valor"
}
```

**Response (200):**
```json
{
  "campo": "valor"
}
```

**Erros:**
- `400` — [descrição]
- `403` — [descrição]
- `404` — [descrição]

## Dependências técnicas

- Dependência 1
- Dependência 2

## Riscos técnicos

| Risco | Probabilidade | Impacto | Mitigação |
|-------|---------------|---------|-----------|
| ... | ... | ... | ... |

## Plano de validação

- [ ] Testes unitários: [quais funções/serviços]
- [ ] Testes integração: [quais fluxos]
- [ ] Smoke: [quais endpoints/ações críticas]
- [ ] Regressão: [quais fluxos existentes checar]

## Decomposição em tarefas

- [ ] Tarefa 1 (Backend)
- [ ] Tarefa 2 (Frontend)
- [ ] Tarefa 3 (Dados)
- [ ] Tarefa 4 (Testes)

## Critérios de pronto

- [ ] Coverage Matrix com todos os REQ-* in IMPLEMENTADO
- [ ] Build verde
- [ ] Testes passando
- [ ] Docs atualizados
