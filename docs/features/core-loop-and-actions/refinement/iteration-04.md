# Feature 0014 - Core Loop and Actions (Refinement 04)

> Revisão derivada do **Playtest 04** (pontos 2 e 6) — bug estrutural de fadiga.
> Decisão de modelo validada com o usuário (G1): **fadiga por dia (proporcional)**.

## Problema (causa-raiz)

A fadiga de uma ação era um **lump-sum aplicado na conclusão**, enquanto a
recuperação passiva (`-1/dia`) incidia sobre **todos os dias avançados**. Como o
relógio salta a duração inteira de uma ação de uma vez, a recuperação acumulada ao
longo da própria duração **cancelava** (ou superava) a fadiga do fim:

| Ação | Dias | Fadiga (antes) | Recup. passiva | Líquido (antes) |
|---|---:|---:|---:|---:|
| Turnê nacional | 45 | +45 lump | −45 | ≈ 0 |
| Mini-turnê | 14 | +45 lump | −14 | ≈ +31 |
| Gravar álbum | 35 | **0** (sem custo) | −35 | ≈ −35 |

Sintomas: turnê nacional não cansava (ponto 2); gravar álbum "zerava" a fadiga
(ponto 6); mini-turnê cansava mais que a nacional (Playtest 03, ponto 9.1).

## Decisão — modelo de fadiga por dia (proporcional)

1. **Cada ação tem uma taxa de fadiga por dia** (`fatiguePerDay`), aplicada
   **enquanto a ação está em curso**, em vez de um lump-sum na conclusão. A fadiga
   total de uma ação passa a ser **proporcional à sua duração** → uma turnê de 45
   dias cansa mais que uma de 14.
2. **A recuperação passiva (`-1/dia`) só corre em dias ociosos** — quando **nenhuma
   ação `main` está em curso**. Tocando/gravando/em turnê, a banda não "descansa de
   graça".
3. **`rest` é a ação de recuperação ativa**: `fatiguePerDay` negativo (recupera mais
   que o passivo). Ações `background` (marketing) não cansam nem suspendem o passivo.
4. A fadiga deixa de ser um `chip` no evento de conclusão — ela sobe/desce
   **gradualmente** no painel de stats conforme o tempo passa (trade-off aceito).

### Taxas (placeholders de balance — 0003)
| Ação | `fatiguePerDay` | Duração | Fadiga total (aprox.) |
|---|---:|---:|---:|
| Tocar show | 18 | 1 | +18 |
| Ensaiar | 4 | 2–4 | +8 a +16 |
| Compor | 1.5 | 5 | +8 |
| Gravar demo | 1.5 | 3 | +5 |
| Gravar single | 1.5 | 10–16 | +15 a +24 |
| Gravar álbum | 1.5 | 35–50 | +53 a +75 |
| Turnê | 2 | 14 / 45 | +28 / +90 |
| Marketing (bg) | 0 | 14 | 0 |
| Descansar | −6 | 5 | −30 |

Resultado: turnê nacional cansa **muito mais** que a mini; gravar álbum **acumula**
fadiga (não zera). Pontos 2 e 6 resolvidos na raiz; 9.1 (P03) absorvido.

## Implementação (band-quest-game)
- `data/actions.ts`: novo campo `fatiguePerDay` em `ActionDef`; **remover** `fatigue`
  de `outcome.metrics` de todas as ações; ajustar comentários.
- `stores/game.ts`: em `advanceDays`, trocar a recuperação passiva fixa por
  `applyFatigueForSpan(days)` — soma `fatiguePerDay * days` das ações ativas e aplica
  o passivo **só se não há ação `main` em curso**; arredonda para inteiro.
- Testes: atualizar os que assumiam fadiga em `resolveOutcome`/chip de conclusão e
  adicionar cobertura para (a) turnê proporcional à duração, (b) álbum não zera a
  fadiga, (c) passivo suspenso durante ação main.

## Checklist result
- [x] Scope reviewed.
- [x] Questions updated — nenhuma bloqueante (números são placeholders de balance/0003).
- [x] Handoff reviewed — **G1 liberado** (modelo validado pelo usuário).
