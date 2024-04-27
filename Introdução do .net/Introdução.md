# Introdução ao .NET

O .NET é uma plataforma de desenvolvimento unificado que permite a construção de sistemas e aplicações.

C# é uma linguagem de programação usada no .NET

![Plataforma .NET](https://images.ctfassets.net/23aumh6u8s0i/2bsVrNvzMOk64yfFw0ZU3O/b88d3412d42844d54011f31d69d5860f/dotnet5_platform)

## Linguagens que o .NET suporta
- C#
- F#
- Visual Basic (VB)

## Multiplataforma
Atualmente o .NET é multiplataforma, os sistemas podem ser utilizados em sistemas Windows, Linux e macOS. A versão .NET Framework não é multiplataforma.

## Aplicações
É possível desenvolver aplicações multiplataforma para diversas finalidades, dentre elas:
- Web
- Mobile
- Desketop
- Microsserviços 
- Cloud
- Machine Learning
- Games
- Internet das coisas (IoT)


# História do .NET
A Microsoft começou a trabalhar no C# no final dos anos 90, tendo sua primeira versão do framework lançada em 202, tendo como objetivo competir com o Java.

O conceito de multiplataforma era estrondoso na época, e a Microsoft trabalhou em melhorias e implementações do Java em sua plataforma, mas foi impedida pela Sun.

Isso motivou a Microsoft a desenvolver um ecossistema integrado ao Windows, que fosse fácil para desenvolver aplicativos desktop e web, e que fosse amarrado apenas ao Windows, faumentando assim a sua relevância.

# Diferença entre o .NET Framework (Legado) e .NET
O .NET Framework é a versão legada que só funciona no sistema operacional Windows, o .NET Core ou apenas .NET é a versão mais recente e multiplataforma.

![Diferenças entre o .NET Framework e o .NET Core](https://live.staticflickr.com/65535/53683017103_91d97da8df_z.jpg)

Após a versão 3.1, O .NET Core passou a ser chamado apenas de .NET; Sempre que nos referimos a .NET Core, estamos citando a versão 3.1 ou anteriores, a partir da versão 5 ele foi passado a se chamar apenas .NET;

A partir da versão do do .NET Core 3.1, a nova versão foi diretamente para o .NET 5; Um dos motivos para essa decisão foi para não gerar confusão com o .NET Framework 4.X; A palavra Core também foi removida, o objetivo é enfativar que a nova versão do .NET é a principal implementação do .NET no futuro.

Todos os esforços atualmente estão no .NET, um dos principais fatores é o fato de ser multiplataforma;

# Compilador .NET e seu funcionamento

A primeira etapa é entender um pouco mais sobre as linguagens de baixo nível e de alto nível.

- **Linguagem de alto nível**: A linguiagem que entendemos e escrevemos os códigos.
- **Linguagem de baixo nível**: É a linguagem que a máquina entende. Possui pouca abstração, sendo difícil de entender.

O computador por sí, só pode compreender binário. Os compiladores tem a a função de traduzir o nosso código escrito em alto nível para uma linguagem de baixo nível. O computador vai fazer o trabalho de traduzir os códigos escritos por nós programadores, para uma linguagem que o computador possa entender.

![Função do compilador](https://lh6.googleusercontent.com/80KkpsaGvzNzneQMQP7Uq4IOXYIgaWxUqRL2VxZFJGXEcTOeDc2B0h2eSgz1YZLSF17idTsNkcsv1tR00JFc1jtsoeoMXalSivfTF3f0wJo8AtQI4uGccaIsFFpFPmmQfVhyfF0U)

## O compilador do .NET

![Compilador do .NET](https://dotnettrickscloud.blob.core.windows.net/img/netframework/econojit.png)

## Compilador e Transpilador

- **Compilador:** É um porgrama que realiza a conversão de uma linguagem de alto nível para uma linguagem de baixo nível;
- **Transpilador:** É a conversão de uma linguagem ou interpretação para outra. A sua saída permanece em linaguagem de alto nível. Por exemplo: Typescript para Javascript;

Existem linguagens que são compiladas e linguagens que são interpretadas.

- **Linguagens compiladas**: São linguagens onde o código fonte é traduzido para o código de máquina. Por exemplo: C# e Java;
- **Linguagens interpretadas**: São linguagens que fazem a leitura e interpretação diretamente do código fonte, não são transformadas em linguagem de máguina. Por exemplo: Javascript e PHP;