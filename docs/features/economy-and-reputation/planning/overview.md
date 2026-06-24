# Feature 0003 - Economia e Reputação (Planejamento)

## Problema
Formalizar os sistemas de **dinheiro** e **reputação** impactados por escolhas e
resultados. Além de reger o loop, a 0003 virou o **contrato numérico** consumido por
outras features: a nota e a derrota da **0010**, os bônus da **0011**, os custos/
efeitos da **0012** e os custos da **0013** dependem da calibragem definida aqui.

## Objetivos
- Definir as **variáveis e faixas** de economia e reputação.
- Definir as **dinâmicas** (como cada métrica sobe/desce e ao longo do tempo).
- Definir a **forma** das fórmulas que outras features consomem (nota, derrota,
  recompensas, custos) — os valores concretos ficam numa iteração de balance.
- Vincular decisões do jogador aos impactos nesses indicadores.

## Entidades principais
- **Dinheiro (caixa, R$):** receitas, custos, investimentos, saldo. Pode ficar
  **negativo (dívida)** — base para a falência da 0010.
- **Reputação (0–100):** percepção de público/mercado. **Decai se a banda fica
  inativa** (sem shows/lançamentos por um intervalo).
- **Fãs (≥ 0):** base acumulada; entrada principal da nota e da reputação.
- **Fadiga (0–100):** acima do limiar bloqueia ações; piso prolongado → dissolução.

## Cadência (turno↔calendário)
- O turno **não** equivale a um ano. Mapeia uma unidade de **calendário mais
  granular** (semana/mês — a fixar com a 0008).
- **Ações têm duração variável em turnos** (ex.: gravar álbum = N turnos conforme
  qualidade/produtor; turnê = N turnos). Custos recorrentes (salários, decay)
  acumulam **por turno**.
- A unidade exata e o **modelo de duração de ações** são desdobramento cross-cutting
  (ver `questions.md`; toca 0008 e o core loop).

## Non-goals (nesta fase)
- Os valores concretos (tabelas de custos/ganhos/limiares) — vão para uma iteração
  de balance dedicada, mais perto da implementação.
- A linha do tempo tecnológica e a unidade de calendário em si (é da 0008).
- A UI de loja/contratações (é da 0012/0013).

## Critérios de aceite
- Variáveis, faixas e dinâmicas de dinheiro e reputação estão definidas.
- A forma das fórmulas consumidas por 0010/0011/0012/0013 está descrita.
- A relação causa→efeito entre decisões e indicadores está clara.
