# Feature 0016 - Venues and Shows (Questions)

## Open Questions
*(Nenhuma. Q1–Q6 resolvidas na iteration-02 — G1 liberado.)*

## Resolved Questions

### [Q1] Geografia/progressão dos locais → começa abstrata (tiers), futuro híbrido
**Decisão (it-02 D1):** MVP com **tiers abstratos** (bar → casa de shows → ginásio →
estádio/festival) para validar a mecânica. Objetivo de longo prazo: **híbrido** (tiers
dentro de regiões/cidades a partir da origem) — `Venue` já nasce com campo de região.

### [Q2] Desbloqueio → reputação + fãs
**Decisão (it-02 D2):** cada local exige **limiar de reputação E público mínimo (fãs)**.
Local travado mostra o requisito que falta.

### [Q3] Receita → cachê base + bilheteria
**Decisão (it-02 D3):** **cachê base** (garantia, escala com reputação) + **bilheteria**
`min(fãs interessados, capacidade) × preço`. Preço **fixo por tier** no MVP; escolha de
preço pelo jogador (Q3.1) fica como evolução.

### [Q4] Agenda → compromisso datado
**Decisão (it-02 D4):** o jogador **agenda** o show num local para uma **data futura**; no
dia, credita cachê+bilheteria. Janela permite promover (slice futura); faltar penaliza.

### [Q5] Turnê/staff → turnê fica na 0014 por enquanto
**Decisão (it-02 D5):** turnê continua ação única (0014) no MVP; vira **trajeto de
locais/datas** numa slice futura (depende de 0013 e da geografia híbrida).

### [Q6] MVP → catálogo+desbloqueio, depois agendar+receita
**Decisão (it-02 D6):** MVP = slice 1 (catálogo + desbloqueio) → slice 2 (agendar show +
cachê+bilheteria). Promoção/penalidade e turnê-trajeto vêm depois.
