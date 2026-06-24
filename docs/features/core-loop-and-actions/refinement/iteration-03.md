# Feature 0014 - Core Loop and Actions (Refinement 03)

> Revisão derivada do Playtest 01 (ponto 1) + decisão de avanço de tempo.
> Turno = **dia** (0008 iteration-02 / 0003 iteration-04).

## Decisions

### Durações das ações passam a ser em DIAS
- O turno é o **dia**. As `durationTurns` do catálogo passam a representar **dias**.
- Placeholders de balance (0003) em dias, ex.: show 1, ensaio 2–4, compor ~5,
  demo ~3, single ~10–16, álbum ~35–50, turnê ~14–45, marketing ~14, descanso ~5.
  (Números finais na iteração de balance.)

### Avanço de tempo orientado por ações — "pula para a próxima conclusão"
- O jogador **não avança dia a dia**. O tempo avança ao executar ações:
  - Iniciar uma ação principal a enfileira pelos seus N dias.
  - Um botão único **"Avançar"** salta o relógio até a **próxima conclusão de ação**
    (o menor `turnsRemaining` entre as ações ativas), concluindo o que chega a zero e
    decrementando o restante.
  - Sem ações ativas, "Avançar" dá um passo mínimo de 1 dia (evita beco sem saída).
- Mantém o foco em **decisões**, não em cliques, mesmo com sessões de milhares de dias.
- Ações `background` continuam correndo em paralelo e podem concluir antes da `main`.

### Calendário exibido: Ano · Mês · Dia
- 12 meses × 30 dias = 360 dias/ano (dono: 0008). Ex.: "Ano 1 · Março, dia 12".

## Implementação (band-quest-game)
- `actions.ts`: durações reinterpretadas em dias (ajuste de placeholders).
- `game.ts`: `calendar` passa a derivar Ano/Mês/Dia (360); `advanceTurn` vira avanço
  por N dias até a próxima conclusão (`advanceToNextCompletion`).
- `GameView`: badge de calendário e botão "Avançar" para a próxima conclusão.

## Checklist result
- [x] Scope reviewed.
- [x] Questions updated.
- [x] Handoff reviewed.
