# Feature 0010 - Session Modes and Outcomes (Questions)

## Open Questions

*(Nenhuma bloqueante. As pendências restantes são calibragem numérica — feature
0003 — e o detalhamento de marcos/itens, agora donos das features 0011 e 0012.)*

## Resolved Questions

### [Q8] Quais os limiares conceituais de derrota?
**Decision:** Falência = N turnos consecutivos de caixa negativo; dissolução =
fadiga/moral no piso por M turnos [A]. N e M (números) ficam na 0003.
**References:** Solved in `iteration-03.md`.

### [Q7] Quais toggles de personalização o modo livre oferece?
**Decision:** Conjunto completo configurável por métrica e por sistema [C] (não um
preset fixo): game over on/off, dinheiro infinito, reputação travada, sem fadiga/
dissolução, eventos negativos on/off, etc. Lista detalhada + UI na 0005d.
**References:** Solved in `iteration-03.md`.

### [Q6] Como funcionam os marcos de carreira e os itens desbloqueáveis?
**Decision:** Viram duas features próprias (lacuna emergente): **0011 - Career
Milestones** (marcos + bônus) e **0012 - Unlockable Items** (catálogo de itens +
desbloqueio). A 0010 apenas referencia ambas para compor a nota.
**References:** Solved in `iteration-03.md`.

### [Q5] Como o score combinado mapeia para 1–5 estrelas?
**Decision:** Média ponderada de status positivos (fãs, caixa, reputação, prêmios,
discos vendidos, streams, álbuns…) menos os negativos [A], com faixas fixas de
score por estrela multiplicadas por um fator de duração. Pesos/cortes ficam na 0003.
**References:** Solved in `iteration-03.md`.

### [Q4] A derrota também vale no modo livre?
**Decision:** O jogador escolhe. O modo livre é configurável via toggles ao
iniciar (game over on/off, dinheiro infinito, sem perda de reputação, etc.).
**References:** Solved in `iteration-02.md`.

### [Q3] Como funciona o modo livre?
**Decision:** As duas variações [C]: duração personalizada (com relatório final,
sem vitória/derrota) e sandbox indefinido (até o jogador encerrar).
**References:** Solved in `iteration-02.md`.

### [Q2] O que define a DERROTA?
**Decision:** Falência (caixa negativo por X turnos) + dissolução (fadiga/moral no
fundo por tempo prolongado) [A], amplificadas por eventos negativos da 0009.
**References:** Solved in `iteration-02.md`.

### [Q1] O que define a VITÓRIA nos modos temporizados?
**Decision:** Score combinado [B] escalável por duração, traduzido em uma nota de
1–5 estrelas (resultado não-binário). Marcos de carreira são objetivos opcionais
que dão bônus (dinheiro/reputação/nota) e desbloqueiam itens.
**References:** Solved in `iteration-02.md`.
