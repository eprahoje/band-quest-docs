# Feature 0012 - Unlockable Items (Refinement 02)

## Decisions

### Categorias: 4 trilhas temáticas — Q1 resolvida [A]
- **Equipamento** (instrumentos/amps), **Estúdio**, **Marketing**, **Cosmético/visual**.
- Reconciliação com a Q3 (efeitos só funcionais): a trilha **Cosmético/visual** é
  uma categoria **temática** (itens de imagem/identidade), mas nesta fase seus
  itens entregam **efeito funcional** (ex.: modificador de reputação). Uma camada
  puramente cosmética (sem efeito mecânico) fica para iteração futura.

### Fontes de desbloqueio: marcos + compra + época — Q2 resolvida [C]
- **Marcos da 0011** (item liberado ao atingir um marco).
- **Compra** com dinheiro (loja — ver Q5).
- **Época/tecnologia** da 0008 (itens surgem conforme a linha do tempo avança).

### Efeitos: só funcionais nesta fase — Q3 resolvida [B]
- Itens são **modificadores de mecânica**: caixa, reputação e/ou eficiência das
  ações (ex.: gravar mais barato/melhor, ganhar mais fãs por show).
- Sem camada puramente cosmética por ora (adiada).

### Há loja, integrada à economia — Q4 resolvida [B]
- Existe **loja**: o jogador compra equipamento melhor (nova guitarra, amplificador,
  equipamentos em geral), integrada à economia da **0003**.
- Parte dos itens **não** é comprável e sim **desbloqueada por marcos** (0011).
- O usuário sinalizou que **a loja pode virar feature própria** → ver Q5.
- O usuário propôs um **sistema de Staff** (empresário, preparador vocal, roadies,
  motorista) que leva a outros desbloqueios/caminhos → candidato a feature 0013
  (ver Q6 e `roadmap.md`).

## Model (resumo — detalhe em `planning/design.md`)
- `Item`: `id`, `name`, `category` (equipment/studio/marketing/cosmetic),
  `unlockSources` (`milestone:<id>` | `purchase` | `era:<ano>`),
  `cost?` (se comprável — calibrado na 0003),
  `effects` (modificadores funcionais — calibrados na 0003).

## New questions (ver `questions.md`)
- **Q5** — A loja vira feature própria ou fica dentro da 0012?
- **Q6** — Criar a feature 0013 (Staff/contratações) agora ou adiar?

## Checklist result
- [x] Scope reviewed.
- [x] Questions updated.
- [ ] Handoff reviewed.
