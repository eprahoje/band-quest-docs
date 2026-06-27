# Feature 0016 - Venues and Shows (Questions)

## Open Questions

### [Q1] Como modelar a geografia/progressão dos locais?
**Contexto:** Define a sensação de "para onde a carreira vai" e o quanto de simulação
geográfica entra. É a decisão estruturante da feature.
**Status:** 🔴 Bloqueante
**Opções:**
- [A] **Tiers abstratos** de local (bar → casa de shows → ginásio → estádio/festival),
  sem mapa; o "tamanho" cresce com a reputação. Simples e direto.
- [B] **Cidades/estados do Brasil** começando no estado de origem; o jogador expande pelo
  mapa. Mais imersivo, mais complexo (precisa de dados geográficos).
- [C] **Híbrido**: tiers de local DENTRO de cidades/regiões que se abrem com a reputação
  (ex.: bares na cidade natal → casas de shows em capitais → festivais nacionais).
**Resposta:**

### [Q2] Como o local é desbloqueado?
**Contexto:** O roadmap fala em "desbloqueia conforme a reputação cresce".
**Status:** 🔴 Bloqueante
**Opções:**
- [A] Só por **limiar de reputação** (ex.: ginásio exige rep ≥ X).
- [B] Reputação **e/ou fãs** (público mínimo para encher).
- [C] Reputação + **marcos de carreira** (0011) para os grandes (estádio/festival).
**Resposta:**

### [Q3] Como funciona a receita do show (ingressos)?
**Contexto:** P03 7.2 pede "reputação → venda de ingressos". Hoje o show paga cachê fixo
(× reputação na 0014 it-06).
**Status:** 🔴 Bloqueante
**Opções:**
- [A] **Ingressos = receita principal**: `min(fãs interessados, capacidade) × preço`;
  o cachê fixo some. Preço pode ser fixo por tier (ou escolhido — ver Q3.1).
- [B] **Cachê + ingressos**: mantém um cachê base (garantia) e soma uma fração de
  bilheteria (mais realista para banda pequena).
- [C] Manter o modelo atual (cachê × reputação) e só amarrar ao local/capacidade como teto.
- **[Q3.1]** O **preço do ingresso** é fixo por tier ou o jogador define (risco: caro =
  mais R$/pessoa, mas menos público)? (responder junto se A/B)
**Resposta:**

### [Q4] Agenda/calendário: como o show entra no tempo?
**Contexto:** Hoje `play-show` é uma ação imediata de 1 dia (0014). P03 7.3/P04 3.3 pedem
agenda.
**Status:** 🔴 Bloqueante
**Opções:**
- [A] **Compromisso datado**: o jogador agenda o show para uma data futura; nesse dia o
  show acontece (pode dar tempo de "promover" antes; faltar tem penalidade).
- [B] **Ação imediata por local** (sem data): escolhe o local e toca já — como hoje, só
  que com destino/lotação. Agenda fica para iteração futura.
- [C] **Os dois**: shows avulsos imediatos + turnê como sequência agendada de datas/locais.
**Resposta:**

### [Q5] Relação com a turnê (0014) e o gate de staff (0013)?
**Contexto:** A turnê hoje é uma ação única de N dias. P01 ponto 10 quer trajeto por
cidades; P03 9.2 quer gate de staff.
**Status:** 🟡 Requer Discussão
**Opções:**
- [A] Turnê vira **sequência de locais/datas** (depende de Q1/Q4); 0016 é dona do trajeto.
- [B] Turnê continua ação única na 0014; 0016 cuida só de shows avulsos por enquanto.
- [X] Aberto.
**Resposta:**

### [Q6] Qual o MVP (primeira slice) da 0016?
**Contexto:** Para fatiar e entregar incrementos validáveis.
**Status:** 🟡 Requer Discussão
**Opções:**
- [A] **Catálogo de locais + desbloqueio + escolha do local no show** (sem agenda nem
  ingressos novos) — menor passo que já dá progressão.
- [B] **Locais + receita por ingresso** (sem agenda).
- [C] **Locais + agenda** (sem ingressos).
**Resposta:**

## Resolved Questions
*(Mover as resolvidas para cá documentando a decisão.)*
