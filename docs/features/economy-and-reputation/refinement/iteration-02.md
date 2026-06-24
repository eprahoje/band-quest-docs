# Feature 0003 - Economia e Reputação (Refinamento 02)

> Esta iteração reposiciona a 0003 como o **contrato numérico** do jogo e moderniza
> a feature ao padrão SDD. Por decisão do usuário, fecha-se a **estrutura/fórmulas**
> agora; os **valores concretos** ficam para uma iteração de balance dedicada.

## Decisions

### Caixa pode ficar negativo (dívida) — [Sim, permite dívida]
- O caixa pode ir **negativo**. **Falência** = N turnos consecutivos no vermelho
  (N na iteração de balance), destravando a condição de derrota da 0010.
- **Handoff p/ `band-quest-game`:** remover o trava-zero do caixa em `game.ts`
  (`applyStatDelta` usa `Math.max(0, cash + delta)` — passa a permitir negativo).

### Reputação decai se inativa — [Decai se inativo]
- Sem atividade qualificadora (show/lançamento) por um intervalo, a reputação **cai
  gradualmente** ("use it or lose it"). Variável: `reputationDecayPerTurn` aplicada
  quando não houve atividade nos últimos `K` turnos (valores no balance).

### Cadência granular + ações multi-turno — [resposta custom do usuário]
- O turno **não** equivale a um ano; mapeia uma unidade de calendário **mais
  granular** (semana/mês — a fixar com a 0008).
- **Ações têm duração variável em turnos**: uma ação consome `N` turnos conforme
  escopo/qualidade (ex.: gravar álbum depende da qualidade-alvo e do produtor; turnê
  ocupa vários turnos). Objetivo: ritmo realista de carreira, evitando "0 ao 1000".
- Custos recorrentes (salários de staff 0013, decay de reputação) acumulam por turno.
- **Desdobramento aberto** (Q3): unidade exata de calendário + **modelo de duração
  de ações** — cross-cutting (0008 + core loop); ver `questions.md`.

### Estrutura agora, números depois — [Só estrutura, números depois]
- Fecham-se aqui **variáveis, faixas e a forma das fórmulas**; os **valores** vão
  para uma **iteração de balance** dedicada, perto da implementação.

## Contrato (forma das fórmulas consumidas por outras features)
- **Nota final (0010):** média ponderada de status positivos (fãs, caixa, reputação,
  prêmios, discos vendidos, streams, álbuns) menos negativos, com **faixas de estrela
  × fator de duração**. Pesos e cortes = balance.
- **Derrota (0010):** falência = `N` turnos de caixa negativo; dissolução = `M`
  turnos de fadiga/moral no piso.
- **Recompensas de marcos (0011):** valores de `cash`/`reputation`/`scoreBonus` por
  marco/tier.
- **Itens (0012):** `cost` e `effects.modifier` por item.
- **Staff (0013):** custo de contratação e salário por turno por papel.

## Questions
- Q3 (calendário/duração de ações) e demais follow-ups abertos em `questions.md`.

## Checklist result
- [x] Scope reviewed.
- [x] Questions updated.
- [ ] Handoff reviewed.
