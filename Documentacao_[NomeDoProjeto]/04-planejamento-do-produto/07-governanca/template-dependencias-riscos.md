# Mapa de Dependências e Riscos

**Release**: 0.0.1  
**Última atualização**: 2026-04-20

---

## Dependências Estruturais

### Internas (entre features desta release)

| Dependência | Bloqueada por | Estado | Mitigação |
|-------------|---------------|--------|-----------|
| Feature B depende de estar ligada à Feature A | Feature A pronta | 🟡 Em andamento | Paralelizar se possível |

### Externas (fora da release)

| Dependência | O que bloqueia | Estado | Mitigação |
|-------------|---------------|--------|-----------|
| API do [Sistema X] | Integração em Feature Y | 🟡 Em progresso | Usar mock em dev até estar pronto |
| Dados de [Sistema Z] | Seed de dados em prod | 🟡 Em progresso | Executar migration logo após deploy |

---

## Riscos Técnicos

| ID | Risco | Impacto | Probabilidade | Prioridade | Mitigação | Dono |
|----|-------|--------|---------------|-----------|-----------|------|
| RT-001 | [Risco TI A] | Alto | Média | 🔴 Crítico | [Ação] | [NOME] |
| RT-002 | [Risco TI B] | Médio | Baixa | 🟡 Alto | [Ação] | [NOME] |

---

## Riscos de Produto

| ID | Risco | Impacto | Probabilidade | Prioridade | Mitigação | Dono |
|----|-------|--------|---------------|-----------|-----------|------|
| RP-001 | [Risco Prod A] | Alto | Alta | 🔴 Crítico | [Ação] | [NOME] |
| RP-002 | [Risco Prod B] | Médio | Média | 🟡 Alto | [Ação] | [NOME] |

---

## Decisões Arquiteturais Importantes

Consulte `decisoes/` para ADRs completos.

**Decisão 1**: [Descrição]  
**Rationale**: Por quê essa escolha  
**Data**: 2026-04-20  
**Status**: ✅ Aprovada

---

## Status de Blocker

🟢 **Nenhum blocker ativo** (em 2026-04-20)

Se houver blocker:
🔴 **Blocker ID**: [Descrição]  
— Impacto: [O que está parado]  
— ETA de resolução: [Data]  
— Owner: [NOME]

---

**Mantido por**: [NOME]  
**Revisto em**: 2026-04-20  
**Próxima revisão**: [DATA]
