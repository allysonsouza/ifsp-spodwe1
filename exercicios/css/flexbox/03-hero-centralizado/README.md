# Exercício 03 — Hero centralizado

## Objetivo

Criar uma seção "hero" que ocupa a altura total da janela, com título, texto e botão centralizados na vertical e na horizontal.

## Conceitos praticados

`min-height: 100vh` · `flex-direction: column` · `justify-content` · `align-items` · `gap` · `text-align`

## Arquivos

- `index.html` — `section.hero` com três filhos: `h1`, `p` e `a` (botão).
- `style.css` — reset e estilos visuais prontos (gradiente, tipografia, botão). O layout é escrito ao final.

## Resultado esperado

```
┌────────────────────────────────────────────┐
│                                            │
│                                            │
│         Aprenda Flexbox na prática         │
│                                            │
│      Centralize qualquer conteúdo, na      │
│        vertical e na horizontal, sem       │
│       truques de posicionamento.           │
│                                            │
│              ( Começar agora )             │
│                                            │
│                                            │
└────────────────────────────────────────────┘
  ← ocupa 100% da altura da janela →
```

## Passo a passo

### Passo 1 — Observar o comportamento padrão

A seção tem apenas a altura do conteúdo e tudo fica encostado no topo e à esquerda.

### Passo 2 — Ocupar a altura da janela

```css
.hero {
  min-height: 100vh;
}
```

`100vh` equivale a 100% da altura da janela. Usa-se `min-height` (e não `height`) para que a seção continue crescendo se o conteúdo for maior que a tela.

### Passo 3 — Container flex em coluna

```css
.hero {
  min-height: 100vh;
  display: flex;
  flex-direction: column;
}
```

Com `column`, título, texto e botão ficam empilhados (eixo principal vertical). Observe que o botão se estica por toda a largura: `align-items` padrão é `stretch` e a largura agora é o eixo transversal.

### Passo 4 — Centralizar na vertical

```css
.hero {
  min-height: 100vh;
  display: flex;
  flex-direction: column;
  justify-content: center;
}
```

Em `column`, o eixo principal é vertical, portanto `justify-content` controla o alinhamento **vertical**.

### Passo 5 — Centralizar na horizontal

```css
.hero {
  min-height: 100vh;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}
```

`align-items` atua no eixo transversal (horizontal). Os itens deixam de se esticar e passam a ter a largura do próprio conteúdo; o botão volta ao tamanho natural.

### Passo 6 — Espaçamento e texto centralizado

```css
.hero {
  /* ...regras anteriores... */
  gap: 20px;
  text-align: center;
}
```

`align-items: center` centraliza as **caixas**. `text-align: center` centraliza as **linhas de texto** dentro das caixas. O parágrafo quebra em mais de uma linha, então as duas propriedades são necessárias.

## Solução completa

```css
.hero {
  min-height: 100vh;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  gap: 20px;
  text-align: center;
}
```

## Desafios extras

1. Remover `flex-direction: column` e observar o que acontece com os três elementos em linha.
2. Envolver título, texto e botão em uma `<div class="hero__content">` e centralizar apenas com `display: flex` no `.hero` e `margin: auto` na div.
3. Trocar `100vh` por `100dvh` e pesquisar a diferença em navegadores mobile.
4. Fazer o botão ocupar a largura do parágrafo usando `align-self: stretch` somente nele.
