# Feature 0003 - Economia e Reputação (Questions)

## Open Questions

*(Nenhuma bloqueante. Restam a feature 0014 — Core Loop and Actions — e a iteração
de balance com os valores concretos.)*

## Resolved Questions

### [Q4] Quais as fontes de receita e de custo base do loop?
**Decision:** Básicas + royalties + patrocínios [C]. Receita: shows/cachês, vendas,
streaming, royalties passivos do catálogo, patrocínios/eventos (0009). Custo:
gravação, marketing, logística/turnê, salários (0013), manutenção mínima por turno.
**References:** Solved in `iteration-03.md`.

### [Q3] Qual a unidade de calendário e o modelo de duração das ações?
**Decision:** Turno = **semana** (~52/ano). O **modelo de duração de ações** vira a
feature **0014 - Core Loop and Actions**; a 0003 fornece custos/ganhos, a 0014 a
duração e a mecânica.
**References:** Solved in `iteration-03.md`.
**⚠️ Revisado:** a unidade passou a ser **dia** (12×30 = 360/ano) após o Playtest 01.
Ver `iteration-04.md` e a iteration-02 da 0008.

### [Q2] Como a reputação se comporta ao longo do tempo?

### [Q2] Como a reputação se comporta ao longo do tempo?
**Decision:** Decai gradualmente quando a banda fica inativa (sem show/lançamento
por K turnos). Variável `reputationDecayPerTurn`; números no balance.
**References:** Solved in `iteration-02.md`.

### [Q1] O caixa pode ficar negativo (dívida)?
**Decision:** Sim — caixa pode ir negativo; falência = N turnos consecutivos no
vermelho. Remove o trava-zero do `game.ts`. N no balance.
**References:** Solved in `iteration-02.md`.

### [Q0] Onde ficam os valores concretos (custos, ganhos, limiares)?
**Decision:** A 0003 fecha estrutura/fórmulas; os valores vão para uma iteração de
balance dedicada, perto da implementação ("só estrutura, números depois").
**References:** Solved in `iteration-02.md`.
