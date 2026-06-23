# Feature 0007 - Band Members and Roster (Log)

## [0.1.0] - 2026-06-23T00:00:00Z

### Input
- Usuário pediu para registrar a lacuna do "member card / membros da banda" e
  criar uma nova feature dona do modelo de membro e do roster, incluindo
  handoff de arte para os ícones dos personagens iniciais. Refinamento será
  colaborativo (ideias do usuário + perguntas do agente).

### Summary
- Identificada a lacuna: o card de membro é da 0006 e a criação da banda é da
  0005, mas o modelo de membro e o roster não tinham dono.
- Criado o scaffold da feature 0007 (overview, decomposition, checklist,
  questions, iteration-01, log, diagrams, handoff).
- Registrada nos índices (`features/README.md` e `roadmap.md`).
- Criado o brief de handoff de ícones em `handoff/character-icons-handoff.md`
  com as restrições de estilo já conhecidas (herdadas da 0006) e placeholders
  para o cast (dependem de Q1/Q2).

### Open questions
- Q1 (formação), Q2 (cast), Q3 (atributos), Q4 (progressão) — ver `questions.md`.

### Next step
- Refinar Q1–Q4 com o usuário, fechar o cast inicial e completar o brief de
  ícones; então criar `iteration-02.md` com as decisões.

## [0.2.0] - 2026-06-23T00:00:00Z

### Input
- Usuário respondeu Q1–Q4: formação variável de 3–5 com trade-offs por tamanho;
  personagens pré-definidos com ≥3 opções por função; atributos Técnica/Carisma/
  Criatividade/Energia; progressão individual fora desta feature.

### Summary
- Q1–Q4 resolvidas e movidas para "Resolved Questions".
- Criado `iteration-02.md` com as decisões.
- Abertas Q5–Q8 (funções, regras de composição, opções por função, onde
  especificar os trade-offs de tamanho).

### Open questions
- Q5, Q6, Q7, Q8 — ver `questions.md`.

### Next step
- Refinar Q5–Q8, fechar funções e contagem de personagens, e então completar a
  tabela do cast no brief de ícones (iteration-03).

## [0.3.0] - 2026-06-23T00:00:00Z

### Input
- Usuário respondeu Q5–Q8: 5 funções no lançamento (extensível); instrumentos
  repetem, vocal não (máx.1) e é opcional, mín. 3 instrumentistas com bateria
  obrigatória (permite bandas instrumentais); exatamente 3 opções por função;
  trade-offs de tamanho com conceito aqui e números na 0003.

### Summary
- Q5–Q8 resolvidas; `iteration-03.md` criado.
- Criado `planning/design.md` com o modelo de dados (Member/role/atributos),
  as regras de composição e o cast proposto de 15 personagens.
- Brief de handoff de ícones completado (15 SVGs, definition of done) — status
  PRONTO PARA PRODUÇÃO.
- Overview (non-goals), checklist e índices atualizados.

### Open questions
- Nenhuma bloqueante. Cast (nomes/perfis) é proposta aberta a refino do usuário.

### Next step
- Aprovar/ajustar o cast e disparar o handoff de ícones; em paralelo, implementar
  em `band-quest-game` na ordem do `decomposition.md` (modelo → MemberCard →
  integração no roster/criação). (Superado pelas iterações 04–05.)

## [0.4.0] - 2026-06-23T00:00:00Z

### Input
- Usuário pediu para refinar o cast dando "cara de Brasil" (nomes, descrições) e
  complementar cada entrada do handoff/produção dos ícones.

### Summary
- Cast renomeado com identidade brasileira e diversidade do país; criado
  `iteration-04.md`.
- `planning/design.md` e o brief de handoff atualizados com novos nomes, slugs
  (`member-<slug>.svg`) e **briefings visuais por personagem** (prompt-ready).
- Adicionada seção de identidade brasileira no brief.

### Open questions
- Nenhuma bloqueante. Nomes/descrições seguem ajustáveis.

### Next step
- Decidir o produtor dos ícones (gerar localmente vs Gemini/Nano Banana vs outro
  agente) e iniciar a produção; depois implementar a feature no jogo.

## [0.5.0] - 2026-06-23T00:00:00Z

### Input
- Usuário pediu para construir, juntos, uma história breve para cada personagem,
  para aproximar o jogador e não deixar o membro como mera peça de build.

### Summary
- Definido o tom (realista + bem-humorado, com equilíbrio variável por
  personagem) via comparação de registros.
- Escritas as 15 histórias curtas e adicionadas a `planning/design.md`.
- Criado `iteration-05.md`.

### Open questions
- Nenhuma bloqueante. Histórias e nomes seguem ajustáveis.

### Next step
- Gerar o sample de 2 ícones (Lila Tavares, Rita Camargo) para validar o estilo;
  depois produzir os 15 e implementar a feature no jogo.

## [0.6.0] - 2026-06-23T00:00:00Z

### Input
- Usuário aprovou o estilo flat-vector (Gemini descartado nesta fase) e pediu a
  criação dos 13 ícones restantes.

### Summary
- Criados os 13 SVGs restantes (total 15) em `band-quest-game/src/assets/members/`.
- Teste de validação de SVG reforçado com cobertura cruzada do cast.
- `type-check` limpo e 34 testes passando.
- Criado `iteration-06.md`; handoff marcado como produzido.

### Open questions
- Nenhuma.

### Next step
- Implementar `MemberCard.vue` consumindo os ícones e popular o roster no store
  (decomposition #2 e #3).
