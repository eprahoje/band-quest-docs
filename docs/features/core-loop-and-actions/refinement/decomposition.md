# Feature 0014 - Core Loop and Actions (Decomposition)

## Epic breakdown
- Modelo de ação (duração/pré-requisitos/resultado/escala).
- Ciclo de vida e estado de ação em progresso + avanço de turno.
- Conjunto inicial de ações.
- Integração: economia (0003), membros (0007), marcos (0011), itens/staff (0012/0013).

## Why split
- O modelo e o ciclo de vida podem ser definidos antes do conjunto completo.
- A escala por qualidade/recursos é refinável separadamente.
- A integração é uma fatia testável independente.

## Recommended order
1. Modelo de ação + ciclo de vida (estado em progresso, avanço de turno).
2. Conjunto inicial de ações.
3. Escala por qualidade/recursos.
4. Integração com economia, membros, marcos, itens e staff.
