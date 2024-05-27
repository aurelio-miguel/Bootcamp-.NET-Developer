# Introdução
Nessa etapa vamos aprender a utilizar algumas funções do SQL para poder manipular alguns dados.

## Bult-in functions
Bult-in functions são funções pré-existentes que auxiliam na manipulação de dados, como por exemplo contar, somar, média, etc.

## Usando o COUNT
O COUNT é uma função utilizada para contar quantas linhas existem na tabela com uma determinada condição. 

Segue abaixo um exemplo de como podemos utilizar essa função para a contagem:
```
SELECT COUNT(*) FROM Produtos
```
Com o `SELECT COUNT (*)` Podemos contar a quantidade de linhas da tabela produtos, aliado a isso podemos inserir um WHERE no final para contar as linhas baseadas em um filtro em específico.

## Usando o SUM
Nós podemos utilizar a função SUM para somar valores das linhas. Na tabela **Produto** por exemplo, existe uma coluna com os preços. Podemos somar o preço de todos os itens da nossa tabela com essa função, além disso podemos também utilizar o WHERE para filtrar os itens que vão fazer parte da soma.

Segue abaixo um exemplo de como podemos utilizar essa função:
```
SELECT SUM(Preco) FROM Produtos
```
Passaremos como parâmetro da função `SUM()` a coluna da tabela que deve ser utilizada na soma.

Segue abaixo um exemplo de soma com o WHERE:
```
SELECT SUM(Preco) FROM Produtos
WHERE Cor = 'Branco'
```
No exemplo acima ele vai somar o preço apenas dos produtos que possuem o valor 'Branco' na coluna de cor da tabela **Produtos**.

## Usando o MIN, MAX e AVG
O operador MIN tem como finalidade exibir o menor valor de uma determinada coluna da nossa base de dados. O MAX tem como finalidade pegar o maior valor de uma determinada coluna e o AVG tem como finalidade pegar o valor médio de todos os elementos de uma determinada coluna em uma consulta.

No exemplo abaixo utilizaremos a função MAX para pegar o valor mais caro da tabela Produtos, os preços estão inseridos na coluna **Preco**:
```
SELECT MAX(Preco) FROM Produtos
```
No nosso SELECT utilizamos a função `MAX(coluna)` e passamos como parâmetro a coluna que queremos verificar qual é o preço mais caro. Após isso utilizaremos o `FROM Tabela` para identificar em qual tabela queremos verificar. Após o FROM podemos também inserir o WHERE para filtrar as linhas que vão fazer parte dessa consulta.

Segue abaixo um exemplo utilizando o MIN para pegar o valor mais baixo da tabela Produtos, os preços do exemplo abaixo também estão inseridos na coluna **Preco**:
```
SELECT MIN(Preco) FROM Produtos
```
Nesse caso, passamos como parâmetro a coluna que queremos utilizar para obter o valor mínimo.

Para obter o valor médio, utilizaremos o método AVG passando como parâmetro a coluna que queremos extrair a média, conforme o exemplo abaixo:
```
SELECT AVG(Preco) FROM Produtos
```

## Concatenando colunas
Com o SQL também podemos retornar uma concatenação de strings entre as colunas. Imagina que temos uma coluna com o nome "Nome" e outro coluna com o nome "Cor". Podemos criar uma consulta para trazer essas informações de colunas diferentes contatenadas.

Segue abaixo um exemplo para concatenar o texto da coluna Nome com o texto da coluna "Cor" da tabela Produtos:
```
SELECT Nome + ' - ' + Cor FROM Produtos
```
Utilizando o operador de adição foi possível contatenar as duas colunas com um texto " - " para separar os dados de cada uma das colunas.

## Upper e Lower
É possível também fazer um tratamento no texto para transformar o resultado da consulta para maiúsculo ou minúsculo.

Para transformar o resultado de uma coluna de uma consulta todo em maiúsculo, basta realizar a utilização do Upper
```
SELECT UPPER(Nome) FROM Produtos
```
Dessa forma todos os textos da coluna Nome da tabela Produtos serão exibidos em maiúsculo.

Para transformar para minúsculo, basta alterar a função `UPPER()` para `LOWER()`.

## Entendendo o Group By
Também é possível realizar um agrupamento de dados com base em uma determinada condição. Por exemplo, podemos contar a quantidade de itens que temos agrupando pelo tamanho do produto que está na coluna Tamanho da tabela Produto, por exemplo saber a quantidade de produtos com o tamanho 'M' que temos na tabela. 

Segue abaixo um exemplo de como podemos utilizar o Group By para fazer isso:
```
SELECT Tamanho, COUNT(*) FROM Produtos GROUP BY Tamanho
```

## Primary Key e Foreign Key
**Primnary Key:** Chave única que identifica cada registro na tabela.
**Foreign Key:** Chave que identifica um registro existente em outra tabela.

Nos exemplos acima, o Id é a coluna que possue a chave primária. Essa coluna vai possuir números únicos que vão identificar cada um dos registros da tabela.

A Foreign Key é a chave que vai identificar o registro que existe em uma outra tabela.

Imagina que temos uma tabela com o nome **Clientes** e outra tabela com o nome **Enderecos**, precisamos criar uma relação entre essas duas tabelas pois todos os clientes vão ter um endereço. Dessa forma, podemos inserir na tabela Cliente uma coluna que vai conter as chaves estrangeiras  que vão ser inseridas os Id's das colunas da tabela Endereco que representa o endereço de um determinado cliente.

Na imagem temos a coluna 'IdCliente' da tabela endereço que é a coluna com as chaves estrangeiras para representar de qual cliente é cada uma das linhas da tabela Enderecos.
![Imagem exemplificando as tabelas](/imagens/Exemplo%20foreign%20key.png)