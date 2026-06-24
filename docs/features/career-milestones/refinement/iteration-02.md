# Feature 0011 - Career Milestones (Refinement 02)

## Decisions

### Catálogo inicial ~12 com mídia dos anos 2000 — Q1 resolvida [B]
- Conjunto de ~12 marcos cobrindo começo/meio/fim de carreira, incluindo **marcos
  de mídia da época** (viralizar no fotolog/MySpace, tocar na TV) — alinhado à
  identidade da 0009.
- Catálogo concreto proposto em [`planning/design.md`](../planning/design.md)
  (aberto a refino do usuário).

### Único vs. escalável: cada marco declara — Q2 resolvida [C]
- Cada marco declara seu tipo: **único** (one-shot, ex.: "1º álbum") ou
  **escalável em degraus/tiers** (ex.: discos vendidos 1k/10k/100k; certificação
  ouro/platina/diamante).
- Marcos escaláveis disparam uma recompensa por degrau atingido.

### Recompensas: status + nota + item + evento — Q3 resolvida [C]
- Um marco pode conceder qualquer combinação de:
  - **Bônus de status** (dinheiro e/ou reputação),
  - **Bônus na nota final** da sessão (0010),
  - **Desbloqueio de item** (0012),
  - **Evento narrativo** no feed (categoria `milestone`).

### Conceito aqui, números na 0003 — Q4 resolvida [A]
- A 0011 é dona da **estrutura, dos gatilhos e do catálogo**; os **números**
  (limiares das condições e valores das recompensas) ficam na **0003**.

## Model (resumo — detalhe em `planning/design.md`)
- `Milestone`: `id`, `title`, `description`, `track` (estúdio/palco/mídia/negócios),
  `kind` (`unique` | `scalable`), `tiers?` (para escaláveis),
  `condition` (métrica + limiar — limiar calibrado na 0003),
  `rewards` (`cash?`, `reputation?`, `scoreBonus?`, `unlockItemId?`, `eventMessage?`).

## Outcome
- Q1–Q4 resolvidas; modelo e catálogo proposto criados em `planning/design.md`.
- Status: **Ready for Implementation** (estrutura + catálogo), pendente apenas a
  calibragem numérica (0003) e os ids de item (0012).

## Checklist result
- [x] Scope reviewed.
- [x] Questions updated.
- [x] Handoff reviewed.
