# Feature Template

Use this file as the starting point for every new feature.

## Folder layout

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
    iteration-02.md
    log.md
```

## Planning template

```md
# Feature 000X - Feature Name (Planning)

## Problem
Describe the problem the feature solves.

## Goals
- Goal one.
- Goal two.

## Initial scope
- Slice one.
- Slice two.

## Acceptance criteria
- The feature is described clearly enough for refinement.
- The scope is small enough for incremental implementation.
```

## Refinement checklist template

```md
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

```md
# Feature 000X - Feature Name (Checklist)

## Scope
- [ ] The problem statement is still accurate.
- [ ] The current iteration fits the planned scope.
- [ ] No hidden assumptions were introduced.

## Questions
- [ ] Open questions are listed in `questions.md`.
- [ ] Blocking doubts are explicit.
- [ ] Nothing important is waiting only in chat.

## Handoff
- [ ] The latest iteration is ready for implementation.
- [ ] The change can be split into small tasks.
- [ ] The feature can move to `band-quest-game` safely.
```

## Questions template

```md
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

```md
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

```md
# Feature 000X - Feature Name (Log)

## Change Log

- **[0.1.0]** `YYYY-MM-DD` 
  - **Intent**: Initial feature kick-off.
  - **Action**: Created planning structure.
  - **Status**: Blocked / Refining / Done

- **[0.1.1]** `YYYY-MM-DD` 
  - **Intent**: ...
  - **Action**: ...
  - **Status**: ...
```

## Local README template

```md
# Feature 000X - Feature Name

**Status:** Planning / In Refinement / Ready for Implementation

## Navigation
- [Planning overview](planning/overview.md)
- [Open questions](refinement/questions.md)
- [Latest iteration](refinement/iteration-01.md)
- [Action log](refinement/log.md)
```

## Log template

```md
# Feature 000X - Feature Name (Log)

## [0.1.0] - 2026-06-18T00:00:00Z

### Input
- Original user request or change request.

### Summary
- What the agent did in this iteration.

### Open questions
- Anything still unresolved.

### Next step
- The next decision or action.
```

## Code snippet examples

```text
feature/
  diagrams/
  planning/
  refinement/
    decomposition.md
    checklist.md
    questions.md
    iteration-01.md
    log.md
```

```md
## [0.2.0] - 2026-06-18T14:30:00Z
### Added
- New refinement question.
### Changed
- Scope updated after review.
```