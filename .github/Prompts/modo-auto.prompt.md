# Prompt: Modo AUTO (Orquestrador)

Use este prompt para ativar o modo AUTO de delegação inteligente de tarefas entre agentes especializados.

---

## Ativação

```
@workspace Modo AUTO: [SUA TAREFA AQUI]
```

---

## Exemplos de Uso

### 1. Tarefa Simples
```
@workspace Modo AUTO: Corrija o bug no endpoint de login
```
**Resultado:** Orquestrador → Programador

### 2. Tarefa com Testes
```
@workspace Modo AUTO: Implemente validação de e-mail com testes
```
**Resultado:** Orquestrador → Programador → QA

### 3. Feature Completa
```
@workspace Modo AUTO: Crie módulo de notificações completo com arquitetura, implementação e testes
```
**Resultado:** Orquestrador → plan agent → Programador → QA

### 4. Apenas Planejamento
```
@workspace Modo AUTO: Planeje a arquitetura do módulo de fidelidade
```
**Resultado:** Orquestrador → plan agent

### 5. Revisão de Segurança
```
@workspace Modo AUTO: Revise a segurança do módulo de autenticação
```
**Resultado:** Orquestrador → security-review agent

---

## Como o Orquestrador Funciona

1. **Analisa** as palavras-chave da solicitação
2. **Classifica** o tipo de tarefa (arquitetura, código, teste, revisão, documentação)
3. **Seleciona** o(s) agente(s) mais adequado(s) de `.github/Agents/`
4. **Coordena** a execução e comunicação entre agentes
5. **Consolida** a resposta final com evidências rastreáveis

---

## Palavras-Chave de Identificação

| Palavras-chave | Agente Delegado |
|----------------|-----------------|
| planeje, arquitete, estruture, workstream, plano técnico | plan agent |
| implemente, crie, codifique, corrija, desenvolva | Programador (agente padrão) |
| teste, coverage, qualidade, valide, QA, browser | QA agent |
| revise, review, segurança, auditoria, SecOps, SAST | security-review agent |
| documente, sincronize docs, atualize spec, release, planner | doc-manager |
| completo, módulo inteiro, feature full, pipeline completo | Multi-agente (orquestrado) |

---

## Notas

- Adapte os agentes disponíveis conforme `.github/Agents/` do seu projeto
- Para features críticas, prefira `/start-feature <spec_path>` para pipeline estruturado completo
