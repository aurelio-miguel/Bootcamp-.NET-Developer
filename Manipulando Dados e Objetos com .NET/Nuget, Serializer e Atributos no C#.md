# Nuget, Serializer e Atributos no C#

## Introdução ao gerenciador de pacotes
Um pacte é um conjunto de códigos úteis, que possibilita o compartilhamento e reuso de código. O pacote é um conjunto de códigos que resolve um problema em específico, é um pequeno projeto que resolve um problema em específico. 

Esse pacote pode ser compartilhado com outros pessoas e sistemas, esses outros sistemas e pessoas poderão utilizar esse pacote

## Nuget
O Nuget é um gerenciador de pacotes, que permite desenvolvedores compartilharem códigos e bibliotecas. O Nuget é o gerenciador de pacotes oficial do .NET. 

![Imagens pacotes Nuget](/imagens/pacotes%20nuget.png)

No link abaixo você poderá conhecer mais sobre o Nuget e sobre os pacotes disponíveis
[Link para o site do Nuget](https://www.nuget.org/)

## Instalando um pacote pelo VS Code
O primeiro passo vai ser acessar o site do Nuget e selecionar o pacote que você deseja utilizar. Na nova tela você conseguirá ver mais detalhes sobre o pacote e também o comando que deve ser utilizado no terminal do VS Code para que esse pacote seja baixado para o projeto.

Segue abaixo uma imagem que indica onde contem o comando que deve ser utilizado para instalar o pacote:

![Imagem com os detalhes sobre um pacote no site Nuget](/imagens/nuget%20site.png)

Conforme indicado na imagem acima, existem diversas formas diferentes para realizar a instalação. Para que possamos instalar pelo VS Code, vai ser preciso utilizar o .NET CLI como método para instalação.

O comando que consta na área em azul é o comando que deve ser executado no terminal do VS Code. Lembe-se de que é preciso estar na raiz do seu projeto para realizar o comando em questão. 

Após realizar a instalação do pacote, você conseguirá visualizar a referência desse pacote no arquivo **.csproj**. Segue abaixo uma imagem que consta essa referência que vai estar no arquivo:

![Imagem com a referência do pacote](/imagens/referência%20de%20pacote.png)

Nessa referência podemos visualizar o nome do pacote e também a sua versão.

## Introdução serealização.
