# Feature 0014 - Core Loop and Actions (Log)

## [0.13.0] - 2026-06-27T00:00:00Z — balance da turnê (Playtest 05 ponto 9)

### Input
- Playtest 05 ponto 9: um show na Casa de Shows Aurora rendia mais que uma turnê de 14
  dias. Causa: o show escala com fãs (bilheteria) e a turnê era um valor fixo → conforme
  os fãs crescem, o show sempre vence.

### Summary
- A turnê passa a ter **cachê escalado por fãs** (toca para a base em várias praças):
  `cash = (TOUR_GUARANTEE + fãs × TOUR_CASH_PER_FAN) × esforço × multiplicador de reputação`
  (placeholders 1500 / 30 → 0003). Override no `completeAction` para `category === 'tour'`,
  substituindo o cash fixo do catálogo. Reputação/fãs/fadiga da turnê seguem como antes.

### Validate (gate verde)
- `test:unit` 158 (+turnê escala com fãs e supera a bilheteria de um show grande).
  `type-check`/`lint`/`build` OK. Playtest deferido (leva).

### Next step
- Gate de staff para locais maiores (Playtest 05 ponto 7) — depende da iteração da 0013.

## [0.12.0] - 2026-06-26T00:00:00Z — iteration-07 (reputação por faixa) — G1→G4

### Input
- Playtest 04 ponto 4 (feedback): reputação do show não precisa ser fixa; sortear entre
  N e M (ex.: 1–5). Refina a it-06.

### Summary
- `ActionOutcome.reputationRange [min,max]`; `resolveOutcome` sobrepõe a reputação por um
  inteiro sorteado. `play-show` → `[1, 5]` (removido o `reputation` fixo). Cachê ∝
  reputação (it-06) mantido. Números = placeholders (0003).

### Validate (gate verde)
- `test:unit` 141 (+faixa sorteada dentro de [1,5]; teste-base do show ajustado p/ 3 com
  rng 0.5). `type-check`/`lint`/`build` OK. Playtest deferido.

## [0.11.0] - 2026-06-26T00:00:00Z — iteration-06 (cachê ∝ reputação) — G1→G4

### Input
- Playtest 04 ponto 4 (+ Playtest 03 ponto 7, aberto): shows rendem pouco mesmo com a
  reputação subindo; ganho de reputação parecia fixo em +1. Leva de iterações (playtest deferido).

### Summary
- **Cachê ∝ reputação**: flag `cashScalesWithReputation` (play-show, tour);
  `resolveOutcome` aplica `reputationCashMultiplier` ao cash positivo; store calcula
  `1 + reputação × REP_CASH_FACTOR` (0.01 → +50% a rep 50, +100% a rep 100).
- **Reputação do show 1 → 2**: deixa de cair sempre em +1 por arredondamento.
- Números = placeholders de balance (0003).

### Validate (gate verde)
- `test:unit` 140 (+cachê escala com reputação no resolveOutcome e no store); teste-base
  do show atualizado (rep 2). `type-check`/`lint`/`build` OK. Playtest deferido.

## [0.10.0] - 2026-06-26T00:00:00Z — Inception → Implement → Validate → Deploy (G1→G4)

### Input
- Proposta do usuário após o playtest da it-04: (a) mostrar quanto cada ação custa de
  fadiga ANTES de iniciar; (b) em vez de travar a fadiga em 100, deixar estourar e
  promover CONSEQUÊNCIAS. Modelo de consequência validado (G1): **ganhos reduzidos +
  perda de reputação**, escalando com o excesso. Ver iteration-05.

### Summary
- **Preview de fadiga no card** (`GameView`): cada botão de esforço mostra o custo de
  fadiga (`fatiguePerDay × duração`); descanso mostra a recuperação; aviso (⚠, cor ember)
  quando iniciar ultrapassaria 100.
- **Sem teto superior de fadiga** (`applyStatDelta`): removido o `min(100, …)`; mantido o
  piso 0. O overflow acima de 100 é intencional.
- **Consequências do excesso** (`completeAction`): ao concluir com fadiga > 100, os ganhos
  positivos da ação são reduzidos por `1 − min(excesso × 0.01, 0.5)` e a reputação leva um
  golpe de `−round(excesso × 0.1)`; mensagem ganha sufixo de flavor. Números = placeholders
  de balance (0003).

### Validate (gate verde)
- `test:unit` 135 (era 134; +1: estouro reduz ganhos + reputação, sem teto); teste de
  clamp atualizado (piso 0, sem teto). `type-check`, `lint`, `build` OK.

### Open questions
- Nenhuma. Calibragem das penalidades/curva → iteração de balance da 0003.

### Next step
- Playtest humano do feel (ver o ⚠ e sentir o peso do estouro); seguir backlog do
  Playtest 04 (gênero na composição / gravadoras / descartar músicas).

## [0.9.1] - 2026-06-26T00:00:00Z — fast-track (UX/reporting)

### Input
- Report imediato do playtest da it-04: shows e descansos pararam de mostrar o ganho/
  recuperação de fadiga nos acontecimentos (efeito colateral de tirar a fadiga dos
  `outcome.metrics`).

### Summary
- `completeAction` volta a anexar o **chip de fadiga** ao evento de conclusão, atribuindo
  o total da ação (`fatiguePerDay × totalTurns`) — só para exibição, sem reaplicar ao
  estado (a fadiga continua acumulando por dia no avanço). Show = +18 (neg); descanso =
  −30 (pos). Sem mudança de mecânica.
- 134 testes (era 133; +1 chip de recuperação do descanso); chip de show restaurado no
  teste de efeitos. Gate verde (type-check/lint/build OK).

## [0.9.0] - 2026-06-26T00:00:00Z — Inception → Implement → Validate → Deploy (G1→G4)

### Input
- **Playtest 04** (pontos 2 e 6): turnê nacional não cansava e gravar álbum "zerava"
  a fadiga. Investigação no código confirmou bug estrutural; modelo de correção
  validado com o usuário (G1) → **fadiga por dia (proporcional)**. Ver iteration-04.

### Summary
- **Modelo de fadiga por dia** (`fatiguePerDay` em `ActionDef`): a fadiga de uma ação
  passa a acumular **proporcional à duração**, enquanto a ação está em curso, em vez do
  antigo lump-sum na conclusão. Removida a fadiga de `outcome.metrics` de todas as ações.
- **Recuperação passiva só em dias ociosos**: `applyFatigueForSpan(days)` no store soma
  `fatiguePerDay × days` das ações ativas e só aplica o passivo (`-1/dia`) quando **não
  há ação `main` em curso**. `rest` recupera pela própria taxa negativa (−6/dia).
- Resultado: turnê nacional (45d) cansa **+90**; mini (14d) **+28**; gravar álbum (35d)
  **acumula ~+53** (não zera). Pontos 2 e 6 resolvidos na raiz; P03 9.1 absorvido.
- Trade-off aceito: a fadiga deixa de ser `chip` no evento de conclusão (sobe gradual
  no painel de stats). Números são placeholders de balance (0003).

### Validate (gate verde)
- `test:unit` 133 (era 130; +3: turnê proporcional, álbum não zera, passivo suspenso
  durante ação main); `type-check`, `lint`, `build` OK. Playtest manual (feel) fica com
  o humano — a lógica do bug está coberta por teste determinístico.

### Open questions
- Nenhuma. Calibragem fina das taxas → iteração de balance da 0003.

### Next step
- Playtest humano para confirmar o feel; seguir o backlog do Playtest 04 (gênero na
  composição / gravadoras / descartar músicas) ou balance de cachê de show.

## [0.8.0] - 2026-06-25T00:00:00Z — Implement → Validate → Deploy (G2→G3→G4)

### Input
- Fast-track de UX (regra de escala do AI-DLC): quick wins adiados dos Playtests 01
  e 02 — timeline inflando a página (P01 ponto 12) e painéis sempre expandidos
  (P02 ponto 4). Sem mudança de mecânica/economia.

### Summary
- **Timeline com cap + rolagem** (`EventFeed.vue`): renderiza só os 40 acontecimentos
  mais recentes, com `max-height`/scroll e aviso de quantos ficaram ocultos. O feed
  deixa de inflar a altura da página.
- **Painéis recolhíveis**: novo componente reutilizável `CollapsibleSection.vue`
  (header-botão com chevron, `aria-expanded`, slot, `hint` opcional). No `GameView`
  as seções Custos, Banda, Em andamento e Ações viraram recolhíveis; `StatsPanel` e a
  loop-bar de avanço permanecem fixas (controle principal sempre à vista).
- Tipografia do header reaproveita `.section-title` (tokens.css), sem novo token.

### Validate (gate verde)
- 95 testes (era 90): +3 `CollapsibleSection.spec.ts`, +2 `EventFeed.spec.ts`.
- type-check, lint e build OK. Mudança UI-only ⇒ sem playtest manual exigido.

### Open questions
- Nenhuma. Backlog futuro: histórico completo separado / poda de eventos no store.

### Next step
- Voltar ao backlog: features candidatas 0015 (Songwriting) e 0017 (Contracts) ou
  balance pass 2 (0003).

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

## [0.7.0] - 2026-06-24T00:00:00Z

### Input
- Refinamento do modelo de ação durante o balance da 0003 (iteration-05).

### Summary
- Adicionado `outcomeModifier` à `ActionEffortOption`: o esforço passa a **modular o
  resultado** (escala ganhos positivos), não só o custo/duração. Corrige o caso em
  que opções "caprichado" eram estritamente piores (mais caro/lento, mesmo retorno).
- `resolveOutcome` aplica `outcomeModifier` junto do modulador de qualidade da banda.

### Open questions
- Nenhuma.

### Next step
- Continuar o balance (0003) e seguir para fim de sessão (0010) e marcos (0011).
