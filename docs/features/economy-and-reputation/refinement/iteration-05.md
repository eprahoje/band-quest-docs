# Feature 0003 - Economia e Reputação (Refinamento 05 — Balance pass 1)

> Primeira calibragem numérica (base diária — turno = dia). Valores são um ponto de
> partida a ser afinado jogando; o objetivo é dificuldade **equilibrada**.

## Decisões

### Modelo de custos estruturado
Três fontes de custo (visíveis ao jogador num painel de "Custos"):
1. **Custos mensais por membro** — cada membro custa por mês, **crescendo com a
   reputação** da banda (e, no futuro, com a experiência/progressão do membro — 0007).
   Cobrados a cada virada de mês (30 dias). Fórmula inicial:
   `custoMensal = nMembros × BASE × (1 + reputação/100)`, com `BASE = 100`.
2. **Custos por ação** — aluguel de estúdio / gravação (demo, single, álbum),
   campanha de marketing, etc. Já embutidos no `outcome.cash` negativo de cada ação.
3. **Custos de staff/estrutura** — futuro (feature 0013); placeholder.

### Reputação: mais escassa + decai se inativa
- **Ganhos reduzidos** (no playtest, 40+ vinha fácil demais): show +1 (era +3),
  single +2 (era +4), álbum +6 (era +12), turnê +5 (era +8), demo +1, ensaio +1.
  Chegar a 40+ passa a exigir uma sequência consistente de lançamentos/shows.
- **Decay por inatividade pública:** sem atividade voltada ao público (show, turnê,
  lançamento, marketing) por mais de um período de carência, a reputação cai aos
  poucos. Parâmetros: `REP_GRACE_DAYS = 30`, `REP_DECAY_PER_DAY = 0.1`
  (~3 pontos/mês após a carência). Atividade pública zera o contador de inatividade.

### Esforço passa a modular o resultado (refinamento do modelo da 0014)
- Correção de design: hoje as opções "caprichado" custam/demoram mais **sem render
  mais** (estritamente piores). Adiciona-se `outcomeModifier` a cada opção de
  esforço, que **escala os ganhos positivos** (fãs/reputação). Assim "caprichado"
  vira um trade-off real: mais dias + mais custo → mais qualidade.
- (Registrado também no log da 0014, pois altera o `ActionDef`.)

### Dificuldade-alvo: equilibrada
- Possível crescer com boas decisões; risco real (dívida/fadiga) se administrar mal.

## Tabela de balance (placeholders — base diária)

| Ação | Esforço (dias · custoMod · outMod) | cash | rep | fans | fatiga |
|------|-----------------------------------|------|-----|------|--------|
| Ensaiar | leve 2·1·1 / pesado 4·1·1.6 | — | +1 | — | +10 |
| Compor | 5·1·1 (produz 1 música) | — | — | — | +8 |
| Gravar demo | 3·1·1 (req. 1 música) | -150 | +1 | +25 | — |
| Gravar single | 10·1·1 / caprichado 16·1.6·1.7 (req. 1) | -400 | +2 | +120 | — |
| Gravar álbum | 35·1·1 / caprichado 50·1.7·1.8 (req. 3) | -1500 | +6 | +600 | — |
| Tocar show | 1·1·1 | +150 | +1 | +30 | +18 |
| Turnê | mini 14·1·1 / nacional 45·1.5·1.6 (req. rep 30) | +1800 | +5 | +500 | +45 |
| Marketing | 14·1·1 (paralela) | -300 | — | +90 | — |
| Descansar | 5·1·1 | — | — | — | -30 |

- Início: caixa R$ 500, reputação 10, fãs 0, fadiga 0.
- `outcomeModifier` e o modulador de qualidade da banda escalam apenas ganhos
  positivos (não a fadiga nem o custo).

## Non-goals desta passada
- Números finais (isto é a 1ª passada — afinar jogando).
- Custos de staff (0013) e itens (0012).
- Aba de Custos completa/rica — nesta slice, um painel simples no GameView.

## Checklist result
- [x] Scope reviewed.
- [x] Questions updated.
- [x] Handoff reviewed.
