# Feature 0012 - Unlockable Items (Decomposition)

## Epic breakdown
- Modelo de item (id/categoria/fonte/efeito).
- Fontes de desbloqueio (marcos da 0011 e/ou outras condições).
- Tipos de efeito (cosmético vs. impacto no loop/economia).
- Catálogo inicial por categoria.

## Why split
- O modelo e os tipos de efeito podem ser definidos antes do catálogo completo.
- O mapa marco→item depende da 0011 estar minimamente fechada.
- Efeitos numéricos são calibrados na 0003.

## Recommended order
1. Modelo de item + tipos de efeito.
2. Fontes de desbloqueio (integra 0011).
3. Catálogo inicial.
4. Integração no loop/economia.
