# Feature 0015 - Songwriting and Releases (Log)

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
