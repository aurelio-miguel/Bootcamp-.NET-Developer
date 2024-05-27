# Introdução
O nosso objetivo é aprender e desenvolver uma API, utilizando o Entity Framework para persistência de dados, juntamente com seus principais conceitos e funcionalidades.

## O que é uma API
Uma API (Application Programming Interface) é uma forma de dcomunicação entre computadores ou programas de computadores. É um software que fornece informações para outro software. A API é uma forma de integração entre sistemas.

![Imagem com o exemplo de uma API](/imagens/exemplo%20api.png)

A API pode ser exemplificada com a imagem acima, o garçom é a API que é responsável por pegar o pedido do cliente e levar até a cozinha, a API também é o responsável para retornar o pedido da cozinha até o cliente. O cliente não consegue pedir a comida diretamente para o cozinheiro, ele precisa pedir para o garçom e o garçom vai fazer essa comunicação entre o cliente e a cozinha.

No exemplo acima o cliente é a aplicação, o garçom é a API e a cozinha é o servidor.

Na API temos dois conceitos muito importantes, o **request** e o **response**.

- **Request:** O requeste é a requisição que fazemos para a nossa API, por exemplo o pedido que o cliente faz para o garçom.
- **Response:** O response é a resposta da nossa API para a requisição que foi feita. É o envio do prato para o cliente, por exemplo.

## Exemplo de uso
Imagine um cenário onde tem uma empresa de Ecommerce que vai vender os produtos e existe também uma empresa de transporte que é a responsável por entregar os produtos. 

É importante considerar que a empresa de transporte não precisa considerar se o cliente pagou, qual foi a forma de pagamento, etc. Ela apenas precisa saber que ela tem que entregar para o cliente X e o endereço do cliente X. Já a empresa, ela precisa saber e informar o cliente em quanto tempo um determinado produto será entregue para informar para o cliente. 

Com o trecho acima podemos perceber que existem informações em que uma empresa depende da outra para obter. Essa comunicação pode ocorrer através de uma API.

Quando um produto é vendido, a empresa vai fazer uma chamada na API de entregas para informar que um produto X foi vendido contendo todas as informações relevantes para a entrega. A empresa de transportes vai receber essa requisição da API. A empresa de transporte vai disponibilizar um endereço na API para que o banco de dados que possui o status do pedido possa ser pesquisado.

![Imagem como exemplo de uso de API](/imagens/exemplo%20de%20uso%20de%20api.png)

No exemplo abaixo temos como pode funcionar uma API para que o frontend possa ter capturar ou inserir dados em um banco de dados.

![Imagem de uma API para comunicação entre o Frontend e o Banco de dados](/imagens/exemplo%20de%20api%20no%20mundo%20da%20tecnologia.png)

O frontend pode fazer um request para listar todos os clientes cadastrados e através da api esses dados do banco de dados serão retornados para o frontend através de uma response, por exemplo.

## Criando nossa API
Primeiramente vamos iniciar criando um novo projeto de console através do comando `dotnet new webapi`.

Após iniciar o projeto, a nossa API foi criada e vários arquivos vão estar disponíveis na pasta, ele cria também uma API de exemplo para que você possa já ver uma API estruturada. Para executar o nosso projeto utilizaremos o comando `dotnet watch run`, o comando `watch` faz com que todas as alterações feitas na API serão recarregadas de forma automática.

Após esse comando vai abrir uma nova tela no navegador padrão com o frontend da nossa API com a ferramenta chamada Swagger, o Swagger é uma ferramenta para documentar a API. Quando criamos uma API no .NET temos o Swagger que é a documentação da nossa API, voltada para desenvolvedores. 

![Imagem do Swagger](/imagens/swagger.png)
Na tela acima podemos ver que temos um método chamado WeatherForecast. Clicando nele vai abrir a tela para que possamos clicar no botão "Try Out" e depois no botão "Execute" para executar um request e obter uma resposta.

Por enquanto essa API funciona apenas na sua máquina através do localhost. Caso queira que essa API esteja disponível para todos, será necessário hospedar ela em um servidor da web.

O Swagger não é uma ferramenta necessária para que possamos utilizar a API, o Swagger é apenas uma ferramenta para testar a API e documentar.

... Continua

