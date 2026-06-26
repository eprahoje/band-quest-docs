# Feature 0015 - Songwriting and Releases (Decomposition)

## Epic breakdown
Slices candidatas (validáveis de forma independente, na ordem sugerida):

1. ✅ **Modelo de música** *(feito 2026-06-25)* — substituir o contador `songs` por uma
   lista de objetos `Song` (id, name, genre, theme, quality). `compose` passa a criar um
   `Song`. Migrar `record-*` para consumir/referenciar músicas concretas.
2. **Qualidade** — derivar `quality` de atributos da banda (0007) + esforço (0014) +
   variação leve; refletir a qualidade nos efeitos do lançamento.
3. ✅ **Cadeia de lançamento** *(feito 2026-06-25)* — tipos demo/single/álbum com regras de
   composição (mínimos de músicas/singles) e produção de um objeto `Release`.
4. **Receita de longo prazo (royalties)** — lançamentos geram receita decrescente por
   turno; estrutura aqui, números na 0003.
5. **Inventário/janela** — UI consultável de músicas e lançamentos.

## Why split
O modelo de música (slice 1) é o alicerce e já é entregável/testável sozinho (troca o
contador por objetos sem mudar a economia). Qualidade, cadeia de lançamento e royalties
empilham incrementos validáveis. A janela (UI) fecha a experiência.

## Recommended order
1 → 2 → 3 → 4 → 5. As slices 1–3 são mecânica; 4 encosta na 0003; 5 é UI.
