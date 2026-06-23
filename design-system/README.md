# Band Quest — Design System

Identidade visual e biblioteca de componentes do projeto. Artefato-spec da
feature [0006 — Art Direction and Visual System](../docs/features/art-direction-and-visual-system/README.md),
decisão registrada em [iteration-03](../docs/features/art-direction-and-visual-system/refinement/iteration-03.md).

## Direção de arte
- **Atemporal / multi-era** — a era escolhida pelo jogador é tema/acento, não a base.
- **Híbrido** — base de dashboard limpa e legível + acento de atitude rock.
- **Dark** — estética de palco/noturno, acentos vibrantes (spotlight âmbar, ember carmim).

## Estrutura
```text
design-system/
  tokens.css              # fonte única de tokens (o CONTRATO visual)
  index.html              # overview da marca
  foundations/
    colors.html           # paleta (superfícies, acentos, semântica de stats)
    typography.html       # Oswald (display) + Inter (body) + escala
    spacing.html          # escala de espaço 4px + raios
  components/
    member-card.html      # card de membro (avatar vetorial + atributos)
    stats-panel.html      # painel de stats (reputação, caixa, fãs, fadiga)
    event-feed.html       # feed de eventos (timeline ícone + texto)
    icons.html            # biblioteca de ícones (Tabler) por ação do jogo
```

## tokens.css é o contrato
A implementação em `band-quest-game` (Vue 3 + Tabler Icons) **consome `tokens.css`**
e nunca hardcoda cor/tipografia/espaçamento. Isso mantém spec e código alinhados.

## Claude Design
Os previews têm marcador `<!-- @dsCard group="..." -->` na primeira linha e são
sincronizados para um projeto *design-system* em claude.ai/design via a ferramenta
`DesignSync`, onde aparecem como cards navegáveis agrupados por Type, Colors,
Spacing, Components e Brand. A sincronização é incremental (um componente por vez),
nunca uma substituição em massa.

## Pré-visualizar localmente
Abra qualquer `.html` no navegador, ou sirva a pasta:
`npx serve design-system` (as fontes Oswald/Inter vêm do Google Fonts).
