# Conhecendo a Organização de um Programa C#
Nessa etapa o nosso objetivo é conhecer os arquivos principais de um projeto .NET e para que eles servem.

## Arquivos de projeto

- **.csproj**: Contém informações referente ao projeto (build, debug, versão), cada projeto criado terá um arquivo desse. 

- **.sln**: sln significa solução e nesse arquivop contêm informações que carregam um agrupamento de projetos. É possível ter vários projetos que fazem determinadas ações no código e esse arquivo **sln** serve para melhorar a organização do projeto. 

![Diagrama com a estrutura de um .sln](/imagens/sln.png)

Imagine que para executar o projeto **Efetuar PIX** e para executar o projeto **Pagar DA** precisamos da classe **ContaCorrente**, se esses projetos forem separados seria necessário criar a classe Conta Corrente nos dois projetos, o código seria duplicado.

Nesse cenário, o ideal é criar um terceiro projeto(.csproj) e esse projeto será o Common, nesse projeto vai ser inserido todas as classes que são comuns a vários projetos, por exemplo a classe Conta Corrente. Esse projeto seria um projeto auxiliar, não sendo possível utilizar ele sozinho. Após isso, basta inserir uma referência desse projeto nos outros projetos que vão utilizar as classes dele. Dessa forma as classes não precisaram ser duplicadas.

A **.sln** serve exatamente para referênciar os projetos, ela serve para que os três projetos façam parte de uma solution. A solution vai apontar quais projetos devem ser carregados. 

A solution não é obrigatória para projetos.
