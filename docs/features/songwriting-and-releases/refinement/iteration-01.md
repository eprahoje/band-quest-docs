# Feature 0015 - Songwriting and Releases (Refinement 01)

## Decisions

### D1 — Metadado: auto + editável (Q1=A)
- `compose` cria uma **Música** com **nome** e **tema** autogerados (pool IP-safe) e
  **gênero herdado da banda**. O jogador **pode editar** nome/tema, mas nada é
  obrigatório — zero fricção em sessões longas.
- Modelo `Song`: `id`, `name`, `genre`, `theme`, `quality`, `status`
  (`composed` | `released`), e referência ao lançamento quando aplicável.

### D2 — Qualidade: banda + esforço + entrosamento + variação (Q2=C)
- `quality` (0–100) = combinação de:
  - **atributos relevantes dos membros** (0007),
  - **esforço** da ação (`outcomeModifier`, 0014),
  - **entrosamento** da banda — um fator que **sobe com `rehearse`** (liga a
    progressão ao songwriting),
  - **variação leve** (RNG pequeno).
- Os **pesos** de cada termo são placeholders de balance → **0003**.
- A qualidade move **fãs / reputação / royalties** do lançamento (não só custo),
  resolvendo o "o que muda no caprichado além do custo" (Playtest 02, 5.2).

### D3 — Cadeia de lançamento: Demo + Single + Álbum (Q3=A)
- **Demo** — pacote de **N músicas não lançadas** (placeholder N=3, ≥2). Barata/crua;
  rende **reputação + fãs iniciais**; royalty pequeno/nulo. Degrau de início de carreira.
- **Single** — **1 música**. Marca a música como `released` (como single). Gera
  **royalties** (cauda curta-média).
- **Álbum** — exige **X singles já lançados + Y músicas não lançadas** (placeholders
  X=2, Y=4). As faixas dos singles contam no álbum + as músicas novas. Gera
  **royalties** maiores, com cauda mais longa.
- Números (N, X, Y, custos, durações) são **placeholders de balance → 0003**.

### D4 — Receita de longo prazo: royalty decrescente (Q4=A)
- Cada **Release** guarda `{ type, releaseTurn, quality, fanBaseAtRelease, currentRoyalty }`.
- Ao lançar, define-se um **royalty inicial** ∝ `quality × fanBaseAtRelease`; a cada
  turno ele **decai geometricamente** até um piso/expirar.
- A soma dos royalties ativos é a **receita por turno** que alimentará a futura
  **aba de Ganhos** (Playtest 02, ponto 6). Fórmula/decay/piso são **números da 0003**.

### D5 — Inventário/janela: lista consultável (Q5=A, default)
- Painel **recolhível** no GameView (reusa `CollapsibleSection` da sessão anterior):
  - **Músicas**: nome · gênero · tema · qualidade · status.
  - **Lançamentos**: tipo · data (calendário) · royalty atual.

## Questions
- Q1–Q5 **resolvidas** (ver [questions.md](questions.md)). Nenhuma bloqueante aberta.

## Checklist result
- Escopo confirmado; decisões D1–D5 fecham o desenho da feature.
- Pronta para handoff (G1). Implementação segue a ordem da
  [decomposition](decomposition.md): modelo de música → qualidade → cadeia de
  lançamento → royalties → inventário.
