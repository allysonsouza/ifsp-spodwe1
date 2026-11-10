# Exercícios de Layout com Flexbox

Série de 8 exercícios progressivos para o primeiro contato com construção de layouts web usando CSS Flexbox. Cada exercício reproduz um layout ou componente clássico.

## Estrutura

```
.
├── README.md                          ← este arquivo
├── 01-eixos-e-alinhamento/
├── 02-navbar/
├── 03-hero-centralizado/
├── 04-cards-responsivos/
├── 05-media-object-comentarios/
├── 06-pricing-cards/
├── 07-sticky-footer/
└── 08-holy-grail/
```

Cada subpasta contém:

| Arquivo      | Conteúdo                                                                                  |
| ------------ | ----------------------------------------------------------------------------------------- |
| `index.html` | Estrutura pronta. Não precisa ser alterada.                                               |
| `style.css`  | Reset e estilos visuais (cores, bordas, tipografia) prontos. O layout deve ser escrito ao final do arquivo, abaixo do comentário `LAYOUT`. |
| `README.md`  | Objetivo, resultado esperado (ASCII), passo a passo com snippets, solução completa e desafios extras. |

## Como resolver cada exercício

1. Abrir `index.html` no navegador (duplo clique, ou extensão Live Server do VS Code).
2. Ler o `README.md` do exercício e comparar o resultado esperado com o estado atual da página.
3. Editar `style.css` seguindo o passo a passo, salvando e atualizando o navegador a cada passo.
4. Usar as ferramentas de desenvolvedor do navegador (F12). No inspetor, elementos com `display: flex` exibem o selo `flex`, que ativa a visualização dos eixos e do espaçamento.
5. Só consultar a seção "Solução completa" depois de tentar.

## Pré-requisitos

- HTML básico (tags, classes, estrutura de documento).
- Seletores de classe e propriedades CSS básicas.
- Modelo de caixa (`padding`, `border`, `margin`, `box-sizing`).

## Índice

| #  | Exercício                  | Conceitos principais                                              |
| -- | -------------------------- | ----------------------------------------------------------------- |
| 01 | Eixos e alinhamento        | `display: flex`, `flex-direction`, `gap`, `justify-content`, `align-items` |
| 02 | Navbar                     | Flex aninhado, `align-items`, `margin-left: auto`                 |
| 03 | Hero centralizado          | Centralização vertical e horizontal, `min-height: 100vh`          |
| 04 | Cards responsivos          | `flex-wrap`, `flex: 1 1 <basis>`, layout responsivo sem media query |
| 05 | Media object (comentários) | `flex-shrink: 0`, `flex: 1`, `min-width: 0`, `justify-content: space-between` |
| 06 | Pricing cards              | Alturas iguais, flex em coluna, `margin-top: auto`                |
| 07 | Sticky footer              | `min-height: 100vh`, coluna, `flex: 1`                            |
| 08 | Holy Grail                 | Combinação de todos os conceitos, media query com `flex-direction` |

## Modelo mental: eixos

O Flexbox organiza itens ao longo de dois eixos. A direção do eixo principal é definida por `flex-direction`.

```
flex-direction: row (padrão)

   eixo principal ─────────────────────►
   ┌──────┐ ┌──────┐ ┌──────┐          │
   │  1   │ │  2   │ │  3   │          │ eixo
   └──────┘ └──────┘ └──────┘          │ transversal
                                       ▼

flex-direction: column

   eixo principal
        │    ┌──────────┐    eixo transversal
        │    │    1     │  ──────────────────►
        │    └──────────┘
        │    ┌──────────┐
        │    │    2     │
        ▼    └──────────┘
```

- `justify-content` alinha no **eixo principal**.
- `align-items` alinha no **eixo transversal**.
- Ao trocar `row` por `column`, os eixos se invertem e o efeito de cada propriedade muda de direção.

## Referência rápida

### Propriedades do container (`display: flex`)

| Propriedade       | Valores comuns                                                    | Função                                              |
| ----------------- | ----------------------------------------------------------------- | --------------------------------------------------- |
| `display`         | `flex`                                                            | Cria o container flex; filhos diretos viram itens.  |
| `flex-direction`  | `row` (padrão), `column`, `row-reverse`, `column-reverse`         | Define o eixo principal.                            |
| `flex-wrap`       | `nowrap` (padrão), `wrap`                                         | Permite quebra de linha dos itens.                  |
| `justify-content` | `flex-start`, `center`, `flex-end`, `space-between`, `space-around`, `space-evenly` | Distribuição no eixo principal.   |
| `align-items`     | `stretch` (padrão), `flex-start`, `center`, `flex-end`, `baseline` | Alinhamento no eixo transversal.                   |
| `gap`             | `16px`, `1rem`                                                    | Espaço entre itens.                                 |

### Propriedades dos itens

| Propriedade   | Função                                                                                     |
| ------------- | ------------------------------------------------------------------------------------------ |
| `flex-grow`   | Fração do espaço livre que o item ocupa (`0` = não cresce).                                |
| `flex-shrink` | Capacidade de encolher quando falta espaço (`0` = não encolhe).                            |
| `flex-basis`  | Tamanho inicial no eixo principal, antes de crescer ou encolher.                           |
| `flex`        | Atalho para `grow shrink basis`. `flex: 1` equivale a `1 1 0%`.                            |
| `align-self`  | Sobrescreve `align-items` para um único item.                                              |
| `order`       | Altera a ordem visual sem mudar o HTML (padrão `0`).                                       |
| `margin: auto`| Margens automáticas absorvem o espaço livre do eixo correspondente.                        |

## Observações

- Apenas os **filhos diretos** do container se tornam itens flex. Para alinhar elementos mais internos, o filho precisa ser também um container flex (flex aninhado).
- Um elemento pode ser item de um container flex e container flex ao mesmo tempo.
- Todos os exercícios funcionam sem JavaScript e sem dependências externas.
