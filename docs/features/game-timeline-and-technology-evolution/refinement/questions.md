# Feature 0008 - Game Timeline and Technology Evolution (Questions)

## Open Questions

### [Q1] Granularidade da linha do tempo?
**Context:** Define o nível de detalhe e o trabalho de modelagem.
**Status:** 🔴 Blocking
**Options:**
- [A] Blocos de era (~4–5 anos cada).
- [B] Por ano.
- [C] Por marco tecnológico (evento dispara a mudança, sem grade fixa).
- [X] Aberto.

**Answer:**

### [Q3] Quais eixos tecnológicos modelar?
**Context:** Define o que muda com o tempo.
**Status:** 🟡 Needs Discussion
**Options:**
- [A] Distribuição/mídia (CD → digital → streaming).
- [B] A + comunicação/marketing (rádio/TV → redes/viralização).
- [C] B + gravação/produção (estúdio caro → home studio).
- [X] Aberto.

**Answer:**

### [Q4] Tipo de impacto mecânico de cada era?
**Context:** Como a era muda o jogo (a calibragem numérica é da 0003).
**Status:** 🟡 Needs Discussion
**Options:**
- [A] Modifica alcance de público e custos de lançamento.
- [B] A + muda os canais disponíveis (ex.: streaming destrava nova ação).
- [X] Aberto.

**Answer:**

## Resolved Questions

### [Q2] Ritmo do tempo: relação turno ↔ ano?
**Decision:** 1 turno = **1 dia**. Calendário de jogo de 12 meses × 30 dias = 360
dias/ano, exibido como Ano · Mês · Dia. O tempo avança pelas ações (0014), não dia a
dia. Revisão da cadência após o Playtest 01 (substitui turno = semana).
**References:** Solved in `iteration-02.md`.
