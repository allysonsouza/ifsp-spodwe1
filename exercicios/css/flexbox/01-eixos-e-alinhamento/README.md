# Exercício 01 — Eixos e alinhamento

## Objetivo

Entender o modelo de eixos do Flexbox e controlar direção, espaçamento e alinhamento de itens dentro de um container.

## Conceitos praticados

`display: flex` · `flex-direction` · `gap` · `justify-content` · `align-items`

## Arquivos

- `index.html` — cinco containers (A a E), cada um com três itens. Não precisa ser alterado.
- `style.css` — reset e estilos visuais prontos. As regras de layout são escritas ao final, nas seções A a E.

## Resultado esperado

**A.** Itens em linha com espaço entre eles

```
┌──────────────────────────────────┐
│ [1] [2] [3]                      │
└──────────────────────────────────┘
```

**B.** Itens em coluna

```
┌──────────────────────────────────┐
│ [1]                              │
│ [2]                              │
│ [3]                              │
└──────────────────────────────────┘
```

**C.** Primeiro e último nas extremidades, o do meio distribuído

```
┌──────────────────────────────────┐
│ [1]           [2]            [3] │
└──────────────────────────────────┘
```

**D.** Centralizados nos dois eixos

```
┌──────────────────────────────────┐
│                                  │
│           [1] [2] [3]            │
│                                  │
└──────────────────────────────────┘
```

**E.** Canto inferior direito

```
┌──────────────────────────────────┐
│                                  │
│                                  │
│                      [1] [2] [3] │
└──────────────────────────────────┘
```

## Conceito prévio: eixos

```
flex-direction: row (padrão)            flex-direction: column

  eixo principal ───────►                eixo principal
  [1] [2] [3]            │ eixo               │   [1]
                         │ transversal        │   [2]
                         ▼                    ▼   [3]
                                                  ───► eixo transversal
```

- `justify-content` trabalha no **eixo principal**.
- `align-items` trabalha no **eixo transversal**.

## Passo a passo

### Passo 1 — Observar o comportamento padrão

Abra `index.html`. Os itens aparecem empilhados porque cada `div` é um elemento de bloco. Nenhuma regra flex foi aplicada ainda.

### Passo 2 — Ativar o Flexbox (A)

`display: flex` no **container** transforma seus filhos diretos em itens flex.

```css
.container-a {
  display: flex;
}
```

Resultado: os itens passam a ficar em linha (o valor padrão de `flex-direction` é `row`), porém sem espaço entre eles.

### Passo 3 — Espaçamento com `gap` (A)

```css
.container-a {
  display: flex;
  gap: 12px;
}
```

`gap` cria espaço apenas **entre** os itens, sem margem nas bordas externas.

### Passo 4 — Inverter o eixo principal (B)

```css
.container-b {
  display: flex;
  flex-direction: column;
  gap: 12px;
}
```

Com `column`, o eixo principal passa a ser vertical. O `gap` continua funcionando.

### Passo 5 — Distribuir nas extremidades (C)

```css
.container-c {
  display: flex;
  justify-content: space-between;
}
```

`space-between` posiciona o primeiro item no início, o último no fim e distribui o espaço restante igualmente entre os demais.

### Passo 6 — Centralizar nos dois eixos (D)

```css
.container-d {
  display: flex;
  justify-content: center; /* eixo principal (horizontal em row) */
  align-items: center;     /* eixo transversal (vertical em row) */
  gap: 12px;
}
```

O container tem `height: 160px` (definido no CSS pronto). Sem altura, não existe espaço vertical livre e `align-items` não teria efeito visível.

### Passo 7 — Canto inferior direito (E)

```css
.container-e {
  display: flex;
  justify-content: flex-end; /* encosta no fim do eixo principal (direita) */
  align-items: flex-end;     /* encosta no fim do eixo transversal (embaixo) */
  gap: 12px;
}
```

## Solução completa

```css
.container-a {
  display: flex;
  gap: 12px;
}

.container-b {
  display: flex;
  flex-direction: column;
  gap: 12px;
}

.container-c {
  display: flex;
  justify-content: space-between;
}

.container-d {
  display: flex;
  justify-content: center;
  align-items: center;
  gap: 12px;
}

.container-e {
  display: flex;
  justify-content: flex-end;
  align-items: flex-end;
  gap: 12px;
}
```

## Desafios extras

1. No container D, trocar `flex-direction` para `column` mantendo `justify-content: center` e `align-items: center`. Observar o que muda e por quê.
2. Comparar `space-between`, `space-around` e `space-evenly` no container C.
3. Aplicar `flex-direction: row-reverse` no container A e observar a ordem dos itens.
4. No container D, aplicar `align-self: flex-start` apenas ao item 2.
