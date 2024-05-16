# Nuget, Serializer e Atributos no C#

## Introdução ao gerenciador de pacotes
Um pacte é um conjunto de códigos úteis, que possibilita o compartilhamento e reuso de código. O pacote é um conjunto de códigos que resolve um problema em específico, é um pequeno projeto que resolve um problema em específico. 

Esse pacote pode ser compartilhado com outros pessoas e sistemas, esses outros sistemas e pessoas poderão utilizar esse pacote

## Nuget
O Nuget é um gerenciador de pacotes, que permite desenvolvedores compartilharem códigos e bibliotecas. O Nuget é o gerenciador de pacotes oficial do .NET. 

![Imagens pacotes Nuget](/imagens/pacotes%20nuget.png)

No link abaixo você poderá conhecer mais sobre o Nuget e sobre os pacotes disponíveis
[Link para o site do Nuget](https://www.nuget.org/)

## Instalando um pacote pelo VS Code
O primeiro passo vai ser acessar o site do Nuget e selecionar o pacote que você deseja utilizar. Na nova tela você conseguirá ver mais detalhes sobre o pacote e também o comando que deve ser utilizado no terminal do VS Code para que esse pacote seja baixado para o projeto.

Segue abaixo uma imagem que indica onde contem o comando que deve ser utilizado para instalar o pacote:

![Imagem com os detalhes sobre um pacote no site Nuget](/imagens/nuget%20site.png)

Conforme indicado na imagem acima, existem diversas formas diferentes para realizar a instalação. Para que possamos instalar pelo VS Code, vai ser preciso utilizar o .NET CLI como método para instalação.

O comando que consta na área em azul é o comando que deve ser executado no terminal do VS Code. Lembe-se de que é preciso estar na raiz do seu projeto para realizar o comando em questão. 

Para prosseguir com o conteúdo vai ser necessário fazer a instalação do pacote `Newtonsoft.Json` no seu projeto.

[Link do pacote](https://www.nuget.org/packages/Newtonsoft.Json)

Após realizar a instalação do pacote, você conseguirá visualizar a referência desse pacote no arquivo **.csproj**. Segue abaixo uma imagem que consta essa referência que vai estar no arquivo:

![Imagem com a referência do pacote](/imagens/referência%20de%20pacote.png)

Nessa referência podemos visualizar o nome do pacote e também a sua versão.

## Introdução serialização e deserialização.
O processo de serializar consiste em trnasformar objetos em um fluxo de bytes para seu armazenamento ou transmissão.

![Imagem com diagrama para explicar a serealização](/imagens/serealização.png)

Quando instânciamos um objeto ele é utilizado apenas pelo nosso programa e no escopo do nosso programa. Para que possamos transmitir esse dado para outras aplicações ou armazenar esse estado do objeto, para isso vai ser necessário realizar o processo de serialização. 

A serialização permite que os objetos sejam transformados para uma estrutura aceita em um banco de dados, na memória do computador ou até mesmo em um arquivo, por exemplo. 

Na serialização um objeto é transformado em um fluxo de bytes para armazenar ou transmitir esse dado. É tirar algo do objeto da programação e representar ele de outra forma em um destino desejado.

O processo de deserialização é o inverso da serialização. Nesse processo pegamos em outros formatos e origens e fazemos o processo de deserialização para transformar essas informações em um objeto. Podemos pegar os dados de uma pessoa em um arquivo e vamos deserializar para que ele vire um objeto no nosso programa, por exemplo.

### Formato JSON
JSON é um acrônimo para JavaScript Notation Object é um formato de texto que segue a sintaxe do Javascript, muito usado para transmitir dados entre aplicações. 

Esse formato é muito utilizado para transmitir dados, como comunicação de APIs, representar dados entre objetos e etc. Toda linguagem que sabe ler e gravar um JSON pode se comunicar com outras linguagens que também possuem essa capacidade, basta utilizar o JSON para isso

![Ilustração do JSON entre linguagens](/imagens/json%20entre%20linguagens.png)

O JSON padroniza a escrita de um objeto em um formato de texto. Isso permite que diferentes tecnologias possam ler e trabalhar com uma mesma estrutura de arquivos, isso possibilida uma comunicação entre tecnologias diferentes ou também entre a mesma tecnologia, por exemplo 2 programas em C# podem se comunicar via JSON. 

## Serialização na prática
Imagine que você está trabalhando em um projeto e você precisa fazer uma integração para enviar os dados para um cliente, os dados serão dados de vendas.

No primeiro passo criaremos uma classe com o nome **Vendas** na pasta **Models** que está na raiz do nosso projeto. Segue abaixo a estrutura básica da classe Vendas:
```
using System;
using System.Collections.Generic;
using System.Linq;
using System.Threading.Tasks;

namespace projeto1.Models
{
    public class Vendas
    {
        
    }
}
```

Vamos criar agora as propriedades. Criaremos uma propriedade com o nome de **Id** que será do tipo inteiro, criaremos uma outra propriedade com o nome de **Produto** que será do tipo string e por último teremos uma propriedade com o nome de **Preco** do tipo decimal. Além disso, criaremos um construtor para facilitar na hora de instânciar a classe. Segue abaixo a nossa classe com as propriedades criadas:
```
using System;
using System.Collections.Generic;
using System.Linq;
using System.Threading.Tasks;

namespace projeto1.Models
{
    public class Vendas
    {
        public Vendas(int id, string produto, decimal preco)
        {
            Id = id;
            Produto = produto;
            Preco = preco;
        }
        public int Id { get; set; }
        public string Produto { get; set; }
        public decimal Preco { get; set; }
    }
}
```

Agora vamos instânciar um objeto da classe **Venda** no arquivo principal do nosso projeto, no arquivo **Program.cs**:
```
using projeto1.Models;

Vendas v1 = new Vendas(1, "Torneira", 3.87M);
```
Imagina que precisamos enviar a informação dessa venda para um cliente no formato JSON, porém, atualmente informações da venda estão em um objeto no C#. Para transformar esse objeto em um JSON precisaremos realizar o processo de serialização.

Para fazer essa transformação utilizaremos o pacote `Newtonsoft.Json` que instalamos anteriormente. 

### Utilizando o pacote Newtonsoft.Json
Para utilizar esse pacote no nosso projeto, precisaremos chamar ele no nosso arquivo principal **Program.cs**. Para isso utilizaremos o comando `using Newtonsoft.Json`. Esse comando é similar ao comando utilizado para quando utilizamos as classes que estão no models.

Agora vamos serializar, para serializar utilizaremos o método `SerializeObject()` da classe `JsonConvert`. Conforme consta no código abaixo:
```
using Newtonsoft.Json;
using projeto1.Models;

Vendas v1 = new Vendas(1, "Torneira", 3.87M);

string serializado = JsonConvert.SerializeObject(v1);
```
Primeiro criaremos uma variável do tipo string que vai receber o resultado da serialização, essa váriável foi criada com o nome de `serializado`. Utilizamos o método `SerializeObject(objeto_a_ser_serializado)` e passamos como parâmetro o objeto que desejamos serializar. 

Agora vamos imprimir a string `serializado` para que possamos ver o objeto que istânciando serializado. Segue abaixo o trecho de código com a saída do programa:
```
using Newtonsoft.Json;
using projeto1.Models;

Vendas v1 = new Vendas(1, "Torneira", 3.87M);

string serializado = JsonConvert.SerializeObject(v1);

Console.WriteLine(serializado);

Output:
{"Id":1,"Produto":"Torneira","Preco":3.87}
```

A nossa string no formato Json foi exibida em apenas uma linha, porém, podemos passar como parâmtro junto com o objeto a ser serializado o comando `Formatting.Indented` para que ele siga a identação padrão do json. Segue abaixo essa alternativa com o output:

```
using Newtonsoft.Json;
using projeto1.Models;

Vendas v1 = new Vendas(1, "Torneira", 3.87M);

string serializado = JsonConvert.SerializeObject(v1, Formatting.Indented);

Console.WriteLine(serializado);

Output:
{
  "Id": 1,
  "Produto": "Torneira",
  "Preco": 3.87
}
```

Com a serialização o `v1` deixou de ser um objeto e foi transformado em um Json que qualquer outra linguagem consegue interpretar. 

## Escrevendo um arquivo JSON
O nosso código já está conseguindo transformar o nosso objeto em uma string no formato JSON e retorna uma string com esse objeto serializado. Agora vamos escrever um arquivo Json contendo as informações serializadas.

Para escrever esse arquivo utilizaremos o método `WriteAllText()` da classe `File`. Conforme consta no script abaixo:
```
using Newtonsoft.Json;
using projeto1.Models;

Vendas v1 = new Vendas(1, "Torneira", 3.87M);

string serializado = JsonConvert.SerializeObject(v1, Formatting.Indented);

File.WriteAllText("Arquivos/result.json", serializado);
```

O método `WriteAllText()` recebe como primeiro parâmetro o local do arquivo, nesse parâmetro deve ser inserido o local em que esse arquivo deve ser inserido e o nome do arquivo com o seu formato. O segundo parâmetro é a string que você deseja que seja escrita nesse arquivo.

```
//Arquivo result.json
{
  "Id": 1,
  "Produto": "Torneira",
  "Preco": 3.87
}
```
Após executar esse código um arquivo com o nome `result.json` será criado dentro da pasta `Arquivos` que está na raiz do nosso projeto. Ao abrir esse arquivo conseguiremos ver o Json com o objeto `v1` que foi serializado na terceira linha do código acima.

## Serializando uma coleção
Nos exemplos anteriores nós serializamos apenas um objeto, no nosso contexto nós serializamos apenas uma venda. Nesta etapa iremos serializar uma lista de objetos. 

O primeiro passo vai ser criar mais vendas. Vamos criar a venda `v2` instânciando a classe `Venda` que criamos anteriormente. Segue abaixo esse trecho de código:
```
using Newtonsoft.Json;
using projeto1.Models;

Vendas v1 = new Vendas(1, "Torneira", 3.87M);
Vendas v2 = new Vendas (2,"Saco de areia", 53.90M);
```

Agora criaremos uma lista do tipo vendas para agrupar todas os objetos de vendas, após a criação da lista vamos inserir as duas vendas através do método `Add()` da classe `List`. Segue abaixo o trecho de código com a criação da lista:
```
using Newtonsoft.Json;
using projeto1.Models;

Vendas v1 = new Vendas(1, "Torneira", 3.87M);
Vendas v2 = new Vendas(2, "Saco de areia", 53.90M);

List<Vendas> vendasRealizadas = new List<Vendas>();
vendasRealizadas.Add(v1);
vendasRealizadas.Add(v2);
```

Após isso vamos serializar a nossa `listaVendas` passando ela como parâmetro para o método `SerializeObject`. Após isso vamos utilizar o método `WriteAllText()` para escrever no arquivo. Conforme o trecho abaixo:
```
using Newtonsoft.Json;
using projeto1.Models;

Vendas v1 = new Vendas(1, "Torneira", 3.87M);
Vendas v2 = new Vendas(2, "Saco de areia", 53.90M);

List<Vendas> listaVendas = new List<Vendas>();
listaVendas.Add(v1);
listaVendas.Add(v2);

string serializado = JsonConvert.SerializeObject(listaVendas, Formatting.Indented);

File.WriteAllText("Arquivos/result.json", serializado);
```
Segue abaixo agora o texto que foi inserido no arquivo `result.json`:
```
[
  {
    "Id": 1,
    "Produto": "Torneira",
    "Preco": 3.87
  },
  {
    "Id": 2,
    "Produto": "Saco de areia",
    "Preco": 53.90
  }
]
```

## Deserializando um objeto
Agora vamos entender como podemos deserializar um objeto. Imagine um cenário onde você vai receber um arquivo JSON e você precisa importar esse arquivo JSON em um objeto no seu sistema. 

Caso você tenha ainda a classe `Vendas` criada no seu projeto, delete ela para que possamos mapear e exemplificar desde o inicio. 

Utilizaremos o arquivo `result.json` para que possamos importar ele no nosso sistema através da deserialização. Agora pegaremos os dados que estão no arquivo em questão e vamos transformar ele em um objeto.

O primeiro passo é estudar o conteúdo do arquivo JSON para que possamos visualizar as propriedades, tipos de dados de cada uma das propriedades. A partir dessa leitura do JSON, criaremos uma classe contendo as propriedades e os tipos de dados que cada uma vai ter.

Segue abaixo o conteúdo do arquivo `result.json`:
```
[
  {
    "Id": 1,
    "Produto": "Torneira",
    "Preco": 3.87
  },
  {
    "Id": 2,
    "Produto": "Saco de areia",
    "Preco": 53.90
  }
]
```
Com base no JSON sabemos que a nossa classe precisará ter três atributos, sendo o primeiro o **Id** com o tipo inteiro, o segundo será uma string com o nome **Produto** e o terceiro será o **Preco** do tipo decimal.

Com base nas informações acima criaremos a nossa classe. A nossa classe será criada dentro da pasta **Models** e terá o nome de Vendas:
```
using System;
using System.Collections.Generic;
using System.Linq;
using System.Threading.Tasks;

namespace projeto1.Models
{
    public class Venda
    {
        public int Id { get; set; }
        public string Produto { get; set; }
        public decimal Preco { get; set; }
    }
}
```
Agora o arquivo JSON está representado na nossa classe `Vendas` e as propriedades foram criadas seguindo a mesma estrutura do JSON que iremos deserializar mais a frente. 

A partir de agora iremos retornar para o arquivo principal do nosso projeto que possui o nome de **Program.cs** e vamos iniciar realizando a leitura do arquivo `result.json` que está inserido na pasta `Arquivos` na raiz do nosso projeto . Segue abaixo o trecho de código que deve ser inserido no arquivo principal:
```
using Newtonsoft.Json;
using projeto1.Models;

string conteudoArquivo = File.ReadAllText("Arquivos/result.json");
```
O resultado da leitura do arquivo foi armazenado na string `conteudoArquivo`.

Como no nosso arquivo JSON temos uma coleção, também precisaremos representar eles uma coleção do tipo `Vendas`, que é a nossa classe que está representando os dados JSON. Para isso, criaremos uma lista do tipo Vendas e utilizaremos o método `DeserializeObject` da classe `JsonConvert` para inserir os dados da string recebida a partir da leitura para uma lista do tipo `Vendas`. Segue o código abaixo com a execução desse processo:
```
using Newtonsoft.Json;
using projeto1.Models;

string conteudoArquivo = File.ReadAllText("Arquivos/result.json");

List<Venda> listaVenda = JsonConvert.DeserializeObject<List<Venda>>(conteudoArquivo);
```

A partir de agora criaremos um laço foreach para percorrer a lista `listaVenda` para poder visualizar os novos objetos do tipo `Venda` que estão agrupados na `listaVenda`:
```
using Newtonsoft.Json;
using projeto1.Models;

string conteudoArquivo = File.ReadAllText("Arquivos/result.json");

List<Venda> listaVenda = JsonConvert.DeserializeObject<List<Venda>>(conteudoArquivo);

foreach (Venda venda in listaVenda)
{
    Console.WriteLine($"Id: {venda.Id}, Produto: {venda.Produto} e Preço: {venda.Preco}");
}

Output:
Id: 1, Produto: Torneira e Preço: 3,87
Id: 2, Produto: Saco de areia e Preço: 53,90
```

Dessa forma conseguimos realizar a deserialização de um arquivo JSON e representar os seus dados através de objetos da classe `Venda`.

## Atributos
Ao deserializar, o Newtonsoft.Json vai comparar o valor do item do arquivo JSON com o valor da propriedade na classe. Se na classe a propridade estiver com o nome "Produto" e no JSON estiver com o nome "Nome_Produto", ele não conseguirá realizar essa deserialização. 

Para resolver esse problema, trabalharemos com os atributos. Para isso, vamos até a classe `Venda` e vamos utilizar o Newtonsoft.Json diretamente na classe com o comando `using Newtonsoft.Json`. Segue abaixo o trecho de códig mostrando como realizamos essa criação de atributo:
```
using System;
using System.Collections.Generic;
using System.Linq;
using System.Threading.Tasks;
using Newtonsoft.Json;

namespace projeto1.Models
{
    public class Venda
    {
        public int Id { get; set; }

        [JsonProperty("Nome_Produto")]
        public string Produto { get; set; }
        
        public decimal Preco { get; set; }
    }
}
```

O comando `JsonProperty` deve estar exatamente acima da propriedade que vai receber essa informação com uma estrutura de nome diferente. 