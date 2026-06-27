# Feature 0015 - Songwriting and Releases (Log)

## [0.8.0] - 2026-06-26T00:00:00Z — iteration-03 (gênero na composição + descarte) — G1→G4

### Input
- Playtest 04 pontos 1.1 (escolher gênero/tema ao compor), 5 (descartar músicas), 1.5
  (âncora ao gravar). Leva de iterações com playtest deferido (avaliar em lote).

### Summary
- **D8 — gênero/tema na composição**: `SONG_GENRES` + `pickGenre`; `compose` abre seletor
  de gênero (default = gênero da banda) e tema, com botão 🎲 Aleatório; título segue
  autogerado + editável. `ActionSelection.genre/theme` + `ActiveAction.composeGenre/Theme`.
- **D9 — descartar músicas**: `discardSong(id)` remove música `composed`; música lançada
  não pode ser descartada (botão 🗑 só nas prontas, com confirmação).
- **UX — âncora**: ao abrir o painel de composição/seleção, `scrollIntoView` puxa a visão
  (guardado p/ jsdom).

### Validate (gate verde)
- `test:unit` 140 (+gênero aplicado, +autogeração sem escolha, +descarte composed/released);
  `type-check`/`lint`/`build` OK. Playtest deferido (leva).

### Next step
- (Mesma leva) cachê de show ∝ reputação está na 0014 it-06.

## [0.7.0] - 2026-06-26T00:00:00Z — Implement → Validate → Deploy (slice 4: royalties + aba de Ganhos)

### Input
- Slice 4 da decomposition (D4). Playtest 03 ponto 8 (prioritária): receita de longo
  prazo dos lançamentos + aba de Ganhos espelhando a de Custos.

### Summary (band-quest-game)
- **`data/releases.ts`:** `Release` ganhou `fanBaseAtRelease`, `currentRoyalty` (pago no
  próximo turno) e `totalRoyaltiesEarned`. Novas funções puras: `initialRoyalty(quality,
  fanBase, type)` (∝ qualidade × base de fãs × multiplicador do tipo) e `accrueRoyalty(
  current, decay, days)` (soma geométrica fechada `c·(1−d^n)/(1−d)`; expira ao cair abaixo
  do piso). `ROYALTY_PROFILE` por tipo: **demo** não rende (multiplier 0), **single** cauda
  curta-média (decay 0.96), **álbum** cauda longa (decay 0.985). `createRelease` agora exige
  `fanBase` e semeia o royalty inicial.
- **Store:** `royaltyIncomePerTurn` (soma dos royalties ativos) e `royaltiesEarnedTotal`
  (acumulado da sessão). `advanceDays` chama `accrueRoyalties(days)` antes dos custos:
  credita só a parte inteira no caixa (resíduo fracionário acumulado), decai cada lançamento
  e expira no piso. Royalties reportados como **um evento por virada de mês** (`flushRoyalties`,
  par com os custos mensais) — não inflam a timeline.
- **UI:** nova seção recolhível **Ganhos** no GameView (espelha Custos: royalties/dia +
  total recebido, tom positivo). `SongLibrary` ganhou a coluna **royalty atual** por
  lançamento (`R$ x/dia`, ou `—` quando expirado).

### Validate (gate verde)
- 130 testes (era 117): +13 (releases royalty puros ×6, store royalties ×5, SongLibrary
  coluna ×1, GameView aba ×1).
- type-check, lint, build OK.
- **Playtest manual da receita (compor → single/álbum → ver royalties acumulando):
  DESTRAVADO** e recomendado ao humano — não executado no navegador pela IA.

### Open questions
- Nenhuma. Pesos do royalty (multiplier/decay/piso/peso de fãs) são **placeholders → 0003**.

### Next step
- Resta da 0015: **slice 2** (entrosamento via `rehearse` na qualidade). Demais candidatas
  do Playtest 03: ordenação+cap do SongLibrary (ponto 10), EP/LP (8.1).

## [0.6.0] - 2026-06-26T00:00:00Z — Implement → Validate → Deploy (D6 + D7)

### Input
- Playtest 03 (pontos 4/4.1, 2/3) + quick win ponto 6. Refinamento iteration-02.

### Summary (band-quest-game)
- **Seleção de faixas ao gravar (D6):** `startAction(id, effort?, selection?)` aceita
  `{ songIds, singleIds }` e valida a quantidade; sem seleção mantém o auto-pick. GameView
  ganhou um **painel de seleção inline** ao clicar o esforço de uma gravação (lista as
  músicas com qualidade; álbum também escolhe os 2 singles), com Confirmar/Cancelar.
- **Edição de metadado (D7):** store `editSong(id, {name,genre,theme})` e
  `renameRelease(id, title)`; SongLibrary com edição inline por linha (música e
  lançamento).
- **Quick win (ponto 6):** removido o contador "Músicas prontas" da loop-bar (redundante
  com a aba Músicas).

### Validate (gate verde)
- 117 testes (era 111): +6 (store seleção/edição, GameView picker, SongLibrary edit).
- type-check, lint, build OK.
- Nota de processo: parte dos edits de código-fonte se perdeu numa compactação de
  contexto e foi **reaplicada**; o working tree do docs foi restaurado do HEAD (o commit
  do Playtest 03 estava íntegro).

### Open questions
- Nenhuma. Pools maiores de nomes (ponto 5) e filtro/ordenação avançada (ponto 10.1)
  ficam para depois.

### Next step
- Slice 4 (royalties + aba de Ganhos) — agora prioritária pelo Playtest 03 (ponto 8).
  Slice 2 (entrosamento) segue pendente.

## [0.5.0] - 2026-06-25T00:00:00Z — Implement → Validate → Deploy (slice 5)

### Input
- Slice 5 da decomposition: inventário visível (D5). Destrava o playtest acumulado
  das slices 1 e 3 (músicas/lançamentos antes invisíveis).

### Summary (band-quest-game)
- Store: extraído `computeCalendar(turn)` (puro, exportado) e exposto `calendarAt(t)`
  para formatar a data de um lançamento a partir do `releaseTurn`.
- Novo `components/SongLibrary.vue`: dois painéis recolhíveis (reusa
  `CollapsibleSection`) — **Músicas** (nome · gênero · tema · qualidade · status) e
  **Lançamentos** (tipo · título · data · nº de faixas · qualidade). Ambos colapsados
  por padrão, com contagem no hint. Chips de status/tipo alinhados ao design-system.
- GameView: `<SongLibrary />` inserido após "Em andamento".

### Validate (gate verde)
- 111 testes (era 108): +3 (`SongLibrary.spec.ts`).
- type-check, lint, build OK. Render do inventário coberto por teste.
- **Playtest manual da cadeia (compor → single → álbum): DESTRAVADO** e recomendado
  ao humano — não executado no navegador nesta sessão.

### Open questions
- Nenhuma. Coluna "royalty atual" do inventário entra com a slice 4 (royalties).

### Next step
- Slice 4 (royalties decrescentes) — completa a coluna de receita do inventário e a
  base da aba de Ganhos. Slice 2 (entrosamento) segue pendente.

## [0.4.0] - 2026-06-25T00:00:00Z — Implement → Validate → Deploy (slice 3)

### Input
- Slice 3 da decomposition: cadeia de lançamento (D3). Slice 2 (entrosamento) pulada
  por ora — entra depois.

### Summary (band-quest-game)
- Novo `data/releases.ts`: modelo `Release` (id, type, title, releaseTurn, trackIds,
  quality, consumedByAlbumId) + `RELEASE_RULES` (demo: 3 músicas; single: 1 música;
  álbum: 2 singles + 4 músicas) + `createRelease`/`averageQuality`/`generateAlbumTitle`.
- `actions.ts`: `ActionRequirements.singles`, `ActionDef.release`; record-demo agora
  exige 3 músicas (release demo); record-single 1 música (release single); record-album
  exige 2 singles + 4 músicas (release album).
- Store: `releases[]` + `availableSingles` (singles não absorvidos). Ao iniciar, reserva
  músicas (released) e singles, guardando os ids na ActiveAction; ao concluir, cria o
  `Release` (single herda o nome da faixa; álbum gera título e agrega faixas dos singles
  absorvidos + músicas novas, marcando os singles com `consumedByAlbumId`). Evento nomeia
  o lançamento.
- GameView: cards mostram requisito de `single(s)`.

### Validate (gate verde)
- 108 testes (era 101): +7 (`data/releases.spec.ts` + cadeia single/álbum no store).
- type-check, lint, build OK. Mecânica mudou (gating de álbum/demo), mas releases só
  ficam visíveis na slice 5 ⇒ playtest manual adiado, coberto por testes automatizados.

### Open questions
- Nenhuma. Royalties (receita de longo prazo) = slice 4; entrosamento na qualidade =
  slice 2. Mínimos (3/1/2+4) e custos seguem placeholders (0003).

### Next step
- Slice 4 (royalties decrescentes por lançamento) ou slice 5 (inventário visível, que
  destrava o playtest da cadeia).

## [0.3.0] - 2026-06-25T00:00:00Z — Implement → Validate → Deploy (slice 1)

### Input
- G1 liberado. Slice 1 da decomposition: modelo de música.

### Summary (band-quest-game)
- Novo `data/songs.ts`: modelo `Song` (id, name, genre, theme, quality, status) +
  geração de metadado autogerado (pools IP-safe, gênero herdado da banda) +
  `rollSongQuality` (banda + esforço + variação; entrosamento fica p/ slice 2).
- Store: contador inteiro `songs` → `Song[]`; novo `availableSongs` (status
  `composed`). `compose` cria uma música (evento nomeia a faixa); ações de gravação
  marcam as músicas mais antigas como `released` (mantidas no inventário p/ royalties/
  discografia). `canStartAction`/start/reset migrados.
- GameView: "Músicas prontas" usa `availableSongs.length`.

### Validate (gate verde)
- 101 testes (era 95): +6 (`data/songs.spec.ts` ×5-6 e casos novos no store).
- type-check, lint, build OK. Superfície ao jogador quase idêntica (evento de compor
  agora nomeia a música) ⇒ playtest adiado até a slice de inventário (5) tornar as
  músicas visíveis.

### Open questions
- Nenhuma. Pesos de qualidade e mínimos de lançamento seguem placeholders (0003).

### Next step
- Slice 2 (qualidade: somar entrosamento via `rehearse`) ou slice 3 (cadeia de
  lançamento single/álbum com regras de composição).

## [0.2.0] - 2026-06-25T00:00:00Z — Inception → G1 (Spec pronta)

### Input
- Respostas do usuário às Q1–Q4 (Q5 default).

### Summary
- Decisões D1–D5 registradas na iteration-01:
  - D1 metadado auto + editável; D2 qualidade = banda + esforço + entrosamento(ensaio)
    + variação; D3 cadeia Demo+Single+Álbum (álbum exige X singles + Y músicas);
    D4 royalties decrescentes por turno; D5 inventário consultável em painel recolhível.
- Q1–Q5 movidas para resolvidas; checklist de handoff completo.
- **Gate G1 liberado**: nenhuma bloqueante aberta, iteração aprovada, feature fatiável.

### Open questions
- Nenhuma. Números (N/X/Y, custos, decay, pesos de qualidade) são placeholders de
  balance (0003), a calibrar jogando.

### Next step
- **Implement (game)** — slice 1 da decomposition: substituir o contador `songs` por
  um modelo `Song[]` e fazer `compose` criar uma música (com metadado autogerado).

## [0.1.0] - 2026-06-25T00:00:00Z — Inception (rumo a G1)

### Input
- Decisão de priorização: scaffoldar a 0015 (candidata desde os Playtests 01 e 02).
- Intenção original: música com nome/gênero/tema; cadeia composição→demo/single/álbum
  com mínimos; inventário consultável; "caprichado" mexendo em qualidade/royalties,
  não só custo; base para a futura aba de Ganhos.

### Summary
- Criado o scaffold da feature 0015 (README, planning/overview, refinement/
  {decomposition, checklist, questions, iteration-01, log}, diagrams).
- Decomposição em 5 slices: modelo de música → qualidade → cadeia de lançamento →
  royalties → inventário.
- Abertas Q1–Q5 (Q1–Q3 bloqueantes): profundidade do metadado, origem da qualidade,
  tipos/regras de lançamento, estrutura de royalties, escopo do inventário.

### Open questions
- Q1–Q5 (ver questions.md). Q1–Q3 bloqueiam o handoff (G1).

### Next step
- Resolver as bloqueantes com o usuário, registrar as decisões na iteration-01 e
  passar G1 (Spec pronta) para iniciar a slice 1 (modelo de música).
