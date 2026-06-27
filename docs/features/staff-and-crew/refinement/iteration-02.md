# Feature 0013 - Staff and Crew (Refinement 02)

> Iteração que resolve Q1–Q3 e Q6 (respostas do usuário) e fecha Q4/Q5 com defaults.
> Motivada pelo Playtest 05 ponto 7 (gate de staff para locais maiores). Libera **G1**.
> Números = placeholders de balance (0003).

## Decisions

### D1 (Q1) — 4 papéis no conjunto inicial
- **Empresário**, **Preparador vocal**, **Roadie**, **Motorista**. Conjunto enxuto para
  validar o sistema; ampliar (produtor, assessor de imprensa…) é evolução.

### D2 (Q2) — Contratação + salário recorrente
- Contratar tem **custo único** (entrada) **+ salário mensal** recorrente, cobrado na
  virada de mês (espelha o custo mensal dos membros da banda — 0003). Demitir encerra o
  salário. Dá peso econômico real à decisão de montar equipe.

### D3 (Q3) — Efeito híbrido (modificadores + desbloqueios)
- Cada papel declara **modificadores passivos** e/ou **desbloqueios**:
  - **Empresário** — modificador: **+% no cachê** de shows (negócios).
  - **Preparador vocal** — modificador: **reduz a fadiga** dos shows (ou parte dela).
  - **Roadie** — desbloqueio: **habilita locais maiores** (ver D4/gate) + modificador leve
    de fadiga (carrega/monta equipamento).
  - **Motorista** — desbloqueio: **turnês maiores/mais longas** (gancho da turnê-trajeto,
    0016 slice 4) + reduz fadiga de turnê.

### D4 (Q6, ponto 7) — Gate de locais ESCALONADO por tier
- Cada `Venue` (0016) declara um **requisito de equipe** por tier:
  - **Bar** — livre (sem staff).
  - **Casa de shows** — exige **1 roadie**.
  - **Ginásio** — exige **crew maior** (ex.: 2 roadies, ou roadie + motorista).
  - **Estádio/Festival** — exige **crew completo** (ex.: 3+).
- Sem a equipe exigida, o local fica **bloqueado para agendar** (a UI mostra "Requer:
  reputação + fãs + equipe"). Resolve a "Aurora = dinheiro fácil": agora exige montar (e
  pagar) uma equipe. **Acopla 0013 ↔ 0016**: a 0016 ganha um campo `requiredStaff` no
  `Venue`; a 0013 é dona do catálogo/contratação.

### D5 (Q4 — default) — Relação com itens (0012) e marcos (0011)
- No escopo atual, o staff é **independente** e declara seus próprios efeitos/desbloqueios
  (incl. o gate de locais). A ligação fina — staff desbloqueando itens (0012) ou habilitado
  por marcos/época (0011) — fica como **gancho/evolução**, não bloqueia o MVP.

### D6 (Q5 — default) — Números na 0003
- Conceito/estrutura aqui (papéis, efeitos, gate, regra de pagamento); **custos, salários,
  percentuais e tamanhos de crew** são placeholders calibrados na 0003.

## Modelo (alto nível)
- `StaffRole`: `manager | vocal-coach | roadie | driver`.
- `StaffMember` / catálogo: `id, role, hireCost, monthlySalary, effects[] (modificadores),
  unlocks[] (capacidades: ex. 'venue-crew', 'longer-tours')`.
- Estado no store: `hiredStaff[]`; custo mensal soma ao `monthlyMemberCost` na virada de mês.
- `Venue.requiredStaff` (0016): contagem/composição de crew exigida por tier.

## Decomposição (slices)
1. **Modelo + contratação + salário** *(MVP)* — catálogo dos 4 papéis, contratar/demitir,
   custo único + salário mensal no loop econômico. Painel de equipe (reusa CollapsibleSection).
2. **Gate de locais escalonado** *(MVP — resolve o ponto 7)* — `Venue.requiredStaff`; agendar
   exige a crew; UI mostra o requisito de equipe que falta.
3. **Modificadores passivos** — empresário (+cachê), preparador vocal (−fadiga de show).
4. **Desbloqueios de turnê** *(futuro)* — motorista habilita turnês maiores (pareia com a
   0016 slice 4 turnê-trajeto).

MVP = slices 1 e 2 (modelo + gate), que entregam a barreira pedida no Playtest 05 ponto 7.

## Checklist result
- [x] Scope reviewed.
- [x] Questions updated — Q1–Q3, Q6 resolvidas; Q4/Q5 fechadas por default.
- [x] Handoff reviewed — **G1 liberado**. Próximo: Implement da slice 1 (quando priorizado).
