# Feature 0013 - Staff and Crew (Refinement 03)

> Resolve a Q7 (Playtest 06) e expande o catálogo: staff vira **cargo único** (upgrade, não
> contratação infinita) e os locais maiores passam a exigir **mais cargos distintos** (mais
> gente na produção), não N cópias do mesmo papel. Supersede o gate por contagem da it-02/
> slice 2. Números = placeholders (0003).

## Decisions

### D7 (Q7) — Cargos ÚNICOS (1 por papel)
- Cada papel é contratado **no máximo uma vez** (sem duplicatas). `hireStaff` recusa um papel
  já contratado. Isso reflete a ideia de **upgrade/cargo** em vez de "exército de roadies".
- *(Níveis de upgrade por cargo — ex.: roadie → chefe de equipe — ficam como evolução futura.)*

### D8 — Catálogo expandido (8 cargos)
**Negócio/pessoal** (modificadores — slice 3, futuro):
- **Empresário** — +cachê. · **Preparador vocal** — −fadiga de show.

**Crew/produção** (habilitam locais — gate; "mais gente para locais maiores"):
- **Roadie** — montagem básica. · **Técnico de som** · **Iluminador** ·
  **Motorista** (turnês) · **Segurança** (grandes públicos) · **Produtor de palco**.

### D9 — Gate de locais por CONJUNTO de cargos (rico)
`Venue.requiredStaff` deixa de ser contagem e passa a ser um **conjunto de cargos distintos**;
o local libera quando a banda tem **todos** os cargos exigidos. Escalonado (rico):
| Local | Cargos exigidos |
|---|---|
| Bar | — |
| Casa de shows | Roadie |
| Ginásio | Roadie · Técnico de som · Iluminador |
| Estádio/Festival | Roadie · Técnico de som · Iluminador · Segurança · Produtor de palco |
- Resolve o **Playtest 06 ponto 7** na raiz (some a contagem confusa "2 roadies"). Locais
  maiores = **montar uma produção** (mais cargos, mais salários mensais).

## Implementação (band-quest-game)
- `data/staff.ts`: +4 papéis (`sound-tech`, `lighting-tech`, `security`, `stage-manager`)
  com custo/salário (placeholders).
- `data/venues.ts`: `Venue.requiredStaff: StaffRole[]` (conjunto); `venueStaffShortfall`
  retorna os **cargos faltantes**; `venueStaffSatisfied` = nenhum faltando.
- `stores/game.ts`: `hireStaff` recusa papel já contratado; `venueCatalog.staffShortfall`
  vira lista de cargos; `scheduleShow` lista os cargos que faltam.
- UI: `StaffPanel` mostra cada cargo como **Contratar** ou **Contratado/Dispensar** (sem
  duplicar); `VenueList` mostra os cargos exigidos com ✓ (tem) / ✗ (falta).

## Checklist result
- [x] Scope reviewed.
- [x] Questions updated — Q7 resolvida.
- [x] Handoff reviewed — **G1 liberado**; implementação nesta mesma leva (supersede a slice 2).
