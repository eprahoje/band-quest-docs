# Feature 0011 - Career Milestones (Planning)

## Problem
A 0010 definiu que **marcos de carreira** dão bônus (dinheiro, reputação e bônus
na nota final) e podem desbloquear itens, mas não há dono do **catálogo de marcos**
nem das regras de gatilho/recompensa. Sem isso, a progressão não tem objetivos
intermediários memoráveis e a nota final perde uma de suas entradas.

## Goals
- Definir o **modelo de um marco** (gatilho, condição, recompensa, repetível ou não).
- Criar um **catálogo inicial de marcos** de carreira (ex.: primeiro show, 1k fãs,
  primeiro álbum, primeira turnê, assinar com gravadora, disco de ouro).
- Definir as **recompensas**: dinheiro, reputação, bônus na nota final (0010) e/ou
  desbloqueio de item (0012).
- Conectar ao loop e ao feed de eventos (um marco gera um evento `milestone`).

## Initial scope (proposta — refinar via questions)
- Modelo de dados de marco (id, título, condição, recompensa, ícone, único/repetível).
- Catálogo inicial enxuto (ex.: 8–12 marcos cobrindo cedo/médio/fim de carreira).
- Regra de avaliação: quando e como um marco é checado e disparado.

## Non-goals (nesta fase)
- Catálogo de itens em si (é da 0012).
- Calibragem numérica fina das condições e dos bônus (é da 0003).
- Progressão individual de membros (fora de escopo; ver 0007/0002).

## Acceptance criteria
- O modelo de marco está descrito.
- Há um catálogo inicial de marcos com gatilho e recompensa.
- A relação com 0010 (nota), 0012 (itens) e 0003 (números) está clara.
