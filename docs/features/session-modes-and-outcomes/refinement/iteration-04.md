# Feature 0010 - Session Modes and Outcomes (Refinement 04 — implementação, fatia 1)

> Primeira fatia de implementação no `band-quest-game`. Escopo acordado com o
> usuário: modos temporizados + nota em estrelas + derrota por falência. Modo livre
> básico (sem fim). Dissolução por fadiga e modo livre com toggles ficam para depois.

## Decisions (implementadas)

### Seleção de duração no setup (0005d)
- A `StartView` oferece **10 / 20 / 30 anos** (temporizado) ou **Livre**.
- A escolha vai para o store (`sessionMode`, `durationYears`) no `startGame`.

### Fim por tempo (sucesso) → nota em estrelas
- Turno = dia; `endTurn = durationYears × 360`. Ao atingir `endTurn`, a sessão termina.
- **Score** (placeholder de balance): `reputação + fãs/100 + max(0, caixa)/100`.
- **Estrelas (1–5):** faixas `[120, 250, 400, 600]` (base 10 anos), **escaladas pela
  duração** (× `durationYears/10`). Lógica pura em `data/session.ts`.

### Derrota por falência
- Caixa negativo por **90 dias consecutivos** → game over (`reason: 'Falência'`).

### Modo livre (básico)
- `endTurn = 0`: não termina por tempo. (Toggles de personalização — Q7 — depois.)

### Tela de resultado
- Nova `ResultView` (rota `/result`): mostra estrelas + score (sucesso) ou o motivo
  da derrota, os status finais e "Novo jogo". O `GameView` navega ao detectar o fim.

## Deferred (próximas fatias)
- Dissolução por fadiga/moral no piso por M dias (a outra condição de derrota — Q2).
- Modo livre com toggles (dinheiro infinito, sem perda de reputação, etc. — Q7).
- Bônus de marcos (0011) entrando na nota; relatório final mais rico.

## Checklist result
- [x] Scope reviewed.
- [x] Questions updated.
- [x] Handoff reviewed.
