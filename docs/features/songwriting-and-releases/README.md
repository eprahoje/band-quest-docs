# Feature 0015 - Songwriting and Releases

**Status:** In Implementation — slices 1 e 3 entregues (faltam 2, 4, 5) (G1 ✅)

Modelo de **música como objeto de primeira classe** (nome, gênero, tema, qualidade)
e a **cadeia de lançamento** composição → demo / single / álbum, com inventário
consultável e impactos de longo prazo (royalties/receita).

## Navigation
- [Planning overview](planning/overview.md)
- [Decomposition](refinement/decomposition.md)
- [Checklist](refinement/checklist.md)
- [Open questions](refinement/questions.md)
- [Latest iteration](refinement/iteration-01.md)
- [Action log](refinement/log.md)
- [Diagrams](diagrams/README.md)

## Relação com outras features
- **0014 Core Loop and Actions** — hoje dona das ações `compose`/`record-*` e do
  contador `songs`. A 0015 substitui o contador por um **modelo de música**; as ações
  de gravação passam a consumir/referenciar músicas concretas.
- **0003 Economy and Reputation** — contrato numérico. A 0015 define a **estrutura**
  da receita por lançamento (royalties); os **números** ficam na 0003.
- **0007 Band Members and Roster** — atributos dos membros alimentam a **qualidade**.
- **0008 / 0004** — gênero/tema × tendências de mercado: fora de escopo nesta fase.
