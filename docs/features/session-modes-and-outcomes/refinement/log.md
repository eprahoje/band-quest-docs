# Feature 0010 - Session Modes and Outcomes (Log)

## [0.1.0] - 2026-06-23T00:00:00Z

### Input
- Desdobramento da 0001: o jogador escolhe a duração da sessão. Pedido do usuário:
  modos de 10/20/30 anos com vitória/derrota e um modo livre sem vitória/derrota
  com duração personalizada.

### Summary
- Criado o scaffold da feature 0010 e registrado nos índices.
- Direção dos modos registrada (temporizados + livre).

### Open questions
- Q1 (vitória), Q2 (derrota), Q3 (modo livre), Q4 (derrota no livre) — ver
  `questions.md`.

### Next step
- Refinar as condições de vitória/derrota e o comportamento do modo livre.

## [0.2.0] - 2026-06-23T00:00:00Z

### Input
- Usuário respondeu Q1–Q4. Vitória: score combinado escalável por duração, com
  resultado em estrelas (1–5, não-binário) e marcos de carreira opcionais que dão
  bônus e desbloqueiam itens. Derrota: falência + dissolução, amplificadas por
  eventos negativos. Modo livre: ambas as variações (duração custom + sandbox).
  Derrota no livre: o jogador escolhe via toggles de personalização.

### Summary
- Q1–Q4 resolvidas e movidas para "Resolved Questions".
- Criado `iteration-02.md` com as decisões de vitória, derrota e modos.
- Abertas Q5–Q8 (mapeamento score→estrelas; marcos/itens e relação com 0002;
  toggles do modo livre; limiares conceituais de derrota).
- Checklist de planning/refinement marcado; handoff ainda pendente.

### Open questions
- Q5, Q6, Q7, Q8 — ver `questions.md`.

### Next step
- Refinar Q5–Q8 (especialmente Q6: decidir o dono dos marcos/itens) e então fechar
  o handoff; em paralelo, a 0005d pode consumir os modos já definidos na seleção.

## [0.3.0] - 2026-06-23T00:00:00Z

### Input
- Usuário respondeu Q5–Q8 diretamente no `questions.md`. Q5: nota = média de status
  positivos menos negativos, com faixas fixas × fator de duração. Q6: marcos e itens
  viram duas features próprias. Q7: toggles do modo livre totalmente configuráveis
  por métrica/sistema. Q8: derrota por acúmulo (N turnos de caixa negativo; M turnos
  de fadiga/moral no piso).

### Summary
- Q5–Q8 resolvidas e movidas para "Resolved Questions"; criado `iteration-03.md`.
- Núcleo da feature fechado → status **Ready for Implementation** (modos + nota +
  derrota + princípio de toggles), com calibragem na 0003 e UI na 0005d.
- Q6 gerou duas features novas (lacuna emergente): **0011 - Career Milestones** e
  **0012 - Unlockable Items**, ambas scaffoldadas e registradas nos índices.
- Checklist com seção de dependências/delegações.

### Open questions
- Nenhuma bloqueante na 0010.

### Next step
- Implementar o núcleo da 0010 quando a 0003 (números) estiver pronta, ou levar os
  modos já definidos para a fatia de UI (0005d). Refinar 0011 e 0012 em paralelo.

## [0.4.0] - 2026-06-24T00:00:00Z

### Input
- Implementação (fatia 1) acordada: temporizados + nota em estrelas + derrota por
  falência; modo livre básico; dissolução depois.

### Summary
- Criado `iteration-04.md`. No jogo: `data/session.ts` (modos + computeScore/
  computeStars puros), config de sessão no store, fim por tempo (sucesso → estrelas),
  derrota por falência (90 dias no vermelho), `ResultView` + rota `/result`, seleção
  de duração na `StartView` (0005d). 90 testes; type-check/lint/build OK.

### Open questions
- Dissolução por fadiga (Q2) e toggles do modo livre (Q7) — adiados.

### Next step
- Próximas fatias: dissolução; bônus de marcos (0011) na nota; toggles do modo livre.
