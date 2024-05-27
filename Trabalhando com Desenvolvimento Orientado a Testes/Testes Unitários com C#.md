# Introdução
O objetivo geral desse módulo é aprender os principais conceitos de testes unitáriois, seu objetivo e sua importância em qualquer projeto, independente de seu tamanho.

## Introdução a testes de software
Existem vários tipos de testes de software: unitários, integração, regressivo, segurança, etc. Os testes são fundamentais para garantir a qualidade e o correto funcionamento de um software. Serve principalmente para validar se o que foi contruído está atendento ao que se é esperado.

## Introdução a testes unitários
O teste unitário (ou teste de unidade) são testes realizados diretamente no código fonte, buscando testar a menor unidade de código possível, atra´ves de cenários que podem ocorrer no sistema

Exemplo: Um usuário do sistema só é cadastrado se possuir um CPF e um e-mail válido. Caso contrário, retornará um erro indicado que está errado.

Possíveis vasos de teste:
- Usuário com todos os dados válidos.
- Usuário com CPF inválido.
- Usuário com e-mail inválido.

## Vantagens dos testes
A maior vantagem é a qualidade. Garente que a alteração não tenha impactos no sistema. Os testes também diminuem os bugs, ajudar a trazer uma maior confiança de que suas classes e métodos funcionam e ajudar a prevenir problemas futuros. 

## Frameworks de teste
Para escrever testes unitários precisaremos escrever códigos que validam o nosso código. Para isso, faremos uso de alguns frameworks, os mais conhecidos são **MSTeste**, **NUnit** e **xUnit**. 

Para o nosso curso, utilizaremos o **xUnit**, porém, qualquer outro pode ser utilizado.

### Como os testes unitários são organizados
Cada projeto que criamos temos um arquivo **.csproj**, nós teremos também um outro arquivo de testes também com o formado **.csproj**. Teremos o principal que é o da esquerda na imagem abaixo e o projeto de testes que é o da direita na imagem abaixo. Todos os testes serão escritos no arquivo de testes e vai validar o projeto da esquerda.

![Diagrama que exemplifica o funcionamento dos teste unitários](/imagens/funcionamento%20dos%20testes%20unitários.png)

## Criando nosso projeto
Em uma nova pasta vamos criar dois projetos, um dos projetos vai ter a implementação do nosso programa e o outro projeto vai ter os testes. Para facilitar vamos inserir os dois dentro de uma solution.

Dentro da nova pasta, antes mesmo de iniciar qualquer um dos dois projetos, vamos abrir uma nova pasta com o nome do nosso projeto, por exemplo **Calculadora** e vamos criar uma nova pasta com o nome **CalculadoraTestes**

![Imagem com estrutura de pastas para testes](/imagens/estrutura%20de%20pastas%20para%20testes.png)

Agora abra o terminal e vá até a pasta **Calculadora**, dentro dessa pasta vai ser preciso utilizar o comando `dotnet new console` para iniciar um novo projeto dentro de console dentro dessa pasta.

Após isso, vamos ir até a outra pasta com o nome **CalculadoraTestes** e vamos criar um projeto de testes utilizando o comando `dotnet new xunit`.

Agora vamos criar uma solution para agrupar esses dois projetos. 

![Imagem com projetos e solutions](/imagens/projetos%20e%20solution.png)

Agora precisaremos inserir uma referência no projeto **CalculadoraTestes** para que ele possa reconhecer o projeto **Calculadora**

## Implementando a classe calculadora
Primeiramente vamos criar uma pasta com o nome *Services* no nosso projeto **Calculadora**. Dentro dessa pasta vamos criar uma classe com o nome **CalculadoraImplementacao** 

Nessa classe **CalculadoraImplementacao** teremos apenas um método com o nome `Somar()` que vai receber dois inteiros por parâmetro e vai retornar a soma, segue abaixo o código com a implementação:
```
namespace Calculadora.Services
{
    public class CalculadoraImplementacao
    {
        public int Somar(int num1, int num2)
        {
            return num1 + num2;
        }
    }
}
```

Agora vamos até o arquivo **Program.cs** do nosso projeto para implementar essa classe. Segue abaixo o trecho de código onde esse procedimento é realizado:
```
using Calculadora.Services;


CalculadoraImplementacao c = new CalculadoraImplementacao();
int num1 = 5;
int num2 = 10;

Console.WriteLine($"{num1} + {num2} = {c.Somar(num1, num2)}");
```

## Criando a classe de testes
Agora vamos acessar o nosso projeto de testes e criar um cenário para realizar os testes para o projeto **Calculadora**.

O arquivo **UnitTest1.cs** contêm o esqueleto para um cenário de teste. O padrão para nomes de arquivos de teste unitários é colocar o nome do que queremos testes + "Test". Por exemplo, **CalculadoraTests.cs**. Por conta disso vamos renomear o arquivo **UniTest1.cs** para **CalculadoraTests.cs**. O nome da classe também deve ser alterado, segue abaixo o esqueleto após as alterações:
```
namespace CalculadoraTestes;

public class CalculadoraTests
{
    [Fact]
    public void Test1()
    {

    }
}
```

Caso nós tivessemos mais classes no projeto **Calculadora**, nós também iriamos criar novas classes de testes para isso. 

Cadas método de testes vai ter uma anotação com o nome `[Fact]` que significa que esse método é um cenário de teste e indica que ele deve ser validado de acordo.

Agora vamos alterar o nome do método que vem por padrão como `Teste1` e e dentro dessa função vamos testar para verificar se ao passar dois números a soma vai retornar os dois valores somados. Vamos criar um cenário de teste para validar o cenário em questão, o nosso do método do nosso teste deve ser descritivo. Segue abaixo o código da classe **CalculadoraTests**:
```
public class CalculadoraTests
{
    [Fact]
    public void DeveSomar5Com10ERetornar15()
    {

    }
}
```

Dentro do método vamos escrever algumas etapas para poder criar o teste unitário, atualmente temos três conceitos. O Arrange, Act e Assert. Essas são métodologias muito práticas e válidas para escrever um método.

- Arrange: Serve para que possamos montar o cenário, disponibilizando os números para o cenário que vamos testar.
- Act: Vamos chamar a ação que vamos testar.
- Assert: É para validar se tudo que foi feito tem o resultado esperado.

O primeiro passo vai ser instânciar a classe calculadora, conforme consta no trecho abaixo, lembrando que é necessário fazer o import dela.
```
using Calculadora.Services;
namespace CalculadoraTestes;

public class CalculadoraTests
{
    private CalculadoraImplementacao _calc;

    public CalculadoraTests()
    {
        _calc = new CalculadoraImplementacao();
    }

    [Fact]
    public void DeveSomar5Com10ERetornar15()
    {

    }
}
```

## Implementando o teste unitário
Primeiro vamos iniciar com o **Arrange**, nessa etapa vamos preparar o que deve ser passado para realizar o teste. Vamos passar os dados que serão somados como variáveis, conforme consta no trecho abaixo:
```
...
    public void DeveSomar5Com10ERetornar15()
    {
        //Arrange
        int num1 = 5;
        int num2 = 10;

        //Act
        //Assert
    }
```

No **Act** vamos inserir a ação de soma, dessa vamos chamar a função `Somar()` do objeto `_calc`, conforme consta no trecho abaixo:
```
...
    public void DeveSomar5Com10ERetornar15()
    {
        //Arrange
        int num1 = 5;
        int num2 = 10;

        //Act
        int resultado = _calc.Somar(num1, num2);
        //Assert
    }
```

No **Assert** vamos realizar a validação do nosso resultado, para isso vamos utilizar a classe `Assert` e os seus métodos para validação, conforme consta no trecho abaixo:
```
...
    public void DeveSomar5Com10ERetornar15()
    {
        //Arrange
        int num1 = 5;
        int num2 = 10;

        //Act
        int resultado = _calc.Somar(num1, num2);

        //Assert
        Assert.Equal(15, resultado);
    }
```
Utilizamos o método `Equal()` da classe `Assert` para no primeiro parâmetro o resultado esperado, como segundo parâmetro o retorno da função `Somar()` que estamos testando. Esse método vai validar se o resultado é o esperado.

### Executando o teste
Primeiro vamos acessar o terminal e ir até a pasta onde está o nosso projeto de testes. Após isso, basta executar o comando `dotnet test` no terminal. Segue abaixo o trecho com o output do console do nosso teste:
```
Iniciando execução de teste, espere...
1 arquivos de teste no total corresponderam ao padrão especificado.

Aprovado!  – Com falha:     0, Aprovado:     1, Ignorado:     0, Total:     1, Duração: < 1 ms - CalculadoraTestes.dll (net8.0)
```
O resultado vai mostrar todos os testes realizados e se eles tiverram alguma falha. 
