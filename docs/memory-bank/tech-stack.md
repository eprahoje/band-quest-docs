# Band Quest — Estudo de Trade-off: Tech Stack

**Data:** 2026-06-23
**Status:** Decisão registrada (ver seção "Decisão final")

---

## Critérios de avaliação

Os critérios foram ordenados de acordo com as prioridades do projeto
nesta fase:

| # | Critério | Peso | Justificativa |
|---|---|---|---|
| 1 | **Independência do agente de IA** | Alto | O agente deve conseguir atestar e auditar seu próprio trabalho sem depender de screenshots ou ferramentas externas. Quanto mais o agente puder verificar a si mesmo (testes, linting, build), menor o custo de ciclo. |
| 2 | **Velocidade até MVP jogável** | Alto | O objetivo imediato é validar o core loop (decisões → dinheiro/reputação) antes de investir em infraestrutura de plataforma. |
| 3 | **Fit com o tipo de jogo** | Médio | Band Quest MVP é uma UI de gestão: cards, painéis de stats, feed de eventos. Não é um jogo com game loop em tempo real, física ou sprites animados. |
| 4 | **Canais de distribuição** | Médio | Browser (web hosting), Android, Itch.io. PC desktop é desejável mas não bloqueante para o MVP. |
| 5 | **Caminho de evolução** | Médio | Se o jogo precisar de mecânicas mais complexas (animações, procedural, física) depois do MVP, o custo de migração precisa ser razoável. |

---

## Opção 1 — Vue 3 + Vite + Capacitor

### O que é
Framework web reativo (Vue 3) com build tool moderna (Vite), empacotando
para Android via Capacitor (wrapper nativo de WebView).

### Avaliação por critério

**Independência do agente: ALTA**
- Arquivos `.vue`, `.js`, `.css` — leitura e escrita direta.
- `npm run dev` inicia servidor local; `npm run build` produz HTML/JS
  auditável em `dist/`.
- Testes unitários com **Vitest** (saída de texto pura, sem GUI).
- Testes e2e com **Playwright** (modo headless, saída em texto + screenshots
  opcionais). O agente pode escrever assertions sobre DOM, não apenas
  inspecionar visualmente.
- Type checking: `tsc --noEmit`. Linting: `eslint`.
- **Conclusão:** o agente fecha o loop de verificação inteiramente em
  texto/terminal, sem depender de prints do usuário.

**Velocidade até MVP: ALTA**
- `npm create vue@latest` → projeto rodando em minutos.
- HTML/CSS cobre o visual system inteiro da feature 0006 sem nenhum
  framework de game.
- Pinia (state management) é simples o suficiente para o modelo de dados
  do MVP (band state, market state, event feed).

**Fit com o tipo de jogo: ALTA**
- Um jogo de gestão é essencialmente um dashboard interativo.
- Data binding reativo (Vue) é o padrão de mercado para dashboards.
- Tabler Icons tem pacote Vue nativo.
- Não há nada no MVP que exija um game engine.

**Distribuição:**
- Browser: build estático → qualquer hosting (Vercel, GitHub Pages, Itch.io).
- Itch.io: HTML5 upload direto — sem nenhum passo extra.
- Android: Capacitor adiciona uma WebView nativa; o app funciona como
  APK sem reescrever código. Maturidade: alta (Ionic/Capacitor é usado
  em apps de produção).
- PC Desktop: Electron é possível mas pesado; não prioritário para MVP.

**Caminho de evolução:**
- Se o jogo ficar dentro do espaço de gestão/tycoon: nenhuma mudança
  necessária. Vue + Capacitor sustenta o produto completo.
- Se surgir necessidade de sprites, física ou efeitos de canvas:
  integrar **Pixi.js** ou **Phaser** como camada de canvas dentro do
  app Vue — padrão comum em jogos browser híbridos.
- Se a decisão for migrar para Godot: os modelos de dados e a lógica
  de negócio documentados no `band-quest-docs` sobrevivem intactos como
  contrato. O custo é a reimplementação da UI (estimado em 30-50% do
  trabalho do MVP).

### Limitações mapeadas
- Não tem acesso nativo a APIs de hardware (câmera, acelerômetro, etc.)
  além do que a Web Platform oferece.
- Distribuição em lojas (Google Play, App Store) via Capacitor funciona,
  mas requer configuração de build nativo e conta de desenvolvedor.
- Se o jogo evoluir para exigir performance de game engine (60fps com
  centenas de sprites), o limite da WebView vai aparecer.

---

## Opção 2 — Godot Engine

### O que é
Game engine open-source com editor visual, exportação para HTML5, PC,
Android e outras plataformas. Linguagem nativa: GDScript (Python-like).

### Avaliação por critério

**Independência do agente: MÉDIA-BAIXA**
- O agente consegue escrever e ler arquivos `.gd` e `.tscn` (cenas em
  texto).
- Verificação de lógica pura: possível via GDScript headless
  (`godot --headless --script`), mas requer Godot instalado e o setup
  correto.
- Verificação da UI: requer rodar o editor Godot ou exportar o jogo —
  sem screenshot ou print é impossível saber se o layout está correto.
- Framework de testes GUT existe, mas a integração com CI headless é
  significativamente mais complexa que Vitest/Playwright.
- **Conclusão:** o agente pode escrever código, mas precisa de prints
  do usuário ou de um MCP com acesso ao editor para fechar o loop de
  verificação visual. Custo de ciclo é maior.

**Velocidade até MVP: MÉDIA**
- O sistema de UI do Godot (Control nodes) consegue criar o visual system
  da feature 0006, mas é mais verboso que HTML/CSS.
- Curva de aprendizado do sistema de nós e cenas pode atrasar o início.
- Uma vez dominado, a iteração é rápida dentro do editor.

**Fit com o tipo de jogo: MÉDIA-ALTA**
- Godot é capaz de criar UIs de gestão, mas não foi projetado para isso
  como caso de uso primário.
- O ponto forte do Godot (animação, física, input, audio) não é exigido
  pelo MVP.
- Para versões futuras com sprites animados, efeitos visuais ou mecânicas
  mais complexas: Godot seria o ambiente certo.
- Distribuição no Itch.io via HTML5 export é o caminho mais natural do Godot.

**Distribuição:**
- Browser (Itch.io): exportação HTML5 nativa — o canal mais forte do Godot.
- Android: exportação nativa para APK — sem WebView, performance melhor.
- PC Desktop (Windows/Linux/Mac): exportação nativa.
- Web hosting genérico: HTML5 export funciona, mas exige servidor CORS-safe
  para carregar (não serve direto de `file://`).

**Caminho de evolução: ALTA**
- Se o jogo evoluir para sprites, animações, mapas procedurais, áudio
  dinâmico: já está no ambiente certo.
- Sem custo de migração para mecânicas de game engine.

### Limitações mapeadas
- O agente é menos autônomo: precisa de prints para verificar UI e de
  Godot instalado para rodar testes.
- Tempo até MVP maior, especialmente para quem não conhece GDScript e
  o sistema de cenas.
- Para um jogo que é essencialmente um dashboard, é overhead de plataforma
  no curto prazo.

---

## Opção 3 — React / React Native

### React (web puro)

**Independência do agente: ALTA** — idêntica ao Vue.
Mesma auditabilidade (Vitest, Playwright, build HTML).

**Fit: ALTA** para gestão de estado e UI de dashboard.

**Diferença vs Vue:**
- Mais boilerplate (JSX + hooks + escolha de state manager).
- Ecossistema maior, mais material de referência.
- Para um projeto solo com IA como co-piloto, a maior opinionatidade do
  Vue (SFC + Pinia) reduz decisões e é vantagem, não desvantagem.
- Tabler Icons tem pacote React — paridade com Vue.

**Veredito:** funcionaria bem, mas Vue oferece menos atrito para
o perfil deste projeto. Não há ganho que justifique preferir React
sobre Vue aqui.

### React Native (+ Expo)

**Independência do agente: MÉDIA**
- Para web (Expo web): alta — mesmo padrão do React web.
- Para Android/iOS nativo: o agente precisa de emulador ou device para
  verificar. Detox (e2e nativo) é significativamente mais complexo que
  Playwright.

**Fit: BAIXA para o MVP**
- React Native é otimizado para experiências nativas com gestos, scroll
  nativo e componentes de plataforma.
- Um jogo de gestão com cards e dashboards não precisa de nenhum desses
  diferenciais.
- O custo de lidar com divergências entre web e nativo (StyleSheet vs CSS,
  ausência de algumas APIs web) não se paga para o MVP.

**Veredito:** descartado para MVP. O caminho web (Vue ou React) +
Capacitor entrega Android com muito menos fricção para este tipo de app.

---

## Comparativo geral

| Critério | Vue 3 + Vite | Godot | React Native |
|---|---|---|---|
| Independência do agente | ⭐⭐⭐ | ⭐ | ⭐⭐ (web) / ⭐ (native) |
| Velocidade até MVP | ⭐⭐⭐ | ⭐⭐ | ⭐⭐ |
| Fit com tipo de jogo (MVP) | ⭐⭐⭐ | ⭐⭐ | ⭐⭐ |
| Distribuição | ⭐⭐⭐ | ⭐⭐⭐ | ⭐⭐ |
| Caminho de evolução | ⭐⭐ | ⭐⭐⭐ | ⭐⭐ |
| **Total** | **14/15** | **11/15** | **9/15** |

---

## Estratégia de duas fases (recomendada)

### Fase 1 — MVP em Vue 3 + Vite

**Objetivo:** validar o core loop (decisões → dinheiro/reputação) em browser.

**O que entrega:**
- Features 0006 e 0005 implementadas (visual system + start screen).
- Deploy estático (GitHub Pages ou Vercel) + Itch.io.
- Android via Capacitor quando o core loop estiver estável.
- Teste suite completo que o agente pode rodar e auditar autonomamente.

**O que não entrega:**
- Performance nativa de game engine.
- Assets de arte final (placeholder com ícones e iniciais).

**Critério de saída da Fase 1:**
O core loop está validado quando um jogador consegue criar uma banda,
tomar decisões por 10 turnos e observar impacto mensurável em
reputação e caixa — sem depender de arte original.

### Fase 2 — Decisão baseada em evidência

Depois de validar o core loop, há dois caminhos naturais:

**Caminho A: continuar em Vue**
- Indicado se o jogo permanecer no espaço de gestão/tycoon.
- Adicionar Pixi.js para efeitos de canvas pontuais, se necessário.
- Empacotamento Android via Capacitor + publicação em lojas.

**Caminho B: migrar para Godot**
- Indicado se surgir necessidade de: sprites animados, mapa procedural,
  efeitos de partículas, áudio dinâmico por estado de jogo.
- O que sobrevive da Fase 1: toda a documentação em `band-quest-docs`
  (decisões de produto, UX, mecânicas). O custo é a reimplementação
  técnica da UI — estimado em 30-50% do esforço da Fase 1.
- O que não sobrevive: o código Vue. Mas como o MVP é curto e bem
  documentado, este custo é aceitável.

A migração para Godot **não é um recomeço** — é uma reimplementação
em cima de uma spec validada. É diferente de fazer Godot desde o início
sem saber se o core loop funciona.

---

## Decisão final

**Adotar Vue 3 + Vite para o MVP (Fase 1).**

Razão primária: maximiza a independência do agente de IA, permitindo
ciclos de verificação curtos sem depender de prints ou ferramentas
externas. Com Vitest + Playwright o agente fecha o loop de qualidade
autonomamente.

Razão secundária: é o caminho mais rápido para um jogo de gestão com
visual system baseado em cards e ícones — exatamente o que as features
0006 e 0005 especificam.

**Stack decidida:**
- Framework: Vue 3 (Composition API)
- Build: Vite
- State: Pinia
- Icons: Tabler Icons (pacote `@tabler/icons-vue`)
- Testes unitários: Vitest
- Testes e2e: Playwright
- Android (Fase 1 tardia): Capacitor
- Itch.io: build HTML5 estático (`npm run build` → `dist/`)

**Revisão obrigatória da decisão** se qualquer uma das condições abaixo
for verdadeira ao final da Fase 1:
- O jogo precisar de sprites animados em mais de 20% das telas.
- A performance da WebView no Android for insatisfatória para o core loop.
- Surgir necessidade de distribuição em lojas de PC (Steam, itch.io nativo).
