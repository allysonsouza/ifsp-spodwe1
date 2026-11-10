# Exercício 06 — Pricing cards

## Objetivo

Construir três cards de planos com a mesma largura e a mesma altura, com o botão sempre alinhado na base, independentemente da quantidade de itens da lista.

## Conceitos praticados

`flex: 1` · alturas iguais (`align-items: stretch`) · flex em coluna aninhado · `margin-top: auto` · `flex-wrap`

## Arquivos

- `index.html` — `section.plans` com três `article.plan`. As listas têm 3, 5 e 4 itens.
- `style.css` — reset e estilos visuais prontos. O layout é escrito ao final.

## Resultado esperado

```
┌─────────────┐ ┌─────────────┐ ┌─────────────┐
│ Básico      │ │ Pro         │ │ Empresarial │
│ R$ 29/mês   │ │ R$ 79/mês   │ │ R$ 199/mês  │
│             │ │             │ │             │
│ • item      │ │ • item      │ │ • item      │
│ • item      │ │ • item      │ │ • item      │
│ • item      │ │ • item      │ │ • item      │
│             │ │ • item      │ │ • item      │
│             │ │ • item      │ │             │
│             │ │             │ │             │
│ [ Assinar ] │ │ [ Assinar ] │ │ [ Assinar ] │
└─────────────┘ └─────────────┘ └─────────────┘
                 ↑ os três botões alinhados na base
```

## Passo a passo

### Passo 1 — Cards lado a lado com larguras iguais

```css
.plans {
  display: flex;
  gap: 24px;
}

.plan {
  flex: 1;
}
```

Os três cards dividem a largura igualmente. Como `align-items` padrão é `stretch`, todos têm também a **mesma altura**, a do maior card. Porém, o botão fica logo abaixo da lista em cada card, em alturas diferentes.

### Passo 2 — Tornar cada card um container flex em coluna

```css
.plan {
  flex: 1;
  display: flex;
  flex-direction: column;
}
```

Cada `.plan` é, ao mesmo tempo, item de `.plans` e container flex dos próprios filhos (nome, preço, lista e botão). Agora o espaço livre vertical dentro do card pode ser distribuído pelo Flexbox.

Observação: o botão passa a ocupar a largura total do card (eixo transversal em `stretch`).

### Passo 3 — Empurrar o botão para a base com `margin-top: auto`

```css
.plan__button {
  margin-top: auto;
}
```

Margens `auto` em itens flex absorvem o espaço livre do eixo. Com `margin-top: auto`, todo o espaço vertical sobrando no card é colocado acima do botão, que fica encostado na base. Os botões dos três cards ficam alinhados.

O `margin-bottom: 24px` da lista (CSS pronto) garante um espaço mínimo entre a lista e o botão no card mais cheio.

### Passo 4 — Tornar responsivo

```css
.plans {
  display: flex;
  flex-wrap: wrap;
  gap: 24px;
}

.plan {
  flex: 1 1 260px;
  display: flex;
  flex-direction: column;
}
```

Com `flex-basis: 260px` e `flex-wrap: wrap`, em janelas estreitas os cards passam para linhas separadas. O alinhamento do botão na base continua válido em cada linha.

## Solução completa

```css
.plans {
  display: flex;
  flex-wrap: wrap;
  gap: 24px;
}

.plan {
  flex: 1 1 260px;
  display: flex;
  flex-direction: column;
}

.plan__button {
  margin-top: auto;
}
```

## Desafios extras

1. Remover `margin-top: auto` do botão e usar `flex: 1` na lista (`.plan__features`). Comparar o resultado.
2. Adicionar `align-items: flex-start` em `.plans` e observar por que os cards perdem a altura igual.
3. Destacar o card `.plan--featured` com `transform: scale(1.04)` sem quebrar o alinhamento dos demais.
4. Posicionar o card "Pro" como primeiro em telas estreitas usando `order`.
