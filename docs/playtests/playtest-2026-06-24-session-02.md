# Playtest 02 — 2026-06-24

Segundo playtest, após o Balance pass 1 (custos mensais, reputação escassa + decay,
esforço modula resultado). Feedback do usuário, preservado e mapeado.

## Resumo da classificação

| # | Tema | Tipo | Dona / candidata | Status |
|---|------|------|------------------|--------|
| 1 | Reputação começa em 0 e é ilimitada (sem teto 100) | Modelo/balance | 0003 | ✅ feito |
| 2 | Salário por reputação + atributos, cresce com a evolução do membro | Nova feature | Cand. 0017 | documentado |
| 2.1 | Cards da banda mostrarem o salário | UX | 0006/0007 | documentado |
| 2.2 | Contratos (1 ano, renovação aumenta salário + exigências) | Nova feature | Cand. 0017 | documentado |
| 3 | Ensaiar → pontos de evolução do membro; custa estúdio até comprar o próprio | Nova feature | 0007 (progressão) + 0012 (estúdio) | documentado |
| 4 | Abas recolhíveis/expansíveis para melhor visualização | UX | 0014 (UI) | documentado |
| 5 | Janela para consultar músicas gravadas | Nova feature | Cand. 0015 | documentado |
| 5.1 | Álbum exige X singles + X músicas | Nova feature | Cand. 0015 | documentado |
| 5.2 | Diferença single/álbum normal × caprichado além do custo | Design | 0015 / 0014 | parcial (outcomeModifier) |
| 6 | Aba de "Ganhos" (royalties, vendas) espelhando a de Custos | Nova feature | 0003 + 0015 | documentado |
| 7 | Mostrar o ano real (jogo começa em 2000) | UX | 0008/0014 | ✅ feito (display) |
| 7.1 | Tela de contextualização histórica ao dar start | Nova feature | 0005 (start) + 0009 | documentado |
| 8 | Passar o tempo restaura um pouco de energia | Balance | 0014 | ✅ feito |
| 9 | Acontecimentos registram os efeitos (deltas) da ação | UX | 0014 | ✅ feito |
| 10 | Escolher o tamanho da sessão no setup | Feature | 0010 + 0005d | próxima slice |

## Pontos (input original preservado)

### 1. Reputação ilimitada, começando em 0
"A reputação deve começar em 0. Pensando em features futuras (loja e outros
desbloqueios) a reputação não deve se limitar em 100, e sim ser Reputação = X, indo
subindo e subindo."
**✅ Feito:** reputação inicial 0; removido o teto (mantém piso 0). StatsPanel deixa
de mostrar "/100". **Atenção de balance:** o salário mensal usa `(1 + rep/100)` — com
reputação ilimitada o salário cresce junto (alinhado ao ponto 2); reavaliar no balance.

### 2. Salário por reputação + atributos, crescendo com a evolução
"O salário pode ser atrelado à reputação e aos atributos de cada personagem. À medida
que o personagem evolui, o salário individual dele também."
- **2.1** Evoluir o design dos cards para conter o salário.
- **2.2** Feature de contrato: a banda começa com contrato de 1 ano; ao renovar, o
  salário aumenta e podem vir exigências.
**Encaminhamento:** candidata **0017 - Contracts and Salaries** (salário individual
por atributos+reputação, contratos, renovação/exigências). Depende da progressão de
membros (0007) para o "evoluir". Card com salário entra junto (0006/0007).

### 3. Ensaiar rende evolução, não reputação
"Ensaiar deve render pontos de evolução para os membros (não reputação), e no começo
custar dinheiro (aluguel de estúdio) até o jogador comprar o próprio estúdio."
**Encaminhamento:** redefine a ação `rehearse` (0014) para conceder XP de membro →
exige **progressão de membros** (0007, hoje adiada) e **estúdio** como item/upgrade
(0012). Conjunto a tratar junto da 0017/0007.

### 4. Abas recolhíveis/expansíveis
"Uma feature onde o jogador pode recolher ou mostrar as abas, melhorando a
visualização e diminuindo a quantidade de informações ao mesmo tempo."
**Encaminhamento:** UI da 0014 — painéis colapsáveis (Custos, Banda, Em andamento,
Acontecimentos). Casa com a timeline infinita (Playtest 01, ponto 12).

### 5. Janela de músicas + cadeia de lançamento
"Uma janela onde o jogador visualiza as músicas que gravou, consultando quando
quiser."
- **5.1** Para gravar o álbum, exigir um número X de singles e X de músicas.
- **5.2** Qual a diferença do single/álbum normal para o caprichado além do custo?
**Encaminhamento:** candidata **0015 - Songwriting and Releases** — modelo de música
(nome/gênero/tema), inventário consultável, cadeia composição→single→álbum (com
mínimos), e o que "caprichado" muda (qualidade → fãs/royalties de longo prazo, não só
custo). Hoje o `outcomeModifier` já dá mais fãs/reputação ao caprichado; aprofundar.

### 6. Aba de Ganhos
"Assim como a aba de custos, ter uma aba de Ganhos, reportando royalties, vendas etc."
**Encaminhamento:** exige um sistema de **receita rastreada** (royalties de catálogo,
vendas, cachês) — 0003 + 0015. Painel de Ganhos espelhando o de Custos.

### 7. Mostrar o ano histórico
"Começamos no ano 1, mas que ano? Se o jogo começa nos anos 2000, reportar isso."
- **7.1** Tela de contextualização histórica ao apertar start.
**✅ Feito (display):** o calendário passa a mostrar o ano real (início em **2000**).
**Encaminhamento (7.1):** tela de contexto histórico no start → feature 0005 + sabor
da 0009.

### 8. Passar o tempo restaura energia
"Ao passar um dia sem fazer nada, restaurar ao menos um pouco da energia — hoje não
acontece nada."
**✅ Feito:** recuperação passiva leve de fadiga por dia avançado.

### 9. Acontecimentos com efeitos
"Os acontecimentos têm que registrar os efeitos que a ação/consequência teve."
**✅ Feito:** eventos de conclusão de ação passam a listar os deltas aplicados
(ex.: cachê, fãs, reputação, fadiga).

### 10. Escolher o tamanho da sessão no setup
"Já podemos implementar no setup a possibilidade de o jogador escolher o tamanho da
sessão."
**Encaminhamento:** próxima slice — seleção de modo/duração na StartView (0005d),
consumindo os modos da 0010 (10/20/30 anos + livre). Pareia naturalmente com o
fim de sessão da 0010 (nota/derrota).
