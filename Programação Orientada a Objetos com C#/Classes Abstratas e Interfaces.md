# Classes abstratas e interfaces com C#

## Classes abstratas
Uma classe abstrata tem como objetivo ser exclusivamente um modelo para ser herdado, portanto não pode ser instânciada. Você pode implementar métodos ou deix-alos a cargo de quem herdar. As classes abstratas não podem ser trabalhadas diretamente com ela através de uma instância, por exemplo. Para trabalhar com esse tipo de classe precisamos obrigatoriamente herdar ela. 

No exemplo abaixo temos uma classe abstrata com o nome **Conta** e uma classe que está herdando a classe **Conta** que possui o nome de **Corrente**

![Diagrama de uma classe abstrata](/imagens/diagrama%20classe%20abstrata.png)

Conforme consta na imagem acima, os métodos também pode ser abstratos. Se um método for abstrato, será necessário implementar o método abstrato na classe que tiver herdando a classe do método que foi herdado, por exemplo com o método `Creditar()` do diagrama acima. 

A classe abstrata tem como objetivo servir como um molde para as classes que vão herdar ela.

## Classe abstrata na prática
Seguindo o exemplo do diagrama acima, vamos criar um novo projeto para implementa-lo. 

Para isso vamos criar a classe **Conta** e a classe **Corrente** na pasta **Models** do nosso projeto.

Para indicar que uma classe é abstrata vamos indicar com o termo `abstract` logo após a definição de `public`. Segue abaixo o exemplo na nossa classe **Conta**:
```
using System;
using System.Collections.Generic;
using System.Linq;
using System.Threading.Tasks;

namespace Exemplo_POO.Models
{
    public abstract class Conta
    {
        
    }
}
```
A partir desse momento a classe se torna abstrata e não poderá ser instânciada diretamente. 

Após isso vamos inserir uma propridade protegida com o nome de `saldo` e vamos criar o método `ExibirSaldo()` na classe **Conta**, além disso vamos criar o método abstrato `Creditar()`:
```
using System;
using System.Collections.Generic;
using System.Linq;
using System.Threading.Tasks;

namespace Exemplo_POO.Models
{
    public abstract class Conta
    {
        protected decimal saldo;

        public void ExibirSaldo()
        {
            Console.WriteLine($"O seu saldo é: {saldo}");
        }

        public abstract void Creditar(decimal valor);
    }
}
```
A propriedade `saldo` está como `protected`, esse termo faz com que essa propriedade esteja protegida de alterações, apenas as classes filhas poderão realizar alterações.

Perceba que o método `Creditar()` não possui um corpo com as funcionalidades dele, isso está ocorrendo pois ele é um método abstrado. A funcionalidade dele vai ser criada na classe que herdar a classe **Conta**

Agora vamos criar a classe **Corrente** que vai herdar a classe **Conta**. Vamos iniciar herdando a classe **Conta**, conforme consta no trecho abaixo:
```
using System;
using System.Collections.Generic;
using System.Linq;
using System.Threading.Tasks;

namespace Exemplo_POO.Models
{
    public class Corrente : Conta
    {
        
    }
}
```

Agora deveremos obrigatoriamente implementar o método abstrato `Creditar` da classe **Conta** que herdamos. Todos os métodos abstratos devem ser obrigatoriamente implementados. Segue abaixo o trecho de código com a implementação dessa classe:
```
using System;
using System.Collections.Generic;
using System.Linq;
using System.Threading.Tasks;

namespace Exemplo_POO.Models
{
    public class Corrente : Conta
    {

        public override void Creditar(decimal valor)
        {
            saldo += valor;
        }
    }
}
```
O método abstrado que foi herdado também deve ser criado com o `override` para indicar que está sobrescrevendo esse método da classe pai. o método `saldo` que foi incrementado nesse método está sendo utilizado da classe **Conta**

Agora no nosso arquivo **Program.cs** poderemos instânciar a classe **Corrente** para poder visualizar todos os detalhes:
```
using Exemplo_POO.Models;

Corrente c1 = new Corrente();
c1.Creditar(500);
c1.ExibirSaldo();

Output:
O seu saldo é: 500
```

## Construtor por herança
É possível implementar um construtor padrão na classe pai para que ele possa ser utilizado nas classes filhas. Para isso, vamos criar um novo projeto contendo uma classe **Pessoa** que será a classe pai e uma classe **Aluno** que vai herdar a classe **Pessoa**.

Vamos supor que ao instânciar a classe **Pessoa** queremos que obrigatório passar a propriedade `Nome`. Segue abaixo um exemplo de criação de um construtor para esse contexto:
```
namespace Exemplo_POO.Models
{
    public class Pessoa
    {
        public Pessoa(string nome)
        {
            Nome = nome;
        }
        public string Nome { get; set; }
        public int Idade { get; set; }

        public virtual void Apresentar()
        {
            Console.WriteLine($"Olá, meu nome é {Nome} e tenho {Idade} anos");
        }
    }
}
```

Agora precisaremos passar obrigatoriamente o valor de  `nome` nas classes que herdam a classe **Pessoa**. Para fazer isso, criaremos um construtor na classe filho que vai receber o `nome` e esse nome não será utilizado na classe filho, passaremos ele para a classe pai utilizando o termo `: base(nome)` diretamente no construtor, conforme o código abaixo:
```
namespace Exemplo_POO.Models
{
    public class Aluno : Pessoa
    {
        public Aluno(string nome) : base(nome)
        {

        }

        public double Nota { get; set; }

        public override void Apresentar()
        {
            Console.WriteLine($"Olá, meu nome é {Nome}, tenho {Idade} e sou um aluno nota {Nota}");
        }
    }
}
```

## Introdução a classe selada
Uma classe selada tem como objetivo impedir que outras classes façam uma herança dela, ou seja, nenhuma classe pode ser sua derivada. Também existem métodos e propriedades seladas. 

Na imagem abaixo podemos ver o exemplo da classe selada com o nome de **Professor**. A partir do momento que essa classe é selada, não podemos herdar essa classe em outras classes. A classe **Diretor** não pode herdar de **Professor**. A classe **Professor** pode herdar a classe **Pessoa** normalmente, porém, a classe **Professor** não pode ser herdade por nenhuma classe.

![Diagrama com classe selada](/imagens/classe%20selada.png)

### Metodo selado
O método selado é um método que não pode ser sobrescrito na classe filho. O método da classe pai pode ser utilizado normalmente na classe filho, porém, se esse método for selado, o filho não conseguirá sobrescrever ele. Conforme consta no exemplo do diagrama abaixo:

![Diagrama com método selado](/imagens/metodo%20selado.png)

## Classe selada na prática
Agora veremos na prática como funciona uma classe selada e um método selado. Para selar uma classe utilizaremos o comando `sealed` antes de iniciar a nossa classe. Conforme consta no exemplo abaixo:
```
namespace Exemplo_POO.Models
{
    public sealed class Professor : Pessoa
    {
        public decimal Salario { get; set; }
    }
}
```
A partir desse momento, nenhuma classe vai poder herdar da classe **Professor**, por mais que ela esteja herdando a classe **Pessoa**.

Uma classe selada significa que essa classe é uma instância final de uma herança. Ela não pode mais ter classes filhas. 

## Selando um método na prática
Segue abaixo um exemplo de como podemos selar um método para que as classes filhos não possam sobrescrever ele.
```
namespace Exemplo_POO.Models
{
    public class Aluno : Pessoa
    {
        public double Nota { get; set; }

        public sealed override void Apresentar()
        {
            Console.WriteLine($"Olá, meu nome é {Nome}, tenho {Idade} e sou um aluno nota {Nota}");
        }
    }
}
```
A partir do momento que utilizamos o termo `sealed` na classe `Apresentar`. Nenhuma classe que herdar a classe **Aluno** poderá sobrescrever o método `Apresentar()`.

## Introdução a classe object
A classe System.Object é a mãe de todas as classes na hierarquia do .NET. Todas as classes derivam, direta ou indiretamente da classe Object, ela tem como objetivo prover serviços de baixo nível para suas classes filhas.

Quando criamos uma classe, ela já herda de forma automática e sem a necessidade de implementação a classe Object, de forma automática também temos acesso a diversos métodos, conforme consta na imagem abaixo.

![Métodos da classe Object](/imagens/métodos%20classe%20object.png)

Esses métodos são objetos de mais baixo nível. Todas essas operações são operações um pouco mais complexas. Após criar uma nova classe, podemos ter acesso a todos esses métodos.

## Introdução a interfaces
Uma interface é um contrato quye pode ser implementado por uma classe. É como se fosse uma classe abstrata, podendo definir métodos abstratos para serem implementados. Assim como uma classe abstrata, uma interface não pode ser instânciada.

![Diagrama que exemplifica uma interface](/imagens/diagrama%20interface.png)
No diagrama acima podemos ver uma interface que possui o nome de **ICalculadora**, essa interface possui os métodos somar(), subtrair(), multiplicar() e dividir(). Esses métodos foram criados sem uma implementação na interface, eles são apenas contratos. Isso significa que toda classe que implementar essa interface, precisará implementar os métodos da interface. 

As classes **CalculadoraComum** e **CalculadoraCientifica** implementam a interface **ICalculadora**, por conta disso elas precisam implementar também todas as classes que estão na interface em questão. 

**Obs:** Quando falamos de interface, não utilizamos o termo herdar ou herando, quando estamos falando sobre interfaces utilizamos o termo "implementar".

Uma classe pode implementar várias interfaces, diferente da herança onde pode herdar apenas de uma classe.

## Interface na prática
Agora vamos criar um novo projeto para implementar o diagrama indicado na aula anterior.

Para inserir os arquivos de interface, vamos criar uma nova pasta na raiz do nosso projeto com o nome **Interfaces**, dentro dessa pasta vamos inserir todas as interfaces do nosso projeto.

A nossa interface terá o nome de **ICalculadora** e o arquivo terá o nome de **ICalculadora.cs**, Por convenção, todas as interfaces começam com a letra *i* em maiúsculo. Segue abaixo a estrutura básica de uma interface:
```
using System;
using System.Collections.Generic;
using System.Linq;
using System.Threading.Tasks;

namespace Exemplo_POO.Interfaces
{
    public interface ICalculadora
    {
        
    }
}
```
Diferente das classes que vimos anteriormente, na classe temos o termo `public class NomeClasse` na sua implementação, já na interface temos a estrutura `public interface INomeInterface`.

Agora vamos inserir na interface a descrição dos métodos matemáticas conforme o diagrama. Segue abaixo o trecho de código em questão:
```
namespace Exemplo_POO.Interfaces
{
    public interface ICalculadora
    {
        int Somar(int num1, int num2);
        int Subtrair(int num1, int num2);
        int Multiplicar(int num1, int num2);
        int Dividir(int num1, int num2);
    }
}
```
Aqui podemos ver mais algumas diferenças em relação a o que é feito nas classes. A primeiro diferença é que não utilizamnos a os ascessores como public, private e etc. Isso ocorre pois por ser uma classe fica subententido que todos são públicos. Um outro detalhe que podemos perceber é que as operações não possuem implementação, isso ocorre pois a implementação das funções deve ser feita obrigatoriamente pela classe que implementar essa interface, a interface vai funcionar como um contrato que vai obrigar a implementação desses métodos. Temos apenas a descrição dos métodos, temos apenas a assinatura dos métodos contendo o tipo de retorno, o nome e os parâmetros. 

Agora vamos criar uma classe com o nome **Calculadora** e vamos implementar a interface **ICalculadora** e também implementar os métodos. Para implementar a interface, segue abaixo o trecho de código com o procedimento:
```
using Exemplo_POO.Interfaces;

namespace Exemplo_POO.Models
{
    public class Calculadora : ICalculadora
    {
        
    }
}
```
A implementação da interface funciona de forma similar a herança, utilizamos o termo `: NomeInterface` logo após a implementação da classe. Um ponto importante é que devemos referenciar o endereço da interface através do namespace da interface. O namespace da interface deve ser citado utilizando o `using namespace_da_interface`, conforme consta no exemplo acima, dessa forma inserimos o import dela na nossa classe.

A partir do momento que implementamos a interface, precisamos obrigatoriamente implementar todos os métodos definidos na interface. Segue abaixo o código completo com a implementação dos métodos:
```
using Exemplo_POO.Interfaces;

namespace Exemplo_POO.Models
{
    public class Calculadora : ICalculadora
    {
        public int Somar(int num1, int num2)
        {
            return num1 + num2;
        }
        public int Subtrair(int num1, int num2)
        {
            return num1 - num2;
        }

        public int Multiplicar(int num1, int num2)
        {
            return num1 * num2;
        }
        public int Dividir(int num1, int num2)
        {
            return num1 / num2;
        }
    }
}
```

A partir de agora podemos instânciar a classe **Calculadora** no arquivo **Program.cs** e utilizar os métodos que a classe implementou da interface, segue abaixo um exemplo:
```
using Exemplo_POO.Models;

Calculadora c1 = new Calculadora();
Console.WriteLine(c1.Somar(2, 3));

Output:
5
```

## Método padrão na interface
Podemos também implementar um método padrão na interface, da mesma forma que fazemos na classe abstrata. Isso é feito escrevendo a implementação do determinado método diretamente na interface, conforme consta o exemplo abaixo:
```
namespace Exemplo_POO.Interfaces
{
    public interface ICalculadora
    {
        int Somar(int num1, int num2);
        int Subtrair(int num1, int num2);
        int Multiplicar(int num1, int num2);
        int Dividir(int num1, int num2)
        {
            return num1 / num2;
        }
    }
}
```

A partir desse momento, as classes que implementarem a interface **ICalculadora** não precisaram necessariamente implementar o método `Dividir()`, não vai ser necessário implementar o método dividir na nossa classe pois nesse caso ele vai utilizar o método que já foi construído diretamente na interface.