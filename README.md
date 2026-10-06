# [NOME DA DISCIPLINA]

<table style="width: 100%;">
    <tbody>
		<tr>
            <th rowspan="2" scope="col">
                <img width="100" src="https://thumb.wikimedia.org/wikipedia/commons/thumb/f/f5/IFSP_Logo.jpg/250px-IFSP_Logo.jpg" alt="Instituto Federal São Paulo" />
            </th>
            <th scope="col">Curso</th>
            <th scope="col">Sigla</th>
            <th scope="col">Professores</th>
        </tr>
        <tr>
            <td>[NOME DO CURSO]</td>
            <td>[SIGLA]</td>
            <td><a href="https://allysonsouza.com.br/" target="_blank" rel="noopener noreferrer">Allyson Souza</a></td>
        </tr>
    </tbody>
</table>

<hr style="border-color: #379936; margin: 2em 0;"/>

Este repositório é destinado a armazenar exemplos programados em sala, exercícios, bem como demais materiais didáticos relacionados ao curso/unidade curricular/disciplina. O repositório pode ser **"forkado"** (_bifurcado_) pelos estudantes para terem acesso ao conteúdo e desenvolverem suas atividades no diretório `📁 aluno`, o qual sempre permanecerá vazio no repositório original.

## Estrutura de pastas 📁
```
	📁 aluno/         /* Pasta destinada aos estudantes para colocarem seus exercícios. Este diretório NÃO será atualizado no repositório original alunos devem commitar suas soluções em seus próprios forks/clones. */
	📁 aulas/         /* Pastas com exemplos de sala de aula. */
	📁 conteudo/      /* Material e notas da disciplina. */
	📁 exercicios/    /* Exercícios por tema. */
	📄 LICENSE        /* Licença do repositório. */
	📄 README.md      /* Documento principal com instruções e links. */
```

## Criando fork (bifurcação) 🔀

Criar um fork irá criar um novo repositório idêntico a este, mas na sua conta, para isso, clique no botão `Fork` na área superior e siga as instruções.

Depois do fork criado, você deve clonar o projeto (o fork, e não este repositório) para a sua máquina para trabalhar localmente nele, usando o GitHub Desktop, outro app de interface gráfica Git ou a linha de comando, o que preferir.

## Fazendo os exercícios 📝

Há uma pasta específica em que deve armazenar os arquivos de seus exercícios, a pasta `📁 aluno`. Ela é e sempre será vazia no repositório original, então você pode realizar suas alterações, comitar e enviar **para o seu repositório**, que assim dificilmente terá conflitos ao sincronizar qualquer atualização do repositório original.

## Sincronizando 🔂

O GitHub irá gerenciar caso haja alterações a serem sincronizadas no seu fork. Para verificar se há alterações, procure pelo botão `Fork Sync` na região superior da página do seu repositório. Clique no botão para atualizar e se tudo der certo, os commits feitos no repositório original serão puxados para o seu repositório.

## Glossário 📖

-   **Ahead**: indica que o repositório local possui commits que ainda não estão presentes no repositório remoto. Significa que você tem alterações locais que precisam ser enviadas (push) para o repositório remoto.

-   **Behind**: indica que o repositório remoto possui commits mais recentes que não estão presentes no repositório local. Significa que você precisa buscar e integrar (pull) as atualizações do repositório remoto.

-   **Commit**: conjunto de alterações realizadas em um repositório Git, associados a uma mensagem que o identifica (um "marco" na linha do tempo do projeto).

-   **Conflict**: situação que ocorre quando o Git não consegue automaticamente mesclar alterações de diferentes branches ou commits, geralmente quando as mesmas linhas de código foram modificadas de formas diferentes. Requer intervenção manual para resolver.

-   **Fork**: um fork é uma cópia do repositório (inteiro ou de algumas ramificações (branchs) específicas), que mantém a referência ao repositório original, permitindo a colaboração com o repositório original, enviando ou recebendo atualizações.

-   **Merge**: processo de integrar alterações de uma branch para outra, combinando o histórico de commits de ambas as branches em uma única linha de desenvolvimento.

-   **Pull**: comando que busca (fetch) as alterações mais recentes do repositório remoto e automaticamente as integra (merge) ao branch local atual.

-   **Pull Request**: solicitação para integrar alterações de uma branch para outra (geralmente para a branch principal). Permite revisão de código, discussão e aprovação antes da integração das alterações.

-   **Push**: comando que envia os commits locais para o repositório remoto, atualizando o repositório remoto com as alterações feitas localmente.

-   **Sync**: processo de sincronização entre repositório local e remoto, garantindo que ambos tenham as mesmas alterações atualizadas. Pode envolver tanto pull quanto push dependendo da situação.
