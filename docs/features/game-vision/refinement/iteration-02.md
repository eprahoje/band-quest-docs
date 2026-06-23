# Feature 0001 - Visão do Jogo (Refinamento 02)

## Foco da Iteração
Redefinir a premissa temporal do jogo (mudança MAJOR): de "escolha de época" para
"início fixo no Brasil dos anos 2000 + evolução no tempo + modos de sessão".

## Decisions
- **Início fixo no Brasil dos anos 2000.** O jogador **não escolhe a época**;
  todos começam na mesma era. (Resolve Q1.)
- **O mundo evolui no tempo** a partir dos anos 2000 — tecnologia e mercado mudam
  conforme os anos passam (mídia física → digital → redes/streaming). O
  detalhamento é da nova feature **0008**. (Resolve Q2.)
- **Modos de sessão por duração**, no lugar de seleção de era — nova feature
  **0010**:
  - Temporizados: **10 / 20 / 30 anos**, com **condições de vitória/derrota**.
  - **Modo livre:** sem vitória/derrota, com **duração personalizada**.
- **Cenários e eventos do Brasil dos anos 2000** (com homenagens IP-safe) — nova
  feature **0009**.
- O split antigo "Era Selection and New Game Flow" é **descontinuado**.

## Impacto em cascata
- **0004 (Competição, Tendências e Tecnologia):** a evolução tecnológica como
  linha do tempo migra para a 0008; a 0004 mantém competição e pressão de
  mercado. Reconciliar quando a 0008 for construída.
- **0005 (Start Screen / nova partida):** a tela de nova partida passa a oferecer
  **seleção de modo/duração** (definido na 0010), não seleção de era.
- **0006 (Arte):** a decisão "atemporal/multi-era" **permanece válida** — o jogo
  segue atravessando eras, agora avançando no tempo. Apenas a justificativa muda.

## Questions
- Resolvidas: Q1, Q2 (ver `questions.md`).
- As novas decisões abrem questões próprias dentro de 0008, 0009 e 0010
  (refinamento de cada uma em separado).

## Registro
- Estado: premissa redefinida; features-filhas a refinar.
