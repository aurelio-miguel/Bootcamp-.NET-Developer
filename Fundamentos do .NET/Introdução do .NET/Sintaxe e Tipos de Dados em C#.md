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