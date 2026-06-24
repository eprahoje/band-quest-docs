# Feature 0014 - Core Loop and Actions (Refinement 01)

## Decisions
- Feature criada a partir da Q3 da 0003: o modelo de ação e o core loop ganham dono
  próprio, separados da economia (0003) e do calendário (0008).
- Direção: ações têm **duração variável em turnos** (turno = semana, da 0003/0008) e
  um **ciclo de vida** (idle → em progresso por N turnos → resultado → efeitos).
- A 0003 fornece custos/ganhos; a 0014 fornece duração, mecânica e integração.

## Questions
- Q1 (conjunto de ações), Q2 (uma vs. várias ações), Q3 (qualidade × duração),
  Q4 (falha/variação de resultado) abertas em `questions.md`.

## Checklist result
- [x] Scope reviewed.
- [x] Questions updated.
- [ ] Handoff reviewed.
