# Feature 0020 - UI Shell and Navigation (Log)

## [0.1.0] - 2026-06-28T00:00:00Z — Inception + Implement (abas por área)

### Input
- Playtest 07 ponto 4: priorizar a refatoração de UI/UX. Decisões do usuário: abas por área
  + ações distribuídas (ver iteration-01).

### Summary
- Scaffold da feature (README, overview, iteration-01, log) + registro no índice.
- (Implementação registrada no próximo bump quando o gate fechar.)

### Next step
- `ActionCard.vue` + refatorar `GameView` em HUD + abas; ajustar `GameView.spec`.

## [0.2.0] - 2026-06-28T00:00:00Z — Implement → Validate → Deploy (abas por área)

### Summary
- **`ActionCard.vue`** (novo): card de ação apresentacional (nome/desc/custo/requisitos +
  botões de esforço com preview de fadiga) que emite `start` — evita duplicar a marcação nas
  3 telas com ações.
- **`GameView` refatorado**: HUD fixo (identidade + calendário + `StatsPanel` + loop-bar
  Avançar) + **barra de abas** (Visão · Banda · Estúdio · Shows · Equipe · Finanças) + só o
  conteúdo da **aba ativa** (v-if). Ações **distribuídas** por tela (`TAB_ACTIONS`):
  Banda = ensaiar/descansar; Estúdio = compor/gravar; Shows = turnê/marketing. Seções
  movidas: Em andamento/Feed → Visão; SongLibrary → Estúdio; VenueList → Shows; StaffPanel →
  Equipe; Custos/Ganhos → Finanças (Custos agora mostra o salário mensal da equipe).
- Overlays de composição/seleção seguem no fluxo do Estúdio; store inalterado (estado
  preservado ao trocar de aba).

### Validate (gate verde)
- `test:unit` 172; `GameView.spec` ajustado com helper `goTab` (navega entre abas).
  `type-check`/`lint`/`build` OK.

### Open questions
- Nenhuma. Futuro: virar rota/URL por aba; responsividade fina; realçar aba com pendências.

### Next step
- Backlog do Playtest 07: cancelar show com consequência (0016), balance da equipe (0013+0003),
  rework da turnê (0014+0016+0008).
