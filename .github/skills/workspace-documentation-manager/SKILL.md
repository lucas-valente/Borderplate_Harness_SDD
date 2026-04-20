---
name: workspace-documentation-manager
description: "Use when creating, revising, reorganizing, or synchronizing project documentation. Actions: classify the request by layer, identify source-of-truth documents, update the correct folders in the correct order, sync dependencies between release/planner/spec/governance/technical planning/daily execution/manuals, and avoid drift between child workstreams and parent waves. Triggers: documentacao, planner, release, spec, governanca, manual, execucao diaria, sincronizacao documental, estrutura do workspace, ordem de alteracao, dependencia documental, fonte de verdade."
---

# Workspace Documentation Manager — Estrutura, Dependências e Sequência Documental

Skill para criar, revisar e manter a documentação do projeto sem perder coerência entre:

1. estrutura documental
2. fonte de verdade
3. dependências entre camadas
4. ordem correta de alteração
5. sincronização de status entre artefatos técnicos, funcionais e operacionais

---

## Mapa do Workspace

```text
Seu Projeto/
├── 00-central-do-workspace.md
├── 01-documentacao-tecnica/
├── 02-documentacao-executiva/
├── 03-documentacao-oficial-do-sistema/
├── 04-planejamento-do-produto/
├── 05-execucao-diaria-do-desenvolvimento/
├── 06-planejamento-tecnico-do-desenvolvimento/
├── .github/
├── Manual/
├── Testes/
└── Treinamento/
```

## Papel de Cada Camada

| Pasta | Papel |
|---|---|
| `00-central-do-workspace.md` | entrada estrutural do workspace |
| `01-documentacao-tecnica` | visão técnica, arquitetura, módulos, integrações e regras de sistema |
| `02-documentacao-executiva` | narrativa executiva, roadmap, comunicação e leitura formal |
| `03-documentacao-oficial-do-sistema` | consolidação funcional oficial do sistema |
| `04-planejamento-do-produto` | release, planner, backlog, especificações, governança e dependências estruturais |
| `05-execucao-diaria-do-desenvolvimento` | semana, dia, kanban curto, daily notes, revisões e planos operacionais |
| `06-planejamento-tecnico-do-desenvolvimento` | visão técnica por release, workstreams, contratos, matrizes, riscos, validação e rollout |
| `Manual` | manual funcional, narrativa de uso e reflexo das superfícies reais do sistema |
| `Testes` | testes e artefatos de apoio de verificação |
| `Treinamento` | materiais de onboarding, suporte e capacitação |

## Quando Usar

### Obrigatório

- quando a sessão precisar decidir **onde** um documento deve viver
- quando uma frente exigir sincronização entre `04`, `05`, `06` e `Manual`
- quando for necessário atualizar ordem, dependência, risco, prioridade ou leitura estrutural
- quando um workstream for concluído e os espelhos documentais precisarem refletir isso
- quando um rename funcional ou mudança de narrativa afetar docs técnicos, operacionais e manuais

### Recomendado

- antes de criar documento novo em área de planejamento
- antes de mover uma frente de produto para execução
- ao fechar uma micro-entrega e refletir isso na release, kanban e manuais

### Não Usar

- para alterações puramente de código sem impacto documental
- para notas pessoais temporárias fora das camadas oficiais
- para atualizar apenas um espelho isolado quando a mudança afeta mais de uma camada

## Fontes de Verdade (ordem de prioridade)

| Camada | Documento principal |
|---|---|
| Estrutural | `Documentacao_[NomeDoProjeto]/00-central-do-workspace.md` |
| Planejamento | `Documentacao_[NomeDoProjeto]/04-planejamento-do-produto/Planner.md` |
| Release ativa | `Documentacao_[NomeDoProjeto]/04-planejamento-do-produto/06-releases/01-ativas/` |
| Governança | `Documentacao_[NomeDoProjeto]/04-planejamento-do-produto/07-governanca/` |
| Hub de execução | `Documentacao_[NomeDoProjeto]/05-execucao-diaria-do-desenvolvimento/` |
| Hub técnico | `Documentacao_[NomeDoProjeto]/06-planejamento-tecnico-do-desenvolvimento/00-hub-planejamento-tecnico.md` (se existir) |
| Manual funcional | `Documentacao_[NomeDoProjeto]/Manual/` |

## Regra Central de Dependência

As camadas do workspace não são paralelas. Elas possuem dependência de leitura e dependência de alteração.

### Dependência de leitura

```text
release ativa
  -> planner
  -> spec da frente
  -> governança
  -> planejamento técnico (quando aplicável)
  -> execução diária (quando a frente já virou trabalho da semana ou do dia)
  -> manual / docs funcionais (quando a mudança chega na superfície do sistema)
```

### Dependência de alteração

```text
mudança estrutural ou funcional
  -> release
  -> planner
  -> spec
  -> governança

mudança de implementação
  -> release
  -> planner
  -> spec
  -> governança
  -> 06-planejamento-tecnico-do-desenvolvimento

mudança que já virou execução
  -> release
  -> planner
  -> spec
  -> governança
  -> 06-planejamento-tecnico-do-desenvolvimento
  -> 05-execucao-diaria-do-desenvolvimento

mudança de superfície real do sistema
  -> tudo acima, quando aplicável
  -> Manual
```

## Sequência Obrigatória de Alteração

### Regra base

Se a conversa mudar regra de negócio, ordem da release, dependência ou leitura estrutural:

```text
1. release ativa
2. Planner
3. spec funcional
4. governança
```

Se a conversa mudar desenho de implementação, contrato, matriz, dependência técnica, validação ou rollout:

```text
1. release ativa
2. Planner
3. spec funcional
4. governança
5. pasta 06
```

Se a frente já estiver aprovada e virar trabalho rastreável da semana ou do dia:

```text
1. release ativa
2. Planner
3. spec funcional
4. governança
5. pasta 06
6. pasta 05
```

Se a mudança alterar interface, naming ou comportamento exposto ao usuário:

```text
1. sincronizar 04/05/06 conforme o caso
2. sincronizar Manual
3. revisar 03-documentacao-oficial-do-sistema se o entendimento funcional oficial mudou
```

## Workflow Obrigatório por Sessão

```text
1. Identificar a natureza da frente:
   - estrutural
   - produto
   - técnico
   - operacional
   - funcional/manual

2. Confirmar a release ativa e a spec de origem

3. Classificar a mudança:
   - mudou o que entra?
   - mudou a ordem?
   - mudou a dependência?
   - mudou o risco?
   - mudou a prioridade?
   - mudou a execução?
   - mudou a superfície real do sistema?

4. Atualizar as camadas na ordem correta

5. Fechar a coerência entre:
   - release
   - planner
   - spec
   - governança
   - execução (quando aplicável)
```

---

## Dicas Rápidas

- **Sempre comece pela release**: É o documento mais importante
- **Planner é o índice**: Consulte-o para confirmar prioridade e estado
- **Governança é o guardião**: Se não está em governança, não é oficial
- **Daily execution reflete a release**: Não é fonte de verdade, é espelho
- **Manual é consequência**: Só muda quando a superfície real muda
