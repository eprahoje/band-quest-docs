# Feature 0006 - Art Direction and Visual System (Planning)

## Problem
O jogo precisa de uma identidade visual jogável desde o MVP, sem depender de
produção de sprites, pixel art ou ilustração de personagens — que tem custo e
tempo de produção incompatíveis com a fase de validação do core loop.

## Goals
- Validar a mecânica de gestão de banda antes de investir em arte original.
- Definir um sistema visual reutilizável (cards, ícones, painéis) que sirva
  tanto para o MVP quanto como base para uma camada de polimento futura.
- Manter o escopo de arte em zero ou quase zero para o primeiro release jogável.

## Initial scope
- Avatares de membros da banda como iniciais coloridas ou ilustração vetorial
  simples e estática (uma única pose, sem variações/animação).
- Painel de stats (reputação, caixa, fãs, fadiga) como cards numéricos.
- Feed de eventos estilo timeline (ícone de biblioteca + texto), substituindo
  cutscenes ou cenas ilustradas.
- Biblioteca de ícones (ex: Tabler/Lucide) para todas as ações e categorias
  do jogo (show, gravação, turnê, negociação).

## Non-goals (nesta fase)
- Sprites animados ou pixel art de personagens.
- Cenários ilustrados (venues, estúdios, cidades).
- Variações visuais por estado de humor/fadiga do personagem.

## Acceptance criteria
- O MVP é completamente jogável usando apenas cards, ícones e tipografia.
- Nenhuma tela do MVP depende de um asset de arte original ainda não produzido.
- A decisão está registrada para consulta de futuros agentes/colaboradores.
