# Sintaxe e Tipos de Dados em C#

## Entendendo a estrutura de um projeto
Assim que você inicia um novo projeto utilizando o comando ``` dotnet new console ```, vai ser criado uma estrutura com uma pasta com o noma *bin*, uma outra pasta com o nome *obj* e dois arquivos. Um deles com o nomme do seu projeto e a extensão *.csproj* e um outro arquivo com o nome *Program.cs*

![Imagem com a estrutura do projeto](/imagens/estrutura_projeto.png)

- **Program.cs**: *Program* é o nome da classe principal do projeto. Todo arquivo de classe possui a extensão *.cs*, isso identifica que é um arquivo do C#.

- **nome_projeto.csproj**: Esse é um arquivo de projeto do C#, nesse arquivo estão os metadados do projeto, esse arquivo está no formato XML. São informações descritivas sobre o projeto. É possível inserir novas tags reconhecidas pelo C#, essas informações dizem como o projeto deve ser executado e com ele deve funcionar. Esse arquivo é criado de forma automática e geralmente não é necessário alterar esse arquivo.

- **Pasta obj**: Essa pasta é referente a arquivos de debug, são arquivos de compilação. No geral esses arquivos também não são alterados.

- **Pasta bin**: Essa pasta contem os binários do projeto, após compilar o projeto os arquivos serão gerados de forma automática nessa pasta. Essa pasta é criada após a compilação e dentro dessa pasta é possível identificar o executável do projeto.

**Obs: Sempre que um projeto em C# é compilado, as pastas *obj* e *bin* são criadas novamente. Se for compartilhar um projeto não é necessário enviar também essas pastas, tendo em vista que ao compilar, elas serão criadas novamente. Se as pastas forem apagadas, basta gerar o comando ```dotnet build``` para que as pastas sejam criadas novamente.**

## O conceito de classe
A classe está relacionada ao conceito de abstração na programação orientada a objeto (POO). A bastração consiste em basicamente pegar um objeto do mundo real e transformar ele em um objeto na programação, dessa forma você poderá trabalhar com esse objeto e implementar as ações.

Segue abaixo um exemplo de uma abstração e a respectiva classe que representa essa pessoa

![Imagem de uma classe pessoa](/imagens/classe-pessoa.png)
Uma classe é sempre representada com os atributos primeiro e posteriormente os métodos.
~~~~
public class Pessoa{
    public string Nome {get; set;}
    public int Idade {get; set;}

    public void Apresentar(){
        Console.WriteLine($"Olá, Meu nome é {Nome} e tenho {idade} anos");
    }
}
~~~~

Neste exemplo foi possível abstrair os atributos de uma pessoa e também os métodos para esse objeto. As caacterísticas são o nome e a idade, a ação é se apresentar. Só deve ser inserido características e ações que vão trazer sentido ao projeto.

A classe funciona de forma similar a um molde, ela vai representar como um determinado objeto será construído. A classe é a forma como um objeto será representado, conforme consta no código acima.

## Criando a primeira classe

1. Crie uma nova pasta no seu projeto, por padrão coloque o nome de *models*;

2. Dentro dessa pasta clique com o botão direito do mouse sobre a pasta models, posicione o mouse sobre o item *New C#* e clique na opção *Class*;
![Imagem com as etapas para criar uma nova classe](/imagens/criar%20uma%20nova%20classe.png)
Essa opção só vai estar disponível se a extensão *C# Extensions* estiver instalada no VS Code, porém, a criação do arquivo pode ser feita manualmente.

3. Vai ser exibido uma área para que você possa escolher o nome da classe para a classe, o ideal é sempre utilizar a primeira letra do nome da classe em maiúsculo, por convensão. Se for um nome com duas palavras, basta deixar a primeira letra de cada palavra com o maiúsculo, por exemplo "PessoaFisica".
![Imagem com o campo para inserir o nome da classe](/imagens/nome%20para%20a%20classe.png)

4. Após isso, a classe será criada com uma estrutura padrão. Você pode criar o arquivo manualmente e digitar a estrutura sem a necessidade de seguir os passos anteriores. É importante que o nome da classe siga a convensão relacionada a primeira letra em maiúsculo e ela esteja inserida dentro da pasta models.

### Estrutura básica de uma classe
```
using System;
using System.Collections.Generic;
using System.Linq;
using System.Threading.Tasks;

namespace Aula01.models
{
    public class Pessoa
    {
        
    }
}
```

### Inserindo um atributo
Os atributos devem ser inseridos dentro da classe pessoa, conforme consta no trecho abaixo. Nesse trecho serão criados dois atributos, um atributo para o nome e o outro para a idade. Por convensão, os nome dos atributos devem ser criados com a primeira letra em maiúsculo.
```
public class Pessoa{
    public string Nome {get; set;}
    public int Idade {get; set;}
}
```

### Criando os métodos
O método é basicamente uma ação que o objeto **Pessoa** pode realizar. O método também deve ser criado dentro da classe pessoa.

```
public void Apresentar(){
    Console.WriteLine($"Olá, me chamo {Nome} e tenho {Idade} anos");
}
```
Nesse trecho de código foi criado uma classe com o objetivo de exibir um texto na tela contendo o nome do atributo *Nome* e a *Idade* que será atribuída ao objeto em questão. O *$* está dentro da função de escrita para que possamos exibir os objetos junto ao texto.

#### Classe completa
```
using System;
using System.Collections.Generic;
using System.Linq;
using System.Threading.Tasks;

namespace Aula01.models
{
    public class Pessoa
    {
        public string Nome { get; set; }
        public int Idade { get; set; }

        public void Apresentar()
        {
            Console.WriteLine($"Olá, me chamo {Nome} e tenho {Idade} anos");
        }
    }
}
```

### Entendendo a estrutura do código.
- **Classe:** Nessa etapa podemos perceber que esse elemento se trata de uma classe pois ele possui a palavra reservada `class`. A palavra seguida do nome *class* é o nome da determinada classe em questão. A abertura de chaves e o fechamento, representa o inicio da classe e o final dela.
```
public class Pessoa{
    ...
}
```

- **Propriedades:** As propriedades devem estar inseridas dentro do escopo(chaves) da classe em questão. Após a declaração do nome da propriedade foi feito a abertura e fechamento de chaves com o `get` e o `set` inseridos, o get tem como objetivo capturar o valor que está armazenado na propriedade e o set tem como finalidade alterar ou atribuir um valor a propriedade.
```
public class Pessoa{
    public string Nome { get; set; }
    public int Idade { get; set; }
}
```

- **Método:** O método também pode ser chamado de função e até mesmo ação, ele vai possuir uma dupla de parenteses para que possam ser inseridos parâmetros que podemos precisar para executar alguma função desse método. Nessa função temos a palavra void, essa palavra representa o tipo de retorno da função, como essa função não tem nenhum retorno, é utilizado a palavra `void`. Se o retorno fosse um número, seria utilizado a palavra `int`, por exemplo.
```
public class Pessoa{
    //Propriedades aqui

    public void Apresentar(){
        Console.WriteLine($"Olá, me chamo {Nome} e tenho {Idade} anos");
    }
}
```
Dentro desse método foi utilizado o método `Console.WriteLine()` para exibir no console o texto em aspas. Nessa função foi chamado o nome e a idade, dados que constam na declaração das propriedades. O `Console` é uma classe e o `WriteLine` é um dos métodos dessa classe. Um exemplo disso será executar a função *Apresentar()* da classe *Pessoa*, seria necessário escrever da seguinte forma `Pessoa.Apresentar()`. Dentro dos parenteses é inserido os parâmetros da função, a necessidade é a utilização dos parâmetros/argumentos dependem da necessidade deles para a execução da função.

- *Namespace:* A função é inserida dentro do Namespace, o namespace é uma organização das classes existentes no projeto, representa o caminho lógica para identificar classes que estejam no mesmo domínio. No geral o namespace contem o nome do projeto e a posta onde a classe está inserida.

```
namespace Aula01.models
{
    //Classe deve estar aqui
}
```
Nessa declaração temos o nome do projeto e a pasta em que esse projeto está inserido. Esse nome pode ser alterado, porém, é interessante seguir o padrão definido e utilizar de forma organizada. Essa informação é apenas organizacional. 

### Palavras reservadas
Existem algumas palavras que não podemos inserir como nome de variáveis, nome de classes e etc. Essas palavras são as palavras que o próprio C# utiliza, por exemplo *int*, *void*, *class* e etc. Uma alternativa para utilizar palavras reservadas é utilizando o *@* no inicio do nome, por exemplo `@class`, porém, isso não é recomendado.

## Instanciando uma classe
Para que possamos utilizar a classe criada, precisamos instanciar essa classe para a utilização. 

A primeira etapa vai ser retornar para o arquivo principal que está na raiz do projeto, o arquivo principal é o **Program.cs** e sempre que o programa for executado, o primeiro arquivo a ser lido é o arquivo **Program.cs**

### Criando uma nova instância e utilizando o namespace
Para que possamos instanciar a classe, o primeiro passo vai ser informar o caminho de onde essa classe está, para isso utilizaremos o *namespace* da classe criada. O caminho físico até o arquivo não é o importante, vai ser através do namespace que o sistema vai conseguir reconhecer a classe que será instanciada. Isso é necessário pois uma classe pode ser utilizada para mais de um contexto, é possível ter classes com o mesmo nome, desde que o namespace seja diferente pois o namespace é o endereço da classe.
```
using Aula01.Models;
Pessoa pessoa1 = new Pessoa();
```
O termo `Pessoa` indica que a variável `pessoa1` é do tipo pessoa. o termo `new Pessoa` é a chamada para a construção da variável como a determinada classe.

Existe também uma alternativa para o instanciamento da classe que é colocando namespace junto a classe, conforme consta abaixo
```
Aula01.Models.Pessoa pessoa1 = new Aula01.Models.Pessoa();
```
Esse segundo caso é para situações onde o projeto vai possuir classes com o mesmo nome.

## Utilizando a classe instânciada
A partir do momento que uma classe é instanciada, a variável vai receber o tipo da determinada classe instanciada. A partir desse momento a variável vai estar inserida na memória e estará pronta para a utilização.

A partir desse momento podemos mudar os atributos da pessoa, por exemplo o nome e a idade;

### Alterando as propriedades
```
pessoa1.Nome = "Aurélio Miguel";
pessoa1.Idade = 26;
pessoa1.Apresentar();
```
Através do trecho `pessoa1.` podemos ter acesso a propriedades e também métodos da nossa variável *pessoa1*, o ponto após a variável significa uma contiuidade em uma ação. Com o código acima nós conseguimos definir os valores das propriedades para esse objeto e executar a função.

## Convenções case
Durante a escrita dos códigos, é sempre importante se atentar aos padrões/convenções de escritas utilizados pelos desenvolvedores. Caracteres especiais não devem ser utilizados de forma alguma, o único caractere especial aceito é o underline.

O *Case* é um padrão de escrita para nomes, dentre eles temos:
- **camelCase**: Se tiver mais de uma palavra, o espaço é representado pela letra em maiúsculo;
- **PascalCase**: Todas as palavras começam com a letra maiúscula;
- **snack_case**: As palavras são separadas pelo underline;
- **spinal-case** As palavras são separadas pelo travessão;

No C# as cases utilizadas no geral é o **camelCase** e **PascalCase**

### Convenções case no código:
- **Nome de classes**: Sempre utilize o PascalCase;
- **Nome de propriedades**: Sempre utilize o PascalCase;
- **Nome de métodos**: Sempré utilize PascalCase;
- **Variáveis**: Sempre utilize o camelCase;

### Convenções de escrita de classe
É sempre importante que a classe criada tenha o mesmo nome do arquivo em questão. Se criarmos um arquivo com o nome **Pessoa.cs**, a classe inserida nesse aquivo deve manter esse mesmo nome.

Uma convenção importante é nunca abreviar o nome de métodos, propriedades e classes.

# Tipos de dados
Os tipos de dados são basicamente os tipos de informações que podemos iremos armazenar nas variáveis e trabalhar em algumas funcionalidades do nosso sistema, por exemplo no retorno de um método. Abaixo você encontrará uma lista com os principais tipos que utilizaremos.

- **string**: Série de caracteres, as strings sempre devem estar entra aspas duplas, por exemplo o nome Aurélio, cada letra é um caracter. A string é como um texto, aceita letras, espaços, caracters especiais e números;

- **char**: Representa um caractere. O nome "Olá" é composto por 3 caracteres. Uma variável do tipo *char* vai armazenar um único caractere;

- **bool**: O tipo boleano pode armazenar duas informações, true/verdadeiro ou false/falso. Essa variável vai representar um desses dois tipos de dados e é o valor mais utilizado na programação; 

- **int**: É um tipo que representa um número sem casas decimais, por exemplo a representação de uma idade. É utilizado para representar qualquer valor inteiro;

- **decinmal**: Esse tipo de dado pode representar valores decimais com 28-29 casas decimais, normalmente é utilizado para armazenar valores monetários.

- **float**: Representa valores decimais, valores com vírgula. Esse tipo em específico é 32 bits;

- **doble**: Também é utilizado para representar valores com casas decimais, porém, com uma maior precisão em relação ao float. Esse tipo de dado é 64 bits. 

## Declarando os tipos de dados e variáveis

Variável é uma um valor que vai ficar alocado na memória para ser utilizado no programa. Todas as variáveis devem ter um tipo. O nome da variável funciona como um endereço, após a declaração será possível obter a informação armazenada em uma variável através do nome dela. 

A variável só pode ser declarada uma única vez, não sendo possível ter duas variáveis com o mesmo nome.

Na declaração de variáveis sempre utilizaremos a estrutura **tipo_da_variavel + nome da variável = valor_da_variavel;**.

```
string nome = "Aurélio Miguel";
string apresentacao = "Olá, seja muito bem vindo!!";
int quantidade = 4;
double altura = 1.83; //Sempre representado com o . e não vírgula.
decimal preco = 4.99M;
bool casado = true;
```

Após a declaração de uma variável, não será possível atribuir a ela um valor diferente do tipo que ela foi declarada pois o C# é uma linguagem fortemente tipada;

**Obs:**O double não precisa se representado necessariamente com as casas decimais, caso não seja inserido por exemplo *.50*, ele vai interpretar a falta de informação como um *.00*;

### Manipulando uma variável
Para alterar o valor de uma variável, basta seguir a estrutura com o **nome_da_variavel = novo_valor**, lembrando que o valor precisa ser do mesmo tipo da variável que foi decladara inicialmente.


```
string nome = "Aurélio Miguel";

nome = "Aurélindo Miguel"; //A variável iniciou com um valor e foi altrada.
```

### Variáveis do tipo data.
O tipo **DateTime** é uma maneira de representar datas no C#. O primeiro passo vai ser declarar a variável com o tipo `DateTime nomeVariavel = `. Após isso, você conseguirá acessar os métodos do DateTime com o comando `DateTime.`
```
DateTime dataAtual = DateTime.Now;
```
Esse método **Now** pega o horário e data atual do computador em que o comando está sendo executado;

#### Explorando possibilidades
Para inserir dias na data, podemos aplicar o método AddData(valor), por exemplo `DateTime dataAtual = DateTime.Now.AddData(3)`, esse comando vai pegar a data e hora atual e inserir 3 dias, por exemplo.

Para exibir apenas a data, podemos realizar a conversão com o método *ToString()* e podemos passar o formato desejado, por exemplo `Console.WriteLine(dataAtual.ToString("dd/MM/yyyy"));`.

Para exibir apenas a data atual, o horário e os segundos, podemos utilizar o formato `.ToString("dd/MM/yyyy HH:mm")`;