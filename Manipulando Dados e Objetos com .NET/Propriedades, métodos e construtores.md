# Introução do Módulo

O objetivo desse módulo será explocar a linguagem C#, apresentando diferentes possibilidades e capacidades da linguagem, bem como nos aprofundarms mais sobre suas características.

## Introdução Propriedades
Propriedade é um membro que oferece um mecanismo flexível para ler, gravar ou calcular o valor de um campo em particular. A propriedade é um conceito vindo da orientação a objeto que tem como objetivo trazer as caracterísca de um determinado objeto.

Imagine que estamos trabalhando com uma classe pessoa, as propriedades são as características que serão importante para o nosso obejetivo com essa classe. Nesse contexto, as características podem ser por exemplo a idade, nome, cor e etc. A classe é um molde que representa um objeto do mundo real.;

Na imagem abaixo podemos ver a representação da classe pessoa, essa classe possui duas propriedades, o nome e a idade. Além disso, ela possui também um método chamado Apresentar.

![Exemplo classe pessoa](/imagens/classe_pessoa_representação.png)

Segue abaixo um trecho de código exemplificando como fica a representação de atributos de uma classe pessoa:

```
namespace projeto1.Models
{
    public class Pessoa
    {
        public string Nome { get; set; }
        public int Idade { get; set; }

        ...
    }
}
```

No código acima temos as propriedades nome e idade. A propriedade nome possui o tipo string e a propriedade idade possui o tipo inteiro, os geters e seters também são inseridos diretamente na declaraçã das variáveis.

O **get** é utilizado para obter o valor armazenado na propriedade, o **set** é utilizado para atribuir um valor para essa determinada propriedade.

Ao instânciar uma classe pessoa conseguiremos inserir o nome e a idade da determinada pessoa.

## Criando o método
O método é uma ação de uma determinada classe, é uma função que poderá ser executada. No contexto da classe pessoa citada anteriormente, o método se chama *apresentar()* e o objetivo dele é imprimir no console uma apresentação com base nas propriedades já definidas anteriormente.

Segue abaixo a classe **Pessoa** com as propriedades e o método *apresentar()*:
```
namespace projeto1.Models
{
    public class Pessoa
    {
        public string Nome { get; set; }
        public int Idade { get; set; }

        public void Apresentar()
        {
            Console.WriteLine($"Nome: {Nome}, Idade: {Idade}");
        }
    }
}
```
Na definição do método iniciamos com o `public` para indicar que esse método é público. Em seguida informamos o tipo do retorno com o trecho `void`, o void representa que não possui um retorno, caso houvesse um mretorno seria necessário substituir esse trecho pelo tipo do returno. Logo em seguida nós inserimos o nome do nosso método `Apresentar()`, sem nenhum parâmetro.

Dentro das chaves utilizamos o método WriteLine da classe Console para exibir no console a apresentação.

O `{Nome}` e o `{Idade}` é um exemplo de get pois os valores serão capturados e exibidos no console.

### Observações:
A classe **Pessoa.cs** foi inserida dentro da nova pasta *Models* que foi criada na raiz do nosso projeto.

### Instânciando a classe
A primeira etapa é ir até o arquivo *Program.cs* para importar o namespace para indicar o caminho da nossa classe, para importar basta utilizar o comando `using namespaceDaClasse;`

No código abaixo estamos importando o namespace e instânciando a classe Pessoa. Após instânciar a classe pessoa teremos uma variável com o nome **p1** do tipo **Pessoa**.
```
using projeto1.Models;

Pessoa p1 = new Pessoa();
```

A partir do momento que a variável é do tipo pessoa, poderemos inserir os valores de nome e idade para essa variável, além disso podemos utilizar o método **Apresentar()**, conforme consta no código abaixo:

```
using projeto1.Models;

Pessoa p1 = new Pessoa();

p1.Nome = "Aurélio Miguel";
p1.Idade = 26;

p1.Apresentar();
```
O comando `p1.Nome` é um exemplo de um set.

Ao executar o comando `dotnet run` teremos a seguinte saída:
```
Nome: Aurélio Miguel, Idade: 26
```
Essa saída foi graças ao método **Apresentar()** que criamos lá na classe **Pessoa**.

## Validando no GET e SET
Quando iniciamos com o GET e o SET vazio, significa que estaremos aceitando qualquer valor passado para eles, ele não vai validar nenhum valor.

### Validando o nome com o SET
Queremos que o nome não seja vazio, para isso iremos criar um campo do tipo privado e vai ter o nome `_nome`. Segue abaixo o trecho de código com o novo campo:
```
...
public class Pessoa{

    private string _nome;
    public string Nome { get; set; }

    ...
}
```
o campo `_nome` vai ser um campo que vai armezenar a propriedade `Nome`. O **Private** faz com que apenas a classe **Pessoa** possa alterar esse campo. 

Segue abaixo o código para que possamos validar se o o *Nome* não é nolo:
```
private string _nome;
public string Nome
{
    get;

    set
    {
        if (value == "")
        {
            throw new ArgumentException("O nome não pode ser vazio");
        }
        _nome = value;
    }

}
```

Através do `set` realizamos a verificação vo `value` para verificar se ele é nulo ou não. O value é exatamente o valor do nome que foi atribuído logo após a instância desse objeto. No arquivo **Program.cs** foi feito o comando `p1.Nome = "Aurélio Miguel"`, o value do código acima terá exatamente esse valor.

Após realizar a verificação, se o valor fosse nulo foi criado uma excessão, essa excessão gera o erro que foi escrito entre aspas duplas e encerra o nosso código. Após essa verificação, se o código não for encerrado por conta do erro, o campo `_nome` vai receber o value que foi passado no `p1.Nome` no arquivo **Program.cs**

Após executar o comando ``throw new ArgumentExceprion("");`` o código não vai continuar sendo executado, o programa será encerrado.

### Obtendo o valor com o GET
Para obter o valor do nome utilizaremos o GET e retornaremos a variável `_nome` que no tópico anterior o valor que foi passado através do SET

Para obter o valor utilizaremos o trecho de código abaixo:
```
public string Nome
        {
            get
            {
                return _nome.ToUpper();
            }

            set
            {
                if (value == "")
                {
                    throw new ArgumentException("O nome não pode ser vazio");
                }

                _nome = value;
            }

        }
```

O return permite que ao chamar o GET, ele retorne o **_nome** dessa forma poderemos atribuir esse valor a uma variável ou utilizar para a exebição do nome da pessoa no console, por exemplo. Utilizamos o método `.ToUpper` para que o nome fique todo em maísculo.

A partir de agora, teremos uma verificação se o nome e nulo graças ao **SET** e ao chamar a variável `Nome`, vai retornar o nome em maiúsculo por conta do **GET**.

## Body Expressions
É possível simplificar o GET e SET com body expressions. Podemos simplicar o retorno do GET seguindo o padrão abaixo:

```
  public string Nome
        {
            get => _nome.ToUpper();

            set
            {
                if (value == "")
                {
                    throw new ArgumentException("O nome não pode ser vazio");
                }
                _nome = value;
            }

        }
```

Não é possível inserir o Body Expressions no SET pois o set possui uma verificação um pouco maior, se ele tivesse apenas um retorno seria possível utilizar o Body Expressions.

## Validando a propriedade idade
Para realizar a validação, iniciaremos criando um campo privado para a variável idade e depois iremos tratar ela no SET e GEt

Inserindo o campo privado para a propriedade Idade
```
private int _idade;
```

No código abaixo iremos utilizar o GET para retornar o campo `_idade` e o SET para verificar se o value que foi inserido através do comando `p1.Idade` do arquivo **Program.cs** é maior que zero.

```
private int _idade;
public int Idade
{
    get => _idade;
    set
    {
        if (value <= 0)
        {
            throw new ArgumentException("A idade deve ser maior que zero");
        }
        _idade = value;
    }
}
```
Caso o valor seja menor ou igual a zero, o programa será encerrado com o erro inserido entre aspas duplas na excessão.

## Modificadores de acesso
Diversas vezes utilizamos a palavra **public** e **private** nas nossas classes, esses são os modificadores de acesso mais comuns. 

O **public** significa que qualquer um pode acessar essa classe ou propriedade. Quando indicamos que uma classe é pública, qualquer um pode isntânciar a determinada classe. Quando indicamos que uma propriedade é public, significa também que qualquer pessoa pode acessar a determinada classe.

O **private** consegue ter um acesso restrito, ele só permite que uma propriedade seja acessada dentro da própria classe, as propriedades não são acessíveis após instânciar a classe, por exemplo. Com o **private** a propriedade vai estar protegida de alterações externas.

## Propriedades somente leitura
Podemos também ter uma propriedades apenas de leitura, nesse caso a propriedade vai ter apenas o elemento GET. 

Imagina que você tenha uma propriedade com o nome inicial e uma outra com o sobrenome. Em um momento que seja necessário exibir o nome completo, vai ser preciso utilizar as duas própriedades, por exemplo: `Console.WriteLine($"Nome completo: {Nome} {Sobrenome}");`. Nesse caso, podemos criar uma propriedade apenas para juntar o nome e o sobrenome, não vai fazer sentido para essa propriedade ter o SET pois ela não deverá ser alterada quando uma classe for alterada, essa propriedade será apenas de leitura/GET.

Para criar essa propriedade apenas com o GET, podemos utilizar o body expressions para que ela retorne apenas uma string com o Nome e Sobrenome
```
public string NomeCompleto => $"{Nome} {Sobrenome}";
```

## Introdução aos métodos
Um método é um bloco de código que contém uma séria de isntruções, em algumas outras linguagens é conhecida como funções. Você pode entender um método como uma ação que uma determinada classe pode fazer. O método também facilita o aproveitamento de códigos, tendo em vista que podemos chamar o moesmo método várias vezes utilizando apenas o nome dela, sem precisar escrever novamente todo o código com o objetivo do método.

Nos diagramas abaixo temos dois exemplos de casse com cada um dos propriedades e métodos de cada uma das classes. O nome da classe é a informação localizada na parte superior de cada diagrama, as propriedades são as informações localizados na segunda área e os métodos são as informações que estão na terceira área. Conforme a imagem abaixo:
![Diagrama para exemplificar métodos](/imagens/métodos.png)

A propriedade **Alunos** da classe Curso é uma lista de pessoas, é uma lista do tipo Pessoa, podendo explorar todas as propriedades e funcionalidades da classe pessoa.

## Implementando a classe curso
O primeiro passo vai ser criar uma nova classe com o nome **Curso**, o arquivo da classe deve ser inserido dentro da pasta *Models*, na mesma pasta em que está  arquivo da classe Pessoa que criamos anteriormente.

Segue abaixo o esqueleto do arquivo da nossa classe, o arquivo **Curso.cs**:
```
using System;
using System.Collections.Generic;
using System.Linq;
using System.Threading.Tasks;

namespace projeto1.Models
{
    public class Curso
    {

    }
}
```

Vamos iniciar inserindo propriedade para o nome do curso, as propriedades sempre devem ser inseridas dentro do escopo da classe, conforme consta abaixo:
```
public class Curso
{
    public string Nome { get; set; }
}
```

Agora criaremos uma propriedade do tipo lista que vai armazenar as pessoas, a coleção será uma lista de pessoas. Segue abaixo o script para a criação dessa propriedade:
```
public class Curso
{
    public string Nome { get; set; }
    public List<Pessoa> Alunos { get; set;}
}
```

Agora vamos criar o método para adicionais alunos, o método deve ser criado também dentro do escopo da classe Curso, conforme consta no trecho abaixo:
```
public class Curso
{
    ...

    public void AdicionarAluno(Pessoa aluno)
    {
        Alunos.Add(aluno);
    }
}
```
Nós sabemos que essa estrutura é um método por conta da sua assinatura, a assinatura é algo que torna esse método algo único. No exemplo acima a assinatura é o trecho `void AdicionarAluno()`, o comando void significa que esse método não terá nenhum retorno e após ele nós devemos inserir o nome do método com Pascal Case e devemos inserir os parenteses para que possamos possibilitar a insersão dos parâmetros, se for algo necessário para o método. 

### Tipos de retorno
Os métodos podem ter diversos tipos de retorno. Para exemplificar isso iremos criar um método para retornar a quantidade de alunos matriculados no curso.

Segue abaixo o trecho de código em que criamos o método na arquivo **Curso.cs** da classe Curso:

```
public int ObterQuantidadeDeAlunosMatriculados()
{
    int quantidade = Alunos.Count;
    return quantidade;
}
```
Na assinatura desse método podemos visualizar que temos o tipo `int`, isso significa que esse nosso método terá um retorno do tipo inteiro. Sempre que um método tiver um retorno, precisamos inserir o tipo de retorno na assinatura e obrigatoriamente esse método precisará ter um retorno com o mesmo tipo de dado que foi declarado na assinatura. Através do `return ...;` retornaremos o valor inteiro desejado.

### Implementando o método para remover
Agora iremos criar um método para remover um aluno da lista. Esse método em específico não terá nenhum retorno, assinaremos ele com o retorno `void`. Esse método será inserido na classe Curso.

Segue abaixo um trecho de código exemplificando esse método:
```
...
public void RemoverAluno(Pessoa aluno)
{
    Alunos.Remove(aluno);
}
```
Para que possamos saber qual aluno deve ser removido, foi passado por parâmetro uma variável que será utilizada no escopo desse método com o tipo **Pessoa**. Dentro desse método foi inserido o comando `Alunos.Remove(aluno)` para remover o aluno da lista de alunos previamente criada.

### Implementando o método para listar os alunos
Nesta etapa iremos criar um método para listar todos os alunos. O objetivo desse método será listar o nome completo de todos os alunos matriculados

Segue abaixo o trecho de código onde realizamos a criação do método para listar os alunos. Para exibir o nome utilizamos o método WriteLine da classe Console.
```
Public void ListarAlunos()
{
    foreach (Pessoa aluno in Alunos)
    {
        Console.WriteLine($"Aluno: {aluno.NomeCompleto}");
    }
}
```
Nesse método trabalhamos com o `foreach` para listar todos os alunos inseridos na lista Alunos. Acessamos o nome completo através da propriedade `NomeCompleto` de cada um dos alunos, essa propriedade foi criada na classe Pessoa do arquivo **Pessoa.cs**.

### Instânciando a classe Curso e trabalhando com ela
Agora iremos instânciar a classe Curso no arquivo **Program.cs** para que possamos trabalhar com ela. 

Para instânciar a classe utilizaremos o trecho de código abaixo:
```
//Instânciando a classe Pessoa para a criação do p1 e p2

Pessoa p1 = new Pessoa();
p1.Nome = "Aurélio";
p1.Sobrenome = "Miguel";
p1.Idade = 26;

Pessoa p2 = new Pessoa();
p2.Nome = "Leonardo";
p2.Sobrenome = "Campos";
p2.Idade = 25;

//Instânciando a classe Curso para inserir os dados do curso e utilizar o método ListarAlunos para exibir os dois alunos inseridos.

Curso cursoDeIngles = new Curso();
cursoDeIngles.Nome = "Curso de Inglês";
cursoDeIngles.Alunos = new List<Pessoa>();

cursoDeIngles.AdicionarAluno(p1);
cursoDeIngles.AdicionarAluno(p2);

cursoDeIngles.ListarAlunos();
```
Após intânciar a classe Curso, foi necessário criar uma nova lista de alunos vazia para que posteriormente possam ser inseridos os elementos. Sempre que se tratar de uma lista, antes é necessário realizar a criação dela vazia. Esse procedimento foi feito na linha `cursoDeIngles.Alunos = new List<Pessoa>();`. Isso foi necessário pois na classe Curso, a propriedade Alunos é também uma lista.

Após isso foi inserido os alunos utilizando o método `AdicionarAluno(aluno)` para inserir os alunos na lista. O método `ListarAlunos();` é responsável pela exibição dos alunos que foram cadastrados.

## Trabalhando com construtores
Os construtores permitem que o programador defina valores padrão, limite a instanciação e grave códigos flexíveis e fácil de ler. O construtor permite que possamos instânciar uma classe e iniciar ela com valores padrão no momento da instânciação. Os construtores são sempre recomendados para a instânciação da nossa classe. 

### Criando um construtor para a classe Pessoa
O primeiro passo vai ser criar um construtor para a classe pessoa. Para isso, realizaremos a implementação do trecho de código abaixo na classe Pessoa:
```
public class Pessoa
{
    public Pessoa()
    {

    }
    public Pessoa(string nome, string sobrenome, int idade)
    {
        Nome = nome;
        Sobrenome = sobrenome;
        Idade = idade;
    }

    ...
}
```

Por convenção, o construtor é inserido logo no inicio do escopo da classe. Todo construtor deve ter o mesmo nome da classe e ele também não possui um tipo de retorno. O construtor pode ser vazio ou ele também pode receber parâmetros, os parâmetros serão para que possamos popular as propriedades da nossa classe. Nos parâmetros foi inserido o tipo do parâmetro e a variável que vai ser utilizada para que possamos atribuir a propriedade, dentro do escopo do nosso construtor.

Para que possamos ter a possibilidade de instânciar a classe Pessoa sem inserir inicialmente os parâmetros, realizamos a criação de mais um construtor sem os parâmetros, dessa forma podemos instânciar a classe no arquivo **Program.cs** como `new Pessoa();` ou como `new Pessoa(valores_aqui);`. Esses dois construtores são importantes para os casos em que precisaremos instânciar a classe tendo as informações previamente ou mesmo não tendo ainda os dados das propriedades.

Dessa forma teremos um construtor que não vai receber nada e teremos também um construtor que receberá os dados das propriedades.

### Instânciando a classe Pessoa
Agora com os dois construtores criados, poderemos instânciar a classe Pessoa de forma vazia ou já inserido as informações através do construtor no nosso arquivo **Program.cs**, conforme o trecho de código abaixo:
```
Pessoa p1 = new Pessoa();
p1.Nome = "Aurélio";
p1.Sobrenome = "Miguel";
p1.Idade = 26;

Pessoa p2 = new Pessoa("Leonardo", "Campos", 25);
```