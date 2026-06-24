# Feature 0012 - Unlockable Items (Design)

> Modelo de item e catálogo inicial proposto. Os **números** (custos e valores dos
> efeitos) são **calibrados na 0003** — aqui ficam placeholders conceituais. As
> fontes `milestone:<id>` referenciam marcos da **0011**; `era:<ano>` referencia a
> **0008**.

## Componentes afetados
- `band-quest-game`: novo módulo de itens (catálogo + inventário), integração com o
  store (`game.ts`), com a aplicação de efeitos nas ações e com a loja (quando houver).

## Modelo de dados

```ts
type ItemCategory = 'equipment' | 'studio' | 'marketing' | 'cosmetic'

type UnlockSource =
  | { type: 'milestone'; milestoneId: string } // 0011
  | { type: 'purchase' }                        // loja (0003)
  | { type: 'era'; year: number }               // 0008

interface ItemEffect {
  metric: 'cash' | 'reputation' | 'fans' | 'fatigue' | 'efficiency'
  // efeito funcional: modificador aplicado a uma ação ou ao loop.
  // valores calibrados na 0003.
  modifier?: number
  appliesTo?: string // ex.: 'record-demo', 'play-show'
}

interface Item {
  id: string
  name: string
  category: ItemCategory
  description: string
  unlockSources: UnlockSource[] // pode ter mais de uma fonte
  cost?: number                 // se comprável (calibrado na 0003)
  effects: ItemEffect[]
}
```

## Catálogo inicial proposto

| id | Nome | Categoria | Fonte | Efeito (conceito) |
|----|------|-----------|-------|--------------------|
| `guitar-pro` | Guitarra profissional | equipment | compra | +qualidade de show/gravação |
| `amp-upgrade` | Amplificador melhor | equipment | compra | +reputação em shows |
| `home-studio` | Estúdio caseiro | studio | marco (`first-demo`) + compra | grava demo mais barato |
| `multitrack` | Gravador multitrack | studio | compra + época | +qualidade de álbum |
| `flyer-campaign` | Campanha de panfletos | marketing | compra | +fãs por show |
| `web-presence` | Presença na web (fotolog/MySpace pro) | marketing | marco (`went-viral`) + época | +fãs passivos |
| `band-identity` | Identidade visual da banda | cosmetic | compra | +reputação base |
| `stage-outfit` | Figurino de palco | cosmetic | marco (`on-tv`) | +reputação em shows |

## Decisões técnicas
- Catálogo declarativo (lista de `Item`), efeitos aplicados por um módulo puro e
  testável — segue o padrão de `cast.ts` (0007) e do motor de marcos (0011).
- Inventário do jogador no store; loja consulta `unlockSources.purchase` + `cost`.

## Riscos e trade-offs
- Acoplamento com 0011 (marcos), 0003 (custos/efeitos) e 0008 (época): mitigado
  mantendo a 0012 dona só do modelo/catálogo; valores e ids vêm por referência.
- Escopo da loja e do sistema de Staff ainda em aberto (Q5/Q6) — não bloqueiam o
  modelo de item nem o catálogo de desbloqueio por marco.
