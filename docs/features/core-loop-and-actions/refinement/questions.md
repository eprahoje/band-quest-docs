# Feature 0014 - Core Loop and Actions (Questions)

## Open Questions

*(Nenhuma bloqueante. O catálogo de `planning/design.md` aguarda revisão livre; a
calibragem numérica é da iteração de balance da 0003.)*

## Resolved Questions

### [Q4] Como uma ação pode falhar ou variar de resultado?
**Decision:** Faixa de resultado com aleatoriedade leve em torno do esperado +
chance de eventos (0009) interferirem [C]. Nunca injusto.
**References:** Solved in `iteration-02.md`.

### [Q3] Como a qualidade-alvo afeta a duração e o resultado?
**Decision:** Híbrido [C]: o jogador escolhe uma faixa de esforço/duração e os
recursos (membros 0007, itens 0012, staff/produtor 0013) modulam o resultado.
**References:** Solved in `iteration-02.md`.

### [Q2] O jogador faz uma ação por vez ou várias em paralelo?
**Decision:** Uma ação principal por vez + ações passivas/de fundo em paralelo [B].
Modelo de `lane`: `main` | `background`.
**References:** Solved in `iteration-02.md`.

### [Q1] Qual o conjunto inicial de ações?
**Decision:** Essenciais + marketing/demo [A+]: ensaiar, compor, gravar demo/single/
álbum, tocar show, turnê, marketing, descansar. Ações de mídia 2000s depois (0009).
**References:** Solved in `iteration-02.md`.
