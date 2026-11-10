# Exercício 05 — Media object (comentários)

## Objetivo

Construir o padrão "media object": uma mídia de tamanho fixo (avatar) ao lado de um bloco de texto flexível. O padrão é usado em comentários, notificações, itens de lista e resultados de busca.

## Conceitos praticados

`flex: 1` · `flex-shrink: 0` · `min-width: 0` · `justify-content: space-between` · flex aninhado

## Arquivos

- `index.html` — dois comentários. O segundo contém um texto longo **sem espaços**, de propósito, para expor um problema clássico de `flex-shrink`.
- `style.css` — reset e estilos visuais prontos. O layout é escrito ao final.

## Resultado esperado

```
┌────────────────────────────────────────────────────┐
│ ┌────┐  Ana Martins                    há 2 horas │
│ │ AM │  Ótimo conteúdo! A explicação sobre eixo   │
│ └────┘  principal e eixo transversal finalmente   │
│         fez sentido para mim. ...                  │
│         Curtir  Responder                          │
└────────────────────────────────────────────────────┘

┌────────────────────────────────────────────────────┐
│ ┌────┐  Rafael Souza                  há 5 horas  │
│ │ RS │  Material de apoio: https://exemplo.com... │
│ └────┘  ...a URL longa quebra dentro do bloco     │
│         Curtir  Responder                          │
└────────────────────────────────────────────────────┘
```

O avatar mantém 48px de largura e fica no topo. O texto ocupa todo o espaço restante.

## Passo a passo

### Passo 1 — Avatar ao lado do conteúdo

```css
.comment {
  display: flex;
  gap: 16px;
}
```

Os dois filhos diretos (`.avatar` e `.comment__body`) ficam lado a lado.

### Passo 2 — Alinhar ao topo

```css
.comment {
  display: flex;
  align-items: flex-start;
  gap: 16px;
}
```

O avatar já tem altura fixa (48px), então o resultado visual é igual ao padrão (`stretch`). A declaração deixa a intenção explícita e impede que o avatar se estique caso a altura fixa seja removida.

### Passo 3 — O bloco de texto ocupa o espaço restante

```css
.comment__body {
  flex: 1;
}
```

`flex: 1` faz o corpo crescer para preencher toda a largura que o avatar não usa.

### Passo 4 — Reproduzir e corrigir o problema do segundo comentário

Observe o segundo comentário: o texto sem espaços não consegue quebrar, empurra o container e o **avatar encolhe** (fica oval ou estreito).

Dois ajustes resolvem:

```css
.avatar {
  flex-shrink: 0;
}

.comment__body {
  flex: 1;
  min-width: 0;
  overflow-wrap: break-word;
}
```

- `flex-shrink: 0` impede que o avatar seja comprimido.
- `min-width: 0` permite que o corpo encolha abaixo do tamanho mínimo do conteúdo (por padrão, itens flex têm `min-width: auto` e não encolhem além da maior palavra).
- `overflow-wrap: break-word` permite quebrar a palavra longa.

### Passo 5 — Nome e data nas extremidades

```css
.comment__header {
  display: flex;
  justify-content: space-between;
  align-items: baseline;
  gap: 12px;
}
```

Flex aninhado: `.comment__body` é item do `.comment` e o `.comment__header` é container dos dois textos. `align-items: baseline` alinha as linhas de base do nome e da data, que têm tamanhos de fonte diferentes.

### Passo 6 — Ações em linha

```css
.comment__actions {
  display: flex;
  gap: 16px;
}
```

## Solução completa

```css
.comment {
  display: flex;
  align-items: flex-start;
  gap: 16px;
}

.avatar {
  flex-shrink: 0;
}

.comment__body {
  flex: 1;
  min-width: 0;
  overflow-wrap: break-word;
}

.comment__header {
  display: flex;
  justify-content: space-between;
  align-items: baseline;
  gap: 12px;
}

.comment__actions {
  display: flex;
  gap: 16px;
}
```

## Desafios extras

1. Remover `flex-shrink: 0` e `min-width: 0` isoladamente e observar o efeito de cada um.
2. Inverter o layout (avatar à direita) usando `flex-direction: row-reverse` e, em seguida, usando `order`.
3. Adicionar um terceiro item ao `.comment` (por exemplo, um botão "⋮" à direita) sem alterar o comportamento do corpo.
