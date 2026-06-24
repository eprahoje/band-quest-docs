# Feature 0011 - Career Milestones (Decomposition)

## Epic breakdown
- Modelo de marco (gatilho/condição/recompensa/repetível).
- Catálogo inicial de marcos (cedo/médio/fim de carreira).
- Regra de avaliação e disparo (quando o marco é checado).
- Integração: bônus na nota (0010), desbloqueio de item (0012), evento no feed.

## Why split
- O modelo pode ser definido antes do catálogo completo.
- As recompensas podem ser calibradas separadamente (0003).
- A integração com 0010/0012 é uma fatia testável independente.

## Recommended order
1. Modelo de marco.
2. Catálogo inicial.
3. Regra de avaliação/disparo.
4. Integração com nota, itens e feed de eventos.
