# Prompt: Diagnóstico de Projeto

Use este prompt para obter um diagnóstico completo do estado atual do código.

---

## Ativação

```
@workspace /diagnostico
```

---

## Objetivo

Realizar um diagnóstico completo do projeto, identificando o estado atual, falhas, desvios de arquitetura e funcionalidades implementadas, de forma a desbloquear o desenvolvimento de novas features.

## Arquivos de Referência (adapte por projeto)

- `#file:Documentacao_[NomeDoProjeto]/01-documentacao-tecnica/` — Arquitetura e regras do sistema
- `#file:Documentacao_[NomeDoProjeto]/04-planejamento-do-produto/03-especificacoes/` — Contratos funcionais esperados
- `#file:[arquivo de padrões de código do projeto, ex: CODING_STANDARDS.md]`

## Formato de Saída Exigido

### 1. Identificação dos Módulos Principais

Liste os principais módulos encontrados na estrutura do projeto.

---

### 2. Relatório de Diagnóstico por Módulo

Para CADA módulo:

**Módulo:** `[Nome do Módulo]`

- **Funcionalidades Implementadas:** O que este módulo faz? Compare com a spec esperada.
- **Como Funciona:** Resumo do fluxo de dados e lógica principal.
- **Estado Atual (Saúde):** Complexidade, cobertura de teste, duplicação de código.
- **Falhas e Vulnerabilidades:** Bugs óbvios, riscos de segurança ou lógicos.
- **Desvios (Arquitetura e Padrões):** Onde este módulo falha em seguir os padrões definidos.

> Seja objetivo e conciso. NÃO inclua exemplos de código no relatório.

---

### 3. Plano de Ação (TODO List)

Com base em todos os diagnósticos, crie uma lista priorizada de tarefas focada em:

- Corrigir os desvios arquiteturais mais críticos
- Resolver as falhas bloqueadoras
- Indicar os próximos passos para preparar o código para novas features

---

## Notas

- Adapte os arquivos de referência acima com os documentos técnicos reais do seu projeto
- Adicione `#file:[spec relevante]` para direcionar o diagnóstico a um módulo específico se necessário
