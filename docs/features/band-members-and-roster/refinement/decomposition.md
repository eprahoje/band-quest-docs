# Feature 0007 - Band Members and Roster (Decomposition)

## Epic breakdown
- **Modelo de membro + cast inicial** (spec de dados + personagens iniciais).
- **MemberCard.vue** — componente visual (consome o card da 0006 e os tokens).
- **Integração do roster** — criação da banda (0005) + render no `GameView`.
- **Progressão individual de membros** — condicional ao escopo (ver Q4).

## Why split
- O modelo + cast desbloqueia tanto o handoff de arte quanto a implementação.
- O card visual pode ser validado isoladamente com dados de exemplo.
- A progressão é a parte mais incerta e pode ficar para depois sem travar o resto.

## Recommended order
1. Modelo de membro + cast inicial (desbloqueia handoff de ícones).
2. `MemberCard.vue` (visual, dados estáticos de exemplo).
3. Integração no fluxo: criação (0005) + render no `GameView`.
4. Progressão individual (apenas se confirmada no escopo).
