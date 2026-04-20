---
name: Workstream - [NOME]
versao: "1.0"
data-criacao: "2026-04-20"
data-ultima-revisao: "2026-04-20"
status: "planejado"
owner: "[TECH LEAD]"
spec-de-origem: "04-planejamento-do-produto/03-especificacoes/NN-feature-nome-0-0-1.md"
---

# Workstream: [NOME DESCRITIVO]

## Spec de Origem

**Arquivo**: [Caminho relativo para spec](../../04-planejamento-do-produto/03-especificacoes/template-spec-sdd.md)

**Release**: 0.0.1

**Requisitos**: REQ-001, REQ-002, REQ-003

---

## Desenho de Implementação

### Visão Geral

[Parágrafo descrevendo a solução técnica em alto nível]

### Arquitetura

**Backend**:
- Layers afetadas: [controlador, serviço, repository, etc.]
- Novos endpoints: `POST /recurso`, `GET /recurso/{id}`
- Alterações de banco: [Migrations, novas colunas, índices]

**Frontend**:
- Componentes novos: [ComponenteA, ComponenteB]
- Páginas afetadas: [PageA, PageB]
- Store/State: [Qual contexto, reducer, store]

**Dados**:
- Tabelas: [Quais vão mudar]
- Migrations: [O que será alterado]
- Seeds: [Dados iniciais que precisam ser populados]

---

## Coverage Matrix

| REQ-ID | Descrição resumida | Cobertura técnica | Artefato |
|--------|--------------------|-------------------|---------|
| REQ-001 | [Descrição funcional] | `POST /users`, validação de email | `src/controllers/users.controller.ts` |
| REQ-002 | [Descrição segurança] | `AuthGuard`, `TenantGuard` | `src/guards/auth.guard.ts` |
| REQ-003 | [Descrição dados] | Migração de tabela usuarios | `prisma/migrations/001_usuarios.sql` |

**Legenda**:
- `OK`: Cobertura completa planejada
- `PARTIAL`: Cobertura incompleta (descrever o quê ainda falta)
- `PENDING`: Será coberto em fase posterior (descrever quando)
- `MISSING`: Sem cobertura técnica definida (deve ser tratado como blocker)

---

## Decomposição Técnica

### Fase 1: Backend

**Tasks**:
1. [ ] Criar DTO e Controller para novo endpoint
2. [ ] Implementar Service com lógica de negócio
3. [ ] Adicionar Guards (Auth, Tenant, RBAC)
4. [ ] Criar testes unitários

**Dependências**: Nenhuma  
**Duração estimada**: [Horas/dias]

### Fase 2: Dados

**Tasks**:
1. [ ] Criar Migration do Prisma
2. [ ] Atualizar `prisma/schema.prisma`
3. [ ] Executar migration em dev/staging

**Dependências**: Fase 1 (DTO e schema já conhecidos)  
**Duração estimada**: [Horas/dias]

### Fase 3: Frontend

**Tasks**:
1. [ ] Criar componentes React
2. [ ] Conectar aos endpoints do backend
3. [ ] Implementar estado local/global
4. [ ] Testes de integração

**Dependências**: Fase 1 (endpoints já disponíveis)  
**Duração estimada**: [Horas/dias]

---

## Contratos

### Endpoint 1: `POST /[resource]`

**Request**:
```json
{
  "campo1": "string",
  "campo2": 123
}
```

**Response** (201 Created):
```json
{
  "id": "uuid",
  "campo1": "string",
  "campo2": 123,
  "createdAt": "2026-04-20T10:00:00Z"
}
```

**Erros**:
- 400: Validação de input falhou
- 401: Não autenticado
- 403: Acesso negado (RBAC/tenant)
- 409: Recurso duplicado

---

### Endpoint 2: `GET /[resource]/:{id}`

[Mesma estrutura acima]

---

## Decisões Técnicas

- **[Decisão 1]**: Por que essa stack e não a alternativa?
- **[Decisão 2]**: Por que esse padrão de autenticação?

---

## Riscos Técnicos

| Risco | Impacto | Mitigação |
|-------|---------|-----------|
| Performance de query com N+1 | Alto | Usar `include` do Prisma instead de múltiplas queries |
| Tenant isolation quebrada | Crítico | TenantGuard em todo endpoint; testes de tenant boundary |
| Regressão em fluxo existente | Médio | Smoke tests + regression tests antes de merge |

---

## Plano de Validação

### Testes Unitários

- [ ] Services com mocks de repositório
- [ ] Controllers com mocks de service
- [ ] DTOs e validação de input

### Testes de Integração

- [ ] Fluxo end-to-end (request → banco de dados → response)
- [ ] Tenant isolation (requisição de outro tenant é rejeitada)
- [ ] RBAC (usuário sem permissão é rejeitado)

### Smoke Tests

- [ ] Feature básica funciona sem regressão em flows da release
- [ ] Performance está dentro dos limites

---

## Plano de Rollout

**Ambiente**: DEV → STAGING → PROD (em data da release)

**Estratégia**: Feature flag se regressão for detectada em staging

**Monitoramento**: 
- [ ] Erros em logs (procurar `REQ-001`, `REQ-002`, `REQ-003`)
- [ ] Performance (latência, CPU, memória)

---

## Artefatos

- Spec: [Link para spec]
- Branch: `feature/[nome-descritivo]`
- PR: [Link quando existir]
- Testes: `src/__tests__/[feature-name].spec.ts`

---

## Pronto para iniciar quando

- [ ] Coverage Matrix 100% preenchida (sem MISSING)
- [ ] Todos os contratos definidos
- [ ] Dependências exógenas confirmadas (APIs externas prontas, dados seedados, etc.)

---

**Tech Lead**: [NOME]  
**Revisor**: [NOME]  
**Data de aprovação**: [DATA, se já aprovado]
