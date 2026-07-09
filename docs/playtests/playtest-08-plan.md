# Plano do Playtest 08 (proposta — 2026-07-09)

Roteiro de validação para a próxima sessão de jogo. Cobre tudo que foi entregue
**depois do Playtest 07 (2026-06-28)** e ainda não passou por validação humana, mais
duas pendências de sessões anteriores que dependiam de mudança de modelo.

## O que mudou desde o Playtest 07

| Entrega | Log | Status de validação |
| --- | --- | --- |
| UI Shell — HUD fixo + abas por área | 0020 [0.2.0] | **nunca testada** (prioridade) |
| Fix do drift do design system (dropdowns atrás das abas) | 0006 [0.8.1] | nunca testada |
| Tipos de descanso + Férias com cooldown | 0014 [0.15.0] | nunca testada |
| Nome da música na composição | 0015 [0.10.0] | nunca testada |
| Cancelar show com aviso + penalidade | 0016 [0.7.0] | nunca testada |
| Balance da turnê (cachê ∝ fãs) | 0014 [0.13.0] | pendente de sessão dedicada |

Sugestão de partida: **modo temporizado, 10 anos**, banda nova (para passar pelo
early game com os gates de equipe e locais no caminho natural).

---

## Bloco 1 — UI Shell e navegação (0020) — PRIORIDADE

O objetivo é validar a estrutura antes dos detalhes: se a navegação não funciona,
o resto fica contaminado.

1. **Tour pelas abas**: passe por Visão · Banda · Estúdio · Shows · Equipe · Finanças.
   - Cada área está onde você esperava? Algum conteúdo parece "na aba errada"?
2. **HUD fixo**: em qualquer aba, confira que stats, calendário e o botão Avançar
   estão sempre visíveis e funcionais (avance o tempo estando em abas diferentes).
3. **Estado preservado**: inicie uma ação, troque de aba e volte — o painel "Em
   andamento" (Visão) e os cards devem refletir o estado sem perder nada.
4. **Acontecimentos fora da aba ativa**: deixe um show agendado ou royalties correndo
   e fique numa aba que não é a Visão quando o evento disparar.
   - Você sentiu falta de um aviso/realce na aba? (candidato conhecido: realce de
     pendências por aba — confirmar se dói de verdade.)
5. **Scroll**: compare a sensação com a tela única antiga. Alguma aba ainda ficou
   comprida demais?

## Bloco 2 — Compose chooser: dropdowns + nome (0006 [0.8.1] + 0015 [0.10.0])

6. Na aba Estúdio, clique em Compor:
   - **Dropdowns de gênero/tema abrem NA FRENTE** das abas/cards (era o bug do
     z-index — fix 0.8.1). Teste com o painel em posições diferentes de scroll.
   - O campo **Nome** já vem preenchido com um título sugerido.
7. Edite o nome, confirme, conclua a composição:
   - A música nasce com o nome escolhido e o acontecimento cita o título.
8. Use o **🎲 Aleatório**: re-sorteia nome, gênero e tema juntos.
   - O comportamento de re-sortear o NOME junto agrada, ou você preferiria que o 🎲
     preservasse um nome já editado à mão?
9. Deixe o nome em branco e confirme — deve cair no título autogerado (sem erro).
10. Confira que a **edição inline** na aba Músicas continua funcionando (nome/estilo/tema).

## Bloco 3 — Tipos de descanso e Férias (0014 [0.15.0])

11. Na aba Banda, confira o card **Descansar** com 3 opções: Folga (2d/−12),
    Descanso (5d/−30), Prolongado (10d/−60).
    - As três durações fazem sentido no ritmo do jogo? Alguma sobra/falta?
12. Card **Férias** (30d): tire férias com a banda bem cansada.
    - O preview de recuperação (−300) assusta/confunde? (número é placeholder)
    - Durante as férias os custos mensais continuam correndo — o trade-off
      (1 mês parado + salários) é perceptível e justo?
13. Ao voltar das férias, tente tirar férias de novo:
    - O card deve travar com "Disponível de novo em N dia(s)".
    - Cooldown de 1 ano parece certo? (alternativas: 6 meses, ou liberar por marco)
14. **Feel geral da fadiga** com as novas opções: a Folga curta resolve o dia a dia?
    O descanso deixou de ser "sempre a mesma escolha"?

## Bloco 4 — Cancelar show com consequência (0016 [0.7.0])

15. Agende um show para **1 mês** e cancele em seguida:
    - O diálogo deve avisar "sem penalidade" e nada aparece na timeline.
16. Agende para **1–2 semanas** e cancele:
    - O diálogo mostra a multa e a reputação exatas ANTES de confirmar (variante
      vermelha/danger) e o valor cobrado bate com o anunciado.
    - Evento "cancelado em cima da hora" na timeline com chips.
17. Calibragem: janela de 14 dias e multa ∝ cachê do local parecem justas?
    Cancelar um show de estádio em cima da hora deveria doer mais que isso?

## Bloco 5 — Turnê vs shows agendados (0014 [0.13.0] — pendência antiga)

18. Com fãs acumulados (meio de jogo), compare numa mesma janela de tempo:
    - Uma **mini-turnê** vs a mesma janela preenchida com shows agendados no melhor
      local liberado. Qual rende mais por dia e por ponto de fadiga?
    - A turnê ficou competitiva ou o rework (turnê = trajeto de shows, P07 ponto 3)
      continua urgente?

## Bloco 6 — Observação livre (balance em aberto, sem roteiro)

Sem passos — só anote se doer:

- **Equipe cedo demais** (P07 ponto 2): ainda dá para comprar todos os cargos com
  uma tacada de dinheiro?
- **Estádio no endgame** (P06 ponto 11): a bilheteria de um show de estádio ainda
  achata todo o resto?
- **Overexertion**: com Folga/Férias disponíveis, estourar o limite virou escolha
  consciente ou continua acontecendo sem querer?
- **Royalties/Ganhos**: a aba Finanças conta a história da receita de forma legível?

---

## Como registrar

Como nos anteriores: anote os pontos numerados (verbatim, sem filtrar), inclusive
os "ok, sem problema" dos blocos 1–5 — validação positiva também fecha pendência.
O resultado vira `playtest-2026-07-NN.md` + triagem no roadmap, e os pontos de
cada bloco alimentam os logs das features donas (0020, 0006, 0014, 0015, 0016).
