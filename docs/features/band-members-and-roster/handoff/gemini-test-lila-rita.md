# Handoff de teste — Geração de arte no Gemini (Lila & Rita)

**Objetivo:** testar a geração de ícones de personagem no Gemini (Nano Banana /
Gemini Pro 3.1) com 2 personagens, para comparar com os samples flat-vector já
feitos e decidir o produtor da arte.
**Status:** 🧪 Teste / experimento (não é produção final).

## Como usar
1. Cole cada prompt abaixo no Gemini (modo de geração de imagem).
2. Gere as duas variações (flat-vector e ilustrado) por personagem, se possível.
3. Avalie pelos critérios no fim deste arquivo.

## Contexto de estilo (design system)
- Jogo de gestão de banda, **UI dark**. Fundo do card escuro (`#16161d`).
- Avatar exibido em **círculo**, a ~56px no card e até ~180px ampliado.
- Identidade **atemporal/multi-era** (evitar roupa/elementos que datem uma década).
- Identidade **brasileira** e diversa.
- Paleta de acentos: magenta `#ff5c8a`, âmbar `#f5a623`, carmim `#e2473b`,
  verde `#46d39a`, azul `#5aa9ff`.

---

## Personagem 1 — Lila Tavares (Vocal · acento magenta #ff5c8a)
**Descrição:** mulher brasileira, negra, cabelo black power volumoso, pele morena
escura, sorriso largo e olhar magnético; vocalista/líder, performer de palco.

**Prompt A (flat vector — comparável ao sample):**
> Flat vector character avatar, bust and shoulders, front-facing, centered,
> simple geometric shapes, minimal facial detail, clean and readable at small
> sizes (~56px). Subject: a Brazilian Black woman with a voluminous afro (black
> power), deep brown skin, warm wide magnetic smile; rock band lead singer.
> Accent color magenta #ff5c8a on her garment. Transparent background, square 1:1.
> Timeless/era-neutral styling. High contrast for a dark UI. No text, no logo.

**Prompt B (ilustrado — para comparar riqueza):**
> Stylized flat illustration portrait (bust), Brazilian Black woman, voluminous
> afro, deep brown skin, confident warm smile, rock singer energy; limited palette
> with magenta #ff5c8a accent; transparent background; square; era-neutral; clean
> shapes suitable for a game avatar. No text.

---

## Personagem 2 — Rita Camargo (Guitarra · acento âmbar #f5a623)
**Descrição:** mulher brasileira, pele clara, cabelo escuro liso preso, expressão
focada e intensa, sobrancelhas anguladas; guitarrista virtuosa (estilo Polyphia).

**Prompt A (flat vector — comparável ao sample):**
> Flat vector character avatar, bust and shoulders, front-facing, centered,
> simple geometric shapes, minimal facial detail, readable at ~56px. Subject: a
> Brazilian woman, light skin, dark sleek hair pulled back, intense focused
> expression, angular eyebrows; virtuoso rock guitarist. Accent color amber
> #f5a623 on her garment. Transparent background, square 1:1. Timeless styling.
> High contrast for a dark UI. No text, no logo.

**Prompt B (ilustrado — para comparar riqueza):**
> Stylized flat illustration portrait (bust), Brazilian woman, light skin, sleek
> dark hair tied back, focused intense gaze, guitarist; limited palette with amber
> #f5a623 accent; transparent background; square; era-neutral; clean shapes for a
> game avatar. No text.

---

## Saída esperada
- Imagem **quadrada (1:1)**, idealmente com **fundo transparente** (PNG).
- Enquadramento **busto/ombros**, rosto centralizado.
- Sem texto/logo embutido.

## Critérios de avaliação (comparar com os samples flat-vector)
- [ ] **Consistência entre os dois** (parecem do mesmo "kit"?).
- [ ] **Transparência** real (sem fundo opaco indesejado).
- [ ] **Aderência de cor** ao acento indicado.
- [ ] **Legibilidade a 56px** (detalhe não some).
- [ ] **Identidade brasileira** e atemporalidade preservadas.
- [ ] **Convertibilidade para vetor** (se o destino final for SVG).
- [ ] Esforço de limpeza/pós-processamento necessário.

## Observação
Nano Banana/Gemini gera **raster (PNG)**, não SVG. Se a direção final for vetor,
some o custo de vetorizar + alinhar estilo entre os 15. Use este teste para pesar
riqueza ilustrativa (vantagem do Gemini) contra precisão técnica/consistência
(vantagem do flat-vector autoral).
