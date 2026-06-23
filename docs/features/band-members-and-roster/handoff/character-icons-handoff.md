# Handoff — Ícones dos personagens iniciais (Feature 0007)

**Para:** agente(s) responsável(is) por produzir os ícones/ilustrações dos
membros iniciais da banda.
**Status:** 🟢 PRONTO PARA PRODUÇÃO. Cast com identidade brasileira (15
personagens), restrições de estilo fechadas e briefing visual por personagem.

---

## Contexto
Band Quest é um RPG de gestão de banda de rock. Cada membro aparece num **card**
(ver [feature 0006 — member-card](../../art-direction-and-visual-system/README.md))
com um avatar circular. Estes ícones são esses avatares.

## Restrições de estilo (fechadas — herdadas da 0006)
- **Ilustração vetorial simples, estática, uma pose fixa por personagem.** Sem
  animação, sem variações por humor/fadiga.
- **Atemporal / multi-era** — não amarrar a uma década específica (evitar
  elementos que datem o personagem numa única época).
- **Enquadramento:** busto/ombros para cima, centralizado, olhando para frente.
- **Formato de entrega:** `SVG` vetorial, `viewBox` quadrado (ex.: `0 0 48 48`),
  fundo transparente, sem texto embutido.
- **Legibilidade em tamanho pequeno:** o avatar é exibido a ~56px no card e
  ~26–32px em listas. Deve ler bem nesses tamanhos.
- **Paleta:** usar os tokens do design system
  ([`design-system/tokens.css`](../../../../design-system/tokens.css)). Fundo do
  card é escuro (`--bq-bg-surface`); cada membro pode ter uma cor de acento
  vinda dos tokens de stat (`--bq-stat-rep/-cash/-fans/-fatigue`) ou de marca
  (`--bq-spotlight`, `--bq-ember`). Garantir contraste sobre fundo escuro.
- **Referência viva:** o card e a paleta estão no projeto Claude Design
  "Band Quest — Design System".

## Identidade brasileira
- O cast tem **cara de Brasil**: nomes brasileiros e diversidade do país
  (diferentes tons de pele, cabelos e traços regionais, incluindo a diáspora
  nipo-brasileira). Manter essa diversidade na ilustração.
- A brasilidade está na **identidade do personagem**, não na época: o estilo
  segue atemporal/multi-era (evitar amarrar a uma década).

## Naming e entrega
- Um arquivo por personagem: `member-<slug>.svg` (ex.: `member-lila-tavares.svg`).
- Entregar em: `band-quest-game/src/assets/members/` (a confirmar na implementação).

---

## Cast inicial — 15 ícones (5 funções × 3 opções)

**Total a produzir: 15 SVGs**, um por personagem: `member-<slug>.svg`.
Perfis de atributo e dados de jogo completos em
[`../planning/design.md`](../planning/design.md) — a tabela abaixo traz o que
importa para a arte (função, acento, vibe).

| # | Nome | Slug | Função | Cor de acento (token) | Vibe |
|---|------|------|--------|-----------------------|------|
| 1 | Lila Tavares | `lila-tavares` | Vocal | `--bq-stat-fans` | Performer magnética, dona do palco |
| 2 | Juçara Bonfim | `jucara-bonfim` | Vocal | `--bq-ember` | Letrista enigmática, voz peculiar |
| 3 | Dílson Prado | `dilson-prado` | Vocal | `--bq-info` | Vocal técnico, postura confiante |
| 4 | Rita Camargo | `rita-camargo` | Guitarra | `--bq-spotlight` | Shredder de precisão, intensa |
| 5 | Brenno Sales | `brenno-sales` | Guitarra | `--bq-stat-cash` | Criativo, texturas e experimentação |
| 6 | Téo Vasconcelos | `teo-vasconcelos` | Guitarra | `--bq-stat-fans` | Showman de palco, expansivo |
| 7 | Nara Siqueira | `nara-siqueira` | Baixo | `--bq-stat-cash` | Groove sólido, presença firme |
| 8 | Iuri Mendes | `iuri-mendes` | Baixo | `--bq-info` | Melódico, introspectivo |
| 9 | Caíque Romero | `caique-romero` | Baixo | `--bq-stat-fatigue` | Energia de estrada, incansável |
| 10 | Tuca Andrade | `tuca-andrade` | Bateria | `--bq-spotlight` | Precisão, foco, concentrado |
| 11 | Janaína Costa | `janaina-costa` | Bateria | `--bq-ember` | Força bruta, potência |
| 12 | Mari Sato | `mari-sato` | Bateria | `--bq-stat-cash` | Criativa, poliritmia |
| 13 | Vavá Coutinho | `vava-coutinho` | Teclado | `--bq-info` | Técnico, cerebral |
| 14 | Cacá Lemos | `caca-lemos` | Teclado | `--bq-stat-fans` | Carisma synth-pop |
| 15 | Aílton Reis | `ailton-reis` | Teclado | `--bq-spotlight` | Experimental, visionário |

> Nomes/descrições podem ainda ser ajustados pelo usuário. Se mudar, atualizar
> também `../planning/design.md` (que tem os atributos de jogo).

## Briefings de produção por personagem
Use cada bloco como descrição/prompt do personagem. Aplicar a todos as
**restrições de estilo** acima (vetorial, busto, atemporal, fundo transparente,
contraste sobre fundo escuro, cor de acento indicada).

1. **Lila Tavares** (Vocal) — Mulher negra, cabelo black power volumoso, sorriso
   largo e olhar magnético; postura de quem domina o palco.
2. **Juçara Bonfim** (Vocal) — Mulher de traços nordestinos, cabelo trançado,
   expressão introspectiva e enigmática; ar de poeta.
3. **Dílson Prado** (Vocal) — Homem pardo, cabelo curto, queixo erguido, postura
   confiante de vocalista técnico.
4. **Rita Camargo** (Guitarra) — Mulher branca, cabelo escuro liso preso, olhar
   focado e intenso; precisão de guitarrista virtuosa.
5. **Brenno Sales** (Guitarra) — Homem jovem, cabelo cacheado médio, expressão
   curiosa e experimental.
6. **Téo Vasconcelos** (Guitarra) — Homem expansivo, cabelo comprido, sorriso de
   showman, gesto teatral.
7. **Nara Siqueira** (Baixo) — Mulher negra retinta, cabelo raspado nas laterais,
   expressão calma e firme; presença sólida.
8. **Iuri Mendes** (Baixo) — Homem magro, óculos, olhar introspectivo e melódico.
9. **Caíque Romero** (Baixo) — Homem de pele bronzeada de estrada, bandana,
   energia incansável no olhar.
10. **Tuca Andrade** (Bateria) — Homem pardo, cabelo curto, expressão concentrada
    e precisa.
11. **Janaína Costa** (Bateria) — Mulher de presença forte, cabelo preso para
    trás, expressão intensa de potência.
12. **Mari Sato** (Bateria) — Mulher nipo-brasileira, cabelo liso curto, ar
    criativo e atento ao ritmo.
13. **Vavá Coutinho** (Teclado) — Homem mais velho, barba grisalha, olhar cerebral
    e técnico.
14. **Cacá Lemos** (Teclado) — Mulher vibrante, cabelo colorido, carisma
    synth-pop, sorriso aberto.
15. **Aílton Reis** (Teclado) — Homem negro, dreads, expressão experimental e
    visionária.

## Definition of done (por ícone)
- [ ] SVG vetorial, viewBox quadrado, fundo transparente.
- [ ] Busto/ombros, centralizado, leitura boa a 32–56px.
- [ ] Estilo coerente com os demais (mesma linguagem visual atemporal).
- [ ] Usa a cor de acento do personagem com contraste sobre fundo escuro.
- [ ] Nome do arquivo `member-<slug>.svg`, entregue em `band-quest-game/src/assets/members/`.
