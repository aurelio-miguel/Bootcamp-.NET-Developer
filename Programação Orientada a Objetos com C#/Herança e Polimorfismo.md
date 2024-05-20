# Herança e Polimorfismo
Nessa etapa iremos ver mais dois pilares da orientação a objetos, conhecidos como herança e polimorfismo.

## Introdução a Herança
A herança nos permite reutilizar atributos, métodos e comportamentes de uma classe em outras classes. Serve para agrupar objetos que são do mesmo tipo, porém, com característics diferentes.

![Exemplo do por que usar herança](/imagens/exemplo%20herança.png)
No diagrama acima podemos ver uma classe Aluno e uma classe Professor. Perceba que algumas propriedades como `Nome` e `Idade` são propriedades iguais e o método `Apresentar()` também é comum para as duas classes, ao implementar essas classes vai ser possível verificar que vai ocorrer duplicidade de código por conta das propriedades. 

Para evitar essa duplicidade de código exemplificada no diagrama acima, podemos utilizar o conceito de herança.

![Diagrama exemplificando a herança](/imagens//diagrama%20herança.png)

Conforme o exemplo acima, nós introduzimos uma classe `Pessoa`, essa classe é genérica e vai conter os atributos e métodos que são comum entre as duas classes que vão herdar a classe `Pessoa`. Dessa forma não precisaremos duplicar essas propriedades e métodos na classe `Aluno` e `Professor`. A seta está indicando que a classe Aluno e Professor vão herdar da classe `Pessoa`.

Os atributos e métodos que forem específicos de cada uma das classes que estão herdando da classe `Pessoa` devem ser criados em suas classes normalmente.

A partir do momento em que a herança é feita, as classes que estão herdando vão ter os atributos e métodos da classe "pai". Sem a necessidade de implementar na classe "filho". Tudo que está na classe `Pessoa` vai estar nas classes `Aluno` e `Professor`.

## Herança na prática
Agora vamos criar um novo projeto de console para implementar o exemplo do diagrama de herança citado na aula anterior. 

Vamos iniciar criando uma classe chamada `Aluno`, uma outra classe chamada `Professor` e a nossa terceira classe com o nome `Pessoa`, todas as classes devem estar na pasta **Models** na raiz do projeto.

Vamos iniciar trabalhando com a classe `Pessoa`. Nessa classe vamos criar a propriedade `Nome` e `Idade`, além disso criaremos o método `Apresentar()`. Segue abaixo o código da classe `Pessoa`:

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

Agora vamos ir até a classe `Aluno` para fazer o processo de herança. A classe `Aluno` vai herdar os atributos e métodos da classe `Pessoa`. Para isso, logo após o nome da classe vamos inserir o trecho `: classe_que_queremos_herdar`, segue abaixo a classe `Aluno` herdando a classe `Pessoa`:
```
using System;
using System.Collections.Generic;
using System.Linq;
using System.Threading.Tasks;

namespace Exemplo_POO.Models
{
    public class Aluno : Pessoa
    {

    }
}
``` 
Dessa forma a herança já está pronta. Agora poderemos utilizar os atributos e métodos da classe `Pessoa` na classe `Aluno`. Conforme consta abaixo, criando um novo objeto do tipo `Aluno` no arquivo `Programa.cs` podemos utilizar as propriedades e métodos da classe `Pessoa`:
```
using Exemplo_POO.Models;

Aluno aluno1 = new Aluno();

aluno1.Nome = "Aurélio";
aluno1.Idade = 26;
aluno1.Apresentar();

Output:
Olá, meu nome é Aurélio e tenho 26 anos
```

Agora podemos inserir as coisas específicas da classe Aluno normalmanete. Podemos também fazer o mesmo processo de herança na classe `Professor`.

As classes `Professor` e `Aluno` também podem ser classes pais de outras classes. Novas classes também podem herdar essas duas. Dessa forma a classe vai herdar os atributos e métodos da classe `Aluno` e também da classe que o aluno herda que é a classe `Pessoa`. Isso não é algo muito recomendado pois isso aumenta a complexidade do código.

Não é possível herdar de mais de uma classe ao mesmo tempo herança múltipla não existe no C#.

## Introdução ao Polimorfismo
Polimorfismo vem do grego e significa "muitas formas." Com o polimorfismo podemos sobrescrever métodos das classes filhas para que se comportem de maneira diferente e ter sua própria implementação. 

![Diagrama com exemplo de polimorfismo](/imagens/diagrama%20polimorfismo.png)

No diagrama acima podemos ver que a classe **Aluno** e **Professor** herdam da classe **Pessoa**. Porém, percebam que o método `Apresentar()` foi herdado da classe **Pessoa** e ele possui um comportamento diferente nas classes Aluno e Professor. Isso ocorre pois com o polimorfismo podemos sobrescrever os métodos para que eles tenham um comportamento diferente em cada uma das classes herdadas. 

Utilizando o polimorfismo podemos sobrescrever os métodos para casos em que queremos fazer algo diferente. 

## Polimorfismo em tempo de execução
O primeiro passo para que possamos indicar que um método pode ser sobrescrito é inserindo o trecho `virtual` logo após o nome public do método. 

Segue abaixo um exemplo disso na classe `Pessoa`:
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

        public virtual void Apresentar()
        {
            Console.WriteLine($"Olá, meu nome é {Nome} e tenho {Idade} anos");
        }
    }
}
```
O `virtual` indica que esse método poderá ser sobrescrito se a classe filha desejar. 

A partir desse momento as classes que herdarem a classe **Pessoa** poderão sobrescrever esse método `Apresentar()`. 

Para sobrescrever utilizaremos o `override` na criação do método na classe filho, conforme consta abaixo na classe **Aluno** que está herdando a classe **Pessoa**:
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

        public virtual void Apresentar()
        {
            Console.WriteLine($"Olá, meu nome é {Nome} e tenho {Idade} anos");
        }
    }
}
```
Dessa forma podemos sobrescrever a método `Apresentar` para que ela tenha um comportamento diferente na classe `Aluno`. O `override` significa sobrescrever em português, ele permite que possamos sobrescrever métodos da classe pai. O método só será sobrescrito na classe que nós criamos. 