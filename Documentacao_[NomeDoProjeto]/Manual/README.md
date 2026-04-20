# Manual — [NomeDoProjeto]

Esta pasta e destinada aos manuais da aplicacao.

## Para que serve

### Base de conhecimento para usuarios finais

Documente aqui como usar o sistema: fluxos, funcionalidades, perguntas frequentes e guias passo a passo. Pode ser publicado em portais de ajuda, wikis ou entregue diretamente ao usuario.

### RAG para agentes de IA

Esta pasta e ideal para ser indexada como fonte de contexto (RAG — Retrieval-Augmented Generation) em agentes de IA. Com os manuais aqui, o agente consegue responder perguntas sobre o produto sem precisar do codigo-fonte, apenas com o conhecimento documentado.

Exemplos de uso como RAG:

- agente de suporte ao usuario que responde duvidas com base no manual
- agente de onboarding que guia novos usuarios pelo sistema
- agente interno que responde perguntas da equipe sobre funcionalidades

## Estrutura sugerida

```text
Manual/
|- 01-introducao.md              — O que e o sistema e como comecar
|- 02-fluxos-principais.md       — Principais fluxos de uso
|- 03-funcionalidades.md         — Descricao de cada funcionalidade
|- 04-perguntas-frequentes.md    — FAQ
|- 05-glossario.md               — Termos e definicoes do dominio
`- assets/                       — Imagens, diagramas e screenshots
```

## Convencoes

- Escreva para o usuario final, sem jargao tecnico desnecessario.
- Mantenha cada arquivo focado em um topico.
- Use linguagem direta e objetiva.
- Atualize o manual sempre que uma feature mudar o comportamento visivel ao usuario.

---

> Para documentacao tecnica interna, use `01-documentacao-tecnica/`.
> Para specs e planejamento, use `04-planejamento-do-produto/`.
