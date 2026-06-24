# Feature 0011 - Career Milestones (Design)

> Modelo de dados dos marcos e catálogo inicial proposto. Os **números** (limiares
> das condições e valores das recompensas) são **calibrados na 0003** — aqui ficam
> placeholders conceituais. Os `unlockItemId` referenciam itens da **0012**.

## Componentes afetados
- `band-quest-game`: novo módulo de marcos (catálogo + avaliação), integração com o
  store (`game.ts`), com o feed de eventos e com o cálculo de nota da 0010.

## Modelo de dados

```ts
type MilestoneTrack = 'studio' | 'stage' | 'media' | 'business'
type MilestoneKind = 'unique' | 'scalable'

interface MilestoneReward {
  cash?: number          // calibrado na 0003
  reputation?: number    // calibrado na 0003
  scoreBonus?: number    // bônus na nota final da 0010
  unlockItemId?: string  // referência à 0012
  eventMessage?: string  // texto do evento `milestone` no feed
}

interface MilestoneTier {
  threshold: number          // limiar da métrica (calibrado na 0003)
  reward: MilestoneReward
}

interface Milestone {
  id: string
  title: string
  description: string
  track: MilestoneTrack
  kind: MilestoneKind
  metric: 'fans' | 'records_sold' | 'streams' | 'albums' | 'shows' | 'cash' | 'reputation' | 'flag'
  condition?: number         // limiar único (kind === 'unique')
  tiers?: MilestoneTier[]    // degraus (kind === 'scalable')
  reward?: MilestoneReward   // recompensa única (kind === 'unique')
}
```

- Avaliação: a cada turno (ou após uma ação), o motor checa marcos não concluídos
  contra as métricas atuais; ao disparar, aplica `reward`, registra um evento
  `milestone` e (se houver) solicita o desbloqueio do item na 0012.

## Catálogo inicial proposto (~12)

| id | Título | Trilha | Tipo | Métrica | Recompensa (conceito) |
|----|--------|--------|------|---------|------------------------|
| `first-show` | Primeiro Show | stage | unique | shows | reputação + evento |
| `first-demo` | Primeira Demo Gravada | studio | unique | flag | reputação + evento |
| `fanbase` | Base de Fãs | media | scalable | fans | tiers 1k/10k/100k → reputação + item + nota |
| `went-viral` | Viralizou no Fotolog/MySpace | media | unique | flag | fãs/reputação + evento (sabor anos 2000) |
| `first-album` | Primeiro Álbum | studio | unique | albums | reputação + item + nota + evento |
| `records-sold` | Discos Vendidos | business | scalable | records_sold | tiers 1k/10k/100k → dinheiro + nota |
| `first-tour` | Primeira Turnê | stage | unique | flag | dinheiro/reputação + evento |
| `on-tv` | Tocou na TV | media | unique | flag | fãs/reputação + item + evento |
| `label-deal` | Assinou com Gravadora | business | unique | flag | dinheiro + item + nota + evento |
| `certified` | Certificação | business | scalable | records_sold | tiers ouro/platina/diamante → reputação + nota |
| `intl-tour` | Turnê Internacional | stage | unique | flag | dinheiro/reputação + item + nota + evento |
| `industry-award` | Prêmio da Indústria | media | scalable | flag | reputação + nota (acumula por prêmio) |

> `flag` = condição não puramente numérica (um gatilho de jogo, ex.: "assinou
> contrato"), a ser definida pelo loop/ação correspondente.

## Decisões técnicas
- Catálogo como dado declarativo (lista de `Milestone`), avaliado por um motor puro
  e testável — segue o padrão de `cast.ts` da 0007.
- Marcos escaláveis guardam o maior tier já concedido para não repetir recompensa.

## Riscos e trade-offs
- Acoplamento com 0010 (nota) e 0012 (itens): mitigado mantendo a 0011 dona só da
  estrutura; valores e ids vêm por referência.
- Calibragem: limiares/valores placeholder até a 0003 — não bloqueia a estrutura.
