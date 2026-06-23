# Feature 0007 - Band Members and Roster (Refinement 02)

## Decisions
- **Formação variável de 3 a 5 membros.** O tamanho é uma escolha estratégica
  com trade-offs (ideia do usuário):
  - Banda menor → menos recursos iniciais, porém menos membros para gerenciar
    (menos problemas/sobrecarga).
  - Banda maior (5) → mais capacidade, porém mais gestão e custo.
  - A direção do trade-off fica registrada aqui; a calibragem numérica é tema
    de discussão com a economia (ver Q8).
- **Cast de personagens pré-definidos**, com **pelo menos 3 opções por função**.
  Isso permite *builds* com objetivos e estilos diferentes (escolher entre
  personagens com perfis de atributo distintos para a mesma função).
- **Atributos do membro: Técnica, Carisma, Criatividade, Energia** (4 eixos),
  confirmando o modelo prototipado no card da 0006.
- **Progressão individual fica fora desta feature** — entra como feature futura.
  Aqui os atributos são fixos por personagem (estado inicial do roster).

## Questions
- Resolvidas: Q1–Q4 (ver `questions.md`).
- Abertas: Q5 (quais funções existem), Q6 (regras de composição/obrigatoriedade),
  Q7 (quantas opções por função no lançamento), Q8 (onde especificar os
  trade-offs de tamanho — aqui vs economia 0003).

## Checklist result
- [x] Scope reviewed.
- [x] Questions updated.
- [ ] Handoff reviewed (cast depende de Q5/Q7 para fechar a contagem de ícones).
