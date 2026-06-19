# Iteration Playbook

This document is the rulebook for agent-led feature iterations in Band Quest docs.

## Purpose

- Keep every iteration documented and repeatable.
- Preserve the original user input and refine it over time.
- Make it easy to hand off a feature to `band-quest-game`.
- Standardize how the agent communicates with the human.

## Iteration phases

1. Intake: capture the original user request and the feature context.
2. Clarification: identify gaps and ask the human before guessing.
3. Planning: define scope, goals, and constraints in `planning/overview.md`.
4. Checklist: update `refinement/checklist.md` before and after the iteration.
5. Refinement: produce numbered iterations in `refinement/iteration-XX.md`.
6. Validation: compare the iteration against the current request and the open questions.
7. Logging: append the iteration outcome to `refinement/log.md`.
8. Handoff: prepare the resulting contract for `band-quest-game`.

## Required checkpoints

- Preserve the original user input inside the feature log.
- Re-check whether the plan needs improvement after each iteration.
- If the feature or instruction is unclear, stop and ask for clarification.
- Never start implementation work in `band-quest-game` while open questions remain unresolved.
- Keep `refinement/checklist.md` updated as the control surface for the feature.
- Keep log entries append-only and timestamped.

## Feature log

Each feature keeps one append-only log at `refinement/log.md`.

Each entry should record:

- Semantic version label, for example `0.1.0`.
- ISO 8601 UTC timestamp, for example `2026-06-18T14:30:00Z`.
- Original user intent or change request.
- Summary of the agent action.
- Open questions that remain.
- Decision or next step.

### Versioning guidance

- `MAJOR`: breaking scope shift or redefinition of the feature.
- `MINOR`: new documented capability or significant refinement.
- `PATCH`: clarification, correction, or small adjustment.

## Communication patterns

### Welcome message

Use this when starting a feature iteration:

> Vou organizar esta feature em fases, registrar as dúvidas e deixar a decisão pronta para implementação. Primeiro vou alinhar o contexto e identificar o que ainda precisa de confirmação.

### Template onboarding

Use this when starting from the reusable template:

> Vou partir do template padrão da feature, preencher o checklist, registrar o log inicial e só então fechar a primeira iteração.

### Continuation summary

Use this when the user wants to continue a previous iteration:

> Vou retomar a última iteração a partir do que já está documentado, resumir o estado atual e apontar apenas as lacunas que precisam de decisão antes de avançar.

### Checklist reminder

Use this before a refinement pass:

> Vou revisar o checklist da feature antes de alterar a iteração, para garantir que o escopo, as dúvidas e o handoff continuam consistentes.

### Clarification request

Use this when the scope is not clear enough:

> Ainda falta informação para seguir sem suposições. Preciso confirmar: [pergunta objetiva].

### Progress update

Use this during the work:

> Já consolidei o contexto e estou fechando a próxima fase. O próximo passo é [ação curta] para validar se a proposta segue consistente com o objetivo original.

### Decision summary

Use this after a refinement choice:

> A decisão desta iteração foi [decisão]. Isso altera [impacto] e deixa pendente [pendência], que deve ir para `refinement/questions.md`.

### Blocked message

Use this when the work cannot continue safely:

> A iteração está bloqueada até receber confirmação sobre [ponto]. Sem isso, eu correria o risco de registrar uma decisão incorreta.

### Closeout message

Use this when finishing the iteration:

> A iteração foi registrada e o log da feature foi atualizado. A próxima decisão pode seguir a partir de [estado atual].

### Handoff summary

Use this when a feature is ready to move to implementation:

> A feature já está pronta para o handoff. O checklist ficou consistente, as dúvidas estão documentadas e o próximo passo pode seguir para `band-quest-game`.

## Improvement loop

After each iteration, ask:

1. The original user request is still reflected accurately.
2. The iteration can be reused as a template.
3. The questions file contains only unresolved items.
4. The log clearly shows what changed and why.
5. The feature is ready to be refined again or handed off.

If any answer is no, improve the documentation before moving on.