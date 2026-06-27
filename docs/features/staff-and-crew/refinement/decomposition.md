# Feature 0013 - Staff and Crew (Decomposition)

> Consolidada na iteration-02. MVP = slices 1 e 2 (modelo + gate de locais, ponto 7).

## Epic breakdown
1. **Modelo + contratação + salário** *(MVP)* — catálogo dos 4 papéis (empresário,
   preparador vocal, roadie, motorista); contratar/demitir; custo único + salário mensal
   somando ao custo mensal da banda (0003). Painel de equipe na UI.
2. **Gate de locais escalonado** *(MVP — resolve Playtest 05 ponto 7)* — `Venue.requiredStaff`
   por tier; agendar exige a crew; UI mostra o requisito de equipe que falta. Acopla 0016.
3. **Modificadores passivos** — empresário (+% cachê), preparador vocal (−fadiga de show).
4. **Desbloqueios de turnê** *(futuro)* — motorista habilita turnês maiores (pareia com a
   0016 slice 4, turnê-trajeto).

## Why split
O modelo (1) é o alicerce e já tem peso econômico. O gate (2) é o uso prático pedido no
playtest e fecha a "Aurora fácil". Modificadores (3) e desbloqueios de turnê (4) empilham.

## Recommended order
1 → 2 (MVP) → 3 → 4.
