# Exercícios

## Objetos

Faça os exercícios a seguir escrevendo código JavaScript a ser vinculado à sua página HTML com a tag `<script>`.


1. Escreva um programa que declara dois objetos literais `produto`, com as propriedades `nome (string)`, `preco (number)`, `categoria (string | "Laticínios", "Hortifruti", "Pães", "Bebidas", etc.)`. Escreva uma função que recebe dois produtos como parâmetros e exibe no console qual é o produto mais caro, seu nome e categoria.

2. Escreva um programa que declara um objeto literal `aluno`, com as propriedades `nome, idade, curso` e `notas`, que deve ser um array de _n_ números de 0 a 10. Escreva uma função que recebe o objeto como parâmetro e calcula a média de nota do aluno, independente de quantos elementos sua propriedade `notas` possui.
	- Adicione a propriedade `media` ao objeto, com o valor da média que foi calculada;

3. Escreva um programa que declara um objeto carro, com as propriedades `nome (string)`, `cor (string)`, `modelo (string)` e `opcionais (object)`, contendo `ar condicionado (boolean)`, `direção helétrica (boolean)` e `multimídia (boolean)`.
	- Escreva uma função que recebe o carro como parâmetro e exibe seus detalhes
	- Escreva uma função que recebe o carro (`object`), o nome de um opcional (`string`) e um booleano como parâmetro para adicionar/remover um opcional do carro

4. Em um sistema legado de e-commerce estão sendo retornados por `endpoints` distintos os dados de vendas (`preço`, `categoria`, `marca`) e os dados de estoque (`estoque`, `peso`). Escreva um programa que consolide os dados dos produtos em um objeto por produto.

```js
const produtos_vendas = {
	cafes: [
		{
			sku: 7654,
			marca: "Povo Brasileiro",
			preco: 24.00,
			categoria: "Mercearia"
		},
		{
			sku: 8765,
			marca: "Soberano - Gourmet",
			preco: 29.00,
			categoria: "Mercearia",
		},
		{
			sku: 3467,
			marca: "Dose Certa",
			preco: 27.00,
			categoria: "Mercearia"
		}
	]	
}

const produtos_estoque = {
	cafes: [
		{
			sku: 3467,
			peso: 500.00,
			unidade: "mg",
			estoque: 101
		},
		{
			sku: 7654,
			peso: 250.00,
			unidade: "mg",
			estoque: 182
		},
		{
			sku: 8765,
			peso: 250.00,
			unidade: "mg",
			estoque: 46
		}
	]
}
```

5. Dado um objeto `carrinho`, que representa um carrinho de compras em um sistema, adicione os métodos:
	- `adicionarProduto()`: que aceite três parâmetros, `nome`, `preco`e `quantidade`. Adicione o produto no array da propriedade `itens`, caso ele não esteja no carrinho ainda, do contrário, aumente a quantidade, caso ele já esteja.
	- `calcularTotal()`: calcule o preço total da compra, percorrendo os produtos na propriedade itens, e armazene em uma nova propriedade do carrinho.
	- `aplicarDesconto()`: que aceita um parâmetro, `cupom`. Verifique se o cupom passado é um dos cupons válidos na propriedade `cupons`, armazene o cupom utilizado em uma nova propriedade do objeto e modifique o preço total da compra para ter 10% de desconto.
	- `exibirCupom()`: Exiba em detalhes um cupom no console, com dados do cliente, lista de produtos, quantidades e preço, preço total e se houve cupom aplicado ou não.

```js
const carrinho = {
	cliente: "Alice",
	itens: [
	{ nome: "Smartphone", preco: 2200, quantidade: 1 },
	],
	cupons: ["MENOS10", "PROMO10", "10PORCENTO"]
}
```