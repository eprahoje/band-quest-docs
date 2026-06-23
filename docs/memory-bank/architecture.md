# Band Quest — Decisões de Arquitetura

Decisões que atravessam múltiplas features e precisam ser consultadas em
qualquer sessão de IA, independente da feature em foco.

## Tech stack (decidida em 2026-06-23)

**Fase 1 (MVP):** Vue 3 + Vite + Pinia + Tabler Icons + Vitest + Playwright.
Android via Capacitor. Itch.io via build HTML5 estático.
Ver estudo completo de trade-off em [`tech-stack.md`](tech-stack.md).

Critério de revisão: se surgir necessidade de sprites animados em >20% das
telas, performance insatisfatória no Android, ou distribuição em lojas de PC
→ avaliar migração para Godot usando a spec do `band-quest-docs` como contrato.

## Estratégia visual do MVP (Feature 0006)

O MVP é visualmente estático: cards, ícones de biblioteca (Tabler/Lucide) e
painéis de stats. Não usa sprites, pixel art ou ilustração animada. Ver
`docs/features/art-direction-and-visual-system/planning/overview.md` para
o detalhamento completo, Non-goals e critérios de aceite.
