# Feature 0016 - Venues and Shows (Decomposition)

> Consolidada na iteration-02 (Q1–Q6 resolvidas). MVP = slices 1 e 2.

## Epic breakdown
1. **Catálogo de locais + desbloqueio** *(MVP)* — modelo `Venue` (nome, tier, capacidade,
   região, `repThreshold`, `minFans`); lista + UI com travado/liberado e o requisito que
   falta. Desbloqueio por **reputação + fãs** (D2).
2. **Agendar show no local + receita** *(MVP)* — **compromisso datado** (D4): agenda o show
   num local para uma data; no dia, credita **cachê base + bilheteria** (`min(fãs
   interessados, capacidade) × preço`, D3). Substitui o `play-show` imediato da 0014.
3. **Promoção + penalidade de falta** — promover na janela pré-show (mais público); no-show
   penaliza (reputação/multa).
4. **Turnê como trajeto** *(futuro)* — sequência de locais/datas; gate de staff (0013).
5. **Geografia híbrida** *(futuro)* — tiers dentro de regiões/cidades a partir da origem (D1).

## Why split
O catálogo (1) é o alicerce e já dá progressão visível. O agendamento + receita (2) fecha o
novo loop de show. Promoção (3), turnê-trajeto (4) e geografia híbrida (5) empilham depois.

## Recommended order
1 → 2 (MVP) → 3 → 4 → 5.
