# Feature 0003 - Economia e Reputação (Log)

## [0.1.0] - 2026-06-18T00:00:00Z

### Input
- Primeira consolidação do fluxo de documentação da feature.

### Summary
- Planejamento inicial, refinamento 01 e perguntas bloqueantes registrados.

### Open questions
- Fórmulas iniciais.
- Custos-base.

### Next step
- Responder `questions.md` antes da próxima iteração.

## [0.2.0] - 2026-06-23T00:00:00Z

### Input
- Reposicionamento da 0003 como contrato numérico (alimenta 0010/0011/0012/0013).
  Usuário decidiu: caixa pode ficar negativo (dívida); reputação decai se inativa;
  turno é um calendário granular com ações de duração variável em turnos (não
  turno=ano); fechar estrutura/fórmulas agora e números numa iteração de balance.

### Summary
- Feature modernizada ao padrão SDD; `overview.md` reescrito (papel de contrato,
  cadência granular, non-goals).
- Criado `iteration-02.md` com as decisões e a forma das fórmulas consumidas.
- `questions.md` reformatado (padrão A/B/C/X); Q1/Q2/Q0 resolvidas; abertas Q3
  (calendário + duração de ações) e Q4 (fontes de receita/custo).
- `decomposition.md` corrigido: removida a numeração obsoleta "0013/0014/0015"
  (0013 agora é Staff and Crew); sub-modelos passam a ser internos.
- Handoff imediato registrado: remover o trava-zero do caixa em `game.ts`.

### Open questions
- Q3 (unidade de calendário + modelo de duração de ações — cross-cutting 0008/core
  loop) e Q4 (fontes de receita/custo). Não bloqueiam a estrutura.

### Next step
- Decidir Q3/Q4. Avaliar feature de core loop/ações para a duração multi-turno.
  Depois, abrir a iteração de balance com os valores concretos.

## [0.3.0] - 2026-06-23T00:00:00Z

### Input
- Usuário decidiu Q3/Q4: turno = semana (~52/ano); o modelo de duração de ações vira
  feature própria (0014 - Core Loop and Actions); fontes = básicas + royalties +
  patrocínios.

### Summary
- Q3/Q4 resolvidas e movidas para "Resolved Questions"; criado `iteration-03.md`.
- Registradas as fontes de receita/custo e a cadência semanal.
- Feature 0014 - Core Loop and Actions scaffoldada (dona da mecânica de ações e da
  duração em turnos); registrada nos índices/roadmap.

### Open questions
- Nenhuma bloqueante na 0003. Pendem a 0014 e a iteração de balance (valores).

### Next step
- Refinar a 0014; depois abrir a iteração de balance da 0003 com os números.

## [0.4.0] - 2026-06-23T00:00:00Z

### Input
- Implementação no `band-quest-game` do ajuste estrutural desta feature (passo 1 da
  virada para implementação).

### Summary
- `game.ts`: removido o trava-zero do caixa — o caixa agora pode ficar **negativo
  (dívida)**, habilitando a futura condição de falência da 0010.
- Introduzido o calendário **turno = semana** (`WEEKS_PER_YEAR = 52`, computed
  `calendar` ano/semana).
- Teste de caixa atualizado para validar dívida; mantido o piso de fãs em zero.
- Custos recorrentes/decay de reputação NÃO implementados ainda (dependem da iteração
  de balance).

### Open questions
- Nenhuma bloqueante. Falta a iteração de balance (valores).

### Next step
- Abrir a iteração de balance da 0003 (custos/ganhos/durações/decay/limiares) agora
  que o motor de ações da 0014 existe para validar os números jogando.

## [0.5.0] - 2026-06-24T00:00:00Z

### Input
- Feedback do Playtest 01 (ver `docs/playtests/playtest-2026-06-24.md`).

### Summary
- Backlog de balance registrado para a iteração futura:
  - Reputação alta demais cedo e com pouco impacto — equilibrar ganhos/perdas
    (ponto 7).
  - Preços/requisitos por ação visíveis + eventos relatando impactos (ponto 4).
  - Tornar visível a **manutenção** recorrente da banda (dinheiro/reputação/fãs)
    (ponto 8).
  - Granularidade do turno (semana → dia) afeta a calibragem (ponto 1).

### Open questions
- Nenhuma nova bloqueante.

### Next step
- Incorporar estes itens ao abrir a iteração de balance.