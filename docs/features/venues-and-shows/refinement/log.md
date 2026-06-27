# Feature 0016 - Venues and Shows (Log)

## [0.3.0] - 2026-06-27T00:00:00Z — slice 1 (catálogo + desbloqueio) — Implement→Validate→Deploy

### Input
- G1 liberado (it-02). MVP slice 1: catálogo de locais + desbloqueio por reputação + fãs.

### Summary
- `data/venues.ts`: modelo `Venue` (id, name, tier, capacity, region, repThreshold, minFans)
  + `VENUE_TIER_LABEL` + catálogo `VENUES` (um por tier: bar/casa/ginásio/estádio) +
  `isVenueUnlocked` / `missingRequirement` / `getVenue`. `region` = "Nacional" (gancho do
  híbrido futuro). Números = placeholders (0003).
- `stores/game.ts`: computed `venueCatalog` (cada local + `unlocked` + `missing` derivados
  da reputação/fãs atuais), exportado.
- `components/VenueList.vue`: seção recolhível "Locais" (reusa CollapsibleSection) com
  tier, capacidade e estado liberado/🔒 + requisito que falta; hint = liberados/total.
  Inserida no GameView após a SongLibrary.

### Validate (gate verde)
- `test:unit` 147 (era 141; +venues.spec: desbloqueio exige rep E fãs, requisito que falta,
  capacidades crescentes; +store: catálogo só com o bar liberado no início, desbloqueio ao
  cruzar limiares). `type-check`/`lint`/`build` OK. Playtest deferido (leva).

### Open questions
- Nenhuma. Slice 1 é informativa (sem booking ainda — vem na slice 2).

### Next step
- **Slice 2**: agendar show no local (compromisso datado) + receita cachê+bilheteria
  (substitui o `play-show` imediato da 0014).

## [0.2.0] - 2026-06-27T00:00:00Z — Inception → G1 (spec pronta)

### Input
- Respostas do usuário a Q1–Q4 (bloqueantes); Q5/Q6 fechadas como escopo.

### Summary
- **D1 (Q1):** MVP com tiers abstratos; objetivo final híbrido (regiões/cidades) — futuro.
- **D2 (Q2):** desbloqueio por **reputação + fãs**.
- **D3 (Q3):** receita = **cachê base + bilheteria** (`min(fãs, capacidade) × preço`),
  preço fixo por tier no MVP (escolha de preço = evolução).
- **D4 (Q4):** show é **compromisso datado** (agenda → acontece no dia; faltar penaliza).
- **D5 (Q5):** turnê fica na 0014 por ora; vira trajeto numa slice futura (0013).
- **D6 (Q6):** MVP = slice 1 (catálogo + desbloqueio) → slice 2 (agendar + cachê+bilheteria).
- Decomposição consolidada (5 slices; MVP = 1 e 2). Questões movidas para resolvidas.

### Open questions
- Nenhuma. Números (capacidades, preços, limiares, atratividade) = placeholders (0003).

### Next step
- **G1 ✅** — iniciar Implement da **slice 1** (modelo `Venue` + catálogo + desbloqueio).

## [0.1.0] - 2026-06-27T00:00:00Z — Inception (kickoff, rumo a G1)

### Input
- Decisão de priorização: scaffoldar a 0016 (candidata desde os Playtests 01, 03 e 04).
  Intenção: locais por reputação, venda de ingressos, agenda/calendário de shows e turnê;
  base geográfica para a turnê a partir do estado de origem.

### Summary
- Criado o scaffold da feature (README, planning/overview, refinement/{decomposition,
  checklist, questions, iteration-01, log}, diagrams).
- Decomposição provisória em 5 slices (catálogo → escolha do local → ingresso → agenda →
  turnê-trajeto).
- Abertas Q1–Q6 (Q1–Q4 bloqueantes): geografia, desbloqueio, receita por ingresso, agenda;
  Q5 (turnê/staff) e Q6 (MVP) em discussão.

### Open questions
- Q1–Q6 (ver questions.md). Q1–Q4 bloqueiam o handoff (G1).

### Next step
- Resolver as bloqueantes com o usuário, registrar as decisões na iteration-01 e passar G1.
