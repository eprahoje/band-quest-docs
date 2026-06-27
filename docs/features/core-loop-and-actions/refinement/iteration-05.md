# Feature 0014 - Core Loop and Actions (Refinement 05)

> Evolução do modelo de fadiga (it-04) a partir do playtest: **transparência** do
> custo + **consequências** por excesso, em vez de travar a mecânica num teto.
> Decisão validada com o usuário (G1): consequência = **ganhos reduzidos + perda de
> reputação**, escalando com o excesso. Sem teto superior de fadiga.

## Problema / intenção

1. O jogador não vê **quanto de fadiga** cada ação custa antes de iniciá-la (só vê
   custo em R$, duração e requisitos).
2. A fadiga era **clampada em 100**. Isso "limita a mecânica": uma turnê longa que
   deveria esgotar a banda simplesmente parava em 100, sem penalidade. O usuário
   prefere **deixar estourar** (ex.: 120) e **promover consequências**.

## Decisões

### D1 — Preview de fadiga no card da ação
- Cada opção de esforço passa a exibir o **custo de fadiga** = `fatiguePerDay ×
  durationTurns` (ex.: "Turnê nacional · 45 dias · +90 fadiga"). Descanso mostra a
  **recuperação** ("−30 fadiga").
- Se iniciar a ação **ultrapassaria 100** (`fadiga atual + custo > 100`), o card
  marca um **aviso** (a ação é permitida — só sinaliza o desgaste).

### D2 — Sem teto superior de fadiga (overflow intencional)
- `applyStatDelta` deixa de clampar a fadiga em 100 (mantém o **piso 0**). A fadiga
  pode chegar a 120, 160… O bloqueio de iniciar nova ação `main` segue em `≥ 80`
  (`isFatigued`); o overflow vem do acúmulo de uma ação longa já em curso.

### D3 — Consequências do excesso (ao concluir com fadiga > 100)
Seja `excesso = max(0, fadiga − 100)` no momento da conclusão (a fadiga já foi
acumulada no avanço). Quando `excesso > 0`, a ação é avaliada como "no limite":
- **Ganhos reduzidos:** os ganhos positivos da ação (cachê, fãs, reputação) são
  multiplicados por `(1 − penalidade)`, com `penalidade = min(excesso × 0.01, 0.5)`
  (−1% por ponto acima de 100, teto de −50%). → "não ganhou tudo que poderia".
- **Perda de reputação:** golpe adicional `−round(excesso × 0.1)` de reputação
  (banda se exibiu esgotada → imagem ruim).
- O acontecimento sinaliza o desgaste (chips já refletem ganhos menores + reputação
  negativa; mensagem ganha um sufixo de flavor).

Números são **placeholders de balance (0003)**.

## Implementação (band-quest-game)
- `stores/game.ts`:
  - constantes `FATIGUE_SOFT_CAP=100`, `OVEREXERTION_GAIN_PENALTY_PER_POINT=0.01`,
    `OVEREXERTION_GAIN_PENALTY_MAX=0.5`, `OVEREXERTION_REP_PENALTY_PER_POINT=0.1`.
  - `applyStatDelta`: remover o `Math.min(100, …)` da fadiga (manter piso 0).
  - `completeAction`: antes de `applyStatDelta`, aplicar a penalidade de excesso aos
    `deltas` (reduzir ganhos positivos + golpe de reputação) quando `excesso > 0`;
    sufixo de flavor na mensagem.
- `views/GameView.vue`: helpers `fatigueCost(action, effort)` e
  `wouldOverexert(action, effort)`; exibir o custo de fadiga em cada botão de esforço
  e o aviso de estouro.
- `components/StatsPanel.vue`: sem mudança — "130/100" + borda de aviso (≥80) já
  comunicam o overflow.

## Checklist result
- [x] Scope reviewed.
- [x] Questions updated — nenhuma bloqueante (números são placeholders/0003).
- [x] Handoff reviewed — **G1 liberado** (modelo de consequência validado pelo usuário).
