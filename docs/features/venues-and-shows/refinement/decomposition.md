# Feature 0016 - Venues and Shows (Decomposition)

> Provisória — a decomposição final depende das respostas de Q1–Q6 (em especial Q6).

## Epic breakdown
Slices candidatas (validáveis de forma independente, ordem sugerida):

1. **Catálogo de locais + desbloqueio** — modelo `Venue` (nome, capacidade, região/tier,
   gate de reputação) e a lista de locais; UI mostra desbloqueados/travados com requisito.
2. **Escolha do local ao tocar** — a ação de show (0014) passa a referenciar um `Venue`;
   locais maiores rendem mais (ainda no modelo de cachê atual).
3. **Receita por ingresso** — retorno do show = lotação × atratividade × preço (depende de Q3).
4. **Agenda/calendário** — compromisso datado para shows (e turnê) (depende de Q4).
5. **Turnê como trajeto** — sequência de locais/datas; gate de staff (0013) (depende de Q5).

## Why split
O catálogo (slice 1) é o alicerce e já dá progressão visível sem mexer na economia. A
escolha do local (2) liga ao core loop. Ingresso (3) e agenda (4) são incrementos de
mecânica/economia. A turnê-trajeto (5) é a mais acoplada (0013/0008) e fecha a feature.

## Recommended order
1 → 2 → 3 → 4 → 5 (a confirmar com Q6 — o MVP pode parar em 2 ou 3).
