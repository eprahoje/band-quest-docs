# Feature 0012 - Unlockable Items (Questions)

## Open Questions

*(Nenhuma bloqueante. Escopo fechado; calibragem na 0003, ids de marco na 0011,
itens por época na 0008.)*

## Resolved Questions

### [Q6] Criar a feature de Staff (contratações) agora ou adiar?
**Decision:** Criar agora a feature **0013 - Staff and Crew** [A]; Staff é sistema
próprio, distinto de itens. A 0012 apenas referencia a 0013.
**References:** Solved in `iteration-03.md`.

### [Q5] A loja vira feature própria ou fica dentro da 0012?
**Decision:** Fica na 0012 e é extraída só se crescer [C] (preços dinâmicos,
estoque por época). Gatilho de extração registrado no `roadmap.md`.
**References:** Solved in `iteration-03.md`.

### [Q4] Há economia de compra (loja) de itens nesta feature?
**Decision:** Sim [B] — há loja integrada à economia (0003) para comprar
equipamento melhor; parte dos itens é desbloqueada por marcos (0011), não comprada.
A loja pode virar feature própria (ver Q5) e o Staff é candidato a feature (ver Q6).
**References:** Solved in `iteration-02.md`.

### [Q3] Que tipos de efeito um item pode ter?
**Decision:** Só funcional [B] nesta fase — modificadores de caixa/reputação/fãs/
eficiência das ações. Camada puramente cosmética adiada.
**References:** Solved in `iteration-02.md`.

### [Q2] Quais são as fontes de desbloqueio?
**Decision:** Marcos (0011) + compra (loja) + época/tecnologia (0008) [C].
**References:** Solved in `iteration-02.md`.

### [Q1] Quais categorias de item existem?
**Decision:** 4 trilhas temáticas [A]: Equipamento, Estúdio, Marketing,
Cosmético/visual. Itens da trilha cosmético/visual têm, por ora, efeito funcional
(reputação) — reconciliação com a Q3.
**References:** Solved in `iteration-02.md`.
