# Feature Roadmap

This document evaluates how the initial proposals can be split into smaller features.

## Current epic features

- Visão do Jogo
- Progressão da Banda
- Economia e Reputação
- Competição, Tendências e Tecnologia

## Suggested split for smaller features

### Visão do Jogo
- Start Screen and Onboarding
- Era Selection and New Game Flow
- Core Loop and Band Creation
- Player Start Experience Polish

### Progressão da Banda
- Local Shows and First Gigs
- First Recordings and Releases
- Label Contract and Tour Flow

### Economia e Reputação
- Currency Model
- Reputation Model
- Economy Balance Rules

### Competição, Tendências e Tecnologia
- Market Trends Engine
- Rival Bands and Competition Pressure
- Technology Adoption Effects

## Design-focused features

- Start Screen and Onboarding
- Art Direction and Visual System

Note: Start Screen and Onboarding is intentionally cross-cutting. It belongs to the game vision epic and also stands as a design-focused feature.

## Features emerged from gaps

- **0007 - Band Members and Roster** — surgiu de uma lacuna identificada durante
  a implementação da 0006: o *card de membro* é da 0006 e a *criação da banda* é
  da 0005, mas o **modelo de membro e o roster** não tinham dono. A 0002
  (Progressão da Banda) cobre fases de carreira, não o roster. A 0007 referencia
  0005, 0006 e 0002 sem se sobrepor a elas.

## Mudança de premissa temporal (0001, iteration-02)

A 0001 foi redefinida: **sem seleção de era** — o jogo começa fixo no **Brasil
dos anos 2000** e evolui no tempo; o jogador escolhe a **duração/modo da sessão**.
O split antigo "Era Selection and New Game Flow" foi **descontinuado**. Disso
nasceram três features:

- **0008 - Game Timeline and Technology Evolution** — linha do tempo de
  tecnologia/mercado a partir dos anos 2000 (a evolução técnica migra da 0004
  para cá; a 0004 mantém competição/pressão de mercado).
- **0009 - Brazil 2000s Scenarios and Events** — cenários/eventos da época e
  homenagens IP-safe (bandas fictícias; paródia de nomes de banda, não de pessoas).
- **0010 - Session Modes and Outcomes** — modos por duração (10/20/30 anos com
  vitória/derrota) + modo livre sem vitória/derrota com duração personalizada.

## Decision rule

- If a proposal can be built, tested, and approved independently, it should be split into a smaller feature.
- If a proposal still contains multiple player-facing decisions, it should stay in the roadmap until decomposed.