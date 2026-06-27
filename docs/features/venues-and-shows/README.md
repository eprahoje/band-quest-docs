# Feature 0016 - Venues and Shows

**Status:** In Implementation — MVP (slices 1 e 2) entregue: catálogo+desbloqueio + agendar show datado com cachê+bilheteria. Próximas: slice 3 (promoção/penalidade), 4 (turnê-trajeto), 5 (geografia híbrida)

Locais de show por reputação, venda de ingressos e agenda/calendário de shows e turnês.
Dá progressão geográfica e profundidade ao "tocar show" (hoje uma ação genérica de 1 dia
na 0014). Emergiu dos Playtests 01 (pontos 6, 10), 03 (pontos 7.1–7.3) e 04 (ponto 3.3).

## Navigation
- [Planning overview](planning/overview.md)
- [Decomposition](refinement/decomposition.md)
- [Open questions](refinement/questions.md)
- [Checklist](refinement/checklist.md)
- [Latest iteration](refinement/iteration-02.md)
- [Action log](refinement/log.md)

## Relações
- **0014 Core Loop** — dona da ação `play-show`/`tour`; a 0016 dá destino/lotação/cachê a elas.
- **0003 Economia** — números de ingresso/cachê (contrato numérico).
- **0013 Staff and Crew** — gate de turnê (empresário/roadies) — reforçado pelo P03 9.2.
- **0011 Career Milestones** — pode desbloquear locais/marcos geográficos.
- **0008 Timeline** — locais/tecnologia podem evoluir com a época.
