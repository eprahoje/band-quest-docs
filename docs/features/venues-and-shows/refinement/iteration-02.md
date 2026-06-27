# Feature 0016 - Venues and Shows (Refinement 02)

> Resolve as bloqueantes Q1–Q4 (respostas do usuário) e fecha Q5/Q6 com defaults de
> escopo. Libera **G1**. Números são placeholders de balance (0003).

## Decisions

### D1 (Q1) — Geografia: começa abstrata (tiers), objetivo final híbrido
- O **MVP usa tiers abstratos** de local: `bar → casa de shows → ginásio → estádio/festival`
  (o "tamanho" cresce com a reputação/fãs). Sem mapa, para validar a mecânica rápido.
- **Norte de longo prazo:** evoluir para **híbrido** — tiers DENTRO de regiões/cidades do
  Brasil a partir do estado de origem. Registrado como evolução; **não** entra no MVP.
- O modelo `Venue` já nasce com um campo de **região** (default único "Brasil"/"Nacional")
  para o híbrido encaixar depois sem refazer o modelo.

### D2 (Q2) — Desbloqueio por reputação + fãs
- Cada local tem um **limiar de reputação** e um **público mínimo (fãs)** para liberar
  (precisa de imagem *e* base de público para encarar o local). Local travado mostra o
  requisito que falta.

### D3 (Q3) — Receita: cachê base (garantia) + bilheteria
- Retorno do show = **cachê base** (garantia, escala com reputação como na 0014 it-06) +
  **bilheteria** = `min(fãs interessados, capacidade do local) × preço do ingresso`.
- **Preço do ingresso**: fixo por tier no MVP (placeholder). A **escolha de preço pelo
  jogador** (Q3.1) fica como evolução (risco/retorno).
- `fãs interessados` = função simples dos fãs × atratividade (placeholder; afinar na 0003).

### D4 (Q4) — Show é um compromisso datado
- O jogador **agenda** o show num local para uma **data futura**; no dia, o show acontece
  e credita cachê+bilheteria. A janela até a data permite **promover** (slice futura).
- **Faltar/cancelar** tem penalidade (reputação/multa) — regra detalhada na slice de agenda.
- Isso muda o modelo atual (hoje `play-show` é ação imediata de 1 dia, 0014): a 0016 passa
  a ser dona do **agendamento**; a 0014 fornece a execução/efeitos no dia.

### D5 (Q5) — Turnê fica na 0014 por enquanto
- A turnê continua a ação única de N dias da 0014 no MVP. Vira **trajeto de locais/datas**
  (consumindo venues + agenda) numa **slice futura**, acoplada ao gate de staff (0013) e à
  geografia híbrida (D1). Evita inchar o MVP.

### D6 (Q6) — MVP e ordem das slices
- **MVP = slice 1 (catálogo + desbloqueio)** → **slice 2 (agendar show no local +
  cachê+bilheteria)**. A promoção/penalidade (slice 3) e a turnê-trajeto (slice 5) vêm depois.

## Decomposição revisada
1. **Catálogo de locais + desbloqueio** — `Venue` (nome, tier, capacidade, região,
   `repThreshold`, `minFans`); lista + UI travado/liberado com requisito. (MVP)
2. **Agendar show no local + receita** — agenda datada; no dia, cachê base + bilheteria
   (`min(fãs interessados, capacidade) × preço`). Substitui o `play-show` imediato. (MVP)
3. **Promoção + penalidade de falta** — promover na janela pré-show; no-show penaliza.
4. **Turnê como trajeto** — sequência de locais/datas; gate 0013. (futuro)
5. **Geografia híbrida** — tiers dentro de regiões/cidades a partir da origem. (futuro)

## Questions
- Q1–Q4 **resolvidas** (ver questions.md). Q5–Q6 resolvidas como escopo (D5/D6).
- Sem bloqueantes em aberto.

## Checklist result
- [x] Scope reviewed.
- [x] Questions updated — nenhuma bloqueante aberta.
- [x] Handoff reviewed — **G1 liberado**. Próximo: Implement da slice 1.
