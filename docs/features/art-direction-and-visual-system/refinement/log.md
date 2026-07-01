# Feature 0006 - Art Direction and Visual System (Log)

## [0.1.0] - 2026-06-18T00:00:00Z

### Input
- Scaffold da direção visual do jogo.

### Summary
- Planejamento inicial, decomposição e perguntas bloqueantes registrados.

### Open questions
- Direção visual desejada.
- Regras de estilo para UI e gráficos.

### Next step
- Responder `questions.md` antes da próxima iteração.

## [0.2.0] - 2026-06-20T00:00:00Z

### Input
- Discussão sobre custo de geração de arte (sprites/pixel art) vs orçamento do MVP.

### Summary
- Atualizada a estrutura completa da feature 0006, que existia apenas como
  scaffold genérico sem as decisões da sessão de planejamento.
- Decidido reduzir o MVP a um sistema visual estático: cards de membros,
  painéis de stats, feed de eventos com ícones. Sem sprites nem pixel art
  nesta fase.
- `planning/overview.md` reescrito com o problema real, Non-goals explícitos
  e critérios de aceite verificáveis.
- `questions.md` migrado para o formato A/B/C/D/X com Q0 resolvido e Q1 aberta.

### Open questions
- Avatares serão ilustração vetorial única ou apenas iniciais coloridas?
  (Q1 em `questions.md`)

### Next step
- Decidir Q1 e avançar para `iteration-02.md` com a escolha final de avatar.

## [0.3.0] - 2026-06-22T00:00:00Z

### Input
- Usuário respondeu Q1: opção [B] — ilustração vetorial simples, uma pose fixa por personagem, sem animação.

### Summary
- Q1 resolvida e movida para "Resolved Questions" em `questions.md`.
- Criado `iteration-02.md` documentando a decisão de avatar vetorial estático.
- Checklist atualizado: seção "Refinement" totalmente concluída.

### Open questions
- Nenhuma. Todas as perguntas da feature 0006 estão resolvidas.

### Next step
- Revisar handoff readiness no checklist e preparar entrega para `band-quest-game`.

## [0.4.0] - 2026-06-23T00:00:00Z

### Input
- Revisão de handoff readiness para liberar a feature para `band-quest-game`.

### Summary
- Checklist 100% concluído. Ordem de implementação já definida em `decomposition.md`:
  1. Painel de stats (sem dependência de assets).
  2. Feed de eventos (ícone de biblioteca + texto).
  3. Cards de membros com avatar vetorial estático.
  4. Guia de referência da biblioteca de ícones (Tabler/Lucide).
- Feature 0006 liberada para handoff. Feature 0005 receberá iteration-04
  incorporando as decisões desta feature.

### Open questions
- Nenhuma.

### Next step
- Implementar em `band-quest-game` seguindo a ordem do `decomposition.md`.

## [0.5.0] - 2026-06-23T00:00:00Z

### Input
- Usuário pediu para iterar a feature usando Claude Design (ferramenta
  `DesignSync` + claude.ai/design) para construir a identidade visual do projeto.

### Summary
- Capturadas 4 decisões de direção de arte (Q2–Q5) via perguntas estruturadas:
  estética atemporal/multi-era; tom híbrido (base limpa + acento rock); base de
  cor dark; escopo da 1ª passada = foundations + todos os componentes.
- Criado `iteration-03.md` registrando a decisão de construir o design system.
- Q2–Q5 adicionadas a "Resolved Questions" em `questions.md` (append-only).
- Construído o bundle de design system em `band-quest-docs/design-system/`
  (`tokens.css` + foundations + componentes) e sincronizado com Claude Design.

### Open questions
- Nenhuma bloqueante. Refino visual dos componentes segue iterativo no
  design system.

### Next step
- Iterar componente a componente no Claude Design e usar `tokens.css` como
  contrato para a implementação Vue em `band-quest-game`.

## [0.6.0] - 2026-06-23T00:00:00Z

### Input
- Usuário pediu para seguir do design system para a implementação.

### Summary
- Tokens do design system portados para `band-quest-game/src/assets/tokens.css`
  (espelho do contrato), aplicados globalmente via `base.css`/`main.css` +
  fontes Oswald/Inter em `index.html`.
- `StatsPanel.vue` reestilizado com cor semântica por stat (reputação/caixa/
  fãs/fadiga) e tipografia display; ícone de fadiga trocado para `IconBolt`.
- `EventFeed.vue` reestilizado como timeline com acento por categoria.
- `GameView.vue` e `StartView.vue` alinhados à marca (band name display,
  botão primário spotlight, turn badge).
- Verificação: `type-check` limpo, 17/17 testes, build de produção OK.

### Open questions
- Nenhuma bloqueante. Próxima fatia natural: componente `MemberCard` (decomp #3)
  — depende de popular `members` no store ao iniciar a partida.

### Next step
- Implementar `MemberCard.vue` e popular membros iniciais em `startGame`.

## [0.7.0] - 2026-06-23T00:00:00Z

### Input
- Usuário testou geração de arte no Gemini (não agradou nesta fase) e pediu para
  registrar o **pixel-art** como direção de arte futura.

### Summary
- Criada `iteration-04.md`: pixel-art como direção futura (pós-validação);
  flat-vector autoral mantido como camada atual/MVP.

### Open questions
- Nenhuma.

### Next step
- Produzir os ícones flat-vector dos membros (feature 0007) como camada atual.

## [0.8.0] - 2026-06-27T00:00:00Z — padrões de UI: Select/Dropdown + Confirm dialog

### Input
- Playtest 05 (pontos 1 e 5): o `<select>` nativo tinha opções de baixo contraste (quase
  invisíveis) e o descarte usava o `window.confirm` nativo (fora do design system). Decisão
  do usuário: investir no design system e estabelecer um padrão de listas/confirmação.

### Summary
- `tokens.css`: novos tokens **`--bq-overlay`** (scrim de modais) e **`--bq-z-overlay`**.
- `design-system/components/select.html`: padrão de **Select/Dropdown próprio** (botão +
  lista custom, item selecionado em âmbar, legível no tema escuro) — substitui o `<select>`.
- `design-system/components/confirm-dialog.html`: padrão de **Confirm dialog** (scrim +
  diálogo com título/mensagem/ações; ação destrutiva em ember).
- Implementação consumindo `tokens.css` em band-quest-game: `SelectField.vue` (dropdown
  acessível: aria-haspopup/expanded, role=listbox/option, fecha por clique-fora) e
  `ConfirmDialog.vue` (Teleport, aria-modal, foco no confirmar, ESC/scrim cancelam).
- Fios: o compose chooser (0015) passou a usar `SelectField` para gênero/tema; o descarte
  de música (SongLibrary) trocou `window.confirm` pelo `ConfirmDialog`.

### Validate (gate verde)
- `test:unit` 157 (era 150; +SelectField: abre/seleciona/aria-selected; +ConfirmDialog:
  abre/confirma/cancela). `type-check`/`lint`/`build` OK.

### Open questions
- Nenhuma. Próximo: sincronizar os 2 cards novos para o Claude Design (DesignSync) — a
  confirmar com o usuário (ação outward-facing).

### Next step
- Reaproveitar `SelectField`/`ConfirmDialog` nos próximos fluxos que precisarem de lista/
  confirmação (ex.: seleção de faixas, modos no StartView).

## [0.8.1] - 2026-06-30T00:00:00Z — fix: re-sync do bloco Overlay no espelho do game

### Input
- Bug de UI (fast-track, AI-DLC): ao compor uma música, os dropdowns de gênero e tema
  ficavam ATRÁS das abas e dos cards de ação abaixo, em vez de sobrepô-los.

### Summary
- **Causa raiz — drift do contrato, não CSS local.** O [0.8.0] adicionou `--bq-overlay` e
  `--bq-z-overlay` ao `tokens.css` canônico (docs) e os usou em `SelectField.vue` e
  `ConfirmDialog.vue`, mas o **espelho** `band-quest-game/src/assets/tokens.css` nunca
  recebeu o bloco. Com o token indefinido, `z-index: var(--bq-z-overlay)` vira inválido →
  `z-index: auto`; como o compose chooser vem antes das abas/cards no DOM, esses elementos
  posteriores pintavam por cima da lista aberta do dropdown.
  (O `ConfirmDialog` mascarava o problema porque usa Teleport para o `body` → já era o
  último no DOM; o `SelectField`, inline, expunha o bug.)
- **Correção:** re-sincronizado o bloco *Overlay* (`--bq-overlay` + `--bq-z-overlay: 100`)
  no espelho do game, alinhando-o ao contrato.

### Validate (gate verde)
- `test:unit` 172/172, `type-check`/`lint`/`build` OK.

### Open questions
- Nenhuma bloqueante. Itens de correspondência design-system ↔ UI levantados na auditoria
  (ver Next step) ficam como backlog.

### Next step
- Backlog de correspondência (drift residual, não bloqueante):
  1. Previews ausentes no bundle p/ padrões reusáveis que a UI evoluiu: **CollapsibleSection**
     (accordion), **ActionCard** (card de ação + preview de fadiga) e o **shell de abas** (0020).
  2. Hardcode isolado: `ConfirmDialog.vue` usa `color: #fff` no botão danger (trocar por token).
  3. Guarda anti-regressão: teste leve que verifica que o espelho contém os tokens do contrato.
