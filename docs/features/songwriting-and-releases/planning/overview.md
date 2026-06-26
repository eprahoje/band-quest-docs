# Feature 0015 - Songwriting and Releases (Planning)

## Problem
Hoje a "produção musical" é rasa: `compose` apenas incrementa um **contador inteiro**
de músicas (`songs`) e as ações de gravação (`record-demo`, `record-single`,
`record-album`) só consomem esse número. O jogador não controla **o que** está
criando, não consegue **consultar** o que já fez, e o "caprichado" só muda custo —
não há uma noção real de **qualidade** nem de **retorno de longo prazo** (royalties).
Isso esvazia a fantasia central de "construir uma discografia".

Levantado nos Playtests 01 (ponto 3) e 02 (pontos 5, 5.1, 5.2, e 6 para a receita).

## Goals
- Elevar **música** a objeto de primeira classe, com **metadados** (nome, gênero,
  tema) e uma **qualidade** derivada (não puramente aleatória).
- Definir a **cadeia de lançamento**: composição → (demo | single | álbum), com
  **regras de composição** (ex.: álbum exige X singles + Y músicas; demo exige mínimo).
- Dar um **inventário consultável** de músicas e lançamentos (a "janela" pedida).
- Definir a **estrutura de receita de longo prazo** (royalties/vendas por lançamento)
  — base para a futura "aba de Ganhos". Os números são da 0003.
- Tornar o **esforço/qualidade** um trade-off real (mais que custo): qualidade move
  fãs/reputação/royalties.

## Initial scope (proposta — refinar via questions)
- **Modelo de música:** `id`, `name`, `genre`, `theme`, `quality`, estado (composta /
  lançada e em quê).
- **Como nasce o metadado:** auto-gerado com opção de personalizar vs. input manual
  obrigatório (ver Q1).
- **Qualidade:** função de atributos da banda (0007) + esforço (0014) + variação leve
  (ver Q2).
- **Tipos de lançamento e requisitos:** demo, single, álbum — quantas músicas/singles
  cada um exige e o que cada um faz (ver Q3).
- **Receita de longo prazo:** royalties decrescentes por lançamento ao longo dos turnos
  (estrutura aqui; números na 0003) (ver Q4).
- **Inventário/janela:** lista consultável de músicas e lançamentos (ver Q5).

## Non-goals (nesta fase)
- Calibragem numérica fina de custos/ganhos/royalties (é da 0003).
- Interação de gênero/tema com **tendências de mercado** (0004/0008) — futuro.
- Aba de Ganhos completa na UI (consome a estrutura daqui + 0003; slice posterior).
- Charts/paradas de sucesso, prêmios e marcos de discografia (0011).

## Acceptance criteria
- Existe um modelo de música com metadados e qualidade definido e justificado.
- A cadeia composição → demo/single/álbum está especificada com regras claras.
- A estrutura de receita de longo prazo (royalties) está descrita (sem fixar números).
- O inventário consultável está descrito.
- As perguntas abertas estão resolvidas (nenhuma bloqueante) antes do handoff (G1).
