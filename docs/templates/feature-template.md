# Feature Template

Use this file as the starting point for every new feature.

## Folder layout

```
docs/features/000X-feature-slug/
  README.md
  diagrams/
    README.md
  planning/
    overview.md
  refinement/
    decomposition.md
    checklist.md
    questions.md
    iteration-01.md
    log.md
```

## Planning template

```
# Feature 000X - Feature Name (Planning)

## Problem
Describe the problem the feature solves.

## Goals
- Goal one.
- Goal two.

## Initial scope
- Slice one.
- Slice two.

## Non-goals (nesta fase)
- O que explicitamente não está incluso ainda.

## Acceptance criteria
- The feature is described clearly enough for refinement.
- The scope is small enough for incremental implementation.
```

## Decomposition template

```
# Feature 000X - Feature Name (Decomposition)

## Epic breakdown
- Smaller feature one.
- Smaller feature two.
- Smaller feature three.

## Why split
- Reduce cognitive load.
- Create implementation-sized slices.
- Allow independent validation and handoff.

## Recommended order
1. First smaller feature.
2. Second smaller feature.
3. Third smaller feature.
```

## Checklist template

```
# Feature 000X - Feature Name (Checklist)

## Planning
- [ ] Problem is clearly stated.
- [ ] Goals are measurable or at least falsifiable.
- [ ] Non-goals are explicit.

## Refinement
- [ ] All blocking questions in `questions.md` are answered.
- [ ] Latest iteration reflects the current decision, not a stale one.

## Handoff readiness
- [ ] Scope can be split into small, testable implementation steps.
- [ ] `band-quest-game` team/agent has enough context without re-reading the whole history.
```

## Questions template

```
# Feature 000X - Feature Name (Questions)

## Open Questions

### [Q1] Question short title?
**Context:** Why is this a blocking issue or important to define now?
**Status:** 🔴 Blocking / 🟡 Needs Discussion / 🟢 Minor
**Options:**
- [A] Option A: ...
- [B] Option B: ...
- [C] Option C: ...
- [D] Option D: ...
- [X] Open option: (Let user define another solution)

**Answer:** [User, please type your answer here (e.g., A, B, or your custom text)]

## Resolved Questions

### [Q0] Example of a resolved question?
**Decision:** We chose X because of Y.
**References:** Solved in `iteration-XX.md`.
```

## Iteration template

```
# Feature 000X - Feature Name (Refinement 01)

## Decisions
- Decision one.
- Decision two.

## Questions
- Question one.
- Question two.

## Checklist result
- [ ] Scope reviewed.
- [ ] Questions updated.
- [ ] Handoff reviewed.
```

## Log template

Use exactly this format — it is the only valid log format in this repository.

```
# Feature 000X - Feature Name (Log)

## [0.1.0] - YYYY-MM-DDTHH:MM:SSZ

### Input
- Original user request or change request.

### Summary
- What the agent did in this iteration.

### Open questions
- Anything still unresolved.

### Next step
- The next decision or action.
```

## Local README template

```
# Feature 000X - Feature Name

**Status:** Planning / In Refinement / Ready for Implementation

## Navigation
- [Diagrams](diagrams/README.md)
- [Planning overview](planning/overview.md)
- [Decomposition](refinement/decomposition.md)
- [Checklist](refinement/checklist.md)
- [Open questions](refinement/questions.md)
- [Latest iteration](refinement/iteration-01.md)
- [Action log](refinement/log.md)
```
