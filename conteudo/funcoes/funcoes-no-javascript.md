# Funções no JavaScript

O texto abaixo foi elaborado com muitos trechos de suas referências, literalmente traduzidas para o português, com o intuito de deixar um tópico bastante vasto da linguagem JavaScript, mais acessível para os leitores do idioma. Nem todos os aspectos são cobertos, mas alguns que julguei mais essenciais para quem está começando a estudar funções em JavaScript.

# Funções

Uma função é um bloco de código JavaScript que é definido uma única vez, mas pode ser executado, ou invocado, quantas vezes forem necessárias.

As funções do JavaScript são parametrizadas: uma definição de função pode incluir uma lista de identificadores, conhecidos como parâmetros, que funcionam como variáveis locais para o corpo da função. As invocações de função fornecem valores, ou argumentos,
para os parâmetros da função. As funções costumam usar os valores de seus argumentos para calcular um valor de retorno que se torna o valor da expressão de invocação da função. Além dos argumentos, cada invocação possui outro valor — o contexto de invocação — que é o valor da palavra-chave `this`.

No JavaScript, as funções são objetos e podem ser manipuladas por programas. O JavaScript permite atribuir funções a variáveis e passá-las para outras funções, por exemplo. Como as funções são objetos, é possível definir propriedades nelas e até mesmo invocar métodos nelas.

As definições de funções em JavaScript podem ser aninhadas dentro de outras funções e têm acesso a quaisquer variáveis que estejam no escopo em que são definidas. Isso significa que as funções em JavaScript são **closures**, o que possibilita técnicas de programação importantes e poderosas.

## Declaração de funções

A definição da função (também chamada de declaração de função) consiste no uso da palavra chave function, seguida por:

- Nome da Função.
- Lista de argumentos para a função, entre parênteses e separados por vírgulas.
- Declarações JavaScript que definem a função, entre chaves { }.

Por exemplo, o código a seguir define uma função simples chamada _hello_:

```js
function hello(nome) {
	return console.log(`Olá, ${nome}! Seja bem-vindo!`);
}
```

A instrução `return` especifica o valor retornado pela função.

A função pode então ser invocada utilizando o nome (ou identificador) que associamos a ela, no caso, `hello`.

```js
hello("Ada")
```

## Expressões de funções

Funções também podem ser criadas por uma expressão de função, que pode ser então atribuída à uma **variável** ou **constante**. As expressões de função não precisam necessariamente ter um nome, podendo ser assim, **funções anônimas**.

Vejamos a mesma função _hello_ como poderia ficar:

```js
let cumprimentar = function (nome) {
	return console.log(`Olá, ${nome}! Seja bem-vindo!`);
}
```

Ao atribuirmos uma função à uma variável, utilizaremos o nome da variável para invocá-la posteriormente:

```js
cumprimentar("Ada")
```

## Funções flecha (_arrow functions_)

Existe uma terceira notação para funções, que parece muito diferente das outras. Ao invés da palavra-chave function, ela usa uma seta (`=>`) composta por um sinal de igual e um caractere de maior-que (não confundir com o operador maior-ou-igual, que é escrito `>=`):

```js
const media = (n1, n2) => {
	return (n1 + n2) / 2
};
```

A seta vem após a lista de parâmetros e é seguida pelo corpo da função. Expressa algo como “esta entrada (os parâmetros) produz este resultado (o corpo)”.

Quando há apenas um nome de parâmetro, você pode omitir os parênteses ao redor da lista de parâmetros. Se o corpo for uma única expressão em vez de um bloco entre chaves, essa expressão será retornada pela função. Então, estas duas definições de `quadrado`, que retorna um número elevado ao quadrado, fazem a mesma coisa:

```js
const quadrado = (x) => { return x * x; };
const quadrado = x => x * x;
```

Quando uma arrow function não tem parâmetros, sua lista de parâmetros é apenas um conjunto vazio de parênteses.

```js
const latir = () => {
  console.log("Roof! Roof!");
};
```

Não há razão profunda para ter tanto arrow functions quanto expression function na linguagem. Além de um detalhe menor, que discutiremos adiante, elas fazem a mesma coisa. Arrow functions foram adicionadas em 2015, principalmente para tornar possível escrever pequenas expressões de função de forma menos verbosa.

## Argumentos e Parâmetros

**Parâmetro** é a variável que irá receber um valor em uma função, enquanto que um **argumento** é o valor que você passa para a função, em sua invocação.

Você então passa **argumentos**, que são recebidos em **parâmetros** na função.

### Argumentos opcionais

Quando invocamos uma função passando mais argumentos do que a função possui de parâmetros definidos, ela não reclama ou dispara erros. Ela simplesmente ignora os argumentos extras e executa com os necessários.

JavaScript é extremamente tolerante quanto ao número de argumentos que você pode passar para uma função. Se você passar muitos, os extras são ignorados. Se passar poucos, os parâmetros faltantes recebem o valor `undefined`.

A desvantagem disso é que é possível — provável, até — que você acidentalmente passe o número errado de argumentos para funções. E ninguém lhe dirá sobre isso. A vantagem é que você pode usar esse comportamento para permitir que uma função seja chamada com diferentes números de argumentos.

### Valor padrão de parâmetros

Se você escrever um operador = após um parâmetro, seguido de uma expressão, o valor dessa expressão substituirá o argumento quando ele não for fornecido.

Futuramente iremos aprender uma forma pela qual o corpo de uma função pode obter a lista completa de argumentos que lhe foi passada. Isso é útil porque permite que uma função aceite qualquer número de argumentos. Por exemplo, console.log faz isso, exibindo todos os valores que lhe são dados:

```js
console.log("C", "O", 2);
// → C O 2
```

### Parâmetros restantes

Os valores padrão dos parâmetros nos permitem escrever funções que podem ser chamadas com menos argumentos do que parâmetros. 

Os parâmetros restantes permitem o caso oposto: eles nos permitem escrever funções que podem ser chamadas com um número arbitrariamente maior de argumentos do que parâmetros.

Aqui está um exemplo de função que espera um ou mais argumentos numéricos e retorna o maior deles:

```js
function max(first=-Infinity, ...rest) {
	let maxValue = first; // Começamos assumindo que o primeiro argumento é o maior da lista
	
	// Percorre todos os argumentos restantes, procurando por maiores que o primeiro
	for(let n of rest) {
		if (n > maxValue) {
			maxValue = n;
		}
	}
	
	// Retorna o maior valor
	return maxValue;
}
max(1, 10, 100, 2, 3, 1000, 4, 5, 6) // => 1000
```

Um parâmetro “rest” é precedido por três pontos e deve ser o último parâmetro em uma declaração de função. Ao chamar uma função com um parâmetro “rest”, os argumentos passados são primeiro atribuídos aos parâmetros que não são “rest” e, em seguida, quaisquer argumentos restantes (ou seja, o “restante” dos argumentos) são armazenados em um array que se torna o valor do parâmetro “rest”. 

Esse último ponto é importante: dentro do corpo de uma função, o valor de um parâmetro “rest” será sempre um array. O array pode estar vazio, mas um parâmetro “rest” nunca será indefinido (Consequentemente, nunca é útil — nem válido — definir um valor padrão para um parâmetro “rest”)

Não confunda o `...` que define um parâmetro residual na definição de uma função com o operador de expansão (_spread operator_) `...`.

### Tipos de argumento

Em JavaScript não temos tipos declarados, e não é realizada nenhuma verificação de tipo nos valores que passamos para uma função. Você pode ajudar a tornar seu código auto-documentado escolhendo nomes descritivos para os argumentos das funções e documentando-os cuidadosamente nos comentários de cada função.

O JavaScript realiza conversões de tipo flexíveis conforme necessário. Portanto, se você escrever uma função que espera um argumento do tipo string e, em seguida, chamar essa função com um valor de outro tipo, o valor passado será simplesmente convertido em uma string
quando a função tentar usá-lo como uma string.

## Funções como namespace

As variáveis declaradas dentro de uma função não são visíveis fora dela. Por esse motivo, às vezes é útil definir uma função simplesmente para que ela funcione como um espaço de nomes temporário, no qual é possível definir variáveis sem sobrecarregar o espaço de nomes global.

Suponha, por exemplo, que você tenha um trecho de código JavaScript que deseja usar em vários programas diferentes de JavaScript (ou, no caso de JavaScript do lado do cliente, em várias
páginas da web diferentes). Suponha que esse código, como a maioria dos códigos, defina variáveis para armazenar os resultados intermediários de seus cálculos. O problema é que, como esse trecho
de código será usado em muitos programas diferentes, você não sabe se as variáveis que ele cria entrarão em conflito com as variáveis criadas pelos programas que o utilizam.

A solução é colocar o trecho de código dentro de uma função e, em seguida, chamar a função. Dessa forma, as variáveis que seriam globais passam a ser locais à função:

```js
function trechoEmNamespace() {
	// Código no Namespace vai aqui
	// Qualquer variável definida aqui serão locais a esta função
	// ao invés de poluir o escopo global do programa
}
trechoEmNamespace(); // But don't forget to invoke the function!
```

## Closures

Closures são um dos recursos mais poderosos de JavaScript. JavaScript permite o aninhamento de funções e garante acesso completo à função interna a todas as variáveis e funções definidas dentro da função externa (e todas as outras variáveis e funções que a função externa tem acesso). No entanto, a função externa não tem acesso às variáveis e funções definidas dentro da função interna.

```js
function criarPartida(nomeDaPartida){
  let gols = 0;

  return function marcarGol(){
    golsMarcados++;
    return `A partida ${nomeDaPartida} tem ${gols} gols marcados.`
  }
}

const classico = createPartida('Corinthians x Palmeiras');
```

## Considerações finais

Este texto cobre alguns aspectos essenciais sobre funções no JavaScript, mas está longe de cobrir em riqueza de detalhes e maior aprofundamento técnico, e mesmo em riqueza de exemplos.

Portanto, é imprescindível continuar estudando o assunto, buscando a leitura das fontes referenciadas e de outras, bem como exercitando a prática no uso de funções em programas a serem escritos na linguagem. Assunto como closures, higher-order functions e memoização são alguns tópicos interessantes que não foram cobertos.

Mas espero que tenha sido uma introdução útil aos novos programadores na linguagem JavaScript.

# Referências

FLANAGAN, David. **JavaScript: the definitive guide**. 7. ed. Sebastopol: O'Reilly Media, 2020. p. 200-237.

HAVERBEKE, Marijn. **Functions**. In: ______. **Eloquent JavaScript: a modern introduction to programming**. 4. ed. San Francisco: No Starch Press, 2024. cap. 3.

BOS, Wes. **Closures**. Disponível em: https://wesbos.com/javascript/03-the-tricky-bits/closures#examples-of-closures. Acessado em: 02 de agosto de 2026

Mozilla Developer Network. **Funções**. Disponível em: https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Guide/Functions. Acessado em: 02 de agosto de 2026.