# Feature 0007 - Band Members and Roster (Planning)

## Problem
O jogo trata os membros da banda como dado solto — a store já tem
`BandMember { id, name, role, skill }`, mas nenhuma feature especifica:
- quem são os membros iniciais (cast),
- quais atributos descrevem um membro,
- como a formação (roster) é criada e exibida,
- se e como os membros evoluem ao longo do jogo.

O *card de membro* (visual) pertence à 0006 e a *criação da banda* à 0005, mas o
**modelo de membro e o roster** não têm feature dona. Isso é a lacuna que esta
feature fecha — e é pré-requisito para o `MemberCard.vue` e para o handoff de
arte dos ícones dos personagens iniciais.

## Goals
- Definir o **modelo de dados** de um membro (identidade, papel/instrumento,
  atributos).
- Especificar a **formação inicial** (quantos membros, papéis, personagens) de
  modo que vire um brief de arte sem novas perguntas.
- Dar **contrato claro** para o `MemberCard.vue` (0006) e para o fluxo de
  criação (0005) consumirem.
- Decidir se a **progressão individual** entra aqui ou numa feature futura.

## Initial scope (proposta — refinar via `refinement/questions.md`)
- Modelo de membro: identidade + papel/instrumento + conjunto de atributos.
- Especificação do cast inicial como fonte única para o handoff de ícones.
- Fronteiras explícitas com 0005 (criação) e 0006 (card visual).

## Non-goals (nesta fase)
- Simulação social/drama entre membros.
- Mercado dinâmico de contratação/demissão de membros (possível feature futura).
- Animação dos personagens — a 0006 já decidiu: ilustração estática, pose fixa.
- Progressão individual de atributos (decidido fora desta feature — Q4).
- Desbloqueio de novas funções e elevação do cap de 5 membros — direção
  registrada para o futuro, mas fora do escopo de implementação agora.
- Calibragem numérica dos trade-offs de tamanho da banda (é da feature 0003).

## Acceptance criteria
- O modelo de membro está descrito o bastante para implementar em
  `band-quest-game`.
- A formação inicial está especificada o suficiente para um agente de arte
  produzir os ícones sem novas perguntas.
- As fronteiras com 0005 e 0006 estão explícitas.
