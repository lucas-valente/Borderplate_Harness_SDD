> **Prompt: Commit workflow**
> Atue como um Engenheiro de Software Sênior. Acabei de realizar alterações críticas ou de lógica no código. Execute o seguinte workflow:
>
> ---
> ## VALIDAÇÕES OBRIGATÓRIAS (NÃO PULE ESTA ETAPA!)
>
> ### 1. EXECUTAR TESTES — OBRIGATÓRIO
> ```bash
> [customize: npm run test:unit | pytest | go test ./... | etc.]
> ```
> **SE OS TESTES FALHAREM: PARE IMEDIATAMENTE!**
> - Informe quais testes falharam
> - Corrija os testes ANTES de prosseguir
> - NÃO gere mensagem de commit se houver testes falhando
>
> ### 2. EXECUTAR BUILD — OBRIGATÓRIO
> ```bash
> [customize: npm run build | ./gradlew build | cargo build | etc.]
> ```
> **SE O BUILD FALHAR: PARE IMEDIATAMENTE!**
> - Informe os erros de compilação
> - Corrija os erros ANTES de prosseguir
> - NÃO gere mensagem de commit se o build falhar
>
> ### 3. VERIFICAR MIGRAÇÕES DE BANCO (se houver mudanças no schema)
> ```bash
> [customize per ORM: prisma migrate status | alembic current | flyway info | etc.]
> ```
>
> ---
> ## SOMENTE APÓS TODAS AS VALIDAÇÕES PASSAREM:
>
> 1. **Análise:** Analise o `git diff --staged`. Identifique a lógica de fluxo e o problema de negócio/técnico resolvido.
> 2. **Commit Visual:** Gere uma mensagem de commit usando **exatamente** o template abaixo.
>
> **Template Obrigatório:**
>
> ```text
> <Emoji> <TIPO EM MAIÚSCULO>: <Título imperativo>
>
> **Problema corrigido:** (ou **Contexto Atual:**)
>
>   - <O que estava errado ou faltando antes?>
>   - <Quais eram os sintomas ou erros?>
>
> **Alterações:**
>
>   - <Lista técnica do que foi implementado>
>   - <Detalhes específicos de arquivos/funções>
>
> **Fluxo correto:** (Obrigatório se houve mudança de lógica)
>
> 1. <Passo 1 da nova lógica>
> 2. <Passo 2 da nova lógica>
> 3. <Passo 3...>
>
> **Segurança:** (Se aplicável)
> <Nota sobre como isso melhora a segurança ou previne erros>
>
> Fixes: #<issue_id>
> ```
>
> **Emojis sugeridos:** 🚨 (Crítico/Bug), 🔒 (Segurança), ⚡ (Performance), 🐛 (Fix simples), 🔄 (Fluxo/Lógica), ✨ (Nova feature), ♻️ (Refator), 📝 (Docs), 🔧 (Config/Chore).
>
> Forneça os comandos de teste primeiro, e em seguida a mensagem formatada.
