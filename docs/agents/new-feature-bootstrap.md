# New Feature Bootstrap

Use this guide to create a new feature from scratch or to split an epic into smaller pieces.

## Input signals

- A user request that introduces a new capability.
- A refinement that is getting too broad.
- A design need that should become its own feature.

## Decision flow

1. Check whether the request belongs in `docs/features/roadmap.md`.
2. Decide if it is an epic, a feature slice, or a design-focused feature.
3. Start from [docs/templates/feature-template.md](../templates/feature-template.md).
4. Create the feature folder in English.
5. Fill the planning file.
6. Add `decomposition.md` if the proposal can be split.
7. Add `checklist.md`, `questions.md`, `iteration-01.md`, and `log.md`.
8. Register the new feature in [docs/features/README.md](../features/README.md).
9. Update the roadmap if the new feature changes the split strategy.

## Minimal scaffold

```text
docs/features/000X-feature-slug/
  planning/
    overview.md
  refinement/
    decomposition.md
    checklist.md
    questions.md
    iteration-01.md
    log.md
```

## Simplified file starters

### planning/overview.md

```md
# Feature 000X - Feature Name (Planning)

## Problem

## Goals

## Initial scope

## Acceptance criteria
```

### refinement/decomposition.md

```md
# Feature 000X - Feature Name (Decomposition)

## Epic breakdown

## Why split

## Recommended order
```

### refinement/checklist.md

```md
# Feature 000X - Feature Name (Checklist)

## Scope

## Questions

## Handoff
```

### refinement/questions.md

```md
# Feature 000X - Feature Name (Questions)

## Perguntas em aberto
```

### refinement/iteration-01.md

```md
# Feature 000X - Feature Name (Refinement 01)

## Decisions

## Questions

## Checklist result
```

### refinement/log.md

```md
# Feature 000X - Feature Name (Log)

## [0.1.0] - 2026-06-18T00:00:00Z

### Input
### Summary
### Open questions
### Next step
```

## If the request is unclear

- Stop and ask the human for clarification.
- Record the unclear point in `questions.md`.
- Do not expand the feature beyond the confirmed scope.

## If the request is too broad

- Move the proposal into `docs/features/roadmap.md`.
- Split it into smaller features with independent validation.
- Keep design work separate when it affects the first experience or visual system.