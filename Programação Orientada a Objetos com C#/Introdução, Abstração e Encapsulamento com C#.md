# Introdução
Neste módulo iremos estudar sobre a programação orientada a objetos. Neste módulo iremos apresentar e explorar o paradigma de programação orientado a objeto, seus usos e como ele é aplicado no dia a dia da programação.

Inicialmente começaremos na parte teorica e posteriormente iremos para a parte prática. 

## O que é a POO
A Programação Orientada a Objetos é um paradigma de programação, ou seja, corresponde a uma técnica de programação para um fim específico. Um paradigma é um conjunto de métodologias para fazer algo, um conjunto de regras e padrões para fazer algo.

Dentro dessa técnica, existem quatro pilares:
- Abstração
- Encapsulamento
- Herança
- Polimorfismo

O principal conceito da POO são classes e objetos. 
![Imagem com o exemplo de uma classe e um objeto](/imagens/classes%20e%20objetos.png)

- **Classe**: Uma classe é uma representação de um objeto da vida real. A classe funciona como um molde em que contêm atributos/propriedades e ações/métodos de algo da vida real.

- **Objeto**: O objeto é a classe concretizada, é uma instância da classe. O objeto vai possuir os atributos/propriedades e ações/métodos da classe que ela faz parte. O objeto é uma implementação de uma classe. 

A classe é uma representação e o objeto é a concretização da classe. 

## Tipos de paradigma
Um paradigma nada mais é do que um modelo de técnicas, estruturas e formas de solucionar um problema. Um paradigma de programação é diferente de uma linguagem de programação. Uma linguagem de programação implementa um ou mais paradigmas.

### Paradigmas de programação
- Programação orientada a objetos.
- Programação estruturada.
- Programação imperativa.
- Programação procedural.
- Programação orientada a eventos.
- Programação lógica.

E muito mais...

## Introdução Abstração
A abstração consiste em abstrair um objeto do mundo real para um contexto específico, considerando apenas os atributos importantes. A criação de uma classe por exemplo é uma abstração de um objeto do mundo real, voltado para um contexto em específico. 

Qualquer objeto da vida real possui diversas características e ações que estão associadas a ele. No processo de abstração precisaremos considerar apenas as características e ações que vão fazer sentido para o que estramos nos propondo a desenvolver. 

## Abstração na prática
Agora vamos criar um novo projeto para que possamos trabalhar com esses conceitos. 

O primeiro passo vai ser iniciar um novo projeto dotnet, para isso você pode criar uma nova pasta no seu computador e acessar essa pasta via terminal e executar o comando `dotnet new console` para iniciar um novo projeto de console. Após esse comando a estrutura do projeto será criada, conforme a imagem abaixo:

![Imagem da estrutura de um projeto](/imagens/estrutura_projeto.png)

Agora vamos criar uma nova pasta com o nome `Models` na raiz do nosso projeto. Essa pasta vai receber as classes do nosso projeto. 

Dentro da pasta `Models` vamos criar uma nova classe com o nome `Pessoa`. Essa classe vai possuir a sua estrutura base, conforme  código abaixo:
```
using System;
using System.Collections.Generic;
using System.Linq;
using System.Threading.Tasks;

namespace Exemplo_POO.Models
{
    public class Pessoa
    {
        
    }
}
```

Agora vamos representar nessa classe as propriedades que uma pessoa pode ter e as ações que essa pessoa pode realizar. As ações chamaremos de métodos e as propriedades são como as características de uma pessoa. Segue abaixo o trecho de código contendo as propriedades e métodos de uma pessoa:
```
using System;
using System.Collections.Generic;
using System.Linq;
using System.Threading.Tasks;

namespace Exemplo_POO.Models
{
    public class Pessoa
    {
        public string Nome { get; set; }
        public int Idade { get; set; }

        public void Apresentar()
        {
            Console.WriteLine($"Olá, meu nome é {Nome} e tenho {Idade} anos");
        }
    }
}
```
A partir desse momento temos uma classe pessoa que possui as propriedades `Nome` e `Idade`. Além disso temos um método `Apresentar()` que exibira uma apresentação no console. Essa classe por si só é apenas uma representação de uma pessoa.

Para que possamos trabalhar com essa classe Pessoa, precisaremos criar um objeto do tipo Pessoa. Para criar o objeto vamos até o arquivo principal do nosso projeto que possui o nome `Program.cs` e vamos instânciar a classe pessoa a partir da criação de um objeto do tipo Pessoa.

Segue abaixo o trecho de código onde referênciaremos o caminho da nossa classe e logo abaixo realizamos a criação de um objeto do tipo pessoa no arquivo `Program.cs`:
```
using Exemplo_POO.Models;

Pessoa pessoa1 = new Pessoa();
```

No trecho abaixo vamos passar as propriedades do novo objeto `pessoa1` e vamos utilizar o método `Apresentar()`:
```
using Exemplo_POO.Models;

Pessoa pessoa1 = new Pessoa();

pessoa1.Nome = "Aurélio Miguel";
pessoa1.Idade = 26;

pessoa1.Apresentar();

Output:
Olá, meu nome é Aurélio Miguel e tenho 26 anos
```

## Introdução Encapsulamento
O encapsulamento serve para proteger uma classe e definir limires para alteração de suas propriedades. Serve para ocultar seu comportamento e expor somente o necessário. 

Nós podemos definir para que um atributo ou uma classe esteja bloqueado para alterações externas e só a própria classe pode alterar uma determinada propriedade ou atributo em específico. 

Imagina uma classe `ContaCorrente` que possui a propriedade número e a propriedade saldo, além disso ela possui também o método `Sacar()`. A propriedade saldo deve ser uma propriedade privada, isso deve ocorrer para que apenas a propria `ContaCorrente` possa alterar esse valor.

Nós podemos bloquear a propriedade saldo contra alterações externas através do encapsulamento. Nenhum objeto poderá alterar o saldo da conta, apenas a própria classe em que essa propriedade está inserida

![Imagem classe ContaCorrente](/imagens/classe%20conta%20corrente.png)

## Encapsulamento na prática
Para que possamos compreender mais sobre o encapsulamento, vamos implementar a classe indicada na imagem do conteúdo anterior.

Primeiramente vamos criar a classe conta corrente dentro da pasta **Models** que deverá ser criada na raiz do nosso projeto:
```
using System;
using System.Collections.Generic;
using System.Linq;
using System.Threading.Tasks;

namespace Exemplo_POO.Models
{
    public class ContaCorrente
    {
        public ContaCorrente(int numeroConta, decimal saldoInicial)
        {
            NumeroConta = numeroConta;
            saldo = saldoInicial;
        }

        public int NumeroConta { get; set; }
        private decimal saldo;

        public void Sacar(decimal valor)
        {
            saldo -= valor;
        }
    }
}
```
Nessa classe criamos um construtor para que possamos instânciar e já inserir os valores das propriedades. A propriedade `NumeroConta` é pública e podemos acessar e alterar ela a qualquer momento em outros códigos ou objetos que instânciarem essa classe. Já o saldo da conta só será atribuído no construtor, após isso a única classe que poderá alterar ele é a própria classe `ContaCorrente`. Nenhuma instância ou código poderá alterar esse saldo pois ele foi encapsulado através do private. As propriedades privadas são bloqueadas para alterações externas.

Após isso criamos um método sacar que receberá o valor de saque por parâmtro e dentro desse método o saldo poderá ser alterado, com base no valor do saque passado por parâmetro.

Abaixo iremos criar um objeto do tipo ContaCorrente no arquivo **Program.cs** e vamos utilizar o método para sacar:
```
using Exemplo_POO.Models;

ContaCorrente conta1 = new ContaCorrente(12345, 17.589M);
conta1.Sacar(2500M);

//Isso vai gerar um erro
conta1.saldo = 15.900M;

//Isso também vai gerar um erro
Console.WriteLine(conta1.saldo)/
```
Caso você tente alterar o valor da propriedade saldo você não conseguirá. Não será possível nem mesmo acessar essa propriedade do objeto para obter o valor. Isso ocorre pois o atributo saldo foi encapsulado para que ele só possa ser alterado pela classe `ContaCorrente`.

Se em algum momento desejarmos que seja possível um objeto visualizar o valor da propriedade `saldo`, será necessário criar um método na classe `ContaCorrente` para que o objeto consiga chamar esse método e possibilitar a visualização desse valor.

Dessa forma utilizamos o encapsulamento para proteger uma propriedade de alterações e até mesmo a visualização dela.

Todos os métodos e propriedades com o `public` podem ser visíveis e utilizados externamente. Todos os métodos `private` só podem ser visualizados pela própria classe em que eles foram criados.