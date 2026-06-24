# Feature 0012 - Unlockable Items (Planning)

## Problem
A 0010 e a 0011 preveem que marcos de carreira **desbloqueiam itens**, mas não há
dono do **catálogo de itens**, das **fontes de desbloqueio** nem dos **efeitos** que
um item tem no jogo. Sem isso, os marcos não têm o que entregar e o jogador não tem
progressão tangível além das métricas.

## Goals
- Definir o **modelo de item** (id, nome, categoria, fonte de desbloqueio, efeito).
- Definir as **fontes de desbloqueio** (marcos da 0011 e/ou outras condições).
- Definir os **tipos de efeito** (cosmético vs. impacto em loop/economia).
- Criar um **catálogo inicial** de itens.

## Initial scope (proposta — refinar via questions)
- Modelo de dados de item.
- Mapa marco→item (consome a 0011).
- Catálogo inicial enxuto por categoria (ex.: equipamento, estúdio, marketing,
  cosmético/visual).

## Non-goals (nesta fase)
- O catálogo de marcos em si (é da 0011).
- Calibragem numérica fina dos efeitos (é da 0003).
- Loja/economia de compra de itens, se houver (decidir se entra aqui via questions).

## Acceptance criteria
- O modelo de item está descrito.
- As fontes de desbloqueio e os tipos de efeito estão definidos.
- Há um catálogo inicial de itens com sua fonte e efeito.
