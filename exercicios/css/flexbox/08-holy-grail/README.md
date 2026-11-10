# Exercício 08 — Holy Grail

## Objetivo

Construir o layout clássico "Holy Grail": cabeçalho, três colunas (menu fixo, conteúdo flexível, barra lateral fixa) e rodapé na base da janela. Este exercício combina conceitos dos anteriores.

## Conceitos praticados

Flex em coluna no `body` (exercício 07) · flex em linha no meio · `flex: 0 0 200px` (colunas fixas) · `flex: 1` (coluna flexível) · alturas iguais · media query com `flex-direction`

## Arquivos

- `index.html` — `header`, `div.layout` (contendo `nav`, `main` e `aside`) e `footer`.
- `style.css` — reset e estilos visuais prontos (cores, espaçamentos internos). O layout é escrito ao final.

## Resultado esperado

Desktop:

```
┌───────────────────────────────────────────────┐
│                    Cabeçalho                  │
├──────────┬────────────────────────┬───────────┤
│   Nav    │         Main           │   Aside   │
│  200px   │      (flexível)        │   200px   │
│          │                        │           │
│          │                        │           │
├──────────┴────────────────────────┴───────────┤
│                     Rodapé                    │
└───────────────────────────────────────────────┘
```

Mobile (menos de 700px):

```
┌────────────────────────┐
│       Cabeçalho        │
├────────────────────────┤
│          Nav           │
├────────────────────────┤
│          Main          │
│                        │
├────────────────────────┤
│         Aside          │
├────────────────────────┤
│         Rodapé         │
└────────────────────────┘
```

Requisitos:

- O rodapé fica na base da janela quando o conteúdo é curto.
- As três colunas têm a mesma altura.
- Menu e barra lateral têm largura fixa de 200px; o conteúdo ocupa o restante.

## Passo a passo

### Passo 1 — Estrutura vertical (sticky footer)

Mesma técnica do exercício 07.

```css
body {
  min-height: 100vh;
  display: flex;
  flex-direction: column;
}
```

### Passo 2 — A faixa das colunas ocupa o espaço livre

```css
.layout {
  flex: 1;
}
```

`header` e `footer` mantêm a altura natural. `.layout` cresce e preenche o espaço entre eles.

### Passo 3 — As colunas ficam lado a lado

```css
.layout {
  flex: 1;
  display: flex;
}
```

`.layout` é, ao mesmo tempo, **item** do `body` (coluna) e **container** de `nav`, `main` e `aside` (linha). Os três filhos já ficam lado a lado e com a **mesma altura** (`align-items: stretch`, o padrão), que é a da faixa inteira.

### Passo 4 — Colunas laterais com largura fixa

```css
.nav,
.aside {
  flex: 0 0 200px;
}
```

Leitura de `flex: 0 0 200px`:

| Valor   | Propriedade   | Significado                  |
| ------- | ------------- | ---------------------------- |
| `0`     | `flex-grow`   | Não cresce.                  |
| `0`     | `flex-shrink` | Não encolhe.                 |
| `200px` | `flex-basis`  | Largura fixa de 200px.       |

### Passo 5 — Coluna central flexível

```css
.main {
  flex: 1;
}
```

O `main` cresce para ocupar todo o espaço restante.

### Passo 6 — Versão mobile

```css
@media (max-width: 700px) {
  .layout {
    flex-direction: column;
  }

  .nav,
  .aside {
    flex-basis: auto;
  }
}
```

- `flex-direction: column` empilha as três seções.
- O eixo principal passa a ser vertical, então o `flex-basis: 200px` passaria a significar **altura** de 200px. Redefinir para `auto` devolve a altura natural do conteúdo.

## Solução completa

```css
body {
  min-height: 100vh;
  display: flex;
  flex-direction: column;
}

.layout {
  flex: 1;
  display: flex;
}

.nav,
.aside {
  flex: 0 0 200px;
}

.main {
  flex: 1;
}

@media (max-width: 700px) {
  .layout {
    flex-direction: column;
  }

  .nav,
  .aside {
    flex-basis: auto;
  }
}
```

## Desafios extras

1. No mobile, exibir a barra lateral (`.aside`) **antes** do conteúdo principal, sem alterar o HTML. Dica: `order`.
2. Adicionar `gap: 16px` em `.layout` e observar o efeito nas larguras.
3. Fazer o menu (`.nav`) permanecer fixo na tela durante a rolagem do conteúdo. Dica: `position: sticky`, `top: 0` e `align-self: flex-start`.
4. Alterar a ordem visual das colunas para `aside`, `main`, `nav` apenas com CSS.
