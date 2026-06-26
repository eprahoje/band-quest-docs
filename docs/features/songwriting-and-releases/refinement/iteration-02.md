# Feature 0015 - Songwriting and Releases (Refinement 02)

Origem: **Playtest 03 (2026-06-25)**, pontos 4, 4.1, 2 e 3. Refina o comportamento das
slices já entregues (1, 3, 5) — não cria slices novas de escopo, ajusta as existentes.

## Decisions

### D6 — Seleção explícita de faixas ao gravar (Playtest 03, pontos 4/4.1)
- **Problema:** hoje a gravação consome automaticamente as músicas mais antigas
  (`availableSongs.slice(0, n)`), ignorando a qualidade. O jogador gravou uma Q69 tendo
  uma Q71 disponível.
- **Decisão:** o jogador **escolhe as músicas** que entram em cada gravação.
  - UI: ao clicar a opção de esforço de uma ação de gravação, abre um **painel de seleção
    inline** (não modal) listando as músicas disponíveis com **nome + qualidade**; o
    jogador marca **exatamente** a quantidade exigida e confirma. Para o **álbum**, também
    seleciona os **2 singles** a absorver.
  - Store: `startAction(id, effortLabel?, selection?)` ganha um 3º parâmetro opcional
    `{ songIds?, singleIds? }`. Sem seleção, mantém o auto-pick (compatibilidade/testes).
    Com seleção, valida que a quantidade bate com o requisito e que os ids estão
    disponíveis.
- **Não-objetivo:** ordenar/priorizar automaticamente por qualidade — a escolha é do
  jogador.

### D7 — Edição de metadado (Playtest 03, pontos 2/3)
- **Problema:** a D1 prometeu metadado **editável**, mas não há UI; não dá para renomear
  músicas nem lançamentos.
- **Decisão:** edição **inline na aba Músicas** (nome, estilo/gênero, tema) e **renomear
  lançamentos** (título) na aba Lançamentos. Um botão de editar por linha revela campos;
  salvar persiste no store (`editSong`, `renameRelease`).
- **Por que não um prompt ao concluir a composição:** interromper cada `compose` para
  nomear cansaria numa sessão de 10–30 anos (centenas de músicas). O metadado segue
  **autogerado** e o jogador edita quando quiser — cobre o pedido sem fricção.

## Questions
- Nenhuma bloqueante. (Filtro/ordenação avançada da biblioteca e pools maiores de nomes
  ficam para iterações futuras — Playtest 03 pontos 10.1 e 5.)

## Checklist result
- Ajustes de comportamento das slices 1/3/5 definidos (D6, D7). Implementação:
  (a) seleção de faixas (store + GameView), (b) edição de metadado (store + SongLibrary).
