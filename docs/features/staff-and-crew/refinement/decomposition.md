# Feature 0013 - Staff and Crew (Decomposition)

## Epic breakdown
- Modelo de staff (papel/custo/salário/efeito/pré-requisitos).
- Conjunto inicial de papéis.
- Regra de contratação/demissão e custo contínuo (por turno).
- Integração: desbloqueios (0012), marcos (0011), novas ações/eventos.

## Why split
- O modelo pode ser definido antes do conjunto completo de papéis.
- Custos/efeitos são calibrados separadamente (0003).
- A integração com 0011/0012 é uma fatia testável independente.

## Recommended order
1. Modelo de staff.
2. Papéis iniciais.
3. Contratação/demissão + custo por turno.
4. Integração com desbloqueios, marcos e ações.
