# Feature 0005 - Start Screen and Onboarding (Refinement 04)

## Foco da Iteração
Incorporar as decisões de sistema visual da feature 0006 (Art Direction and
Visual System) nas telas de start screen e criação de banda.

## Decisions

### Animação do menu inicial
A "animação simples no menu" decidida em iteration-01 é compatível com o
princípio "MVP estático" da feature 0006. A distinção é:
- **Fora de escopo (0006):** sprites, pixel art, ilustração animada de personagens.
- **Dentro de escopo (0005):** animação de interface — transição de tela, fade,
  loop de logo. Nenhum asset de arte original necessário.
- Decisão mantida: o menu inicial terá uma animação leve de UI (ex: fade-in
  do logo ou transição de elementos). Implementação via CSS/JS puro.

### Tela de criação de banda — avatar dos membros
Na tela de montagem da banda (escolha dos integrantes iniciais), cada membro
é representado por uma **ilustração vetorial estática**, uma pose fixa por
personagem, sem animação — conforme decidido em 0006, iteration-02.
- O avatar não varia por humor, fadiga ou status: esses estados são exibidos
  apenas nos atributos numéricos ao lado do card.
- A produção do avatar é um asset de arte (ilustração vetorial). Pode ser
  placeholder (iniciais coloridas) no primeiro build jogável, substituído
  por arte final em sprint posterior.

### Telas de gênero e background (Traços de Origem)
As opções de gênero musical e Traços de Origem são apresentadas como **cards
com ícone da biblioteca de ícones (Tabler/Lucide) + nome + descrição curta**.
Nenhuma tela de seleção depende de arte original — somente tipografia e ícones.

## Questions
- Sem perguntas abertas nesta iteração.

## Checklist result
- [x] Scope reviewed.
- [x] Questions updated.
- [ ] Handoff reviewed.
