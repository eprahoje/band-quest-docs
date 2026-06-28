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

- **0011 - Career Milestones** e **0012 - Unlockable Items** — surgiram da Q6 da
  0010 (Session Modes and Outcomes). Ao definir que marcos de carreira dão bônus e
  desbloqueiam itens, o usuário optou por separar as duas responsabilidades em
  features próprias: a **0011** é dona do catálogo de marcos e suas recompensas; a
  **0012** é dona do catálogo de itens, das fontes de desbloqueio e dos efeitos. A
  0010 apenas referencia ambas (a nota final lê o bônus dos marcos). A calibragem
  numérica de ambas fica na 0003.

## Desdobramentos do refinamento da 0012

Surgiram durante a Q4 da 0012 (Unlockable Items) e foram decididos nas Q5/Q6:

- **0013 - Staff and Crew (criada)** — contratar empresário, preparador vocal,
  roadies, motorista, etc., levando a desbloqueios e caminhos próprios. É um sistema
  distinto de "itens"; virou feature própria por decisão da Q6 da 0012.
- **Loja (Shop) de itens** — **fica na 0012** como fonte de desbloqueio por compra.
  Gatilho de extração para feature própria: se ganhar preços dinâmicos, estoque por
  época ou UI dedicada que justifiquem escopo separado (decisão da Q5 da 0012).

## Desdobramento do refinamento da 0003

- **0014 - Core Loop and Actions (criada)** — surgiu na Q3 da 0003: ações têm
  **duração variável em turnos** (gravar álbum/turnê ocupam N turnos conforme
  escopo/qualidade) e o turno é uma **semana** (calendário granular), não um ano.
  Hoje as ações estão hardcoded no `GameView`; a 0014 é dona do **modelo de ação +
  duração + ciclo de vida**. A 0003 fornece custos/ganhos; a 0008 fornece o
  calendário. Promovida de candidata a feature por decisão da Q3 da 0003.

## Backlog de playtest — 2026-06-24 (Playtest 01)

Feedback do primeiro playtest do motor de ações (0014) + caixa/calendário (0003).
Detalhe completo e input original em
[docs/playtests/playtest-2026-06-24.md](../playtests/playtest-2026-06-24.md).

### Features candidatas (a scaffoldar quando priorizadas)
- **0015 - Songwriting and Releases (scaffoldada 2026-06-25, In Refinement)** — gravação profunda: o jogador
  controla nome do single, gênero base, temas; cadeia composição → single → álbum
  (álbum exige X singles + músicas; demo exige mínimo de músicas) e seus impactos.
  (Ponto 3.)
- **0016 - Venues and Shows (candidata)** — localidade dos shows; catálogo de
  lugares que se desbloqueia conforme a reputação cresce; trajeto de turnê pelas
  cidades/estados do Brasil (começa no estado de origem e evolui). (Pontos 6 e 10.)

### Revisões de mecânica / escopo
- **Granularidade do turno** (0003 Q3 / 0008 / 0014) — turno = **semana** não
  agradou; migrar para **dia** (ações de 1+ dias) para mais realismo, mais ações
  paralelas e desbloqueio de ações principais via progresso/staff. (Ponto 1.)
- **Marketing desbloqueável** (0014 + 0012/0013) — tirar das ações iniciais;
  liberar via staff ou agência (item caro). (Ponto 9.)
- **Turnê: requisito alto + gate por staff** (0014 + 0013) — turnê difícil de
  conquistar; meta-game inicial = bares/lugares menores até surgirem oportunidades.
  (Pontos 10 e 11.)

### Bug conhecido
- **Soft-lock de descanso** (0014) — `rest` é bloqueado pela fadiga junto das demais
  ações `main`; isentar `rest` do bloqueio. Correção rápida. (Ponto 2.)

### UX / técnico
- ✅ **Timeline "infinita"** (0014 / `EventFeed`) — **feito (2026-06-25)**: cap de 40
  eventos renderizados + rolagem (`max-height`), com aviso de quantos ficaram ocultos.
  Histórico completo separado / poda no store seguem como backlog futuro. (Ponto 12.)

### Backlog de balance (iteração de balance da 0003)
- Curva de reputação: 40+ cedo demais e com pouco impacto; equilibrar ganhos/perdas
  de recursos. (Ponto 7.)
- Preços/requisitos visíveis por ação + eventos relatando impactos em recursos.
  (Ponto 4.)
- Tornar visível a **manutenção** da banda (dinheiro/reputação/fãs por turno).
  (Ponto 8.)

### Backlog de eventos (0009)
- Acontecimentos aleatórios por turno com escopos **membro / banda / mundo**, com
  impacto opcional, para dar variedade à timeline. (Ponto 5.)

## Backlog de playtest — 2026-06-24 (Playtest 02)

Após o Balance pass 1. Detalhe e input original em
[docs/playtests/playtest-2026-06-24-session-02.md](../playtests/playtest-2026-06-24-session-02.md).

### Feito nesta sessão (implementado)
- Reputação começa em 0 e **sem teto** (ponto 1) — futuras lojas/desbloqueios.
- Calendário mostra o **ano histórico real** (início em 2000) (ponto 7).
- **Recuperação passiva** de fadiga ao avançar o tempo (ponto 8).
- Acontecimentos **reportam os efeitos** (deltas) das ações (ponto 9).

### Features candidatas (a scaffoldar quando priorizadas)
- **0015 - Songwriting and Releases (scaffoldada 2026-06-25, In Refinement)** — reforçada: janela de músicas
  consultável; música com nome/gênero/tema; álbum exige X singles + X músicas;
  aprofundar o que "caprichado" muda além do custo (pontos 5, 5.1, 5.2).
- **0017 - Contracts and Salaries (candidata)** — salário individual por atributos +
  reputação, crescendo com a evolução do membro; contratos (1 ano), renovação que
  aumenta salário e traz exigências; salário visível nos cards (pontos 2, 2.1, 2.2).

### Revisões / dependências
- **Ensaiar → XP de membro** (ponto 3) — redefine `rehearse` (0014); depende de
  progressão de membros (0007) e de estúdio como item (0012).
- **Aba de Ganhos** (ponto 6) — espelha a de Custos; exige receita rastreada
  (royalties/vendas) — 0003 + 0015.
- ✅ **Painéis recolhíveis** (ponto 4) — **feito (2026-06-25)**: componente
  `CollapsibleSection` reutilizável; seções Custos, Banda, Em andamento e Ações
  recolhíveis no GameView (Stats e a loop-bar de avanço seguem fixas).
- **Contexto histórico no start** (ponto 7.1) — 0005 + sabor 0009.

### Próxima slice candidata
- **Escolha do tamanho da sessão no setup** (ponto 10) — StartView (0005d) consumindo
  os modos da 0010; pareia com o fim de sessão da 0010 (nota/derrota).

## Backlog de playtest — 2026-06-25 (Playtest 03)

Após a 0015 (slices 1, 3, 5). Detalhe e input original em
[docs/playtests/playtest-2026-06-25.md](../playtests/playtest-2026-06-25.md).

### Follow-up da 0015 (em implementação)
- ✅ **Seleção de faixas ao gravar** (ponto 4) — *feito 2026-06-26* (D6): painel inline
  de seleção; o jogador escolhe as músicas/singles. Qualidade passou a importar.
- ✅ **Edição de metadado** (pontos 2, 3) — *feito 2026-06-26* (D7): edição inline na aba
  Músicas (nome/estilo/tema) e renomear lançamentos.
- ✅ **Quick win — contador redundante** (ponto 6) — *feito 2026-06-26*: removido o
  "Músicas prontas" da loop-bar.
- ✅ **Royalties + aba de Ganhos** (ponto 8) — *feito 2026-06-26* (slice 4): lançamentos
  geram royalty decrescente por turno (demo 0, single cauda curta, álbum cauda longa);
  aba **Ganhos** espelha a de Custos; coluna de royalty atual no SongLibrary. Números são
  placeholders → 0003.
- **SongLibrary: ordenação + cap** (ponto 10) — mais novo → mais antigo + limite com
  indicação de ocultos (espelha o EventFeed). Filtro fica como evolução.
- **Quick win:** remover "Músicas prontas: {qtd}" da loop-bar (ponto 6) — redundante.
- **EP/LP** (ponto 8.1) — extensão de design da 0015 (nova iteration): dividir álbum em
  EP e LP; multi-CD/ao vivo/DVD (8.2) ficam para o futuro.
- **Pools maiores** de nomes autogerados (ponto 5) — futuro.

### Candidatas a feature (novas/reforçadas)
- **0016 - Venues and Shows** (reforçada) — locais por reputação, ingressos, calendário
  de shows (pontos 7.1, 7.2, 7.3).
- **0018 - Label Contracts and Opportunities** (nova) — demo como porta de entrada para
  oportunidades/contrato com gravadora (ponto 1). Casa com "Label Contract and Tour Flow".
- **0019 - Decision Gates / Choice Events** (nova) — eventos que exigem decisão do jogador
  com consequências; complementa a 0009 (ponto 12).
- **Navegação / UI Shell** (nova, sem número) — dividir a tela única em abas/telas
  (ref.: *A Story of a Band*) quando o scroll único ficar grande demais (ponto 11).

### Balance
- **Cachê de show escala com reputação** (ponto 7) — 0003 + 0014.
- **Turnê rende pouco / fadiga mal calibrada** (pontos 9, 9.1) — rever cachê e escalar
  fadiga por duração (mini-turnê não pode cansar mais que a nacional por retorno) — 0014.
- **Gate de staff para turnê** (ponto 9.2) — reforça a 0013.

## Backlog de playtest — 2026-06-26 (Playtest 04)

Após a 0015 (slice 4 royalties/aba de Ganhos + iteration-02 D6/D7). Detalhe e input
original em [docs/playtests/playtest-2026-06-26.md](../playtests/playtest-2026-06-26.md).
Dois itens marcados como bug foram **investigados no código** antes do registro (pontos 2 e 6).

### Bug estrutural de fadiga (pontos 2 e 6) — ✅ corrigido (2026-06-26, 0014 it-04)
- ✅ **Fadiga lump-sum vs recuperação passiva** (0014) — **feito**: modelo de **fadiga por
  dia** (`fatiguePerDay`), proporcional à duração da ação; recuperação passiva só em dias
  ociosos (sem ação `main` em curso). Turnê nacional (45d) +90; mini (14d) +28; gravar
  álbum (35d) ~+53 (não zera). Resolve pontos 2, 6 e o P03 9.1. Números → balance (0003).
- ✅ **Preview de fadiga + estouro com consequências** (0014 it-05, 2026-06-26) — **feito**:
  card mostra o custo de fadiga por esforço (⚠ se passar de 100); teto superior removido
  (overflow intencional); concluir acima de 100 reduz os ganhos da ação (até −50%) e custa
  reputação (∝ excesso). Números → balance (0003).

### Follow-up da 0015 (criação e inventário) — ✅ feito (leva 2026-06-26, playtest deferido)
- ✅ **Gênero/tema escolhidos na composição** (ponto 1.1) — **feito** (0015 it-03, D8):
  `compose` abre seletor de gênero (default = banda) + tema, com 🎲 Aleatório; título segue
  auto + editável. Edição inline da D7 mantida. Gêneros por época = 0008 (futuro).
- ✅ **Descartar músicas ruins** (ponto 5) — **feito** (0015 it-03, D9): `discardSong` na aba
  Músicas (botão 🗑 com confirmação); música já lançada não pode ser descartada.
- ✅ **Quick win — âncora ao gravar** (ponto 1.5) — **feito** (0015 it-03): `scrollIntoView`
  puxa a visão ao abrir o painel de composição/seleção.
- ✅ **Cachê de show ∝ reputação** (ponto 4 + P03 ponto 7) — **feito** (0014 it-06): cachê de
  show/turnê escala com a reputação (`1 + rep × 0.01`).
- ✅ **Reputação do show por faixa aleatória** (ponto 4, feedback) — **feito** (0014 it-07);
  na 0016 slice 2 a lógica do show migrou para `computeShowResult` (venues) e o `reputationRange`
  da 0014 foi removido — o show ainda sorteia **1–5**.
- ✅ **Shows por local + agenda + bilheteria** (P03 7.1–7.3, P04 3.3) — **feito** (0016 MVP,
  slices 1 e 2): catálogo de locais por reputação+fãs; show vira compromisso datado; receita
  cachê+bilheteria; o `play-show` imediato foi substituído. Slices 3–5 (promoção/penalidade,
  turnê-trajeto, geografia híbrida) = futuro.
- ✅ **Músicas prontas vs lançadas** (ponto 2, feedback) — **feito** (0015 fast-track): aba
  Músicas lista só as prontas; Lançamentos mostra as faixas pelo nome (evita confusão no descarte).

### Candidatas a feature (novas/reforçadas)
- **0018 - Label Contracts and Opportunities** (reforçada, urgente) — origem dos royalties
  **e** das vendas de álbum; gravadora como entidade (pontos 1.4, 3, 3.1).
- **0008 - Game Timeline** (reforçada) — gêneros por época + "invenção" de novos gêneros ao
  longo do tempo (pontos 1.2, 1.3; fonte: stringshock rock sub-genres timeline).
- **0016 - Venues and Shows** (reforçada) — agenda/calendário de shows e turnê (ponto 3.3).

### Balance / mecânica
- **Vendas de álbum distintas de royalties** (pontos 3, 3.1) — pico no lançamento (∝
  gravadora + fãs + qualidade) vs cauda decrescente; 0015 + 0018 + 0003.
- **Turnê como marketing do último álbum** (ponto 3.2) — toggle opcional; 0014 + 0015.
- ✅ **Cachê de show ∝ reputação + ganho de reputação não-trivial** (ponto 4 / P03 ponto 7) —
  **feito** (0014 it-06): cachê escala com reputação; reputação-base do show 1 → 2. Calibragem
  fina dos números → balance (0003).

## Backlog de playtest — 2026-06-27 (Playtest 05)

Após o MVP da 0016 (shows datados por local). Detalhe e input original em
[docs/playtests/playtest-2026-06-27.md](../playtests/playtest-2026-06-27.md).

### Bugs / quick wins
- ✅ **Agendamento duplicado** (0016, ponto 6) — **feito** (0016 [0.5.0]): `scheduleShow`
  recusa 2 shows na mesma data.
- ✅ **1 show por vez até a turnê** (0016, ponto 8) — **feito** (0016 [0.5.0]):
  `canBookMultipleShows` (rep ≥ 30) libera agendar vários; até lá, 1 por vez.
- **Editar nome na composição** (0015, ponto 2) — campo de nome no compose chooser
  (placeholder autogerado, editável).
- **Tipos de descanso** (0014, ponto 4) — `rest` com mais opções (folga / descanso / férias 30d).

### Padrões de UI (design system — 0006)
- ✅ **Select/Dropdown próprio** (ponto 1) — **feito** (0006 [0.8.0]): `SelectField.vue`
  (lista própria legível no tema escuro, acessível) + preview `select.html` + token de
  overlay; compose chooser migrado. Substitui o `<select>` nativo.
- ✅ **Confirmação própria** (ponto 5) — **feito** (0006 [0.8.0]): `ConfirmDialog.vue`
  (modal com scrim, Teleport, aria-modal) + preview `confirm-dialog.html`; descarte de música
  migrado do `window.confirm`.

### Balance / gates
- ✅ **Gate de staff para locais maiores** (ponto 7) — **feito** (0013 [0.3.0] slices 1+2):
  contratar equipe (custo + salário mensal); `Venue.requiredStaff` por tier (casa 1 roadie;
  ginásio 2; estádio 2 roadies + motorista) bloqueia agendar sem a crew. Fecha a "Aurora fácil".
- ✅ **Turnê vs show** (ponto 9, + P03 ponto 9) — **feito** (0014 [0.13.0]): cachê da turnê
  passou a **escalar com fãs** (`(garantia + fãs×por-fã) × esforço × reputação`), superando a
  bilheteria de um show avulso. Números → balance (0003).

### Nova mecânica (futuro)
- **Temas múltiplos + combos + tendências** (ponto 3) — música com vários temas; combos com
  bônus; tendências por período com contrapartida (saturar tema → perde fãs). 0015 + 0008 + 0003.
- **Turnê com modificadores de investimento** (proposta 2026-06-27, iteração futura da turnê) —
  ao montar a turnê o jogador escolhe **investimentos** opcionais que melhoram a qualidade/retorno:
  turnê simples vs **iluminação profissional**, **preparação** (ensaios + roteiro), **hospedagem
  da equipe**, **divulgação em TV/rádio**, etc. Cada investimento custa e pode (ou não) render mais
  — permite "investir na própria banda" com risco/retorno. Conecta 0014 (modelo da turnê) + 0013
  (equipe/hospedagem) + 0012 (iluminação como item) + 0009/marketing (TV/rádio) + 0003 (números).
  Substitui/expande o atual `outcomeModifier` de esforço por um conjunto de modificadores ricos.

## Backlog de playtest — 2026-06-27 sessão 02 (Playtest 06)

Sessão jogada pela noiva do usuário + análise do usuário. Detalhe e input verbatim em
[docs/playtests/playtest-2026-06-27-session-02.md](../playtests/playtest-2026-06-27-session-02.md).
Pontos 3 e 7 investigados no código.

### Investigados
- **Custo do marketing varia** (ponto 3, 0014/0003) — a variância (±20%) incide no custo
  (não só nos ganhos); o card mostra o "base". Decisão: **não aplicar variância ao custo**
  (custos previsíveis) e/ou ajustar o rótulo.
- **Gate do ginásio = 2 roadies** (ponto 7) — **não é bug**, é o gate escalonado. UI confunde
  ao mostrar o que "falta" e não o total. Quick win: clareza no requisito de equipe.

### UX / mecânica (iterar)
- **Cancelar ação iniciada** (ponto 2, 0014) — botão cancelar no "Em andamento" antes de
  avançar; devolve insumos reservados.
- **Tipos de descanso** (pontos 4, 8, 8.1, 0014) — descanso prolongado (10d/−60) + **férias**
  (recupera muito, com **cooldown**). Reforça o Playtest 05 ponto 4.
- **Clareza do gate de equipe** (ponto 7) — mostrar total exigido / "faltam X".

### Iterações de feature
- **0017 Contracts and Salaries** (ponto 1) — explicar/iterar salário dos membros (por
  atributos + reputação + contrato). Hoje o custo sobe com a reputação sem feedback.
- **0013 slices 3 e 4** (pontos 5, 6) — preparador vocal (−fadiga), empresário (+cachê),
  motorista (turnês maiores). Decididas na it-02; faltam implementar.
- **Ensaiar ↔ progressão de membros** (ponto 9, 0015 entrosamento + 0007) — ensaiar evolui a
  banda e melhora as composições; refatorar `rehearse`.

### Balance (iteração dedicada — 0003)
- **Variância no custo** (ponto 3) — custos não deveriam ser aleatórios.
- **Show de estádio vs turnê** (ponto 11) — eficiência por fadiga/tempo + conter a escala da
  bilheteria no endgame.

### Arquitetura de UI (0006 + navegação)
- **UI Shell** (O1, retoma Playtest 03 ponto 11) — (a) telas/abas por área mantendo o estado
  (Banda/Estúdio/Shows/Finanças/Equipe); (b) paliativo barato: **layout multi-coluna** para
  reduzir o scroll. Avaliar no design system.

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