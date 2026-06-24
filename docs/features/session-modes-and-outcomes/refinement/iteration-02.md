# Feature 0010 - Session Modes and Outcomes (Refinement 02)

## Decisions

### Vitória (modos temporizados) — Q1 resolvida [B+]
- O resultado **não é binário** (ganhou/perdeu). Ao fim do prazo o jogador recebe
  uma **nota de desempenho em estrelas (1 a 5)**.
- A nota deriva de um **score combinado** das métricas centrais (reputação, fãs,
  caixa — eixos da 0003). O jogador não precisa maximizar tudo para "ganhar":
  a estrela reflete o desempenho geral.
- O score/limiares **escalam conforme a duração escolhida** (10/20/30 anos): uma
  sessão mais longa exige patamares maiores para a mesma nota.
- **Marcos de carreira** funcionam como objetivos opcionais que, ao serem
  atingidos durante a partida, concedem **bônus** (dinheiro, reputação e/ou
  **bônus na nota final**) e podem **desbloquear itens**. São incentivo, não
  requisito de vitória.

### Derrota (modos temporizados) — Q2 resolvida [A+]
- Encerramento prematuro por **falência + dissolução**:
  - **Falência:** caixa negativo por X turnos consecutivos (X na 0003).
  - **Dissolução:** fadiga/moral no fundo por tempo prolongado (limiar na 0003).
- A derrota é **amplificada por eventos negativos** (feature 0009): eventos podem
  pressionar caixa/fadiga e aproximar o jogador das condições de game over,
  tornando o cenário mais difícil em vez de só "perder pontos".

### Modo livre — Q3 resolvida [C]
- Oferece **as duas variações**:
  - **Duração personalizada:** prazo definido no início, sem vitória/derrota,
    com **relatório final** (sem estrelas obrigatórias — é desempenho, não nota).
  - **Sandbox indefinido:** segue até o jogador encerrar manualmente.

### Derrota no modo livre — Q4 resolvida [custom]
- **O jogador escolhe.** O modo livre é configurável: ao iniciar, o jogador
  liga/desliga regras que personalizam a experiência. Exemplos de toggles:
  - Game over por falência **ligado/desligado**.
  - **Dinheiro infinito**.
  - **Sem perda de reputação**.
  - (catálogo completo de toggles → Q7.)

## New questions (abertas para refino — ver `questions.md`)
- **Q5** — Mapeamento score → estrelas (faixas) e como escala por duração.
- **Q6** — Marcos de carreira: catálogo, relação com 0002 (progressão) e onde
  mora o sistema de itens desbloqueáveis.
- **Q7** — Conjunto de toggles de personalização do modo livre.
- **Q8** — Limiares conceituais de derrota (turnos de caixa negativo; gatilho de
  dissolução por fadiga/moral) — números finos ficam na 0003.

## Checklist result
- [x] Scope reviewed.
- [x] Questions updated.
- [ ] Handoff reviewed.
