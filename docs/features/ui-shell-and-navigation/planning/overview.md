# Feature 0020 - UI Shell and Navigation (Planning)

## Problem
O `GameView` cresceu para um **scroll vertical único** com ~10 seções empilhadas (Stats,
Custos, Ganhos, Banda, Em andamento, Músicas, Equipe, Locais, Ações, Feed). Jogar exige
rolar para cima e para baixo o tempo todo (feedback dos Playtests 06/07). Como o jogo
ganhou profundidade (venues, equipe, inventário), a apresentação precisa escalar.

## Goals
- Refatorar em **telas/abas por área**, mostrando só a aba ativa (mata o scroll).
- Manter um **HUD fixo**: stats (reputação/caixa/fãs/fadiga), calendário e o botão **Avançar**
  sempre visíveis (o controle principal e o placar não somem ao trocar de aba).
- **Preservar o estado** ao navegar (o store Pinia é central — trocar de aba não perde nada).
- **Distribuir as ações** para as telas relevantes (ação vive no contexto: compor no Estúdio,
  show em Shows, ensaiar na Banda).

## Decisão (iteration-01)
- Modelo: **abas por área** (não multi-coluna; não feed lateral).
- Telas: **Visão · Banda · Estúdio · Shows · Equipe · Finanças**.
- Ações **distribuídas** por tela.

## Non-goals
- Nenhuma mudança de mecânica/economia (só apresentação).
- Rota/URL por tela (o estado de aba é local; pode virar rota no futuro).
- Redesenho visual dos componentes internos (reusam os atuais + tokens.css).

## Acceptance criteria
- HUD (stats + calendário + Avançar) fica fixo; as demais seções vivem em abas.
- Trocar de aba não altera o estado do jogo.
- Cada ação aparece na sua tela; iniciar/cancelar continua funcionando.
- Gate verde (testes ajustados para navegar entre abas).
