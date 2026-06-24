# Feature 0012 - Unlockable Items (Log)

## [0.1.0] - 2026-06-23T00:00:00Z

### Input
- Desdobramento da Q6 da 0010: o usuário decidiu separar marcos de carreira e itens
  desbloqueáveis em duas features próprias. Esta é a dona dos **itens**.

### Summary
- Criado o scaffold da feature 0012 (README, diagrams, planning/overview,
  decomposition, checklist, questions, iteration-01, log).
- Registrada nos índices (`features/README.md` e `roadmap.md`).
- Abertas Q1–Q4 (categorias, fontes de desbloqueio, tipos de efeito, loja/compra).

### Open questions
- Q1, Q2, Q3, Q4 — ver `questions.md`.

### Next step
- Refinar Q1–Q4 com o usuário, fechar o modelo de item e o catálogo inicial,
  integrando com a 0011 (marcos como fonte de desbloqueio).

## [0.2.0] - 2026-06-23T00:00:00Z

### Input
- Usuário respondeu Q1–Q4. Q1: 4 trilhas (Equipamento/Estúdio/Marketing/Cosmético).
  Q2: desbloqueio por marcos (0011) + compra + época (0008). Q3: efeitos só
  funcionais. Q4: há loja para comprar equipamento melhor, parte dos itens
  desbloqueia por marcos; a loja pode virar feature própria e há um sistema de
  Staff (empresário, preparador vocal, roadies, motorista) como ideia futura.

### Summary
- Q1–Q4 resolvidas e movidas para "Resolved Questions"; criado `iteration-02.md`.
- Criado `planning/design.md` com o modelo de `Item` (categoria/fontes/efeito) e o
  catálogo inicial proposto (8 itens nas 4 trilhas).
- Reconciliação Q1×Q3: trilha cosmético/visual é categoria temática com efeito
  funcional (reputação) nesta fase; camada puramente cosmética adiada.
- Abertas Q5 (loja vira feature?) e Q6 (criar feature 0013 - Staff?); ambas
  registradas como candidatas no `roadmap.md`.

### Open questions
- Q5 (escopo da loja) e Q6 (feature de Staff) — não bloqueantes para o modelo de item.

### Next step
- Decidir Q5/Q6. Com o modelo e o catálogo prontos, a 0012 pode ser implementada no
  jogo após a 0011, com custos/efeitos calibrados na 0003.

## [0.3.0] - 2026-06-23T00:00:00Z

### Input
- Usuário decidiu Q5/Q6: a loja fica na 0012 (extrai só se crescer); criar a feature
  0013 - Staff and Crew agora.

### Summary
- Q5/Q6 resolvidas e movidas para "Resolved Questions"; criado `iteration-03.md`.
- Status → **Ready for Implementation** (modelo + catálogo + loja simples).
- Feature 0013 - Staff and Crew scaffoldada e registrada nos índices/roadmap.
- Gatilho de extração da loja registrado no `roadmap.md`.

### Open questions
- Nenhuma bloqueante na 0012.

### Next step
- Implementar a 0012 no jogo após a 0011, com calibragem na 0003. Refinar a 0013.
