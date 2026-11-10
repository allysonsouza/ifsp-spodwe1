# Exercício 04 — Cards responsivos

## Objetivo

Criar uma grade de cards que se reorganiza sozinha conforme a largura da janela, sem media queries.

## Conceitos praticados

`flex-wrap` · `flex-grow` · `flex-shrink` · `flex-basis` · atalho `flex`

## Arquivos

- `index.html` — `section.cards` com 6 `article.card`, de textos com tamanhos diferentes.
- `style.css` — reset e estilos visuais prontos. O layout é escrito ao final.

## Resultado esperado

Janela larga (3 cards por linha):

```
┌──────────┐ ┌──────────┐ ┌──────────┐
│ Card 1   │ │ Card 2   │ │ Card 3   │
│ ...      │ │ ...      │ │ ...      │
└──────────┘ └──────────┘ └──────────┘
┌──────────┐ ┌──────────┐ ┌──────────┐
│ Card 4   │ │ Card 5   │ │ Card 6   │
│ ...      │ │ ...      │ │ ...      │
└──────────┘ └──────────┘ └──────────┘
```

Janela média (2 por linha) e estreita (1 por linha):

```
┌──────────────┐ ┌──────────────┐        ┌──────────────────────┐
│ Card 1       │ │ Card 2       │        │ Card 1               │
└──────────────┘ └──────────────┘        └──────────────────────┘
┌──────────────┐ ┌──────────────┐        ┌──────────────────────┐
│ Card 3       │ │ Card 4       │        │ Card 2               │
└──────────────┘ └──────────────┘        └──────────────────────┘
        ...                                        ...
```

Cards da mesma linha têm sempre a mesma altura.

## Passo a passo

### Passo 1 — Container flex com espaçamento

```css
.cards {
  display: flex;
  gap: 20px;
}
```

Os cards ficam em linha, cada um com a largura do próprio conteúdo (larguras diferentes). Em janelas estreitas, são comprimidos.

Observação: os cards da mesma linha já têm alturas iguais. Isso vem do `align-items: stretch` padrão.

### Passo 2 — Larguras iguais com `flex: 1`

```css
.card {
  flex: 1;
}
```

`flex: 1` equivale a `flex: 1 1 0%`: o card parte de largura 0 e **cresce** para dividir o espaço disponível igualmente. As larguras ficam iguais, mas os seis cards continuam em **uma única linha**, ficando cada vez mais estreitos.

### Passo 3 — Permitir quebra de linha

```css
.cards {
  display: flex;
  flex-wrap: wrap;
  gap: 20px;
}
```

Somente `flex-wrap: wrap` não basta: com `flex-basis: 0%`, os seis cards sempre "cabem" em uma linha, então nunca quebram.

### Passo 4 — Definir uma largura mínima com `flex-basis`

```css
.card {
  flex: 1 1 240px;
}
```

Leitura do atalho:

| Valor   | Propriedade   | Significado                                          |
| ------- | ------------- | ---------------------------------------------------- |
| `1`     | `flex-grow`   | Pode crescer para ocupar o espaço livre da linha.    |
| `1`     | `flex-shrink` | Pode encolher se necessário.                         |
| `240px` | `flex-basis`  | Largura-alvo. Quando não cabe mais um card de 240px na linha, ele vai para a próxima. |

O número de cards por linha agora depende da largura da janela: a linha recebe quantos cards de 240px (mais o `gap`) couberem, e o espaço restante é dividido entre eles.

### Passo 5 — Testar

Redimensione a janela e observe a transição de 3 → 2 → 1 coluna.

## Solução completa

```css
.cards {
  display: flex;
  flex-wrap: wrap;
  gap: 20px;
}

.card {
  flex: 1 1 240px;
}
```

## Desafios extras

1. Remover os cards 5 e 6 do HTML e observar a última linha: os cards restantes se esticam para preencher a largura. Evitar esse comportamento adicionando `max-width: 320px` ao `.card` (e opcionalmente `justify-content: center` ao `.cards`).
2. Limitar a no máximo 3 cards por linha. Dica: usar `flex-basis` com `calc((100% - 40px) / 3)` e `min-width: 220px`.
3. Fazer o card central (Card 2) crescer o dobro dos demais usando `flex-grow: 2`.
