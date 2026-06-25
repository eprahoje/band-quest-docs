# AI-DLC — As fases do nosso fluxo

Este é o documento **canônico** do AI-Driven Development Lifecycle (AI-DLC) no
Band Quest. Sempre que `AGENTS.md` (em qualquer um dos dois repos) falar em
"fases", "gates" ou "handoff", a definição vale o que está aqui.

Referência externa: [specs.md — What is AI-DLC](https://specs.md/methodology/what-is-ai-dlc)
e [AI-DLC Overview](https://specs.md/aidlc/overview).

## Princípio

> A IA propõe, o humano valida. Como num GPS: o humano define o destino, a IA
> dá o passo a passo, e o humano mantém a supervisão em cada checkpoint.

O trabalho avança em ciclos curtos e revisáveis (*bolts*). Cada ciclo atravessa
fases **explícitas**, e cada fronteira entre fases é um **gate** que o humano
valida antes de avançar.

## As fases (4 de 5 — Operate está deferido)

O método completo tem 5 fases. Enquanto o jogo está em **pré-alpha**, passamos
explicitamente por **4**. `Operate` fica deferido até existir um build publicado.

**Learn é transversal:** depois de cada gate, aprendemos e melhoramos —
atualizar `docs/memory-bank/`, playtests e roadmap faz parte do ciclo, não é uma
fase separada.

```text
Inception ──G1──> Implement ──G2──> Validate ──G3──> Deploy ──G4──> (Operate: deferido)
 [docs]            [game]            [game]           [game + docs]
   └──────────────────────── Learn (transversal) ────────────────────────┘
```

### 1. Inception — vive em `band-quest-docs`

- **Propósito:** capturar a intenção, elaborar requisitos, decidir e decompor —
  antes de qualquer linha de código.
- **Atividades:** `planning/overview.md` → `refinement/questions.md` →
  `refinement/iteration-NN.md` (→ `planning/design.md` quando a feature é grande);
  `refinement/decomposition.md` e `roadmap.md` quando precisa fatiar.
- **Gate G1 — Spec pronta (Inception → Implement):**
  1. O problema da feature está claro.
  2. As perguntas abertas estão documentadas e **nenhuma bloqueante** ficou em aberto.
  3. A última iteração de refinamento está aprovada.
  4. A implementação pode ser fatiada em passos pequenos e testáveis.

  *(Este é o antigo checklist "Handoff to implementation".)*

### 2. Implement — vive em `band-quest-game`

- **Entrada:** G1 passou.
- **Propósito:** codificar contra o contrato (a spec da feature + `tokens.css`),
  já com testes.
- **Atividades:** `data/`, store, views; respeitar `tokens.css` como contrato
  visual; escrever os testes (Vitest) **junto** com o código, não depois.
- **Gate G2 — Código + testes (Implement → Validate):** o comportamento novo está
  implementado e coberto por teste automatizado (lógica e, em componentes Vue,
  render). Nenhum slice é "feito" sem o teste correspondente existir.

### 3. Validate — vive em `band-quest-game`

- **Entrada:** G2 passou.
- **Propósito:** provar a qualidade **sem depender do usuário abrir o browser**.
- **Atividades — o "gate verde":**
  - `npm run test:unit`
  - `npm run type-check`
  - `npm run lint`
  - build (`npm run build`)
  - playtest manual **quando muda mecânica**, registrado em `docs/playtests/`.
  - mini code-review do próprio slice (qualidade, segurança, regressão).
- **Gate G3 — Qualidade (Validate → Deploy):** gate verde completo, sem
  regressão; se mexeu em mecânica/economia/progressão, o playtest está registrado.

### 4. Deploy — vive em `band-quest-game` + `band-quest-docs`

Em pré-alpha **não há produção**. Aqui "Deploy" = **registrar o incremento** e
torná-lo oficial e rastreável (sem build publicado).

- **Entrada:** G3 passou.
- **Atividades:**
  - commit nos **dois** repos;
  - atualizar a memory do projeto, `roadmap.md`, docs de playtest e o
    `refinement/log.md` da feature;
  - marcar a feature como entregue no índice/README.
- **Gate G4 — Incremento registrado:** commitado nos dois repos; memory, roadmap
  e logs refletem o que mudou e por quê.

### Operate — DEFERIDO

Observar, operar e aprender em produção. Reabrir esta fase quando o jogo tiver um
build publicado (ex: GitHub Pages / itch.io). Até lá, não é exigida.

## Regra de escala (não impor cerimônia demais)

A profundidade do ritual acompanha o tamanho da mudança:

- **Mudança pequena/isolada** (typo, copy, bug óbvio, ajuste de número placeholder):
  *fast-track*. Pode atravessar Implement + Validate + Deploy num único ciclo, sem
  gate escrito — basta o gate verde e um commit claro. Pode dispensar a fase de
  Inception (sem pasta de feature), conforme a estratégia SDD em `AGENTS.md`.
- **Mudança de mecânica, economia, progressão ou UI estrutural:** passa
  **explicitamente** pelos 4 gates, registrados inline (ver abaixo).

Na dúvida, comece pelo caminho leve e pergunte ao humano se precisa de mais
estrutura. Não aplique o fluxo completo "por segurança" — isso anula o ganho.

## Como registrar a passagem (inline)

Sem arquivo novo por ciclo. O registro mora nos artefatos que já existem:

- No `refinement/log.md` da feature, a entrada do ciclo nomeia a fase atingida e
  o gate liberado. Exemplo:

  ```md
  - **[0.3.0]** `2026-06-25` — Implement → Validate (G2→G3): gate verde,
    91 testes, type-check/lint/build OK. Playtest 03 registrado.
  ```

- Na memory do projeto (`project-band-quest`), o resumo de sessão menciona em que
  fase o trabalho parou e qual o próximo gate.

## Mapa rápido (fase → artefato → gate)

| Fase | Repo | Artefatos | Gate de saída |
|---|---|---|---|
| Inception | docs | overview, questions, iteration-NN, design | **G1** Spec pronta |
| Implement | game | `data/`, store, views, testes Vitest | **G2** Código + testes |
| Validate | game | gate verde + playtest | **G3** Qualidade |
| Deploy | game + docs | commits, memory, roadmap, log | **G4** Incremento registrado |
| Operate | — | (deferido) | — |
