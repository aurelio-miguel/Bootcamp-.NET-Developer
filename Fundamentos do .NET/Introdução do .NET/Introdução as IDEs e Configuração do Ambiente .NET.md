# Introdução as IDEs e Configuração de Ambiente .NET

Neste módulo realizaremos os estudos sobre as IDEs, vamos aprender sobre as IDEs disponíveis para o desenvolvimento com o .NET e vamos realizar a configuração necessária da IDE escolhida para o Bootcamp.

## O que é uma IDE?

Uma IDE (Integrated Development Environment), ou ambiente de desenvolvimento integrado, é um software que facilida e integra diversas facilidades para a escrita e depuração do código. 

A IDE é um programa utilizado para o desenvolvimento, a IDE fornece diversas ferramentas para auxiliar no desenvolvimento das tecnologias. 

### IDEs para o .NET
- **Visual Studio** (Essa que iremos utilizar): É a principal IDE para o .NET, possui suporte para o Python, Node, Unity, C#, etc. Atualmente essa IDE está disponível para Windows e Mac.
- **Visual Studio Code**: Conhecido também como *VS Code*, esse é um editor de textos utilizado para facilitar o desenvolvimento de diversas linguagens, o VS Code é amplamente utilizado para o desenvolvimento Web e possui a possibilidade de instalar extensões. É um software totalmente gratuito e disponível para Windows, Mac e Linux.
- **Rider**: É uma IDE também voltada para o .NET, possui uma forte integração com o .NET e possui diversas facilidades para trabalhar com o Unity. Esse não é um software gratuito.

## Instalação e configuração do .NET SDK

### Download e nstalando o .NET SDK

[Link para o download do .NET SDK](https://dotnet.microsoft.com/pt-br/download)

A versão pode ser diferente da versão utilizada durante os estudos, sempre busque baixar a versão mais recente e atente-se a realizar o download do SDK e não do Runtime. O SDK é voltado para ambientes de desenvolvimento, já o Runtime é para quem deseja apenas executar o .NET, o Runtime seria voltado para quem deseja rodar a aplicação desenvolvida em .NET em um servidor, por exemplo.

Para realizar o download, basta acessar o link citado acima e clicar no ícone indicado na imagem abaixo:

![Imagem com a indicação do botão de download](https://live.staticflickr.com/65535/53685380425_32bb567cf6_z.jpg)

Os passos de instalação seguem o padrão comum de instalação de qualquer programa. 

### Verificando a instalação e versão

Para visualizar mais detalhes sobre a versão instalada, abra o seu CMD e digite o comando **dotnet --info"

![Ver detalhes sobre o .NET que foi instalado](https://live.staticflickr.com/65535/53685332719_1d158f4119_z.jpg)

Com esse comando você conseguirá visualizar as versões instaladas, runtime e mais alguns detalhes.

## Instalação do VS Code

### Download do VS Code

[Link para realizar o download](https://code.visualstudio.com/download)

Na nova tela você poderá escolher a versão que deseja utilizar, baseado no seu sistema operacional e também na arquitetura do seu computador

![Imagem com as opções de download do VS Code](https://live.staticflickr.com/65535/53685344789_f8e8a05b17_z.jpg)

O processo de download segue o padrão normal de todos os softwares, não tendo nenhuma peculiaridade. 

## Criando o primeiro projeto

### Abrindo a pasta do projeto
O primeiro passo vai ser criar uma pasta vazia no computador para realizar armazenar o projeto.

Para abrir a pasta criada no seu VS Code, basta clicar nos ícones indicados na imagem abaixo e clicar no botão "Abrir pasta".

![Abrir pasta no VS Code](/imagens/image.png)

Após selecionar a sua pasta, o VS Code já vai estar com a sua pasta aberta no programa. Qualquer arquivo ou modificações que você fizer, vai impactar na determinada pasta que foi aberta.

### Criando o projeto através do terminal
Nós podemos realizar a criação do projeto utilizando o terminal integrado do VS Code. Para abrir um novo terminal, clique no item *Terminal* indicado na imagem abaixo e clique no botão *Novo terminal*, ou simplesmente digite o comando *Ctrl+Shifit+'*. Para abrir um terminar que foi fechado, basta digitar o comando *Ctrl+'*

![Abrir terminal no VS Code](/imagens/abrir%20terminal.png)

Dessa forma o terminal será aberto na parte inferior do VS Code.

Para criar um projeto, digite o comando abaixo no seu terminal
```bash
    dotnet new console
```
O termo *dotnet* é o termo utilizado para específicar que será um comando qualquer do .NET, o *new* faz referência ao novo e o *console* é o tipo de projeto que iremos criar.

*Os projetos de console são projetos onde as entradas e saídas do nosso programa vão se dar através do terminal*

No .NET temos vários tipos de projetos, dentre eles API, MVC e etc.

Após o comanda, o .NET vai criar o projeto e você conseguirá ver a estrutura de pastas e arquivos padrão, localizado na parte superior esquerda do VS Code.

![Estrutura de arquivos do .NET](/imagens/estrutura%20de%20arquivos.png)

### Instalando extensões no VS Code
Pelo fato do VS Code se tratar de um editor de textos, será necessário instalar algumas extensões para que possamos facilitar o desenvolvimento.

Para instalar as extensões, clique no ícone indicado na imagem abaixo:
![Imagem com o ícone de extensões](/imagens/ícone%20extensões.png)

Na nova tela você conseguirá buscar pelas extensões desejadas através do campo de busca. Após buscar pela extensão, clique na extensão identificada e após isso clique no botão *Instalar*

![Área de busca das extensões](/imagens/extensões.png)

Segue abaixo a lista com as extensões que utilizaremos:
- C#
- Extensões auxiliares: C# Extensions (autor: JosKreativ), vscode-icons

### Executando o projeto
Para executar o projeto, basta abrir o terminal na pasta do seu projeto e digitar o comando abaixo no terminal
```bash
    dotnet run
```
Após esse comando, o seu projeto será compilado e executado.