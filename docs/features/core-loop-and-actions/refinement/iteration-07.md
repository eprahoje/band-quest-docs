# Feature 0014 - Core Loop and Actions (Refinement 07)

> Ajuste do Playtest 04 ponto 4 (feedback do usuário): reputação do show não precisa ser
> um valor fixo escalado — pode ser **um número aleatório entre N e M**. Refina a it-06.

## Decisão — reputação por faixa aleatória
- Novo `ActionOutcome.reputationRange?: [min, max]`. Quando presente, `resolveOutcome`
  **sobrepõe** `metrics.reputation` por um inteiro sorteado no intervalo.
- `play-show`: reputação passa a ser **1–5** aleatório (`reputationRange: [1, 5]`), em vez
  da base fixa 2 da it-06. O cachê ∝ reputação (it-06) permanece.
- Números = placeholders de balance (0003).

## Implementação
- `data/actions.ts`: `ActionOutcome.reputationRange`; roll no `resolveOutcome` (após o
  laço de métricas); `play-show` com `[1, 5]` (removido `reputation` fixo do `metrics`).

## Checklist result
- [x] Scope reviewed.
- [x] Questions updated — nenhuma bloqueante.
- [x] Handoff reviewed — entregue na leva; playtest deferido.
