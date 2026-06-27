# Feature 0016 - Venues and Shows (Planning)

## Problem
Hoje "Tocar show" (0014) é uma **ação genérica de 1 dia** com cachê/fãs/reputação fixos:
não há *onde* tocar, não há sensação de progressão geográfica, e a reputação não abre
lugares maiores. Os playtests pediram repetidamente:
- locais/cidades para o jogador **sentir para onde a carreira vai** (P03 7.1);
- **venda de ingressos** ligada à reputação/fãs (P03 7.2);
- **agenda/calendário** de shows e turnês (P03 7.3, P04 3.3);
- turnê como trajeto por **cidades/estados do Brasil**, começando no estado de origem
  (P01 ponto 10).

## Goals
- Dar **destinos** ao show: um catálogo de locais que se **desbloqueia com a reputação**
  (e/ou marcos), com capacidade/lotação e perfil próprios.
- Transformar o retorno do show em função de **local × público (fãs/reputação) × preço**
  do ingresso, em vez de um cachê fixo.
- Introduzir **agenda** (compromissos datados) para shows e turnês, dando planejamento.
- Estabelecer a base geográfica para a turnê (trajeto por cidades/estados a partir da origem).

## Initial scope
- Catálogo de **locais** (modelo `Venue`: nome, capacidade, gate de desbloqueio, região).
- **Venda de ingressos**: receita do show derivada de lotação × atratividade × preço.
- **Desbloqueio** por reputação (limiar) — ganchos para marcos (0011) ficam como extensão.
- **Agenda/calendário** de shows (e turnê) — modelo de compromisso datado.
- Integração com a 0014 (a ação de show passa a referenciar um `Venue`).

## Out of scope (por ora)
- Rivais disputando datas/locais (0004).
- Eventos de show ramificados (0009/0019).
- Logística fina de turnê (ônibus, hotel) e staff (0013) — só ganchos.

## Acceptance criteria
- Existe um catálogo de locais com desbloqueio por reputação, visível ao jogador.
- Tocar em um local maior, com mais fãs/reputação, **rende mais** (ingressos), e locais
  travados comunicam o requisito.
- O jogador consegue **agendar** um show/turnê numa data e o tempo respeita o compromisso.
- Tudo coberto por testes; números são placeholders de balance (0003).
