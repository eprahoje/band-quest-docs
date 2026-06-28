# Feature 0013 - Staff and Crew (Log)

## [0.1.0] - 2026-06-23T00:00:00Z

### Input
- Desdobramento da Q6 da 0012: o usuário decidiu criar uma feature própria para o
  sistema de Staff (empresário, preparador vocal, roadies, motorista) que leva a
  desbloqueios e caminhos.

### Summary
- Criado o scaffold da feature 0013 (README, diagrams, planning/overview,
  decomposition, checklist, questions, iteration-01, log).
- Registrada nos índices (`features/README.md` e `roadmap.md`).
- Abertas Q1–Q5 (papéis, pagamento, tipo de efeito, relação com 0011/0012, números).

### Open questions
- Q1, Q2, Q3, Q4, Q5 — ver `questions.md`.

### Next step
- Refinar Q1–Q5 com o usuário, fechar o modelo de staff e o conjunto inicial de papéis.

## [0.2.0] - 2026-06-27T00:00:00Z — Inception → G1 (spec pronta)

### Input
- Playtest 05 ponto 7 (Aurora = dinheiro fácil → exigir staff para locais). Respostas do
  usuário a Q1–Q3 e Q6; Q4/Q5 fechadas por default.

### Summary
- **D1 (Q1):** 4 papéis — empresário, preparador vocal, roadie, motorista.
- **D2 (Q2):** contratação (custo único) + **salário mensal** recorrente (0003).
- **D3 (Q3):** efeito **híbrido** — modificadores (empresário +cachê, preparador −fadiga) e
  desbloqueios (roadie → locais maiores, motorista → turnês maiores).
- **D4 (Q6):** **gate de locais escalonado por tier** — `Venue.requiredStaff` (bar livre →
  casa 1 roadie → ginásio crew maior → estádio crew completo). Acopla 0013 ↔ 0016.
- **D5/D6:** staff independente por ora (gancho p/ 0011/0012); números na 0003.
- Decomposição consolidada (4 slices; MVP = 1 modelo + 2 gate). Questões → resolvidas.

### Open questions
- Nenhuma. Números = placeholders (0003).

### Next step
- **G1 ✅** — Implement da slice 1 (modelo + contratação + salário) quando priorizado;
  depois slice 2 (gate de locais), que resolve o Playtest 05 ponto 7.

## [0.3.0] - 2026-06-27T00:00:00Z — slices 1 e 2 (modelo + gate de locais) — Implement→Validate→Deploy

### Input
- Decisão do usuário: implementar a 0013 para fechar o Playtest 05 ponto 7 (Aurora = dinheiro
  fácil). Fechar o ponto exige as duas slices do MVP (modelo + gate).

### Summary
- `data/staff.ts`: `StaffRole` (manager/vocal-coach/roadie/driver) + `STAFF_ROLES` (label,
  descrição, `hireCost`, `monthlySalary`) + `getStaffRole`/`staffCountsByRole`. Números = 0003.
- `data/venues.ts`: `Venue.requiredStaff` por tier (bar livre; casa 1 roadie; ginásio 2;
  estádio 2 roadies + 1 motorista) + `venueStaffShortfall`/`venueStaffSatisfied`.
- `stores/game.ts`: `hiredStaff` + `hireStaff`/`fireStaff` (custo único na hora; salário
  mensal somado ao custo da virada de mês); `monthlyStaffCost`; `staffCounts`; `venueCatalog`
  ganhou `staffShortfall`/`staffOk`/`bookable`; `scheduleShow` bloqueia se faltar equipe.
- UI: `StaffPanel.vue` (contratar/dispensar, salário mensal) no GameView; `VenueList` mostra
  "Requer equipe: X" e só habilita Agendar quando `bookable`.

### Validate (gate verde)
- `test:unit` 167 (era 158; +staff.spec, +venues staff gate, +store hire/fire/salário/gate de
  local). `type-check`/`lint`/`build` OK.

### Open questions
- Nenhuma. Slices 3 (modificadores passivos) e 4 (motorista → turnê maior) ficam para depois.

### Next step
- Slice 3 (empresário +cachê, preparador −fadiga) quando priorizada; calibrar números (0003).

## [0.4.0] - 2026-06-28T00:00:00Z — iteration-03 (cargos únicos + catálogo expandido + gate por conjunto)

### Input
- Playtest 06 ponto 7 + proposta do usuário: staff como **upgrade/cargo único** (não contratação
  infinita) e locais maiores exigindo **mais cargos distintos** (mais gente na produção). Resolve
  a Q7. Supersede o gate por contagem da slice 2.

### Summary
- **D7 — cargos únicos**: `hireStaff` recusa um papel já contratado (1 por papel).
- **D8 — catálogo expandido (8)**: + `sound-tech` (Técnico de som), `lighting-tech` (Iluminador),
  `security` (Segurança), `stage-manager` (Produtor de palco), além de manager/vocal-coach/roadie/
  driver.
- **D9 — gate por conjunto de cargos**: `Venue.requiredStaff: StaffRole[]` (distintos). Casa =
  roadie; ginásio = roadie + som + luz; estádio = + segurança + produtor de palco.
  `venueStaffShortfall` retorna os cargos faltantes. Resolve o ponto 7 na raiz.
- UI: `StaffPanel` mostra cada cargo como Contratar ou Contratado/Dispensar (sem duplicar);
  `VenueList` lista os cargos exigidos com ✓/✗.

### Validate (gate verde)
- `test:unit` 172 (era 170; +cargos únicos/duplicata bloqueada, +gate por conjunto no ginásio,
  catálogo de 8). `type-check`/`lint`/`build` OK.

### Open questions
- Nenhuma. Níveis de upgrade por cargo (roadie → chefe de equipe) e modificadores (slice 3) =
  futuro. Números = placeholders (0003).

### Next step
- Slice 3 (modificadores: empresário +cachê, preparador −fadiga) + slice 4 (motorista → turnê
  maior) quando priorizadas.
