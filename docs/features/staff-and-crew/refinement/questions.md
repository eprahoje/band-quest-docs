# Feature 0013 - Staff and Crew (Questions)

## Open Questions

### [Q7] Staff são cargos únicos/upgrades ou contratáveis em quantidade? (Playtest 06)
**Context:** A contratação atual permite N do mesmo papel (o gate usa contagem: ginásio = 2
roadies), o que confundiu no Playtest 06 (ponto 7) e parece estranho ("5 empresários"). O
usuário propôs tratar staff como **upgrades**, não infinito.
**Status:** 🟡 Needs Discussion (próxima iteração — it-03)
**Options:**
- [A] **Cargos únicos + upgrades**: 1 por papel, melhorável por nível. O gate de locais passa
  a exigir **cargos/níveis** (casa → roadie; ginásio → técnico de palco; estádio → equipe de
  produção) em vez de contagem. Resolve o ponto 7 na raiz.
- [B] **Híbrido**: papéis de "negócio" (empresário, preparador) são únicos; "crew" (roadie,
  motorista) continua contável (tamanho de equipe).
- [C] Manter como está (contagem para tudo), só melhorando a UI.
- [X] Aberto.

**Answer:** [a definir na iteration-03]

## Resolved Questions

### [Q1] Papéis iniciais → 4 papéis
**Decisão (it-02 D1):** empresário, preparador vocal, roadie, motorista. Ampliar é evolução.

### [Q2] Pagamento → contratação + salário
**Decisão (it-02 D2):** custo único de contratação + salário mensal recorrente (espelha o
custo dos membros, 0003). Demitir encerra o salário.

### [Q3] Efeito → híbrido (modificadores + desbloqueios)
**Decisão (it-02 D3):** cada papel declara modificadores passivos e/ou desbloqueios
(empresário +cachê; preparador vocal −fadiga; roadie habilita locais maiores; motorista
habilita turnês maiores).

### [Q4] Relação com 0011/0012 → independente por ora (default)
**Decisão (it-02 D5):** staff é independente e declara seus próprios efeitos/desbloqueios; a
ligação com itens (0012)/marcos (0011) fica como gancho/evolução.

### [Q5] Números → na 0003 (default)
**Decisão (it-02 D6):** conceito/estrutura aqui; custos/salários/percentuais/crew = 0003.

### [Q6] Gate de locais (Playtest 05 ponto 7) → escalonado por tier
**Decisão (it-02 D4):** `Venue.requiredStaff` por tier (bar livre; casa 1 roadie; ginásio
crew maior; estádio crew completo). Sem a equipe, o local fica bloqueado para agendar.
Acopla 0013 ↔ 0016.
