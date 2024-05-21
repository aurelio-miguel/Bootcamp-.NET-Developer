# Introdução

## Introdução SQL
A linguagem SQL(Structured Query Language) é uma linguagem de banco de dados usada para consulta e manipulação de dados. Quase todos os bancos de dados relacionais utilizam a linguagem SQL, os comandos serão os mesmos independente do banco de dados. 

A linguagem SQL é simples e de alto nível, os comandos são de fácil entendimento. 

A linguagem de SQL é uma linguagem de banco de dados e ela possui alguns comandos, os comandos são separados em 5 categorias que estão representadas como os primeiros elementos logo abaixo do bloco **SQL Commands**
![Imagem com a estrutura de comandos SQL](/imagens/comandos%20sql.png)

## Entendendo um database
Database é uma coleção de dados estruturados, agrupados de forma consisa. É composto de tabelas, procedures, views, etc.

Na imagem abaixo podemos ver dois databases, um com o nome "AdventureWorks2016" e outro com o nome "SistemaVendas".

![Exemplo database](/imagens/exemplo%20database.png)

Um banco de dados será separado por databases e dentro desses databases teremos as tabelas, procedures, views, etc. Podemos utilizar um único servidor de banco de dados para armazenar dados de diferentes sistemas através dos databases.

Os databases vão armazenar os dados de um sistema em específico, onde cada database vai ter os seus dados em específicos. 

Sempre que for trabalhar com um banco de dados, além de indicador o servidor que conectaremos, também precisaremos indicar qual database utilizaremos.

## Acessando o banco de dados
O primeiro passo vai ser abrir o Managemente Studio, após realizar a conexão conseguiremos ver a tela do programa e também o nosso servidor, conforme indicado na imagem abaixo:

![Imagem do servidor no Management Studio](/imagens/servidor%20no%20management%20studio.png)
O servidor que estamos conectados é o `localhost\sqlexpress`

Nessa mesma área podemos ver os nossos databases:

![Imagem com os databases no Management Studio](/imagens/databases%20no%20management%20studio.png)

### Criando um database
Para criar um database, basta clicar com o botão direito do mouse no item "Banco de dados" e depois clicar na opção "Novo banco de dados"

![Imagem exemplificando a criação de um novo database](/imagens/criando%20um%20novo%20database.png)

Na nova tela basta inserir o nome do seu banco de dados e depois clique em "OK", conforme a imagem abaixo:

![Imagem mostrando a inserção do nome do banco de dados](/imagens/criando%20o%20banco%20de%20dados%20e%20inserindo%20o%20nome.png)

Após isso o nosso banco de dados vai estar criado e poderemos visualizar os diagramas, tabelas, views, etc. Conforme a imagem abaixo:

![Visualizando o nosso novo banco de dados](/imagens/banco%20de%20dados%20criado.png)

### Fazendo a primeira consulta
Para fazer uma consulta no nosso banco de dados, precisaremos acessar a funcionalidade de querys no Management Studio, para isso basta clicar no botão "Nova Consulta", conforme indicado na imagem abaixo:

![Imagem indicando o botão para a área de consulta](/imagens/nova%20consulta%20no%20management%20studio.png)

Na nova área você poderá escrever as consultas. 

Para executar uma consulta, certifique-se de que o banco de dados correto esteja selecionado, para executar a consulta basta selecionar com o mouse todo o texto da sua consulta e depois clicar no botão "Executar", conforme a imagem abaixo:

![Imagem indicando como realizar uma consulta](/imagens/executando%20uma%20consulta.png)

## Comando SELECT
O comando SELECT tem como finalidade selecionar dados de uma tabela, nos exemplos abaixo iremos selecionar os dados da tabela **Clientes** do banco de dados **ExemploDB**.

Segue abaixo o comando SQL para selecionar todos os clientes que estão inseridos no banco de dados:
```
SELECT * FROM Clientes
```
O SQL não é case sentitive, ele não vai interpretar de forma diferente se algo for escrito em letra maiúscula ou não. No comando acima temos o comando `SELECT` indicando que queremos selecionar, após isso temos o caractere `*` indicando que queremos selecionar todas as colunas da tabela e após isso temos o `FROM Clientes` que indica de qual bando de dados queremos selecionar.

Ao executar esse comando será mostrado para nós uma grid de resultados, conforme a imagem abaixo:

![Imagem com o resultado da query](/imagens/resultado%20da%20query.png)

## Ordenando os resultados
Aliado com o SELECT podemos ordenar a exibição dos dados em uma ordem crescente ou decrescente. 

Com o comando abaixo podemos por exemplo ordenar a exibição dos nossos dados em ordem  crescente:
```
SELECT * FROM Clientes
ORDER BY Nome 
```
Primeiro selecionamos a exibição de todas as colunas da tabela cliente e com o `ORDER BY nome_coluna` podemos ordenar a exibição em ordem crescente com base na coluna que desejarmos. Para ordenar por ordem decrescente, basta inserir a palavra `DESC` após o nome da coluna, por exemplo `ORDER BY Nome DESC`, dessa forma ele vai selecionar por ordem decrescente dos nomes.

Para ordenar mais de uma coluna ao mesmo tempo, podemos passar por vírgula as colunas que desejamos ordenar, por exemplo `ORDER BY Nome, Sobrenome`. Dessa forma teremos uma ordenação crescente com base no nome e sobrenome.

## Selecionando colunas
Agora vamos ver como podemos selecionar determinadas colunas na consulta. Até o momento estavamos trabalhando com o `*` para selecionar as colunas, isso faz com que todas as colunas sejam selecionadas e exibidas.

Para que possamos selecionar determinadas colunas para serem exibidas, basta substituir o asterístico pelo nome da coluna que desejamos selecionar. Caso tenhamos interesse em selecionar mais de uma coluna, basta separar as colunas utilizando a vírgula. Segue abaixo um trecho de código exemplificando isso:
```
SELECT Nome FROM Clientes
```
Para selecionar mais de uma podemos utilizar substituir o `Nome` por `Nome, Sobrenome`. Dessa forma será selecionado as colunas Nome e Sobrenome da nossa base de dados.

Sempre que precisamos de informações específicas, é uma boa pratica utilizar esse tipo de consulta pois ela possui uma maior performance e também pelo fato de não ser tão interessante trafegar dados que não iremos utilizar. 

## Utilizando o WHERE
O WHERE é uma cláusula que podemos utilizar quando desejamos filtrar determinados tipos de dados. Podemos por exemplo trazer clientes específicos utilizando essa cláusula.

No exemplo abaixo vamos selecionar todos os clientes que possuem o valor AceitaComunicados como zero na nossa base de dados:
```
SELECT * FROM Clientes
WHERE AceitaComunicados = 0
```
Com o comando acima nós selecionamos todas as colunas de todos os clientes que o valor da coluna AceitaComunicados é igual a zero.

Podemos também filtrar com base nos dados que possuem strings, dessa forma utilizaremos as aspas simples, conforme o exemplo abaixo:
```
SELECT * FROM Clientes
WHERE Nome = 'Maria'
```
Com o comando acima vamos selecionar todas as colunas de todos os clientes que possuem o nome Maria.

Após a estrutura do WHERE podemos inserir também o ORDER BY, ele deve ser inserido depois por que primeiro vai ser feito a filtragem e só após a filtragem que é feito o ordenamento. 

### WHERE e AND
Podemos a cláusula WHERE e o AND para filtrar duas informações ao mesmo tempo. Segue abaixo um trecho de código exemplificando a consulta:
```
SELECT * FROM Clientes
WHERE Nome = 'Adam' AND Sobrenome = 'Reynolds'
```
Dessa forma estaremos filtrando todos os clientes que possuem o primeiro nome 'Adam' e o sobrenome 'Reynolds'. Se um cliente tiver o nome 'Adam Miguel', ele não será selecionado nessa consulta.

### WHERE e OR
Com o WHERE e o OR poderemos filtrar os clientes que atenderem uma das filtragens, não precisando necessariamente que ele faça parte das duas filtragens que é o caso do AND.

Segue abaixo um exemplo disso:
```
SELECT * FROM Clientes
WHERE Nome = 'Adam' OR Nome = 'Sebastião'
```
Com o OR será possível filtrar os clientes que possuem o nome 'Adam' OU 'Sebastião'.

## Utilizando o LIKE
O LIKE é utilizado para filtrar as linhas com base em uma busca parcial nos dados. Podemos por exemplo filtrar todos os clientes em que o nome começa com a letra 'G'.

Para isso, podemos utilizar o trecho de código abaixo:
```
SELECT * FROM Clientes
WHERE Nome LIKE 'G%'
```
Com base no comando acima, filtramos todos os clientes que iniciam com a letra g, no local do operador de igualdade utilizamos a palavra `LIKE`. Percebam que na consulta acima utilizamos o caractere especial de porcentagem, esse caractere `%` significa que tem que ter a letra 'G' no começo e o que estiver adiante não importa. 

Seguindo a mesma lógica, podemos inserir o caractere especial `%` antes e depois do 'G' `WHERE Nome LIKE '%G%'`, dessa forma vamos selecionar todas as pessoas que possuem a letra 'G' no nome, ignorando tudo que vem antes ou depois da letra 'G'.

## Realizando um INSERT
Agora vamos aprender a inserir um registro no nosso banco de dados. Para isso utilizaremos a cláusula INSERT.

Existem duas maneiras de fazer o inserção dos dados, podemos inserir especificando o nome da coluna e não específicando o nome da coluna.

Segue abaixo um exemplo da utilização do INSERT especificando o nome da coluna:
```
INSERT INTO Clientes (Nome, Sobrenome, Email, AceitaComunicados, DataCadastro) 
VALUES ('Aurélio', 'Miguel', 'email@email.com', 0, GETDATE())
```
Com o comando `INSERT INTO Clientes` estamos determinando que a inserção deve ser feita na tabela **Clientes**. As colunas devem ser passadas dentro dos parenteses após o nome da tabela e os valores devem ser passados após o comando `VALUES` também entre parenteses e seguindo a mesma ordem determinada na descrição das colunas. Todas as strings devem ser inseridas com aspas simples. Para inserir a data utilizamos a função `GETDATE()`, essa função retornar a data e hora atual. 

Através desse comando será realizado a inserção desse dado na tabela **Clientes**.

Para utilizar o INSERT omitindo as colunas, podemos seguir o padrão do trecho de código abaixo:
```
INSERT INTO Clientes VALUES('Leonardo', 'Buta', 'email@email.com', 1, GETDATE())
```
Dessa forma foi omitido o nome das colunas e os valores serão inseridos conforme a sequência padrão das colunas da tabela **Clientes**.
