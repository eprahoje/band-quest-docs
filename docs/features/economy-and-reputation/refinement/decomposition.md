# Feature 0003 - Economia e Reputação (Decomposição)

## Sub-modelos internos
A 0003 é grande e se organiza em três sub-modelos (internos — **não** são features
numeradas próprias):
- **Modelo de moeda (caixa/dívida):** receitas, custos, saldo, falência.
- **Modelo de reputação:** drivers de subida, decay por inatividade, faixa 0–100.
- **Regras de balance:** valores concretos (custos/ganhos/limiares), em iteração
  dedicada perto da implementação.

> Nota: uma versão anterior deste arquivo numerava estes sub-modelos como
> "0013/0014/0015". Esses números foram **descartados** — nunca viraram pastas e o
> 0013 agora é a feature *Staff and Crew*. Os sub-modelos acima são internos à 0003.

## Why split
- Dinheiro e reputação são sistemas diferentes, mas compartilham regras.
- Separar o balance (valores) da estrutura (variáveis/fórmulas) permite fechar a
  estrutura agora e calibrar números depois.

## Recommended order
1. Modelo de moeda (estrutura).
2. Modelo de reputação (estrutura).
3. Iteração de balance (valores concretos).
