# AGENTS.md

This repository contains the documentation workflow for Band Quest.

## Rules for agents

- Keep folder and file names in English.
- Keep the human-readable content in Portuguese unless a user asks otherwise.
- Treat each feature as an iterative workflow: `planning/overview.md` -> `refinement/questions.md` -> `refinement/iteration-XX.md`.
- Never overwrite a previous iteration. Add a new iteration file instead.
- If a decision is unclear, record it in `refinement/questions.md` before guessing.
- Use the latest refinement as the source of truth when preparing work for `band-quest-game`.
- Update the indexes in `README.md` files whenever a feature path changes.
- Follow the communication and logging rules in [docs/agents/iteration-playbook.md](docs/agents/iteration-playbook.md).
- Start new features from [docs/templates/feature-template.md](docs/templates/feature-template.md).

## Feature structure

Each feature should follow this layout:

```text
docs/features/<feature-id>-<english-slug>/
  planning/
    overview.md
  refinement/
    checklist.md
    questions.md
    iteration-01.md
    iteration-02.md
    log.md
```

## Handoff to implementation

Before coding in `band-quest-game`, verify:

1. The feature problem is clear.
2. Open questions are documented.
3. The latest refinement iteration is approved.
4. The implementation can be split into small, testable steps.