# Feature 0015 - Diagrams

Diagramas-fonte (Mermaid) da cadeia de songwriting e lançamentos.

## Cadeia composição → lançamento (rascunho — confirmar na Q3)

```mermaid
flowchart LR
  compose[Compor] --> song[(Música<br/>nome · gênero · tema · qualidade)]
  song --> demo[Demo<br/>N músicas]
  song --> single[Single<br/>1 música]
  single --> album[Álbum<br/>X singles + Y músicas]
  song --> album
  demo --> rep[+ Reputação]
  single --> royalties[Royalties no tempo]
  album --> royalties
```

*(Estrutura sujeita às decisões de Q3/Q4. Atualizar quando aprovadas.)*
