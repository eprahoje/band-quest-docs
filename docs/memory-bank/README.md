# Memory Bank

Esta pasta contém o contexto válido para **qualquer** sessão de IA no projeto
Band Quest — diferente de `docs/features/`, que contém specs válidas apenas
para a tarefa/feature específica em curso.

## Arquivos

- [`product.md`](product.md) — visão de produto, objetivo do jogo, público.
- [`architecture.md`](architecture.md) — decisões de arquitetura que atravessam
  múltiplas features (ex: estratégia visual definida na feature 0006).
- [`iteration-playbook.md`](iteration-playbook.md) — rulebook para iterações
  de feature lideradas por agentes (migrado de `docs/agents/`).
- [`new-feature-bootstrap.md`](new-feature-bootstrap.md) — guia operacional
  para criar novas features (migrado de `docs/agents/`).

## Relação com AGENTS.md

`AGENTS.md`, na raiz do repositório, é a "constituição" do projeto: contém as
regras de processo que a IA deve seguir (estrutura de features, formato de
log, regras de integridade). Esta pasta complementa `AGENTS.md` com contexto
de produto, arquitetura e guias operacionais — não duplica regras de processo.
