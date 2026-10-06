# Exercícios

## Eventos

Faça os exercícios a seguir escrevendo código JavaScript a ser vinculado à sua página HTML.

1. **Pets `📁 pets/`**: escreva um script que adiciona eventos aos botões 'Ver cachorro' e 'Ver gato'. Ao clicar em ver cachorro, uma foto de cachorro deve ser exibida, ao clicar em ver gato, uma foto de gato deve ser exibida. Ao clicar em mudar background, a cor de fundo da página deve alternar entre 5 cores possíveis (armazene as cores em um array com hexadecimais, por exemplo: `['#06F874', '#8706f8', '#f806a7', '#f80606', '#f8e806']`).

2. **Sidebar `📁 sidebar/`:** escreva um programa que adiciona um evento ao elemento `.toggle` para alternar a posição da barra lateral (sidebar), adicionando/removendo a classe `.open`.

3. **Balão `📁 balao/`**: escreva uma página que exiba um balão (usando o emoji de balão, 🎈). Quando você pressionar a seta para cima, ele deve inflar (crescer) 10 por cento. Quando pressionar a seta para baixo, ele deve desinflar (encolher) 10 por cento.

- Você pode controlar o tamanho do texto (emojis são texto) definindo a propriedade CSS font-size (style.fontSize) no seu elemento pai. Lembre-se de incluir uma unidade no valor — por exemplo, pixels (10px).

- Os nomes das teclas de seta são "ArrowUp" e "ArrowDown". Certifique-se de que as teclas mudem apenas o balão, sem rolar a página.

- Quando tiver isso funcionando, adicione uma funcionalidade onde, se você inflar o balão além de um certo tamanho, ele “explode”. Neste caso, explodir significa que ele é substituído por um emoji 💥, e o manipulador de evento é removido (para que você não possa inflar ou desinflar a explosão).

4. **Baralho `📁 baralho/`:** escreva um código que adiciona um evento ao baralho exibido, fazendo com que uma carta seja comprada a partir do array de objetos no `baralho.js`. Inclua a carta sorteada na página e remova-a do array.

    - Para sortear a carta, utilize o método [Math.random()](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/Math/random)

5. **Vinte e um:** com base em no exercício anterior, implemente um jogo de 21 para 2 jogadores.
    - Cada jogador deve iniciar recebendo duas cartas
    - A mesa vira uma carta
    - Cada jogador escolhe comprar mais uma carta ou não em seu turno
    - Caso um jogador estoure (passe de 21), o outro deve ser considerado ganhador da rodada
    - A carta da mesa é virada
    - Verifique novamente se algum jogador, somando a carta da mesa, estourou, senão quem chegou mais próximo de 21
