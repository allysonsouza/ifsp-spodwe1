# Exercício 07 — Sticky footer

## Objetivo

Garantir que o rodapé fique sempre na base da janela quando o conteúdo é curto, e acompanhe o final do conteúdo quando ele é longo.

## Conceitos praticados

`min-height: 100vh` · `flex-direction: column` no `body` · `flex: 1` · `flex-grow`

## Arquivos

- `index.html` — `header`, `main` e `footer` como filhos diretos do `body`. Conteúdo curto de propósito.
- `style.css` — reset e estilos visuais prontos. O layout é escrito ao final.

## Resultado esperado

Antes (problema):

```
┌────────────────────────┐
│ MeuSite                │
├────────────────────────┤
│ Página com pouco...    │
├────────────────────────┤
│ © 2026 MeuSite         │
│                        │
│   (espaço vazio)       │
│                        │
└────────────────────────┘
```

Depois (objetivo):

```
┌────────────────────────┐
│ MeuSite                │
├────────────────────────┤
│ Página com pouco...    │
│                        │
│   (main cresce e       │
│    ocupa o espaço)     │
│                        │
├────────────────────────┤
│ © 2026 MeuSite         │
└────────────────────────┘
```

## Passo a passo

### Passo 1 — Observar o problema

Abra `index.html`. O rodapé aparece logo após o conteúdo, e o restante da janela fica vazio.

### Passo 2 — Tornar o `body` ao menos tão alto quanto a janela

```css
body {
  min-height: 100vh;
}
```

`min-height` (e não `height`) permite que o `body` continue crescendo se o conteúdo ultrapassar a janela.

### Passo 3 — Transformar o `body` em container flex em coluna

```css
body {
  min-height: 100vh;
  display: flex;
  flex-direction: column;
}
```

`header`, `main` e `footer` viram itens empilhados. Visualmente nada muda ainda, pois ainda não existe distribuição do espaço livre.

### Passo 4 — Fazer o `main` ocupar o espaço livre

```css
.site-main {
  flex: 1;
}
```

`flex: 1` define `flex-grow: 1`: o `main` cresce para absorver todo o espaço vertical que sobra. Header e footer mantêm a altura natural, e o footer é empurrado para a base.

### Passo 5 — Testar com conteúdo longo

Duplique o parágrafo do `main` várias vezes até a página rolar. O `min-height` permite o crescimento do `body`, e o rodapé passa a ficar após o último conteúdo, sem sobreposição.

## Solução completa

```css
body {
  min-height: 100vh;
  display: flex;
  flex-direction: column;
}

.site-main {
  flex: 1;
}
```

## Desafios extras

1. Obter o mesmo resultado sem `flex: 1` no `main`, usando `margin-top: auto` no `.site-footer`.
2. Trocar `100vh` por `100dvh` e pesquisar a diferença em navegadores mobile (barra de endereço dinâmica).
3. Limitar a largura do conteúdo a 720px e centralizá-lo sem alterar o layout do rodapé. Dica: `max-width` e `margin-inline: auto` em um elemento interno do `main`.
