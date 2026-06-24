# Feature 0014 - Core Loop and Actions (Design)

> Modelo de ação e catálogo inicial. Turno = **dia** (0008 iteration-02 / 0003
> iteration-04; calendário 12×30 = 360/ano). As `durationTurns` representam **dias**.
> Os **valores** (durações, custos, ganhos, variância) são calibrados na **iteração
> de balance da 0003** — aqui ficam placeholders conceituais.
>
> **Avanço de tempo:** orientado por ações — o jogador não avança dia a dia; o botão
> "Avançar" salta para a **próxima conclusão de ação** (menor `turnsRemaining`).

## Componentes afetados
- `band-quest-game`: novo módulo de ações (catálogo + máquina de estado), integração
  com o store (`game.ts`), com o feed de eventos e com o avanço de turno. Substitui
  as ações hardcoded em `GameView.vue`.

## Modelo de dados

```ts
type ActionLane = 'main' | 'background'

interface ActionEffortOption {
  label: string         // ex.: 'rápido' | 'caprichado'
  durationTurns: number // semanas (calibrado na 0003)
  costModifier: number  // multiplicador de custo (calibrado na 0003)
}

interface ActionOutcome {
  // métricas-base aplicadas ao concluir (calibradas na 0003)
  metrics: Partial<Record<'cash' | 'reputation' | 'fans' | 'fatigue', number>>
  variance: number       // amplitude da aleatoriedade leve (Q4)
  eventChance?: number   // chance de evento da 0009 interferir (Q4)
}

interface ActionDef {
  id: string
  name: string
  lane: ActionLane
  effortOptions: ActionEffortOption[] // faixas escolhidas pelo jogador (Q3)
  prerequisites?: string[]            // ex.: requer músicas compostas
  resourceModifiers: string          // membros (0007), itens (0012), staff (0013)
  outcome: ActionOutcome
}

// Estado em progresso no store:
interface ActiveAction {
  actionId: string
  lane: ActionLane
  effortLabel: string
  turnsRemaining: number
}
```

- **Ciclo de vida:** `idle → in-progress (turnsRemaining--) → completed`. Ao
  concluir: aplica `outcome` (modulado por recursos + variância), registra um evento
  e pode disparar marco (0011) e/ou consumir/produzir pré-requisitos (ex.: músicas).
- **Lanes:** uma ação `main` por vez; ações `background` podem rodar em paralelo.
- **Avanço de tempo:** "Avançar" salta `delta` dias = menor `turnsRemaining` entre as
  ações ativas (1 dia se não houver ações); decrementa todas as ativas em `delta`,
  conclui as que chegam a zero e cobra custos recorrentes (salários 0013, decay 0003).

## Catálogo inicial proposto

| id | Nome | Lane | Pré-req | Resultado (conceito) |
|----|------|------|---------|------------------------|
| `rehearse` | Ensaiar | main | — | reduz variância das próximas ações; +fadiga |
| `compose` | Compor | main | — | produz músicas (insumo para gravar) |
| `record-demo` | Gravar demo | main | músicas | entrada barata; +reputação/fãs inicial |
| `record-single` | Gravar single | main | músicas | lançamento → fãs/streams/royalties |
| `record-album` | Gravar álbum | main | várias músicas | lançamento grande; muitos turnos |
| `play-show` | Tocar show | main | — | cachê + fãs + reputação; +fadiga |
| `tour` | Turnê | main | reputação mínima | muitos turnos; alto cachê/fãs; alta fadiga/custo |
| `marketing` | Marketing | background | — | +fãs/alcance passivo enquanto roda |
| `rest` | Descansar | main | — | −fadiga |

## Decisões técnicas
- Catálogo declarativo (lista de `ActionDef`) + motor puro/testável — segue o padrão
  de `cast.ts` (0007). As ações hardcoded de `GameView` migram para este módulo.
- `effortOptions` dá a escolha de qualidade (Q3); `variance`/`eventChance` dão a
  variação leve + eventos (Q4).

## Riscos e trade-offs
- Ações `background` em paralelo aumentam o estado: mitigado limitando a 1 main + N
  background simples na primeira versão.
- Acoplamento com 0003/0007/0009/0011/0012/0013: a 0014 é dona só da mecânica;
  valores e catálogos vêm por referência.
