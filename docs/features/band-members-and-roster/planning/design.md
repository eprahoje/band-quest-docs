# Feature 0007 - Band Members and Roster (Design)

Contrato de dados e regras para a implementação em `band-quest-game`.

## Componentes afetados
- `stores/game.ts` — estende `BandMember` e adiciona regras de composição.
- `MemberCard.vue` (novo) — consome o card visual da 0006.
- Fluxo de criação da banda (0005) — seleção do roster a partir do cast.

## Modelo de dados

### Função (role)
```
type MemberRole = 'vocal' | 'guitar' | 'bass' | 'drums' | 'keys'
```
> Projetado para crescer (DJ/Sampler etc.) — tratar como string union extensível.

### Membro
```
interface BandMember {
  id: string
  characterId: string        // referência ao personagem do cast
  name: string
  role: MemberRole
  attributes: {
    technique: number        // Técnica   (0–100)
    charisma: number         // Carisma   (0–100)
    creativity: number       // Criatividade (0–100)
    energy: number           // Energia   (0–100)
  }
  accentColor: string        // token do design system (ex.: var(--bq-stat-fans))
  iconRef: string            // member-<slug>.svg
}
```
Atributos são **fixos por personagem** nesta feature (sem progressão).

## Regras de composição (validação do roster)
- Tamanho: **3 a 5** membros (cap de 5, projetado para ser elevável).
- **Vocal:** opcional, **máx. 1** (não repete).
- **Instrumentos** (guitar/bass/drums/keys): **podem repetir**.
- **Mínimo 3 instrumentistas.**
- **Bateria obrigatória** (≥ 1 baterista).
- Banda sem vocal é válida (instrumental).

## Trade-offs de tamanho (direção — números na 0003)
- Banda menor (3): menos acesso a recursos, porém menos sobrecarga de gestão.
- Banda maior (5): mais capacidade, porém mais custo/gestão.
- A calibragem concreta (valores) é responsabilidade da feature 0003.

## Cast inicial (15 personagens — identidade brasileira)
Atributos em escala 0–100 (T = Técnica, C = Carisma, Cr = Criatividade, E = Energia).
Slugs e briefings visuais para arte em
[`../handoff/character-icons-handoff.md`](../handoff/character-icons-handoff.md).

### Vocal (máx. 1, não repete)
| Personagem | slug | T | C | Cr | E | Acento | Vibe |
|---|---|---|---|---|---|---|---|
| Lila Tavares | `lila-tavares` | 55 | 90 | 60 | 70 | `--bq-stat-fans` | Performer magnética, dona do palco |
| Juçara Bonfim | `jucara-bonfim` | 50 | 65 | 92 | 55 | `--bq-ember` | Letrista enigmática, voz peculiar |
| Dílson Prado | `dilson-prado` | 85 | 50 | 58 | 62 | `--bq-info` | Vocal técnico, grande alcance |

### Guitarra (pode repetir)
| Personagem | slug | T | C | Cr | E | Acento | Vibe |
|---|---|---|---|---|---|---|---|
| Rita Camargo | `rita-camargo` | 92 | 55 | 70 | 58 | `--bq-spotlight` | Shredder de precisão (estilo Polyphia) |
| Brenno Sales | `brenno-sales` | 68 | 52 | 90 | 60 | `--bq-stat-cash` | Texturas e riffs criativos |
| Téo Vasconcelos | `teo-vasconcelos` | 70 | 88 | 55 | 66 | `--bq-stat-fans` | Showman, guitarra de palco |

### Baixo (pode repetir)
| Personagem | slug | T | C | Cr | E | Acento | Vibe |
|---|---|---|---|---|---|---|---|
| Nara Siqueira | `nara-siqueira` | 88 | 58 | 62 | 64 | `--bq-stat-cash` | Groove técnico, base sólida |
| Iuri Mendes | `iuri-mendes` | 66 | 56 | 85 | 60 | `--bq-info` | Baixo melódico e criativo |
| Caíque Romero | `caique-romero` | 64 | 60 | 55 | 92 | `--bq-stat-fatigue` | Energia inesgotável de estrada |

### Bateria (obrigatória, pode repetir)
| Personagem | slug | T | C | Cr | E | Acento | Vibe |
|---|---|---|---|---|---|---|---|
| Tuca Andrade | `tuca-andrade` | 90 | 50 | 60 | 70 | `--bq-spotlight` | Metrônomo humano, precisão |
| Janaína Costa | `janaina-costa` | 68 | 58 | 54 | 95 | `--bq-ember` | Força bruta, aguenta turnê |
| Mari Sato | `mari-sato` | 72 | 55 | 88 | 66 | `--bq-stat-cash` | Ritmos criativos, poliritmia |

### Teclado (pode repetir)
| Personagem | slug | T | C | Cr | E | Acento | Vibe |
|---|---|---|---|---|---|---|---|
| Vavá Coutinho | `vava-coutinho` | 90 | 52 | 66 | 58 | `--bq-info` | Teoria e técnica apuradas |
| Cacá Lemos | `caca-lemos` | 62 | 90 | 64 | 60 | `--bq-stat-fans` | Carisma synth-pop |
| Aílton Reis | `ailton-reis` | 70 | 58 | 92 | 55 | `--bq-spotlight` | Sound design, experimental |

## Histórias dos personagens
Tom: **realista com bem-humorado**, equilíbrio variando por personagem para dar
nuance. Servem para aproximar o jogador e como referência de expressão na arte.

### Vocal
- **Lila Tavares** — Cresceu cantando em rodas de samba no quintal da avó, no
  subúrbio, onde aprendeu que segurar plateia é igual segurar família grande: no
  grito e no afeto. Largou o balcão da loja pra encarar o microfone — e a avó
  ainda liga depois de cada show só pra dizer que dava pra cantar mais baixo.
- **Juçara Bonfim** — Filha de feirante do interior nordestino, enche cadernos de
  versos que ninguém entende de primeira, nem ela às vezes. Responde pergunta com
  metáfora, o que deixa a banda louca no ensaio; quando canta, todo mundo finge
  que entendeu tudo.
- **Dílson Prado** — Estudou canto "do jeito certo", com professor e tudo, e faz
  questão de lembrar a banda disso a cada afinação. Tem alcance de sobra e ego do
  tamanho — mas chega meia hora antes em todo ensaio, então ninguém reclama.

### Guitarra
- **Rita Camargo** — Trancou-se no quarto por anos praticando escala até o vizinho
  decorar o repertório à força. Deixa os dedos falarem e revira os olhos quando
  chamam solo de "apertar corda rápido". Esquece de comer quando acha um riff novo.
- **Brenno Sales** — Coleciona pedais como outros colecionam figurinha e jura que
  cada um "muda tudo" (muda mesmo, dizem só ele e o cachorro). Gênio nos dias bons,
  risco de incêndio nos outros.
- **Téo Vasconcelos** — Aprendeu a tocar pra impressionar na escola e nunca mais
  desligou o "modo palco". Faz pose até pra atravessar a rua, mas treina escondido
  pra que a pose tenha lastro. Se houver câmera no recinto, ele a encontra.

### Baixo
- **Nara Siqueira** — Tocou em igreja antes de tocar em bar e leva os dois com a
  mesma seriedade tranquila. É quem segura o time quando todo mundo surta — o
  groove dela é tipo terapia em grupo. Fala pouco, mas quando fala, a banda para.
- **Iuri Mendes** — Ouve disco antigo procurando linha de baixo escondida e fica
  genuinamente feliz quando acha. Introvertido a ponto de pedir desculpa pro
  amplificador. Toca melodia onde os outros tocam só o tempo.
- **Caíque Romero** — Já dormiu em rodoviária, van e em cima do próprio amplificador,
  e acha tudo ótima história. Último a dormir, primeiro a montar o palco; perde
  objetos pessoais na velocidade que ganha amigos em cada cidade.

### Bateria
- **Tuca Andrade** — Conta tempo até escovando os dentes e corrige o relógio da
  cozinha que "atrasa no compasso". Paciência de santo, exceto com quem acelera no
  refrão. Só fica feliz mesmo quando a banda inteira respira junto.
- **Janaína Costa** — Quebra baqueta como quem quebra palito e já furou uma pele no
  meio do show (achou o máximo). Toca como se devesse dinheiro pro tambor. Doce
  fora do palco, furacão em cima dele.
- **Mari Sato** — Cresceu entre o taikô da comunidade e o rock da garagem, e mistura
  os dois sem pedir licença. Conta tempo em números que ninguém entende e acha
  graça da cara de pânico dos outros.

### Teclado
- **Vavá Coutinho** — Tocou em mais bandas do que lembra e tem história (longa) pra
  cada acorde. O mais velho do grupo, faz questão de dizer que "já vi isso dar
  errado em 1990". Sabe teoria que ninguém pediu, mas salva o arranjo toda vez.
- **Cacá Lemos** — Pinta o cabelo de cor nova a cada turnê pra "marcar a fase" e já
  perdeu a conta das fases. Synth brilhante, sorriso maior ainda; transforma
  soundcheck em festa sem nem tentar.
- **Aílton Reis** — Monta instrumento com o que acha no ferro-velho e jura que "o
  futuro é isso aqui, ó". Às vezes o futuro funciona, às vezes solta fumaça.
  Visionário de verdade — só precisa de alguém por perto com um extintor.

## Riscos e trade-offs
- Perfis de atributo são proposta; o balance fino depende da 0003 (economia) e do
  core loop. Tratar os números como ponto de partida ajustável.
- Permitir repetição de função pode criar combinações dominantes — revisitar no
  balance.
