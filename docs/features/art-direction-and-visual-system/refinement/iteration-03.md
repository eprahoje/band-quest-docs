# Feature 0006 - Art Direction and Visual System (Refinement 03)

## Context / Input
Decisão de construir a **identidade visual** do projeto e um **design system
navegável** usando Claude Design (ferramenta `DesignSync`, que sincroniza uma
biblioteca local com um projeto em claude.ai/design). Parte das decisões já
consolidadas nas iterações 01 e 02 (visual estático; cards, painel de stats,
feed de eventos e biblioteca de ícones; avatar vetorial estático).

## Decisions
- **Âncora estética: atemporal / multi-era.** A era escolhida pelo jogador é
  tema/acento, não a base visual. A identidade funciona em qualquer época sem
  brigar com a mecânica multi-era.
- **Tom: híbrido.** Base de dashboard limpa e legível + acento de atitude rock
  (tipografia display nos títulos, acentos e texturas pontuais). Equilibra
  leitura de stats com personalidade.
- **Base de cor: dark.** Estética de palco/noturno, padrão em apps de música,
  com acentos vibrantes sobre fundo escuro.
- **Escopo da 1ª passada: foundations + todos os componentes-âncora.** Design
  tokens (cor, tipografia, espaçamento) + card de membro, painel de stats,
  feed de eventos e biblioteca de ícones.

## Artifacts
- O design system é mantido como artefato-spec em
  [`band-quest-docs/design-system/`](../../../../design-system/), com previews
  HTML/CSS e `tokens.css` como fonte única de tokens.
- O bundle é sincronizado para um projeto Claude Design (claude.ai/design) para
  navegação por cards agrupados (Type, Colors, Spacing, Components).
- Os tokens em `tokens.css` são o **contrato visual** que o `band-quest-game`
  (Vue 3 + Tabler Icons) consome na implementação — evitando divergência entre
  spec e código.

## Questions
- Novas perguntas Q2–Q5 registradas e resolvidas nesta sessão
  (ver [`questions.md`](questions.md)).

## Checklist result
- [x] Scope reviewed.
- [x] Questions updated.
- [ ] Handoff reviewed (design system em construção).
