# Playtest 06 — 2026-06-27 (sessão 02)

Sexto playtest — sessão jogada pela **noiva do usuário** (olhar de fora, primeira vez),
com a análise do usuário sobre cada ponto. Após o MVP da 0016 (venues/shows), o balance
da turnê e a 0013 slices 1+2 (staff + gate de locais). Dois pontos foram **investigados no
código** a pedido do usuário (3 e 7).

## Resumo da classificação

| # | Tema (relato dela) | Tipo | Visão do usuário / encaminhamento | Dona |
|---|--------------------|------|-----------------------------------|------|
| 1 | Não entendeu o que faz o "valor dos membros" subir | UX/mecânica | Iterar a mecânica de **salário/contratos dos membros** | 0017/0007/0003 |
| 2 | Não dá para **cancelar** uma ação (clicou em ensaio pesado sem querer) | UX/mecânica | Concorda — permitir cancelar antes de avançar | 0014 |
| 3 | Marketing diz "Custo base: R$300" mas cobrou R$256 | Bug/UX | Investigar | 0014/0003 |
| 4 | Sugestão: **férias** que descansam mais, liberadas com limite (2×/ano) | Mecânica | Já reportado — desenvolver | 0014 |
| 5 | Não sentiu diferença com o **preparador vocal** (fadiga igual) | Faltando | Sem impacto ainda — slice 3 da 0013 | 0013 |
| 6 | **Motorista** aparenta não ter utilidade | Faltando | Idem ponto 5 — slice 4 da 0013 | 0013 |
| 7 | 1 roadie não liberou o **ginásio**; liberou com o 2º | "Bug" | Investigado — **é por design** (ginásio = 2 roadies); clareza de UI | 0013/0016 |
| 8 | A dinâmica de descanso cansa; faltam opções (férias/hiato) | Mecânica | Idem ponto 4 | 0014 |
| 8.1 | Descanso prolongado (ex.: 10 dias: −60 fadiga) | Mecânica | Idem ponto 4 | 0014 |
| 9 | Ensaiar muito **não** mudou a qualidade das composições | Mecânica | `rehearse` será refatorado p/ casar com evolução dos membros | 0015/0007 |
| 10 | Turnê com fadiga alta perde reputação e não ganha stats | Esperado | É o propósito (penalidade de excesso) | — |
| 11 | Show em Estádio parece mais vantajoso que turnê (números) | Balance | Iteração de balance do jogo | 0003 |
| O1 | Janelas/telas por ação OU layout em mais colunas (ref. A Story of a Band) | UX/arquitetura | Avaliar UI Shell no design system | 0006/nav |

## Pontos — relato dela (verbatim) + encaminhamento

### 1. O que faz o "valor dos membros" aumentar?
> "não entendi muito bem o que faz o valor dos membros aumentar"

**Usuário:** iterar a questão dos **contratos dos membros** — alterar a mecânica de salário
dos membros. **Encaminhamento:** hoje o custo mensal por membro escala com a reputação
(`MEMBER_BASE_MONTHLY_COST × (1 + reputação/100)`) — daí "o valor sobe" sem explicação visível.
Vira a candidata **0017 (Contracts and Salaries)**: salário por atributos + reputação, contrato,
renovação. Conecta 0007 (atributos) + 0003 (números).

### 2. Cancelar uma ação iniciada
> "queria ensaio leve mas cliquei em ensaio pesado sem querer e não pude voltar atrás"

**Usuário:** concorda — permitir **cancelar a ação antes de executá-la** (avançar os dias).
**Encaminhamento:** a ação vai para a fila ao iniciar; falta um **cancelar** enquanto não
avançou o tempo (devolve insumos reservados, se houver). Mecânica/UX da **0014** (painel "Em
andamento" ganha botão cancelar).

### 3. Custo do marketing variou (R$300 → R$256)
> "o marketing diz 'custo base: R$300' mas uma das vezes foi R$256, não sei se é bug"

**Investigado:** **não é erro de cálculo** — a variância das ações (`±20%`, `outcome.variance`)
é aplicada a **todos** os deltas no `resolveOutcome`, inclusive o **custo** (cash negativo):
`-300 × 0.853 = -256`. O card mostra o **base** (300), por isso a diferença surpreende.
**Decisão a tomar (balance/UX):** (a) **não aplicar variância ao custo** (custos previsíveis;
variar só os ganhos), e/ou (b) mudar o rótulo para indicar que é aproximado. Recomendo (a).

### 4. / 8. / 8.1. Mais tipos de descanso (férias, hiato, prolongado)
> "uma opção de férias que descanse mais, liberada menos vezes (2×/ano ou a cada x meses)"
> "a dinâmica do descanso fica cansativa; precisa de opções que descansem mais"
> "descanso prolongado: o normal é '5 dias: −30', podia ter '10 dias: −60'"

**Usuário:** já reportado (Playtest 05 ponto 4) — desenvolver. **Encaminhamento:** `rest` (0014)
ganha **mais opções**: descanso prolongado (mais dias, mais recuperação) e **férias** (recupera
muito, com **cooldown** — ex.: 1×/x meses). Recuperação proporcional à duração. Números → 0003.

### 5. / 6. Preparador vocal e motorista sem efeito
> "não senti diferença contratando o preparador vocal, o custo de fadiga continuou o mesmo"
> "aparentemente o motorista não tem utilidade também"

**Usuário:** ainda não têm impacto — vamos fazer. **Encaminhamento:** são as **slices 3 e 4 da
0013** (modificadores passivos: preparador −fadiga, empresário +cachê; motorista → turnês
maiores). Já decididas na iteration-02; faltam implementar.

### 7. Roadie e o gate do ginásio
> "tenho um roadie e mesmo assim o ginásio está bloqueado; liberou quando contratei o segundo"

**Investigado:** **comportamento esperado** — o gate é **escalonado** (casa = 1 roadie, **ginásio
= 2**, estádio = 2 roadies + motorista). Com 1 roadie o ginásio fica bloqueado de propósito. O
que confunde é a **UI**: mostra "Requer equipe: 1 roadie" (o que **falta**, não o total). **Quick
win de UI:** indicar o **total exigido** e/ou "faltam X" de forma mais clara.

### 9. Ensaiar não mudou a qualidade das composições
> "ensaiei muito e fiz Q62; ensaiei uma vez e saiu Q71"

**Usuário:** `rehearse` será **refatorado** para casar com a **evolução dos membros**.
**Encaminhamento:** hoje `rehearse` só dá reputação/fadiga e a qualidade da música vem de
atributos + esforço + variância (sem termo de ensaio). Era a **slice 2 da 0015 (entrosamento)**,
pulada — agora redefinida para ligar a **progressão dos membros (0007)**: ensaiar evolui a banda
e isso melhora as composições. Iteração futura (0015 + 0007).

### 10. Turnê exausta perde reputação e não ganha stats
> "fazer turnê com fadiga alta perde reputação e não ganha outros stats"

**Usuário:** **é o propósito** — penalidade de excesso de fadiga (0014 it-05). Sem ação; o
overflow > 100 reduz ganhos e custa reputação de propósito (sinaliza "passou do limite").

### 11. Estádio (show) vs turnê — números
> "Show em Estádio Nacional +R$1.366.200 +1530 fãs +3 rep +18 fadiga"
> "Turnê +R$3.615.132 +590 fãs +5 rep +90 fadiga"

**Usuário:** iteração de **balance** do jogo. **Encaminhamento:** no endgame (fãs altíssimos) os
valores explodem — um show de estádio (1 dia, 18 fadiga) rende ~1,3M e 1530 fãs (bilheteria =
15.000 × R$90). A turnê rende mais caixa mas custa 90 de fadiga e dá menos fãs. Falta **equilibrar
eficiência (retorno por fadiga/tempo)** entre show avulso e turnê, e provavelmente **conter a
escala** da bilheteria. Iteração de balance dedicada (0003 + 0014 + 0016).

## Outro ponto — arquitetura de UI (O1)
> "avaliar janelas diferentes para cada ação/conjunto de features, mantendo o estado entre elas
> (ref. A Story of a Band); ou ao menos dividir em mais colunas para não scrollar tanto"

**Encaminhamento:** retoma a candidata **UI Shell / Navegação** (Playtest 03 ponto 11). Duas
ambições: (a) **telas/abas** por área (Banda, Estúdio, Shows, Finanças, Equipe…) preservando o
estado (store já é central — o estado se mantém); (b) **paliativo**: layout **multi-coluna** para
reduzir o scroll vertical. Decisão de **design system (0006) + arquitetura de navegação**. O (b)
é barato e imediato; o (a) é estrutural.

## Candidatas / iterações emergentes
- **0017 Contracts and Salaries** (reforçada, ponto 1) — salário por atributos + contrato.
- **Cancelar ação** (ponto 2) — UX da 0014.
- **Tipos de descanso** (pontos 4/8) — 0014.
- **0013 slices 3 e 4** (pontos 5/6) — modificadores + motorista.
- **Ensaiar ↔ progressão de membros** (ponto 9) — 0015 entrosamento + 0007.
- **Balance pass** (pontos 3, 11) — variância no custo + escala show/turnê. 0003.
- **UI Shell / multi-coluna** (O1) — 0006 + navegação.
