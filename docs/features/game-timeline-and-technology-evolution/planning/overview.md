# Feature 0008 - Game Timeline and Technology Evolution (Planning)

## Problem
O jogo começa no Brasil dos anos 2000 e avança no tempo (decisão da 0001). Sem
uma linha do tempo de tecnologia/mercado, a passagem dos anos não significa nada
mecanicamente. Precisamos modelar como a tecnologia evolui e afeta o jogo.

## Goals
- Definir uma **linha do tempo** de eras tecnológicas a partir dos anos 2000.
- Dar **impacto mecânico** a cada era (não só estético): formatos de lançamento,
  canais de distribuição, alcance de público, custos.
- Definir o **ritmo** de avanço do tempo (relação turno ↔ ano).
- Integrar com a economia (0003) e a competição (0004).

## Initial scope (proposta — refinar via questions)
- Blocos de era tecnológica, ex.:
  - ~2000–2004: CD/rádio/TV, internet discada, gravadora forte.
  - ~2005–2010: P2P, MySpace/fotolog, iTunes — pirataria e venda digital.
  - ~2010–2015: redes sociais, YouTube — viralização.
  - ~2015+: streaming, algoritmos de playlist.
- Efeitos de alto nível por era (placeholders; números na 0003).

## Non-goals (nesta fase)
- Precisão histórica exaustiva (datas exatas de cada produto).
- Eventos culturais/musicais da época (vão para a 0009).
- Seleção de era pelo jogador (descontinuada na 0001).

## Acceptance criteria
- A linha do tempo está descrita o suficiente para implementação incremental.
- Cada era tem efeitos mecânicos claros (mesmo que calibrados depois pela 0003).
- O ritmo turno↔ano está definido.
