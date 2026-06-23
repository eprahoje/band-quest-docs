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

## Riscos e trade-offs
- Perfis de atributo são proposta; o balance fino depende da 0003 (economia) e do
  core loop. Tratar os números como ponto de partida ajustável.
- Permitir repetição de função pode criar combinações dominantes — revisitar no
  balance.
