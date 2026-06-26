# Feature 0015 - Songwriting and Releases (Questions)

## Open Questions
*(Nenhuma. Q1–Q5 resolvidas — ver abaixo.)*

## Resolved Questions

### [Q1] Quão profundo é o controle do jogador sobre o metadado da música?
**Decisão:** **[A] Auto + editável.** O jogo sugere nome/tema (pool IP-safe) e herda o
gênero da banda; o jogador pode editar. Fricção baixa em sessões longas. (Ver D1.)

### [Q2] De onde vem a "qualidade" de uma música?
**Decisão:** **[C] Atributos + esforço + entrosamento/ensaio + variação leve.** O
`rehearse` eleva um fator de **entrosamento** que entra na qualidade junto dos
atributos (0007) e do esforço (0014). Liga progressão ao songwriting. Pesos = 0003.
(Ver D2.)

### [Q3] Tipos de lançamento e regras de composição.
**Decisão:** **[A] Demo + Single + Álbum.** Demo = N músicas (placeholder 3, ≥2);
Single = 1 música; Álbum = X singles + Y músicas (placeholders 2 + 4). Números = 0003.
(Ver D3.)

### [Q4] Como funciona a receita de longo prazo (royalties)?
**Decisão:** **[A] Royalty decrescente por turno.** Receita inicial ∝ qualidade × fãs
no lançamento, decaindo geometricamente até um piso. Estrutura aqui; números na 0003.
(Ver D4.)

### [Q5] Escopo do inventário/"janela" de músicas e lançamentos.
**Decisão:** **[A] Lista consultável** (músicas + lançamentos) em painel recolhível no
GameView, reusando `CollapsibleSection`. (Ver D5.)
