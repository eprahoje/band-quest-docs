# Feature 0013 - Staff and Crew

**Status:** In Implementation — MVP (slices 1 e 2) entregue: modelo + contratação + salário mensal + gate de locais escalonado (resolve Playtest 05 ponto 7). Próximas: slice 3 (modificadores), 4 (motorista → turnê maior)

## Navigation
- [Diagrams](diagrams/README.md)
- [Planning overview](planning/overview.md)
- [Decomposition](refinement/decomposition.md)
- [Checklist](refinement/checklist.md)
- [Open questions](refinement/questions.md)
- [Latest iteration](refinement/iteration-03.md)
- [Action log](refinement/log.md)

## Relationships
- **0016 (Venues and Shows)** — gate escalonado: `Venue.requiredStaff` por tier; a crew
  destrava locais maiores (Playtest 05 ponto 7). Acoplamento principal do MVP.
- **0014 (Core Loop)** — motorista habilita turnês maiores; modificadores tocam cachê/fadiga.
- **0012 (Unlockable Items)** — origem (Q6 da 0012). Ligação staff↔itens é gancho/evolução.
- **0011 (Career Milestones)** — contratar staff pode ser/destravar marcos (gancho futuro).
- **0003 (Economy and Reputation)** — staff custa (contratação + salário mensal); números na 0003.
- **0007 (Band Members and Roster)** — staff é distinto dos membros (não toca).
