# Feature 0003 - Economia e Reputação (Checklist)

## Planning
- [x] Problem is clearly stated.
- [x] Goals are measurable or at least falsifiable.
- [x] Non-goals are explicit.

## Refinement
- [x] All blocking questions in `questions.md` are answered.
- [x] Latest iteration reflects the current decision, not a stale one.

## Handoff readiness
- [x] Scope can be split into small, testable implementation steps.
- [ ] `band-quest-game` team/agent has enough context without re-reading the whole history. *(depende da 0014 e do balance.)*

## Notas de handoff / dependências
- Implementação imediata possível: remover o trava-zero do caixa em `game.ts`.
- Contrato numérico consumido por 0010 (nota/derrota), 0011 (bônus), 0012 (custos/
  efeitos), 0013 (custos de staff).
- Turno = semana; duração/mecânica de ações → feature 0014 (Core Loop and Actions).
- Unidade de calendário formalizada na 0008.
- Valores concretos → iteração de balance dedicada.
