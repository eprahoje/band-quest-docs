# Feature 0014 - Core Loop and Actions (Refinement 06)

> Derivada do **Playtest 04** (ponto 4) + Playtest 03 (ponto 7, aberto). Leva de
> iterações com playtest deferido. Números = placeholders de balance (0003).

## Problema
- Shows locais rendem o mesmo cachê independentemente da reputação ("geram pouco mesmo com
  a reputação crescendo"). Além disso, o ganho de reputação por show caía sempre em **+1**
  (base 1 arredondada) — parecia fixo.

## Decisões
### Cachê escala com a reputação
- Novo flag `ActionDef.cashScalesWithReputation` (true para `play-show` e `tour`).
- `resolveOutcome` recebe `reputationCashMultiplier` no contexto e multiplica o **cash
  positivo** dessas ações por ele.
- O store calcula `multiplicador = 1 + reputação × REP_CASH_FACTOR` (`0.01` →
  reputação 50 paga +50% de cachê; 100, +100%).

### Ganho de reputação por show menos trivial
- Base de reputação do `play-show` sobe de **1 → 2** (deixa de cair sempre em +1 pelo
  arredondamento). Ajuste pequeno; calibragem fina fica na 0003.

## Implementação (band-quest-game)
- `data/actions.ts`: flag `cashScalesWithReputation`; `ResolveContext.reputationCashMultiplier`;
  aplicação no `resolveOutcome`; `play-show` (rep 2) e `tour` marcados.
- `stores/game.ts`: `REP_CASH_FACTOR`; passa o multiplicador no `completeAction`.

## Checklist result
- [x] Scope reviewed.
- [x] Questions updated — nenhuma bloqueante (números = placeholders/0003).
- [x] Handoff reviewed — entregue na leva; playtest deferido. Resolve P04 ponto 4 + P03 ponto 7.
