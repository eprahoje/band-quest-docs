# Feature 0010 - Session Modes and Outcomes (Refinement 03)

## Decisions

### Nota = média ponderada de status — Q5 resolvida [A]
- A nota final (1–5 estrelas) é uma **média de status positivos** acumulados na
  partida, **descontados os negativos**.
- Entradas positivas (exemplos): fãs, dinheiro em caixa, reputação, prêmios,
  discos vendidos, streams, álbuns lançados — "tudo que é status positivo ajuda
  na média; tudo que é negativo prejudica".
- **Faixas fixas de score por estrela, multiplicadas por um fator de duração**
  (10/20/30 anos): a mesma estrela exige score maior em sessões mais longas.
- A calibragem numérica (pesos de cada entrada, fator de duração, cortes de
  estrela) é da **0003**; a 0010 é dona do **conceito de agregação e do mapeamento
  score→estrelas**.

### Marcos e itens viram features próprias — Q6 resolvida [C, em dobro]
- **Duas novas features** nascem desta decisão (lacuna emergente):
  - **0011 - Career Milestones** — catálogo de marcos de carreira, gatilhos e os
    bônus que concedem (dinheiro/reputação/**bônus na nota final**).
  - **0012 - Unlockable Items** — catálogo de itens, como são desbloqueados (por
    marcos e/ou outras condições) e seus efeitos.
- A 0010 **referencia** ambas: a nota lê o bônus dos marcos; ela não é dona do
  catálogo de marcos nem de itens.

### Toggles do modo livre totalmente configuráveis — Q7 resolvida [C]
- O modo livre expõe um **conjunto completo de toggles por métrica e por sistema**
  (não um preset fixo). Exemplos: game over on/off, dinheiro infinito, reputação
  travada, sem fadiga/dissolução, eventos negativos on/off.
- O **detalhamento da lista** e a UI ficam para a 0005d (seleção) + calibragem;
  a 0010 fixa o princípio "configuração livre por métrica/sistema".

### Limiares conceituais de derrota — Q8 resolvida [A]
- **Falência:** N turnos consecutivos de caixa negativo.
- **Dissolução:** fadiga/moral no piso por M turnos.
- N e M (números) são da **0003**; a 0010 fixa a forma dos gatilhos (acúmulo por
  turnos, não evento único).

## Outcome
- Condições de modos, vitória (nota), derrota e modo livre estão **definidas em
  nível conceitual**. As pendências restantes são calibragem (0003), as duas
  features novas (0011/0012) e a UI (0005d) — nenhuma bloqueia a outra.
- Status da feature: **Ready for Implementation** para o núcleo (modos + nota +
  derrota + princípio de toggles), com marcos/itens delegados à 0011/0012.

## Checklist result
- [x] Scope reviewed.
- [x] Questions updated.
- [x] Handoff reviewed.
