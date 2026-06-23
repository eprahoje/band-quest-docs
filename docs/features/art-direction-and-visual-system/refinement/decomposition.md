# Feature 0006 - Art Direction and Visual System (Decomposition)

## Epic breakdown
- Sistema de cards de membros da banda (avatar + atributos).
- Painel de stats globais (reputação, caixa, fãs, fadiga).
- Feed de eventos (timeline de notícias do jogo).
- Biblioteca de ícones por categoria de ação.

## Why split
- Cada peça pode ser validada isoladamente como componente de UI.
- Permite que o avatar (decisão ainda aberta, ver `questions.md`) evolua sem
  travar o resto do sistema visual.

## Recommended order
1. Painel de stats (mais simples, sem dependência de assets).
2. Feed de eventos.
3. Cards de membros (depende da decisão de avatar).
4. Biblioteca de ícones consolidada como guia de referência.
