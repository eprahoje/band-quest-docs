# Feature 0020 - UI Shell and Navigation (Refinement 01)

## Decisions (respostas do usuário — Playtest 07 ponto 4)

### D1 — Modelo: abas por área
HUD fixo (stats + calendário + Avançar) + barra de abas; só o conteúdo da **aba ativa**
é renderizado. Sem multi-coluna, sem feed lateral. Ref.: *A Story of a Band*.

### D2 — Telas e conteúdo (ações distribuídas)
| Aba | Conteúdo |
|---|---|
| **Visão** | calendário/resumo, Em andamento, Feed de eventos |
| **Banda** | cards de membros + ações `Ensaiar` / `Descansar` |
| **Estúdio** | ações `Compor` / `Gravar demo/single/álbum` + Músicas/Lançamentos (SongLibrary) |
| **Shows** | Locais + agenda (VenueList) + ações `Turnê` / `Marketing` |
| **Equipe** | Staff (StaffPanel) |
| **Finanças** | Custos + Ganhos |

### D3 — Estado preservado
O estado de aba é um `ref` local no shell; o estado do jogo vive no store Pinia, então
navegar entre abas não perde nada. Os overlays de composição/seleção (compose chooser,
track picker) seguem funcionando no fluxo do Estúdio.

## Implementação (band-quest-game)
- Novo componente `ActionCard.vue` (apresentacional: card de ação + preview de fadiga;
  emite `start`) para não duplicar a marcação em 3 telas.
- `GameView.vue` refatorado: HUD (header + `StatsPanel` + loop-bar) + barra de abas + o
  conteúdo por aba (v-if). Ações filtradas por categoria/id em cada tela.
- Sem mudança no store; componentes internos reaproveitados.

## Checklist result
- [x] Scope reviewed.
- [x] Questions updated — decisões D1–D3 (modelo/telas/estado).
- [x] Handoff reviewed — implementação nesta leva.
