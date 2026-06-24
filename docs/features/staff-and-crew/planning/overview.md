# Feature 0013 - Staff and Crew (Planning)

## Problem
Durante o refinamento da 0012, o usuário propôs que o jogador possa **contratar
staff** (empresário, preparador vocal, roadies, motorista, etc.) que leva a
**desbloqueios e caminhos** próprios. Isso é um sistema distinto de itens
(equipamentos): staff são **pessoas com papel, custo e efeito contínuo**, e não há
dono para esse modelo.

## Goals
- Definir o **modelo de staff** (papel, custo de contratação/salário, efeito).
- Definir o **conjunto inicial de papéis** (ex.: empresário, preparador vocal,
  roadie, motorista, produtor).
- Definir como o staff **leva a desbloqueios/caminhos** (itens 0012, marcos 0011,
  novas ações/eventos).
- Conectar o custo contínuo ao loop e à economia (0003).

## Initial scope (proposta — refinar via questions)
- Modelo de dados de staff (id, papel, custo, salário, efeito, pré-requisitos).
- Conjunto inicial de papéis com efeito de alto nível.
- Regra de contratação/demissão e impacto no caixa por turno.

## Non-goals (nesta fase)
- Calibragem numérica de custos/salários/efeitos (é da 0003).
- Catálogo de itens em si (é da 0012) — aqui só a relação de desbloqueio.
- Progressão/atributos dos membros da banda (é da 0007/futuro).

## Acceptance criteria
- O modelo de staff está descrito.
- Há um conjunto inicial de papéis com custo e efeito.
- A relação com 0012 (desbloqueios), 0011 (marcos) e 0003 (números) está clara.
