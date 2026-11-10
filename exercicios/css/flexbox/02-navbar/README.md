# Exercício 02 — Navbar

## Objetivo

Construir uma barra de navegação com logo à esquerda, links de menu e botão de ação à direita.

## Conceitos praticados

`display: flex` · `align-items` · `gap` · flex aninhado · `margin-left: auto`

## Arquivos

- `index.html` — `header.navbar` com três filhos diretos: `.navbar__logo`, `.navbar__menu` (contendo os links) e `.navbar__cta`.
- `style.css` — reset e estilos visuais prontos. O layout é escrito ao final do arquivo.

## Resultado esperado

```
┌────────────────────────────────────────────────────────────────────┐
│ MinhaMarca               Início  Produtos  Sobre  Contato  [Entrar]│
└────────────────────────────────────────────────────────────────────┘
  └─ logo                  └───────── menu ─────────┘         └─ cta ─┘
     (esquerda)                     (direita, junto do botão)
```

Todos os elementos ficam centralizados verticalmente dentro da barra de 64px.

## Passo a passo

### Passo 1 — Observar o comportamento padrão

O `<nav>` é um elemento de bloco e ocupa uma linha própria. Logo e botão são `<a>` (inline). Os três elementos não ficam na mesma linha.

### Passo 2 — Container flex na barra

```css
.navbar {
  display: flex;
}
```

Os três filhos diretos ficam em linha. Observe que o botão **Entrar** se estica até a altura total da barra: o valor padrão de `align-items` é `stretch`.

### Passo 3 — Centralizar verticalmente

```css
.navbar {
  display: flex;
  align-items: center;
}
```

`align-items: center` alinha os itens no eixo transversal (vertical). O botão volta à altura natural.

### Passo 4 — Espaço entre os itens

```css
.navbar {
  display: flex;
  align-items: center;
  gap: 24px;
}
```

### Passo 5 — Flex aninhado nos links

Os links estão dentro de `.navbar__menu`, que é filho direto da barra, mas os links não são. Para controlar o espaçamento entre eles, `.navbar__menu` também vira container flex.

```css
.navbar__menu {
  display: flex;
  gap: 24px;
}
```

Um elemento pode ser, ao mesmo tempo, **item** do container pai e **container** dos próprios filhos.

### Passo 6 — Empurrar menu e botão para a direita

```css
.navbar__menu {
  display: flex;
  gap: 24px;
  margin-left: auto;
}
```

Em um container flex, uma margem `auto` absorve todo o espaço livre do eixo correspondente. Com `margin-left: auto` no menu, todo o espaço livre fica à esquerda dele, e o menu e o botão que vem depois ficam encostados na direita. O `gap` da barra mantém a distância entre menu e botão.

**Comparação:** `justify-content: space-between` na barra posicionaria o menu no **centro** (três itens distribuídos igualmente), não ao lado do botão.

## Solução completa

```css
.navbar {
  display: flex;
  align-items: center;
  gap: 24px;
}

.navbar__menu {
  display: flex;
  gap: 24px;
  margin-left: auto;
}
```

## Desafios extras

1. Substituir `margin-left: auto` por `justify-content: space-between` e comparar o resultado.
2. **Versão mobile.** Abaixo de 600px de largura, exibir o logo e o botão na primeira linha e o menu centralizado na segunda. Dica: `flex-wrap`, `order` e `flex-basis: 100%`.

   <details>
   <summary>Solução do desafio 2</summary>

   ```css
   @media (max-width: 600px) {
     .navbar {
       height: auto;
       flex-wrap: wrap;
       padding-block: 12px;
     }

     .navbar__cta {
       margin-left: auto;
     }

     .navbar__menu {
       order: 3;
       flex-basis: 100%;
       margin-left: 0;
       justify-content: center;
     }
   }
   ```
   </details>
