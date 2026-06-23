# Feature 0007 - Band Members and Roster (Refinement 03)

## Decisions

### Funções (lançamento)
- 5 funções: **Vocal, Guitarra, Baixo, Bateria, Teclado**.
- Sistema projetado para **extensibilidade futura**: desbloquear novas funções
  (DJ/Sampler, 2ª guitarra como função distinta, sopros) e **elevar o cap** de 5
  membros. Isso é direção, não escopo de implementação desta feature.

### Regras de composição (formação de 3 a 5)
- Funções de **instrumento podem repetir** (ex.: duas guitarras).
- **Vocal não repete** (máx. 1) e é **opcional** (0 ou 1) — por enquanto.
- **Mínimo de 3 instrumentistas**, sendo **pelo menos 1 baterista** (bateria
  obrigatória).
- Implicação: banda de 3 = 3 instrumentistas sem vocal; vocal só cabe a partir
  de 4 membros. Permite bandas instrumentais (estilo Polyphia).

### Personagens
- **15 personagens iniciais** = 5 funções × 3 opções.
- Cada um tem atributos fixos (Técnica, Carisma, Criatividade, Energia) com
  perfis contrastantes para habilitar *builds* diferentes.
- Cast proposto (dados) em [`planning/design.md`](../planning/design.md).
  **Proposta para revisão** — nomes/perfis são um ponto de partida.

### Trade-offs de tamanho
- Direção registrada aqui (tamanho → acesso a recursos vs sobrecarga de gestão);
  **calibragem numérica é da feature 0003 (economia/balance)**.

## Questions
- Sem perguntas bloqueantes. O cast é uma proposta aberta a refino.

## Checklist result
- [x] Scope reviewed.
- [x] Questions updated.
- [x] Handoff reviewed (brief de ícones completo com 15 personagens).
