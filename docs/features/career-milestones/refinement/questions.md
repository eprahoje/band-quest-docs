# Feature 0011 - Career Milestones (Questions)

## Open Questions

*(Nenhuma bloqueante. O catálogo proposto em `planning/design.md` aguarda revisão
livre do usuário; a calibragem numérica é da 0003 e os ids de item são da 0012.)*

## Resolved Questions

### [Q4] Onde ficam os números das condições/recompensas?
**Decision:** Conceito/estrutura e gatilhos aqui; números (limiares e valores) na
0003 [A].
**References:** Solved in `iteration-02.md`.

### [Q3] Que recompensas um marco pode conceder?
**Decision:** Qualquer combinação de status (dinheiro/reputação) + bônus na nota
(0010) + desbloqueio de item (0012) + evento `milestone` no feed [C].
**References:** Solved in `iteration-02.md`.

### [Q2] Marcos são únicos ou podem repetir/escalar?
**Decision:** Cada marco declara seu tipo [C]: `unique` (one-shot) ou `scalable`
(degraus/tiers, ex.: discos vendidos 1k/10k/100k).
**References:** Solved in `iteration-02.md`.

### [Q1] Quais marcos compõem o catálogo inicial?
**Decision:** ~12 marcos cobrindo começo/meio/fim + marcos de mídia dos anos 2000
(viralizar no fotolog/MySpace, tocar na TV) [B]. Catálogo concreto em `planning/design.md`.
**References:** Solved in `iteration-02.md`.
