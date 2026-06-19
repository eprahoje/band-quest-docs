# Band Quest Docs

Repositório de documentação do jogo de navegador **Band Quest**, um RPG de gestão de banda de Rock.

## Objetivo do jogo

O jogador cria e gerencia sua própria banda, começando de forma independente em uma época escolhida, publicando músicas na internet, conquistando público, marcando shows, gravando álbuns, assinando com gravadora e planejando turnês nacionais e internacionais.

A banda deve competir com o cenário atual e se adaptar a tendências e tecnologias do mercado. O progresso depende de decisões que afetam **dinheiro** e **reputação**.

## Estrutura da documentação

A documentação é organizada por **features**. Cada feature possui:

- `planejamento`: definição inicial de escopo, objetivos e critérios.
- `refinamento`: decisões iterativas, ajustes e validação human-in-the-loop.

```text
docs/
  features/
    0001-game-vision/
      planning/
        overview.md
      refinement/
        iteration-01.md
        questions.md
    0002-band-progression/
      planning/
        overview.md
      refinement/
        iteration-01.md
        questions.md
    0003-economy-and-reputation/
      planning/
        overview.md
      refinement/
        iteration-01.md
        questions.md
    0004-competition-trends-technology/
      planning/
        overview.md
      refinement/
        iteration-01.md
        questions.md
```

## Processo human-in-the-loop

1. Planejar a feature em `planning/overview.md`.
2. Registrar dúvidas bloqueantes em `refinement/questions.md`.
3. Refinar em iterações numeradas dentro de `refinement/`.
4. Consolidar a decisão antes de levar a implementação para o repositório `band-quest-game`.
5. Nunca sobrescrever uma iteração anterior; sempre criar a próxima.

Consulte o índice em [docs/features/README.md](docs/features/README.md).
