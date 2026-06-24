# Feature 0014 - Core Loop and Actions (Refinement 02)

## Decisions

### Conjunto inicial: essenciais + marketing/demo — Q1 resolvida [A+]
- Ações de lançamento: **ensaiar, compor, gravar demo/single/álbum, tocar show,
  turnê, marketing, descansar**.
- Cobre o ciclo de carreira sem inflar; ações de mídia 2000s (clipe/rádio/internet)
  ficam para depois (ligadas à 0009).

### Uma principal + passivas de fundo — Q2 resolvida [A]
- O jogador conduz **uma ação principal por vez** (ocupa N turnos) e pode ter
  **ações passivas/de fundo** rodando em paralelo (ex.: marketing enquanto grava).
- Modelo de `lane`: `main` | `background`.

### Qualidade híbrida (faixa + recursos) — Q3 resolvida [A]
- O jogador escolhe uma **faixa de esforço/duração** (ex.: rápido vs. caprichado →
  menos/mais turnos e custo); o **resultado é modulado por recursos**: atributos dos
  membros (0007), itens (0012), staff/produtor (0013).

### Variação leve + eventos — Q4 resolvida [C]
- O resultado cai numa **faixa com aleatoriedade leve** em torno do esperado, e há
  **chance de eventos (0009)** interferirem durante a ação. Nunca injusto: a variância
  orbita o valor calibrado.

## Model (resumo — detalhe em `planning/design.md`)
- `ActionDef`: `id`, `name`, `lane`, `effortOptions[]` (faixas de duração/custo),
  `prerequisites?`, `resourceModifiers`, `outcome` (métricas-base + `variance` +
  `eventChance?`).
- Ciclo de vida: `idle → in-progress (N turnos) → completed` → aplica efeitos,
  registra evento e pode disparar marco (0011).

## Outcome
- Estrutura do core loop fechada; modelo + catálogo em `planning/design.md`.
- Status → **Ready for Implementation**, pendente apenas a calibragem (0003 balance)
  e os pontos de integração (0007/0009/0011/0012/0013).

## Checklist result
- [x] Scope reviewed.
- [x] Questions updated.
- [x] Handoff reviewed.
