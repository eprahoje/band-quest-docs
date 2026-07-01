# Feature 0020 - UI Shell and Navigation

**Status:** Delivered (v1) — GameView refatorado em HUD fixo + abas por área (Visão/Banda/Estúdio/Shows/Equipe/Finanças), ações distribuídas. Playtest 07 ponto 4.

Refatora a apresentação do jogo: o **scroll único** do GameView vira **telas/abas por área**
com um **HUD fixo** (stats + avançar), preservando o estado (store Pinia é central). Emergiu
dos Playtests 03 (ponto 11), 06 (O1) e 07 (ponto 4 — priorizado). Ref.: *A Story of a Band*.

## Navigation
- [Planning overview](planning/overview.md)
- [Latest iteration](refinement/iteration-01.md)
- [Action log](refinement/log.md)

## Relações
- **0006 (Art Direction / Design System)** — o shell consome `tokens.css`; padrão de abas/HUD.
- Consome os componentes existentes (StatsPanel, EventFeed, SongLibrary, StaffPanel, VenueList,
  MemberCard) distribuindo-os nas telas. Não muda lógica de jogo (store inalterado).
