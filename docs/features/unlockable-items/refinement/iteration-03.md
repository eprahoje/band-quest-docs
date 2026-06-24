# Feature 0012 - Unlockable Items (Refinement 03)

## Decisions

### Loja fica na 0012, extrai se crescer — Q5 resolvida [C]
- A loja vive na **0012** como fonte de desbloqueio por compra (loja simples que
  consulta itens compráveis + `cost`).
- Vira feature própria **somente** se ganhar complexidade (preços dinâmicos,
  estoque por época, UI dedicada). Registrado como gatilho de extração no roadmap.

### Staff vira feature própria — Q6 resolvida [A]
- Criada a feature **0013 - Staff and Crew** (contratar empresário, preparador
  vocal, roadies, motorista, etc.), distinta de "itens".
- A 0012 **não** absorve Staff; apenas referencia a 0013 quando um membro de staff
  habilitar/condicionar um desbloqueio.

## Outcome
- Escopo da 0012 fechado: modelo de item + 4 categorias + fontes (marcos/compra/
  época) + efeitos funcionais + loja simples.
- Status → **Ready for Implementation**, pendente apenas calibragem (0003), ids de
  marco (0011) e itens por época (0008).

## Checklist result
- [x] Scope reviewed.
- [x] Questions updated.
- [x] Handoff reviewed.
