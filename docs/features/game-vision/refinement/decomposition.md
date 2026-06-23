# Feature 0001 - Visão do Jogo (Decomposição)

## Epic breakdown
- **0005** - Start Screen and Onboarding (entrada + fluxo de nova partida).
- **0007** - Band Members and Roster (criação da banda / cast).
- **0008** - Game Timeline and Technology Evolution (linha do tempo a partir
  dos anos 2000).
- **0009** - Brazil 2000s Scenarios and Events (cenários/eventos da época).
- **0010** - Session Modes and Outcomes (duração + vitória/derrota + modo livre).

## Why split
- A premissa central (início fixo nos anos 2000, mundo que evolui, modos de
  sessão) combina entrada, contexto temporal e condições de fim de jogo.
- Separar melhora o refinamento e o handoff para implementação.

## Note sobre numeração
- O split antigo "Era Selection and New Game Flow" foi **descontinuado**: não há
  mais seleção de era (decisão da iteration-02). A numeração especulativa anterior
  (0007/0008/0009 para outros nomes) não vingou; os números reais em uso são
  0005, 0007, 0008, 0009 e 0010 conforme o índice em `docs/features/README.md`.

## Recommended order
1. Start screen and onboarding (0005).
2. Session modes and outcomes (0010) — define como a sessão começa e termina.
3. Game timeline and technology evolution (0008).
4. Brazil 2000s scenarios and events (0009).
