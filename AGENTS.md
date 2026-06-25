# AGENTS.md

This repository contains the documentation workflow for Band Quest.

## Rules for agents

- Keep folder and file names in English.
- Keep the human-readable content in Portuguese unless a user asks otherwise.
- **CRITICAL:** Before drafting or updating any feature documents (especially `questions.md` and `log.md`), you MUST consult [docs/templates/feature-template.md](docs/templates/feature-template.md) and [docs/memory-bank/iteration-playbook.md](docs/memory-bank/iteration-playbook.md) to ensure exact compliance with formatting, options structures (A, B, C, D, X format), and semantic headers.
- Treat each feature as an iterative workflow: `planning/overview.md` -> `refinement/questions.md` -> `refinement/iteration-XX.md`.
- When an epic is too broad, document the split in `docs/features/roadmap.md` and in `refinement/decomposition.md`.
- Never overwrite a previous iteration. Add a new iteration file instead.
- If a decision is unclear, record it in `refinement/questions.md` before guessing.
- Use the latest refinement as the source of truth when preparing work for `band-quest-game`.
- Update the indexes in `README.md` files whenever a feature path changes.
- Follow the communication and logging rules in [docs/memory-bank/iteration-playbook.md](docs/memory-bank/iteration-playbook.md).
- Always create explicit plans and document your actions whenever you execute creation or editing of files. Use the chat response to clarify the plan before/during execution, and log updates appropriately.
- **CRITICAL:** The `questions.md` file MUST be treated as an append-only historical log. NEVER overwrite or delete old questions/answers. Always append new items so that all agents and developers maintain full historical context.
- Start new features from [docs/templates/feature-template.md](docs/templates/feature-template.md).
- Use `docs/features/roadmap.md` to decide whether a proposal should stay as an epic or be split into smaller features.
- Use [docs/memory-bank/new-feature-bootstrap.md](docs/memory-bank/new-feature-bootstrap.md) as the operational guide for creating a new feature.

## Feature structure

Each feature should follow this layout:

```text
docs/features/<english-slug>/
  diagrams/
  planning/
    overview.md
  refinement/
    decomposition.md
    checklist.md
    questions.md
    iteration-01.md
    iteration-02.md
    log.md
```

## AI-DLC phases

This workflow follows AWS's AI-Driven Development Lifecycle (AI-DLC):
AI proposes, humans validate, work moves in short, reviewable cycles (bolts).
The **canonical definition of the phases and gates lives in
[docs/memory-bank/ai-dlc.md](docs/memory-bank/ai-dlc.md)** — read it before
starting any cycle. Summary:

While the game is in pre-alpha we go explicitly through **4 of the 5 phases**
(`Operate` is deferred until there is a published build):

- **Inception** (this repo, `band-quest-docs`) -> `planning/overview.md`,
  `refinement/questions.md`, `refinement/iteration-NN.md`, `design.md`.
  Exit gate **G1 (Spec pronta)** = the "Handoff to implementation" checklist below.
- **Implement** (`band-quest-game`) -> code against the spec + `tokens.css`,
  with Vitest tests. Exit gate **G2** = new behavior implemented and covered.
- **Validate** (`band-quest-game`) -> the "gate verde": `test:unit` +
  `type-check` + `lint` + build, plus a manual playtest when mechanics change.
  Exit gate **G3**.
- **Deploy** (`band-quest-game` + this repo) -> in pre-alpha this means
  **registrar o incremento**: commit both repos, update memory bank, roadmap,
  playtest docs and the feature `log.md`. Exit gate **G4**.

Never edit a past iteration; create the next one — each iteration file is one
bolt. Scale the ceremony to the size of the change (see the scaling rule in
`ai-dlc.md`): small fixes fast-track through Implement/Validate/Deploy in a
single cycle; mechanics/economy/progression/structural-UI changes go through all
four gates, recorded inline in the feature `log.md`.

## Integrity rule

- No feature may be listed in `docs/features/README.md` unless
  `planning/overview.md` already exists for it.
- Before finishing any edit session, verify every link added or changed in
  any `README.md` index actually resolves to a file that exists in the repo.
- If a feature is referenced but not yet started, mark it explicitly as
  `(not started)` in the index instead of linking to files that don't exist.

## Spec-Driven Development (SDD) strategy

This project follows the spec-anchored level of Spec-Driven Development:
specs are written before implementation, and they are kept and evolved over
time — never deleted once the feature ships. We deliberately do not adopt
spec-as-source (where specs replace code as the only human-edited artifact);
that level is still experimental and adds overhead without reducing LLM
non-determinism, which is a bad trade-off for a one-person team.

### Memory bank vs specs
- **Memory bank** (`AGENTS.md` + `docs/memory-bank/`): context valid for any
  AI session — process rules, product vision, cross-cutting architecture
  decisions.
- **Specs** (`docs/features/000X-*/`): context valid only for the specific
  feature being created or changed.

### Scaling the workflow to the size of the change
- Small, isolated changes (typo fixes, obvious bugs, copy edits) do not need
  a full feature folder. A single `iteration-NN.md` entry, or even just a
  clear commit message, is enough.
- New functionality affecting game mechanics, economy, progression, or
  structural UI must follow the full spec-anchored flow: planning ->
  questions -> iteration -> design (when the feature is large enough to
  warrant a separate technical design).
- When in doubt about which path applies, default to the lighter path and
  ask the human to confirm if more structure is needed. Do not impose the
  full workflow on small changes "to be safe" — that defeats the purpose of
  scaling.

## Handoff to implementation — Gate G1 (Inception -> Implement)

This checklist is the **G1 gate** in [docs/memory-bank/ai-dlc.md](docs/memory-bank/ai-dlc.md).
Before coding in `band-quest-game`, verify:

1. The feature problem is clear.
2. Open questions are documented and **none blocking** remain open.
3. The latest refinement iteration is approved.
4. The implementation can be split into small, testable steps.