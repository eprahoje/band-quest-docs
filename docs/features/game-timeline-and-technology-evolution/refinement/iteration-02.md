# Feature 0008 - Game Timeline and Technology Evolution (Refinement 02)

## Decisions

### Ritmo turno↔tempo: 1 turno = 1 DIA — Q2 resolvida [custom]
- Revisão da cadência após o Playtest 01 (ponto 1): a semana não combinou — ações
  como descansar/ensaiar por uma semana inteira soaram irreais. **1 turno = 1 dia.**
- **Calendário de jogo:** 12 meses × 30 dias = **360 dias/ano** (abstração regular,
  evita meses irregulares). Exibição ao jogador: **Ano · Mês · Dia**
  (ex.: "Ano 1 · Março, dia 12").
- Sessões (0010): 10/20/30 anos = 3.600 / 7.200 / 10.800 dias. Como o tempo **avança
  pelas ações** (não dia a dia — ver 0014), o número alto de dias não vira clique
  manual: o jogador toma decisões e o relógio salta para a próxima conclusão.
- Substitui a decisão anterior de turno = semana (0003, iteration-03).

## Relationships impactadas
- **0003** — recalibra durações/custos para a base diária (revisado na iteration-04
  da 0003).
- **0014** — durações das ações passam a ser em dias; o avanço de tempo é orientado
  por ações (iteration-03 da 0014).

## Questions
- Q1 (granularidade da linha do tempo tecnológica), Q3 (eixos), Q4 (impacto) seguem
  abertas — não dependem da cadência.

## Checklist result
- [x] Scope reviewed.
- [x] Questions updated.
- [ ] Handoff reviewed.
