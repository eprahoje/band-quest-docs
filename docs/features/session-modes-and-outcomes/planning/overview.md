# Feature 0010 - Session Modes and Outcomes (Planning)

## Problem
Com a 0001 removendo a seleção de era, o jogador passa a escolher a **duração/modo
da sessão**. Precisamos definir os modos e o que significa **ganhar ou perder**
uma sessão — caso contrário a partida não tem objetivo nem fim claro.

## Goals
- Definir os **modos de sessão**:
  - **Temporizados:** 10, 20 e 30 anos de jogo, com **condições de vitória/derrota**.
  - **Modo livre:** sem vitória/derrota, com **duração personalizada** (incl.
    possibilidade de seguir indefinidamente).
- Definir **condições de vitória e de derrota** para os modos temporizados.
- Integrar com a economia (0003) e com o ritmo de tempo (0008).

## Initial scope (proposta — refinar via questions)
- Tela/dado de seleção de modo (UI fica na 0005).
- Conjunto de condições de vitória (ex.: atingir marcos de reputação/fãs/caixa
  dentro do prazo) e de derrota (ex.: falência, banda dissolvida).
- Estado de fim de sessão (tela de resultado).

## Non-goals (nesta fase)
- Calibragem numérica fina dos limiares (é da 0003).
- A linha do tempo tecnológica (é da 0008).
- A UI detalhada da tela de seleção (é da 0005).

## Acceptance criteria
- Os modos estão definidos (temporizados + livre).
- Há condições de vitória/derrota claras para os modos temporizados.
- O estado de fim de sessão está descrito.
