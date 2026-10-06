Este é o único operador ternário (que opera sobre três operandos) no JavaScript e, por vezes, é chamado justamente de operador ternário.

Como esse operador tem três operandos, o primeiro vem antes da **?**, o segundo fica entre a **?** e o **:**, e o terceiro vem depois dos **:**. Ele é usado assim:

```js
// X é um número positivo?
x > 0 ? true : false 
```

Os operandos do ternário podem ser de qualquer tipo. O primeiro operando é avaliado e interpretado como um **valor booleano**. Se o valor do primeiro operando for verdadeiro, então, o segundo operando é retornado. Caso contrário, se o primeiro operando for falso, então o terceiro operando é retornado. 

Embora seja possível obter resultados semelhantes usando a instrução `if`, o operador ternário ( `?:`) costuma oferecer um atalho prático.

Aqui está um exemplo típico de uso, que verifica se uma variável está definida (e possui um valor significativo e verdadeiro) e a utiliza, caso esteja, ou fornece um valor padrão caso contrário:

```js
mensagem = "Bem-vindo, " + (username ? username : "meu patrão") + "!";
```

Sem o ternário, este código ficaria assim:

```js
mensagem = "Bem-vindo, "
if ( username ) {
	mensagem = mensagem + username + "!";
} else {
	mensagem = mensagem + "meu patrão!"
}
```

## Ternários aninhados

Colocar um ternário dentro de outro (`? ... ? ... : ... : ...`) cria uma espécie de quebra-cabeça visual. Mesmo programadores experientes gastam tempo extra para identificar a qual condição cada. Cuidado com o seu uso.