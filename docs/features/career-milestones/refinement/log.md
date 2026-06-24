# Feature 0011 - Career Milestones (Log)

## [0.1.0] - 2026-06-23T00:00:00Z

### Input
- Desdobramento da Q6 da 0010: o usuário decidiu separar marcos de carreira e itens
  desbloqueáveis em duas features próprias. Esta é a dona dos **marcos**.

### Summary
- Criado o scaffold da feature 0011 (README, diagrams, planning/overview,
  decomposition, checklist, questions, iteration-01, log).
- Registrada nos índices (`features/README.md` e `roadmap.md`).
- Abertas Q1–Q4 (catálogo inicial, único vs escalável, recompensas, onde ficam os
  números).

### Open questions
- Q1, Q2, Q3, Q4 — ver `questions.md`.

### Next step
- Refinar Q1–Q4 com o usuário, fechar o modelo de marco e o catálogo inicial.

## [0.2.0] - 2026-06-23T00:00:00Z

### Input
- Usuário respondeu Q1–Q4. Q1: catálogo ~12 com marcos de mídia dos anos 2000.
  Q2: cada marco declara se é único ou escalável (tiers). Q3: recompensas podem
  combinar status + nota (0010) + item (0012) + evento. Q4: estrutura aqui,
  números na 0003.

### Summary
- Q1–Q4 resolvidas e movidas para "Resolved Questions"; criado `iteration-02.md`.
- Criado `planning/design.md` com o modelo de `Milestone` e o catálogo inicial
  proposto (~12 marcos, com trilha/tipo/métrica/recompensa).
- Status → **Ready for Implementation** (estrutura + catálogo), pendente calibragem
  (0003) e ids de item (0012).

### Open questions
- Nenhuma bloqueante. Catálogo do `design.md` aberto a refino do usuário.

### Next step
- Refinar a 0012 (itens) para fechar os `unlockItemId`; em paralelo, a estrutura da
  0011 pode ser implementada no jogo (motor de marcos + catálogo declarativo).
