# Arrays

Números, booleanos e strings são os átomos a partir dos quais estruturas de dados são construídas. Muitos tipos de informação requerem mais de um átomo, porém. Objetos nos permitem agrupar valores — incluindo outros objetos — para construir estruturas mais complexas.

---
## Arrays

### Definição de arrays

JavaScript fornece um tipo de dado especificamente para armazenar sequências de valores. É chamado de array e é escrito como uma lista de valores entre colchetes, separados por vírgulas.

```js
let listOfNumbers = [2, 3, 5, 7, 11];
console.log(listOfNumbers[2]);
// → 5
console.log(listOfNumbers[0]);
// → 2
console.log(listOfNumbers[2 - 1]);
// → 3
```

---
### Acesso à elementos de arrays

A notação para acessar os elementos dentro de um array também usa colchetes. Um par de colchetes imediatamente após uma expressão, com outra expressão dentro deles, procurará o elemento na expressão à esquerda que corresponde ao índice dado pela expressão entre colchetes.

O primeiro índice de um array é zero, não um, então o primeiro elemento é obtido com listOfNumbers[0]. A contagem baseada em zero tem uma longa tradição em tecnologia e de certas formas faz muito sentido, mas leva algum tempo para se acostumar. Pense no índice como o número de itens a pular, contando a partir do início do array.

---
Agora iremos falar sobre propriedades e métodos em JavaScript, que serão úteis para trabalharmos com arrays.

## Propriedades

Quase todos os valores JavaScript têm propriedades. As exceções são `null` e `undefined`. Se você tentar acessar uma propriedade em um desses não-valores, obterá um erro:

```js
null.length;
// → TypeError: null has no properties
```

### Acessando propriedades

As duas principais formas de acessar propriedades em JavaScript são com um ponto e com colchetes.

Sendo `value` uma variável, tanto `value.x` quanto `value["x"]` acessam uma propriedade em value.

1. Utilizando a notação de ponto, colocamos o nome da propriedade na sequência
2. Utilizando a notação de colchetes, precisamos passar como string (entre aspas), o nome da propriedade

---
Os elementos em um array são armazenados como propriedades do array, usando números como nomes de propriedades.

Como não podemos usar a notação de ponto com números,  precisamos usar a notação de colchetes para acessar os elementos de um array.

---
Arrays têm uma propriedade length que nos diz quantos elementos o array tem.

---
## Métodos


Métodos são propriedades que possuem armazenadas em si, funções. Lembrando que JavaScript trata funções como valores, que podem ser armazenadas em variáveis e propriedades.

---
### Métodos de string

Toda string tem uma propriedade `toUpperCase`. Quando chamada, retornará uma cópia da string em que todas as letras foram convertidas para maiúsculas. Existe também `toLowerCase`, que faz o inverso.

Propriedades que contêm funções são geralmente chamadas de métodos do valor a que pertencem, como em “toUpperCase é um método de uma string”.

---
### Métodos de arrays

Os métodos `push`, `pop`, `shift` e `unshift` permitem manipular os elementos das extremidades de um array (início ou fim), funcionando como operações de pilha (stack) ou fila (queue). Todos esses quatro métodos alteram (mutam) o array original no local em que são invocados.

#### push

O método `push()` adiciona um ou mais novos elementos ao final de um array.

- Ele modifica o array original no local.
- Ele retorna o novo comprimento (length) do array após a inserção.

```js
let linguagens = ["HTML", "CSS"];

// Adicionando um único elemento
let novoTamanho = linguagens.push("JavaScript");

console.log(linguagens);   // Saída: ["HTML", "CSS", "JavaScript"]
console.log(novoTamanho);  // Saída: 3

// Adicionando múltiplos elementos simultaneamente
linguagens.push("TypeScript", "PHP");
console.log(linguagens);   // Saída: ["HTML", "CSS", "JavaScript", "TypeScript", "PHP"]
```

#### pop

O método `pop()` remove o último elemento de um array.

- Ele decrementa o comprimento do array em 1.
- Ele retorna o valor do elemento que foi removido.

```js
let pilha = ["Primeiro", "Segundo", "Terceiro"];

let elementoRemovido = pilha.pop();

console.log(pilha);            // Saída: ["Primeiro", "Segundo"]
console.log(elementoRemovido); // Saída: "Terceiro"
```

#### shift

O método `shift()` remove o primeiro elemento de um array.

- Ele desloca todos os elementos subsequentes uma posição abaixo para ocupar o espaço vago no início do array.
- Ele reduz o comprimento do array em 1 e retorna o valor do elemento removido.


```js
let fila = ["Cliente 1", "Cliente 2", "Cliente 3"];

let atendido = fila.shift();

console.log(fila);     // Saída: ["Cliente 2", "Cliente 3"]
console.log(atendido); // Saída: "Cliente 1"
```

#### unshift

---
O método unshift() adiciona um ou mais elementos ao início de um array.

- Ele desloca os elementos existentes para índices superiores para abrir espaço aos novos itens.
- Ele retorna o novo comprimento do array após a inserção.

```js
let numeros = [3, 4, 5];

let novoComprimento = numeros.unshift(1, 2);

console.log(numeros);         // Saída: [1, 2, 3, 4, 5]
console.log(novoComprimento); // Saída: 5
```

---
Esses nomes um tanto bobos são os termos tradicionais para operações em uma pilha. Uma pilha, em programação, é uma estrutura de dados que permite empurrar valores para dentro dela e retirá-los na ordem inversa, de modo que o que foi adicionado por último é removido primeiro. Pilhas são comuns em programação

---
### Loops de arrays

As estruturas de repetição permitem iterar sobre coleções de dados. É fundamental diferenciar o controle por índice numérico (for clássico), a iteração por valores (for...of) e a iteração por chaves/propriedades (for...in).

#### For com length

O laço for tradicional utiliza uma variável contadora para acessar os elementos através de seus índices numéricos, iterando de 0 até o limite definido pela propriedade length (array.length - 1).

- Principal característica: Oferece controle total sobre o índice e a ordem de iteração (permite saltar elementos, iterar de trás para frente, etc.).

- Caso de uso ideal: Quando é necessário manipular o índice diretamente ou modificar os elementos originais do array nas posições específicas.

```js
const tecnologias = ["HTML", "CSS", "JavaScript"];

// Iterando com base no tamanho do array (length)
for (let i = 0; i < tecnologias.length; i++) {
    console.log(`Índice ${i}: ${tecnologias[i]}`);
}
```

#### For...of

Introduzido no ES6, o laço for...of percorre diretamente os valores (elementos) de estruturas de dados iteráveis (Arrays, Strings, NodeLists do DOM, Maps e Sets).

- Principal característica: Sintaxe limpa e legível que elimina a necessidade de gerenciar variáveis contadoras ou acessar a propriedade length manualmente.
- Caso de uso ideal: Leitura de elementos de um array ou lista de elementos HTML selecionados do DOM quando o número do índice não é relevante.

```js
const tecnologias = ["HTML", "CSS", "JavaScript"];

// A variável 'tech' recebe o VALOR de cada elemento a cada iteração
for (let tech of tecnologias) {
    console.log(`Tecnologia: ${tech}`);
}
```

#### For...in

O laço for...in foi projetado para percorrer as chaves (nomes de propriedades enumeráveis) de um objeto.

- Principal característica: Em arrays, ele itera sobre os índices, mas os retorna como o tipo String ("0", "1", "2") e não como Number.
- Caso de uso ideal: Inspeção de propriedades em objetos literais ({}).

```js
const curso = {
    nome: "Técnico em Desenvolvimento de Sistemas",
    uc: "Programação Front-end",
    cargahoraria: 120
};

// A variável 'chave' recebe o NOME DA PROPRIEDADE
for (let chave in curso) {
    console.log(`${chave}: ${curso[chave]}`);
}
```

### Mais métodos de arrays

- slice
- splice
- concat
- indexOf
- includes
- join

## Considerações finais

Esta foi uma breve introdução à arrays em JavaScript, e por consequência a tópicos que tangenciam nosso próximo assunto, objetos.

Pratique a manipulação de arrays pois é uma habilidade essencial para a construção de programas mais interessantes e eficientes.