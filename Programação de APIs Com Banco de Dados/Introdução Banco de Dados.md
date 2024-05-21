# Introdução
Neste módulo vamos aprender mais sobre bancos de dados. O objetivo geral desse módulo será aprender os principais conceitos de banco de dados, SQL, comandos, tratamentos e junção de dados, com foco em desenvolvimento.

## Introdução à Banco de Dados
Um banco de dados é uma coleção organizada de informações (ou dados) estruturadas, normalmente armazenadas eletronicamente em um sistema de computador. 

Todo sistema precisa armazenar um tipo de dado, vai ser necessário inserir, atualizar, recuperar um dado e também deletar um dado quando ele não for mais útil. Por conta disso, utilizaremos o banco de dados para armazenar esses dados de forma estruturada para que possamos recuperar esses dados posteriormente.

Dados estruturados são dados organizados de tal forma que podemos identificar e recuperar esse dado rapidamente. O banco de dados possui uma organização que precisa ser obedecida para que possamos inserir os tipos de dados. 

O banco de dados é um local onde os dados serão armazenados para que eles possam ser recuperados posteriormente.

![Imagem representando os sistemas que podem utilizar ele](/imagens/bd%20e%20serviços.png)

Na imagem acima podemos ver que um banco de dados pode ser acessado por diversos sistemas, por exemplo uma API, um sistema em nuvem, um cliente que acessa um sistema web onde esse faz acesso a um banco de dados.

O banco de dados será instalado em um servidor e esse servidor vai rodar o software de banco de dados e esse software vai poder disponibilizar para quem tem acesso autorizado a ele. O banco de dados vai ter mecanismos de segurança, como autenticação. 

Um sistema pode armazenar informações e buscar informações em um banco de dados. Esses dados ficam armazenados no banco de dados de forma estruturada.

## Tipos de banco de dados
Atualmente temos dois tipos de banco de dados no mercado, sendo eles o banco de dados relacionado e o banco de dados não relacional. 

### Banco de dados relacional:
O tipo mais usado atualmente, armazenando dados estruturados, sendo organizado em tabelas, com colunas e linhas, que se relacionam entre si.
Exemplos: SQL Server, Oracle Database, MySQL, Postegres e outros.

Uma tabela é basicamente um agrupamento de dados que possue colunas e linhas, de forma similar a uma planilha do excel. As tabelas podem se relacionar entre si, por exemplo uma tabela de clientes e uma tabela de vendas. Podemos relacionar a tabela de clientes com a tabela de vendas.

#### Entendendo uma tabela
Tabelas são dados estruturados e organizados logicamente em formato de linha e coluna, esse é o principal conceito de um banco de dados relacional.

No exemplo abaixo podemos ter a tabela **Clientes** e **Enderecos**, podemos ver que cada tabela possui as colunas e as linhas que representam os conjuntos de dados. Uma coisa muito comum em tabelas é a coluna para o identificador/id. O Id é o identificador da linha e ele deve ser único.

![Imagem de uma tabela de exemplo](/imagens/tabela%20exemplo.png)

Na tabela **Enderecos** podemos ver a coluna **IdCliente**, essa coluna é utilizada para relacionar que o endereço dessa linha é relacionado a linha que possamo o **IdCliente 1**.

Essas duas tabelas se relacionam entre si através dos IDs, podemos relacionar as tabelas utilizando o Id das tabelas. A coluna **IdCliente** na tabela **Enderecos** vai funcionar como um apontamento para a tabela **Clientes**, conforme consta na imagem abaixo:

![Imagem indicando o relacionamento](/imagens/relacionamento%20entre%20tabelas.png)

Quando as tabelas se relacionam, é preciso ter uma chave/id que aponta para o id de uma outra tabela.

## Banco de dados não relacional
Banco de dados onde os dados não são armazenados em tabela, e sim armazenados de maneira não estruturadas ou semi-estruturadas. O **mongoDB** é um dos principais banco de dados não relacional. Um dado semi-estruturado é um JSON, por exemplo.

Existem vários tipos de banco de dados não relacional, dentre eles: document databases, key-value databases, wide-column stores, e graph databases.

Um banco de dados não relacional é muito útil quando temos uma grande quantidade de informações. Por não tem regras rigidas, podemos inserir e recuperar dados de forma mais rápida se comparado a um banco de dados relacional.

Um banco de dados relacional possui regras rigidas para poder armazenar um tipo de dados, não é possível sair do padrão definido pelo banco de dados. 

## Tipos de dados
Segue abaixo uma representação de um dado semi estruturado e de um dado estruturado.

![Imagem com um exemplo de dado semiestruturado e dado estruturado](/imagens/dado%20estruturado%20e%20semi%20estruturado.png)

Nos bancos de dados relacionais não podemos excluir uma coluna da tabela apenas para uma linha, ao excluir essa coluna ela será excluída para todas as linhas da tabela, uma outra característica diz respeito ao fato de que os dados precisam ser do tipo pré-determinados pela coluna da tabela. Já no banco de dados não relacional, é possível sim remover uma informação apenas de um dado e também temos a possibilidade de inserir valores de tipos diferentes.

## Entendendo o DBMS
Database Management System é um software utilizado para acessar, manipular e monitorar um sistema de banco de dados.

![Imagem exemplificando um DBMS](/imagens/DBMS.png)

Com o DBMS podemos acessar o banco de dados de uma maneira visual e fácil. O bando de dados por si só não possui nenhuma tela para que possamos visualizar e manipular ele visualmente, por conta disso utilizamos um DBMS.

No servidor iremos instalar apenas o banco de dados, já nas nossas máquinas iremos instalar o Management Studio para acessar esse banco de dados visualmente e manipular ele de forma mais facilitada. 

Cada banco de dados possui o seu sistema de gerenciamento de banco de dados. O do SQL Server se chama SQL Server Management Studio.

## Instalando o SQL Server
Para que possamos prosseguir com as aulas, vai ser necessário realizar a instalação do SQL Server. Iremos instalar o SQL Server e também o Management Studio

[Link para download do SQL Server](https://www.microsoft.com/pt-br/sql-server/sql-server-downloads)

[Link para download do Management Studio](https://go.microsoft.com/fwlink/p/?linkid=2206714)