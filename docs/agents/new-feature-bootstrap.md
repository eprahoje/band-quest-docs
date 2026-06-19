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
6. Add `diagrams/` if the feature needs Mermaid or visual flow documentation.
7. Add `decomposition.md` if the proposal can be split.
8. Add `checklist.md`, `questions.md`, `iteration-01.md`, and `log.md`.
9. Register the new feature in [docs/features/README.md](../features/README.md).
10. Update the roadmap if the new feature changes the split strategy.

## Minimal scaffold

```text
docs/features/000X-feature-slug/
  README.md
  diagrams/
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

### README.md

```md
# Feature 000X - Feature Name

**Status:** Planning / In Refinement / Ready for Implementation

## Navigation
- [Planning overview](planning/overview.md)
- [Open questions](refinement/questions.md)
- [Latest iteration](refinement/iteration-01.md)
- [Action log](refinement/log.md)
```

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

## Open Questions

### [Q1] Qual é a dúvida?
**Contexto:** Por que essa questão é importante agora?
**Status:** 🔴 Bloqueante / 🟡 Requer Discussão
**Opções:**
- [A] Opção A: [Descreva cenário A]
- [B] Opção B: [Descreva cenário B]
- [C] Opção C: [Descreva cenário C]
- [D] Opção D: [Descreva cenário D]
- [X] Aberto: [Usuário pode fornecer uma solução alternativa]

**Resposta:** [Usuário, digite sua resposta aqui (ex: A, B ou texto livre)]

## Resolved Questions
*(Mova as perguntas resolvidas para cá documentando a decisão)*
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
## Change Log

- **[0.1.0]** `YYYY-MM-DD` 
  - **Intent**: Initial feature kick-off.
  - **Action**: Created planning structure.
  - **Status**: Blocked / Refining / Done
- **[0.0.1]** `YYYY-MM-DD` - Feature scaffolding created.
```

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

## Mermaid diagram rule

- If a feature has a user journey, interaction flow, or state map, store the source Mermaid diagram under `diagrams/`.
- Keep the long-form explanation in planning or feature docs, but keep the diagram source inside the feature folder.
- Reference the feature diagram from global journey docs instead of duplicating the Mermaid block in multiple places.