# Feature 0014 - Core Loop and Actions (Planning)

## Problem
O loop atual do jogo tem ações **hardcoded** no `GameView` (tocar show, gravar demo,
descansar) que avançam exatamente 1 turno cada. A 0003 (Q3) definiu que o turno é uma
**semana** e que ações têm **duração variável em turnos** conforme escopo/qualidade.
Não há dono do **modelo de ação** nem do core loop — o que é pré-requisito para
calibrar a economia e para um ritmo de carreira realista.

## Goals
- Definir o **modelo de ação** (id, duração em turnos, pré-requisitos, resultado,
  escala por qualidade/recursos).
- Definir o **conjunto inicial de ações** (ensaiar, compor, gravar single/álbum,
  tocar show, turnê, marketing, descansar, etc.).
- Definir como a duração e o resultado **escalam** (qualidade-alvo, produtor 0013,
  itens 0012, atributos dos membros 0007).
- Definir o **estado de ação em progresso** e como o jogador avança turnos.

## Initial scope (proposta — refinar via questions)
- Modelo de dados de ação + máquina de estado (idle → em progresso → concluída).
- Conjunto inicial de ações com duração e resultado de alto nível.
- Regra de avanço de turno e bloqueio por fadiga (0003).

## Non-goals (nesta fase)
- Valores concretos de custo/ganho/duração (balance — 0003).
- A unidade de calendário em si (0008) e a UI final.
- Catálogos de itens/staff/marcos (0011/0012/0013) — aqui só os pontos de integração.

## Acceptance criteria
- O modelo de ação e o ciclo de vida estão descritos.
- Há um conjunto inicial de ações com duração e resultado.
- Os pontos de integração com 0003/0007/0011/0012/0013 estão claros.
