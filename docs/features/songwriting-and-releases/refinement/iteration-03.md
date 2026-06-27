# Feature 0015 - Songwriting and Releases (Refinement 03)

> Derivada do **Playtest 04** (pontos 1.1, 1.5, 5). Leva de iterações com playtest
> deferido pelo usuário (avaliar em lote). Reavalia a edição livre da D7.

## Decisions

### D8 — Gênero e tema escolhidos NA composição (ponto 1.1)
- Ao iniciar **Compor**, abre-se um seletor: **gênero** (lista `SONG_GENRES`, default = o
  gênero da banda) e **tema** (lista `SONG_THEMES`), com um botão **🎲 Aleatório** que
  sorteia ambos (agilidade, evita repetição manual).
- O **título** continua **autogerado e editável** depois (mantém a D1). A escolha de
  gênero/tema deixa de ser só "edição pós-fato" (D7) e passa a ser uma **decisão de autoria
  no ato de compor**.
- A edição inline na aba Músicas (D7) **permanece** para ajustes posteriores.
- A lista de gêneros é estática nesta iteração; a **evolução por época** ("invenção" de
  gêneros ao longo do tempo, pontos 1.2/1.3) é responsabilidade da **0008** (futuro).

### D9 — Descartar músicas (ponto 5)
- O jogador pode **descartar** uma música com status `composed` na aba Músicas (botão 🗑,
  com confirmação). Música **lançada** (`released`) não pode ser descartada — é referenciada
  por um Release (discografia/royalties) e o botão nem aparece.

### UX — Âncora ao abrir gravação/composição (ponto 1.5)
- Ao abrir o seletor de composição ou de faixas (que surgem no topo, longe dos botões de
  ação clicados lá embaixo), a visão **rola até o painel** (`scrollIntoView`). Guardado para
  ambientes sem a API (testes).

## Implementação (band-quest-game)
- `data/songs.ts`: `SONG_GENRES` + `pickGenre`.
- `stores/game.ts`: `ActionSelection.genre/theme`; `ActiveAction.composeGenre/composeTheme`;
  `startAction` guarda a escolha; `completeAction` aplica no `createSong`. Novo
  `discardSong(id)` (só `composed`).
- `views/GameView.vue`: painel de composição (selects + 🎲 + Compor); `start()` roteia
  `compose` para o seletor; âncora (`scrollIntoView`) ao abrir os painéis.
- `components/SongLibrary.vue`: botão de descarte nas músicas prontas.

## Checklist result
- [x] Scope reviewed.
- [x] Questions updated — nenhuma bloqueante (gêneros por época = 0008/futuro).
- [x] Handoff reviewed — entregue na mesma leva; playtest deferido.
