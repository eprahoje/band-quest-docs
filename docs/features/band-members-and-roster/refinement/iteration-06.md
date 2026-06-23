# Feature 0007 - Band Members and Roster (Refinement 06)

## Decisions
- Produzidos os **15 ícones flat-vector** dos membros (camada atual/MVP) em
  `band-quest-game/src/assets/members/`, um por personagem do cast
  (`member-<slug>.svg`).
- Estilo confirmado: **flat-vector autoral**. Gemini descartado nesta fase;
  pixel-art permanece como direção futura (0006, iteration-04).
- Adicionado **teste de validação de SVG** em `band-quest-game` cobrindo:
  XML bem-formado, `viewBox` quadrado, ausência de raster/fundo opaco,
  nomenclatura e cobertura cruzada com o cast (15/15).
- Verificação: `type-check` limpo e 34 testes passando.

## Questions
- Sem perguntas bloqueantes.

## Checklist result
- [x] Scope reviewed.
- [x] Questions updated.
- [x] Handoff reviewed (15/15 produzidos e validados por teste).
