# DOM API

O `document` é o objeto global que representa a sua página HTML dentro do navegador. Sempre que você quiser manipular algo no navegador via JavaScript, você passará por ele. Ele possui métodos que permitem buscar elementos específicos na página para manipulação.

## DOM, Tree, Nodes

O DOM (Document Object Model) é a representação da página HTML como uma estrutura em árvore de objetos, onde cada tag, atributo e texto vira um nó (node). O JavaScript usa essa árvore para ler e modificar o conteúdo, a estrutura e o estilo da página.

```javascript
// A árvore do DOM começa em document,
// que contém o elemento raiz <html>
console.log(document);
console.log(document.documentElement); // <html>
console.log(document.body);            // <body>
```

## Buscar elementos

### querySelector

Retorna o primeiro elemento que corresponde a um seletor CSS. Se nenhum elemento for encontrado, retorna `null`.

```javascript
const titulo = document.querySelector('h1');
const primeiroItem = document.querySelector('.item');
const botaoEnviar = document.querySelector('#btn-enviar');
```

### querySelectorAll

Retorna uma `NodeList` estática com todos os elementos que correspondem a um seletor CSS.

```javascript
const itens = document.querySelectorAll('.item');
itens.forEach(item => {
  console.log(item.textContent);
});
```

### getElementById

Busca um único elemento pelo valor do atributo `id`. É o método mais rápido para essa finalidade.

```javascript
const container = document.getElementById('container-principal');
container.style.border = '1px solid red';
```

### getElementsByClassName

Retorna uma `HTMLCollection` "viva" (atualizada automaticamente) com todos os elementos que possuem a classe informada.

```javascript
const cards = document.getElementsByClassName('card');
console.log(cards.length);
console.log(cards[0]);
```

### getElementsByTagName

Retorna uma `HTMLCollection` viva com todos os elementos de uma determinada tag.

```javascript
const paragrafos = document.getElementsByTagName('p');
for (let p of paragrafos) {
  p.style.color = 'blue';
}
```

### getElementsByTagNameNS

Semelhante ao `getElementsByTagName`, mas permite buscar elementos considerando um namespace específico, útil em documentos XML/SVG.

```javascript
const circulos = document.getElementsByTagNameNS(
  'http://www.w3.org/2000/svg',
  'circle'
);
console.log(circulos.length);
```

## Acessar conteúdo

### textContent

Lê ou define o conteúdo textual de um elemento, ignorando qualquer marcação HTML.

```javascript
const paragrafo = document.querySelector('p');
console.log(paragrafo.textContent);
paragrafo.textContent = 'Novo texto sem HTML';
```

### innerHTML

Lê ou define o conteúdo de um elemento incluindo marcação HTML. Deve ser usado com cuidado por permitir injeção de código malicioso (XSS).

```javascript
const div = document.querySelector('#area');
div.innerHTML = '<strong>Texto em negrito</strong>';
```

### value

Lê ou define o valor atual de elementos de formulário, como `input`, `textarea` e `select`.

```javascript
const campoNome = document.querySelector('#nome');
console.log(campoNome.value);
campoNome.value = 'João';
```

## Alterar estilos

### style

Permite ler ou alterar estilos CSS diretamente no elemento (inline style), usando propriedades em camelCase.

```javascript
const box = document.querySelector('.box');
box.style.backgroundColor = 'yellow';
box.style.padding = '10px';
```

### classList

Fornece métodos para adicionar, remover, alternar e verificar classes CSS de um elemento, sem precisar manipular strings.

```javascript
const menu = document.querySelector('.menu');
menu.classList.add('ativo');
menu.classList.remove('oculto');
menu.classList.toggle('destaque');
console.log(menu.classList.contains('ativo'));
```

## Criar elementos

### createElement

Cria um novo elemento HTML em memória, que ainda não está inserido na página.

```javascript
const novoParagrafo = document.createElement('p');
novoParagrafo.textContent = 'Parágrafo criado dinamicamente';
```

### appendChild

Insere um nó como último filho de um elemento pai, adicionando-o à árvore do DOM.

```javascript
const lista = document.querySelector('ul');
const novoItem = document.createElement('li');
novoItem.textContent = 'Novo item';
lista.appendChild(novoItem);
```

## Ler e alterar atributos

### getAttribute

Retorna o valor de um atributo específico de um elemento.

```javascript
const link = document.querySelector('a');
console.log(link.getAttribute('href'));
```

### setAttribute

Define ou altera o valor de um atributo em um elemento.

```javascript
const imagem = document.querySelector('img');
imagem.setAttribute('src', 'nova-imagem.png');
imagem.setAttribute('alt', 'Descrição da imagem');
```

### hasAttribute

Verifica se um elemento possui determinado atributo, retornando `true` ou `false`.

```javascript
const input = document.querySelector('input');
if (input.hasAttribute('disabled')) {
  console.log('Campo desabilitado');
}
```

### removeAttribute

Remove um atributo de um elemento.

```javascript
const botao = document.querySelector('button');
botao.removeAttribute('disabled');
```

## Remover elementos

### remove

Remove o próprio elemento diretamente da árvore do DOM.

```javascript
const aviso = document.querySelector('.aviso');
aviso.remove();
```

### removeChild

Remove um nó filho específico, sendo chamado a partir do elemento pai.

```javascript
const lista = document.querySelector('ul');
const primeiroItem = lista.firstElementChild;
lista.removeChild(primeiroItem);
```

## Inserção avançada

### prepend

Insere um ou mais nós como os primeiros filhos de um elemento.

```javascript
const lista = document.querySelector('ul');
const novoItem = document.createElement('li');
novoItem.textContent = 'Primeiro item';
lista.prepend(novoItem);
```

### insertBefore

Insere um novo nó antes de um nó de referência existente, sendo chamado a partir do elemento pai.

```javascript
const lista = document.querySelector('ul');
const itemReferencia = document.querySelector('.item-referencia');
const novoItem = document.createElement('li');
novoItem.textContent = 'Item inserido antes';
lista.insertBefore(novoItem, itemReferencia);
```

### insertAdjacentElement

Insere um elemento em uma posição específica em relação a outro elemento: `beforebegin`, `afterbegin`, `beforeend` ou `afterend`.

```javascript
const referencia = document.querySelector('#referencia');
const novoElemento = document.createElement('div');
novoElemento.textContent = 'Elemento adicional';
referencia.insertAdjacentElement('afterend', novoElemento);
```

### insertAdjacentHTML

Insere uma string HTML em uma posição específica em relação a um elemento, sem precisar sobrescrever o conteúdo existente.

```javascript
const referencia = document.querySelector('#referencia');
referencia.insertAdjacentHTML('beforeend', '<p>Novo parágrafo</p>');
```

## Navegando pela árvore do DOM

### parentElement / parentNode

Acessam o elemento pai de um nó. `parentElement` retorna sempre um elemento (ou `null`), enquanto `parentNode` pode retornar outros tipos de nó.

```javascript
const item = document.querySelector('.item');
console.log(item.parentElement);
console.log(item.parentNode);
```

### children

Retorna uma `HTMLCollection` com os elementos filhos diretos, ignorando nós de texto e comentários.

```javascript
const lista = document.querySelector('ul');
console.log(lista.children);
console.log(lista.children.length);
```

### nextElementSibling / previousElementSibling

Acessam, respectivamente, o próximo e o anterior elemento irmão no mesmo nível da árvore.

```javascript
const item = document.querySelector('.item-atual');
console.log(item.nextElementSibling);
console.log(item.previousElementSibling);
```