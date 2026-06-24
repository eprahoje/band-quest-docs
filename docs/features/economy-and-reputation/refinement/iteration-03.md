# Feature 0003 - Economia e Reputação (Refinamento 03)

## Decisions

### Unidade de calendário: semana — Q3a resolvida [Semana]
- O turno equivale a **uma semana** (~52 turnos/ano). Uma sessão de 10/20/30 anos
  = ~520/1040/1560 turnos.
- Custos recorrentes (salários 0013, decay de reputação) acumulam **por semana**.
- A 0008 formaliza o mapeamento turno↔calendário; a 0003 assume a semana para a
  calibragem econômica.

### Duração de ações vira a feature 0014 — Q3b resolvida [Nova feature]
- O **modelo de ação** (custo em turnos, pré-requisitos, resultado, escala por
  qualidade/produtor) é dono da nova feature **0014 - Core Loop and Actions**.
- A 0003 fornece os **custos/ganhos** de cada ação; a 0014 fornece a **duração** e a
  mecânica. Hoje as ações estão hardcoded no `GameView` — a 0014 formaliza isso.

### Fontes de receita/custo: básicas + royalties + patrocínios — Q4 resolvida [C]
- **Receita:** shows (cachês), vendas de disco, streaming, **royalties passivos do
  catálogo lançado** e **patrocínios/eventos** (variáveis, integrados à 0009).
- **Custo:** gravação, marketing, logística/turnê, **salários de staff** (0013) e
  manutenção mínima por turno.
- Valores concretos → iteração de balance.

## Outcome
- Estrutura da economia/reputação fechada o suficiente para virar contrato.
- Pendências remanescentes: a feature **0014** (duração/mecânica de ações) e a
  **iteração de balance** (valores). A 0003 segue *In Refinement* até o balance.

## Checklist result
- [x] Scope reviewed.
- [x] Questions updated.
- [x] Handoff reviewed.
