# Exercícios

## Funções

Faça os exercícios a seguir escrevendo código JavaScript a ser vinculado à sua página HTML com a tag `<script>`.

- Utilize a função `prompt()` para capturar dados do usuário
- Utilize as funções `prompt()` ou `confirm()` para capturar entradas do usuário
- Utilize as funções `alert()` ou `console.log()` para exibir saídas ao usuário
- Faça a verificação se o tipo de dado adequado foi inserido
- Utilize a conversão de tipos, implícita ou explícita, conforme necessidade, em cada exercício
- Os exercícios a seguir NÃO precisam necessariamente que dados sejam fornecidos pelo usuário
- As funções podem ser testadas e invocadas por vocês mesmos no código a fim de testar os seus resultados
- Você pode utilizar tanto DECLARAÇÃO DE FUNÇÃO quanto EXPRESSÃO DE FUNÇÃO

### Essenciais

1. Crie uma função que receba três números como parâmetros e determine qual é o maior entre eles. Determine qual o maior entre eles e imprima-o no console.
2. Escreva uma função chamada `concatenar3` que aceita 4 parâmetros, sendo os três primeiros palavras a serem concatenadas, e o quarto o separador que será utilizado entre elas. Retorne as palavras concatenadas, com o separador entre elas. Defina o valor padrão do parâmetro separador como `“ | “`.
3. Escreva uma função que recebe um número de minutos como parâmetro e retorna a representação do mesmo tempo em horas.
4. Você está indo de carro para uma nova cidade para uma pequena viagem de fim de semana. Escreva uma função chamada `retornarQuantidadeDeGasolina` que receba dois números como parâmetros:
	- o número de quilômetros até o seu destino
	- o consumo médio em litros por 100 km

	A função deve retornar a quantidade de gasolina necessária para completar toda a viagem de ida e volta.

5. Escreva um programa que contenha as seguintes funções aplicáveis a um sistema de loja virtual/financeiro:

	5.1 **Exibir produto com preço** - a função deve receber 2 (dois) parâmetros, o nome de um produto e o preço do produto, ela deve exibir no console o nome do produto seguido do preço com símbolo monetário, aproximadamente assim:
		
	`Jaqueta Jeans …………………………… R$ 220,00`
	
	5.2 **Preço da parcela** - a função deve receber 2 (dois) parâmetros: o preço total do pedido, e a quantidade de parcelas. O número máximo de parcelas deve ser 12. O número padrão de parcelas deve ser 1. A função deve retornar o preço da parcela, caso o segundo parâmetro seja maior que 12, o preço total deve ser retornado.

	5.3 **Aplicar desconto** - a função deve receber 2 (dois) parâmetros: o valor total do pedido, e um segundo parâmetro um desconto. A função deve retornar o preço com o desconto decrescido, caso o desconto seja maior que o valor total do pedido, o valor a ser retornado deve ser 0.

	5.4 **Aplicar cupom de desconto** - a função deve receber 2 (dois) parâmetros: o valor total do pedido, e um segundo uma string. A função deve verificar se a string passada é: `CUPOM50`, `CUPOM100` ou `CUPOM200`. Caso seja `CUPOM50`, deve ser invocada a função de aplicação do desconto passando como parâmetro de desconto o valor 50. O resultado retornado da função de aplicação de desconto deve ser retornado. Caso seja `CUPOM100`, deve ser invocada a função de aplicação do desconto passando como parâmetro de desconto o valor 100. O resultado retornado da função de aplicação de desconto deve ser retornado. Caso seja `CUPOM200`, deve ser invocada a função de aplicação do desconto passando como parâmetro de desconto o valor 200. O resultado retornado da função de aplicação de desconto deve ser retornado. Caso não seja nenhum dos 3 (três), a função deve retornar o valor total.
