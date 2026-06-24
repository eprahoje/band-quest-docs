# Feature 0014 - Core Loop and Actions (Log)

## [0.1.0] - 2026-06-23T00:00:00Z

### Input
- Desdobramento da Q3 da 0003: o usuário definiu que ações consomem N turnos
  conforme escopo/qualidade e que isso vira uma feature própria de core loop.

### Summary
- Criado o scaffold da feature 0014 (README, diagrams, planning/overview,
  decomposition, checklist, questions, iteration-01, log).
- Registrada nos índices (`features/README.md` e `roadmap.md`).
- Abertas Q1–Q4 (conjunto de ações, uma vs. várias, qualidade × duração, falha/
  variação de resultado).

### Open questions
- Q1, Q2, Q3, Q4 — ver `questions.md`.

### Next step
- Refinar Q1–Q4, fechar o modelo de ação e o conjunto inicial; depois substituir as
  ações hardcoded do `GameView` pela mecânica formal.

## [0.2.0] - 2026-06-23T00:00:00Z

### Input
- Usuário respondeu Q1–Q4. Q1: essenciais + marketing/demo. Q2: uma principal +
  passivas de fundo (lanes main/background). Q3: híbrido (faixa de esforço + recursos
  modulam). Q4: variação leve + eventos (0009).

### Summary
- Q1–Q4 resolvidas e movidas para "Resolved Questions"; criado `iteration-02.md`.
- Criado `planning/design.md` com o modelo `ActionDef`/`ActiveAction`, o ciclo de
  vida (idle → in-progress → completed) e o catálogo inicial (9 ações).
- Status → **Ready for Implementation** (estrutura + catálogo); valores no balance.

### Open questions
- Nenhuma bloqueante. Catálogo aberto a refino do usuário.

### Next step
- Virada para implementação: aplicar o ajuste do caixa (0003), implementar o modelo
  de ação da 0014 no jogo e abrir a iteração de balance da 0003 com os números.

## [0.3.0] - 2026-06-23T00:00:00Z

### Input
- Implementação no `band-quest-game` (passos 1+2 da virada): caixa com dívida (0003)
  + modelo de ação da 0014.

### Summary
- `src/data/actions.ts`: catálogo declarativo de 9 ações (espelho do `design.md`),
  tipos (`ActionDef`/lanes/esforço/requires/produces) e `resolveOutcome` puro
  (qualidade + variância + custo por esforço), com números placeholder (balance 0003).
- `src/stores/game.ts`: motor de ações (start/canStart/advanceTurn com conclusão por
  duração, músicas como insumo, lanes main/background, modulação por qualidade da
  banda), calendário turno=semana (`calendar`, `WEEKS_PER_YEAR`), seam de RNG.
- `GameView.vue`: UI orientada ao catálogo (esforços, "em andamento", "avançar
  semana", músicas), substituindo as ações hardcoded.
- Testes: `actions.spec.ts` (catálogo + resolveOutcome), motor + calendário no
  `game.spec.ts`, `GameView.spec.ts`. 70 testes passando; type-check, lint e build OK.

### Open questions
- Nenhuma bloqueante. "Reduz variância" do ensaio e interrupção por evento (0009)
  ficaram como notas (não implementadas nesta slice).

### Next step
- Iteração de balance da 0003 (números reais). Depois: fim de sessão da 0010 (nota
  em estrelas + derrota) e marcos da 0011.

## [0.4.0] - 2026-06-24T00:00:00Z

### Input
- Feedback do Playtest 01 (ver `docs/playtests/playtest-2026-06-24.md`).

### Summary
- Registrados os pontos que tocam a 0014 (não implementados — backlog):
  - **BUG (ponto 2):** soft-lock de descanso — `canStartAction` bloqueia toda ação
    `main` quando `isFatigued`, incluindo `rest`. Isentar `rest` do bloqueio por
    fadiga (correção rápida; defeito desta slice).
  - Granularidade do turno (ponto 1): reavaliar durações se turno virar dia.
  - Preços/requisitos visíveis + impactos nos eventos (ponto 4).
  - Marketing desbloqueável via staff/agência (ponto 9).
  - Turnê com requisito mais alto + gate por staff (pontos 10/11).

### Open questions
- Nenhuma nova bloqueante; itens acima viram trabalho de próximas sessões.

### Next step
- Corrigir o bug de descanso (rápido) e tratar os demais pontos junto do balance da
  0003 e das candidatas 0015/0016.

## [0.5.0] - 2026-06-24T00:00:00Z

### Input
- Retomada da sessão: corrigir o bug do descanso (playtest, ponto 2).

### Summary
- **BUG resolvido:** adicionado `allowWhenFatigued` ao `ActionDef` (marcado em
  `rest`); `canStartAction` só bloqueia ação `main` por fadiga quando
  `!allowWhenFatigued`. Elimina o soft-lock (descansar exausto). Coberto por teste
  (`game.spec.ts`, 71 testes passando).

### Open questions
- Nenhuma. Próximo: granularidade do turno (semana → dia).

### Next step
- Decidir e implementar turno = dia (ponto 1); depois, iteração de balance da 0003.

## [0.6.0] - 2026-06-24T00:00:00Z

### Input
- Decisão de granularidade (Playtest 01, ponto 1): turno = dia + avanço por ações.

### Summary
- Criado `iteration-03.md`: durações das ações em **dias**; **tempo avança pelas
  ações** — botão "Avançar" salta para a próxima conclusão (menor `turnsRemaining`);
  calendário exibido como Ano · Mês · Dia (360/ano). Decisão casada com a 0008
  (iteration-02) e a 0003 (iteration-04).

### Open questions
- Nenhuma nova bloqueante.

### Next step
- Implementar (calendário dia + advanceToNextCompletion + durações em dias) e seguir
  para o balance da 0003.
