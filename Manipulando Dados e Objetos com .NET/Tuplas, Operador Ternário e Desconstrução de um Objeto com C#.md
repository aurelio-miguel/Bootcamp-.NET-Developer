# Introdução
Neste arquivo iremos aprender mais sobre as tuplas, operadores ternários e desconstrução de um objeto com o C#.

## Tuplas
Tuplas fornece siontaxe concica para agrupar vários elementos de dados em uma estrutura de dados leva. A tupla é similar ao conceito de coleção no sentido de agrupar dados, porém, nas tuplas podemos ter dentro de sí itens com tipos diferentes. 

### Implementando uma Tupla
Inicialmente vamos começar declarando uma tupla, para declarar uma dupla podemos utilizar uma sintaxe abreviada e inserir os diversos tipos de dados existentes nela:
```
(tipo_de_dado1, tipo_de_dado2, tipo_de_dado3...) nome = (dado1,dado2,dado3...)
```
A declaração da dupla é feita utilizando parênteses onde dentro dos parênteses vamos inserir o tipo de dado de cada um dos elementos da nossa tupla separado por vírgula. Após os parênteses vamos inserir o nome da tupla seguido pelo operador de igualdade, após esse operador vamos abrir os parênteses para inserir os valores de cada elemento da tupla. Lembrando que ao passar os dados é necessário respeitar a ordem da declaração dos tipos de dados que foi feito na inicialização.

Segue abaixo um trecho de código com a declaração de uma tupla:
```
(int, string, string) tupla = (1, "Aurélio", "Miguel");
```
Com uma úniva variável `tupla` foi possível representar 3 valores de diferentes tipos.

Além disso, podemos também nomear cada um dos objetos da para que possamos exibir ele de forma mais facilidade. Para nomerar os objetos, vamos seguir a estrutura abaixo:

```
(int Id, string Nome, string Sobrenome) tupla = (1, "Aurélio", "Miguel");
```
Após isso, podemos acessar os valores de cada elemento utilizando a estrutura `tupla.Nome`, por exemplo.

### Exibindo os valores
Para exibir os valores, iremos chamar a nossa variável tupla e podemos capturar cada um dos elementos separadamente com o `.ItemX`, o X é a posição desse item na tupla. 

Segue abaixo um exemplo para que seja possível entender melhor esse procedimento:
```
(int, string, string) tupla = (1, "Aurélio", "Miguel");


Console.WriteLine($"ID: {tupla.Item1}");
Console.WriteLine($"Nome: {tupla.Item2}");
Console.WriteLine($"Sobrenome: {tupla.Item3}");

Output:
ID: 1
Nome: Aurélio
Sobrenome: Miguel
```

### Outra sintaxe para as tuplas
Podemos  representar uma tupla com outro tipo de dados, nesse caso utilizaremos a própria struct da tuple. Conforme consta abaixo:
```
ValueTuple<int,string,string> tupla = (1,"Aurélio", "Miguel");
```
Dessa forma criamos uma variável do tipo ValueTuple, definimos o tipo de dados de cada um elemento e após o operador de igualdade foi inserido os dados desejados, tendo o mesmo tipo da declaração. 

### Tuplas em métodos
Nós podemos também retornar uma tupla através de um método de uma classe. Para isso iremos criar uma nova classe dentro da pasta models com o nome de **LeituraArquivo.cs".

A ideia dessa classe vai ser ter um método que vai receber por parâmetro o caminho de um arquivo, vai ler esse arquivo e depois vai retornar uma tupla com três informações, a primeira informação vai ser se foi possível realizar a leitura, a segunda informação vai ser os textos do arquivo lido e a terceira o número de linha.

Segue abaixo um trecho de código com mais detalhes da nova classe que criamos:
```
namespace projeto1.Models
{
    public class LeituraArquivo
    {

        public (bool Sucesso, string[] Linhas, int Quantidadelinhas) LerArquivo(string caminho)
        {
            
        }
    }
}
```
No exemplo acima criamos temos a classe **LeituraArquivo** e o método **LerArquivo**. Perceba que na assinatura do nosso método não temos mais o void ou um tipo específico de retorno. Como esse método vai retornar uma tupla, criamos a estrutura entre parênteses que contem os tres tipos de dados que serão retornados na tupla, além disso inserimos também o apelido para cada um desses valores. Dessa forma poderemos trabalhar com eles mais facilmente.

Segue abaixo  trecho de código para que você possa entender como vai funcionar também o retorno dessa função. tendo em vista que essa função vai retornar uma tupla:
```
...
public (bool Sucesso, string[], int) LerArquivo(string caminho)
{
    string[] linhas = File.ReadAllLines(caminho);

    return (true, linhas, linhas.Count());
}
```

Para retornar também utilizamos a mesma estrutura de parênteses com as informações em ordem, conforme foi feito na declaração dos tipos lá na assinatura desse método.

Segue abaixo o exemplo completo desse método com o try catch para caso ocorra alguma exceção na leitura do arquivo. 

```
namespace projeto1.Models
{
    public class LeituraArquivo
    {

        public (bool Sucesso, string[], int) LerArquivo(string caminho)
        {
            try
            {
                string[] linhas = File.ReadAllLines(caminho);
                return (true, linhas, linhas.Count());
            }
            catch (Exception ex)
            {
                return (false, new string[0], 0);
            }


        }
    }
}
```
No trecho acima temos uma dupla de retorno para caso a leitura do arquivo ocorra bem, caso não ocorra ele vai entrar no `catch` e vai retornar uma dupla contendo o false, uma string vazia e um inteiro com o valor zero que deveria armazenar a quantidade de linhas do arquivo que foi lido. 

### Trabalhando com a nova classe 
Agora iremos instânciar a classe criada anteriormente para que possamos acessar o método que vai ler os arquivos e retornar a tupla, iremos instânciar a classe criada no nosso arquivo principal **Program.cs**. 

O primeiro passo vai ser instânciar a nossa classe LeituraArquivo:
```
LeituraArquivo arquivo = new LeituraArquivo();
```

Agora conseguiremos acessar o método que criamos anteriormente. Pelo fato do método retornar uma tupla, precisaremos receber também como uma tupla, conforme consta abaixo:
```
var(sucesso, linhasArquivo, quantidadeLinhas) = arquivo.LerArquivo("/Arquivos/arquivoLeitura.txt");
```
No exemplo acima utilizamos a palavra `var` para que não fosse necessário passar o tipo das variáveis, utilizamos isso como um atalho. Nesse trecho o retorno da tupla vai ser armazenado na nova tupla que criamos após o var. Nós passamos como parâmetro para a função `LerArquivo()` o caminho para o arquivo "arquivoLeitura.txt" que está na pasta "Arquivos", na raiz do nosso projeto.

A partir dessas informações da tupla, poderemos prosseguir com o nosso programa.

No exemplo abaixo iremos instânciar o método e com base no sucesso da leitura que foi retornado no primeiro item da tupla, iremos realizar a leitura do arquivo e imprimir algumas informações. Lembrando que o primeiro item da tupla é um boleano que retorna true para os casos em que foi possível realizar a leitura do arquivo:
```
LeituraArquivo arquivo = new LeituraArquivo();

var (sucesso, linhasArquivo, quantidadeLinhas) = arquivo.LerArquivo("Arquivo/arquivoLeitura.txt");

if (sucesso)
{
    Console.WriteLine($"Quantidade de linhas do arquivo: {quantidadeLinhas}");
    foreach (string linha in linhasArquivo)
    {
        Console.WriteLine(linha);
    }
}
else
{
    Console.WriteLine("Não foi possível ler o arquivo.");
}

Output:

Quantidade de linhas do arquivo: 2
Linha 1 do arquivo de leitura
Linha 2 do arquivo de leitura - textos aleatórios
```

Caso ocorresse qualquer tipo de erro na leitura do arquivo, o item `sucesso` da tupla seria falso e seria executado o comando de imprimir no console que está inserido dentro do escopo do `else { ... }` no trecho de código acima. 

### Descartes de informações
Agora vamos entender como podemos fazer o descarte de informações de uma tupla. 

Imagine que temos uma tupla que retorna diversas informações, porém, precisamos de apenas duas dessas informações. Neste caso, podemos utilizar o conceito de descarte para que possamos receber apenas as informações.

No exemplo abaixo vamos simular que não utilizaremos o retorno com as informações que constam a quantidade de linhas. Para descartar, basta inserir o `_` na posição em que receberiamos aquele determinado retorno. Segue abaixo um trecho de código que exemplifica isso no nosso arquivo principal **Program.cs**:
```
var (sucesso, linhasArquivo, _) = arquivo.LerArquivo("Arquivos/arquivoLeitura.txt");
```
Com o `_` descartamos o item que receberiamos a quantidade de linhas. Podemos fazer isso para elementos da tupla que não iremos utilizar no escopo do nosso código.

## Desconstrutor
O desconstrutor é uma ação inversa do construtor. O construtor tem como finalidade construir um objeto e o desconstrutor tem como finalidade separar a construção que foi realizada.

De forma similar a tupla, com o desconstrutor poderemos separar por exemplo o nome e o sobrenome de uma pessoa. 

Para verificar a funcionalidade, vamos criar um método especial em uma classe chamada Pessoa. Segue abaixo mais detalhes o trecho de código com o desconstrutor:
```
public void Deconstruct(out string nome, out string sobrenome, out int idade)
{
    nome = Nome;
    sobrenome = Sobrenome;
    idade = Idade;
}
```
Na classe Pessoa temos duas informações, o nome e o sobrenome. O objetivo do desconstrutor vai ser separar essas duas informações. Nos parâmetros do desconstrutor precisaremos inserir a palavra `out` antes de cada um dos elementos que desejamos separar, após isso inserir os tipos e o nome dos elementos em questão. Esse `out` significa que é uma variável de saída

Dentro do escopo do desconstrutor a variável `nome` receberá a propriedade `Nome` e a variável `sobrenome` receberá a propriedade `Sobrenome`.

Perceba que o construtor recebe as duas variáveis e insere elas na propriedade. O descrutor faz o contrário, as duas variáveis vão receber os valores das propriedades.

### Utilizando o Desconstruct
Agora vamos instânciar uma nova classe pessoa no nosso **Program.cs** para que possamos utilizar o desconstrutor. Segue abaixo o trecho de código:
```
Pessoa p1 = new Pessoa("Aurélio", "Miguel", 26);
```
No código acima estamos chamando o construtor. Estamos passando por parâmetro o nome e o sobrenome.

Agora iremos chamar o desconstrutor, para isso utilizaremos o trecho de código abaixo:
```
(string nome, string sobrenome, int idade) = p1;

Console.WriteLine($"{nome} {sobrenome} Idade: {idade}");

Output:
AURÉLIO Miguel Idade: 22
```
Perceba que a estrutura é similar a  uma tupla, iniciamos com os parenteses e passamos o tipo e as variáveis que queremos retornar e após o operador de igualdade indicamos que ele é igual ao `p1`. A partir desse momento podemos acessar os dados utilizando as variáveis que passamos ao chamar o desconstrutor, conforme consta no método `WriteLine`. 

## IF Ternário
Agora conheceremos uma alternativa para o IF para que possamos utilizar uma sintaxe um pouco diferente para representar um caso de IF e ELSE, trazendo uma melhor legibilidade ao código.

A estrutura do IF Ternári funcina da seguinte forma:
```
variavel_booleana ? resultado_se_for_true : resultado_se_for_false;
```
Basicamente o primeiro item vai ser uma variável ou verificação boleana. Após isso temos uma interrogação que funciona como um if e após isso temos o que deve ser feito se for true. Após isso temos os dois pontos que funcionará como um else e em seguida temos o resultado se for um false.

Para que possamos exemplificar, escreveremos um programa que consegue identificar se um determinado número é par ou impar. Segue abaixo um exemplo com o IF Ternário para que possamos entender melhor a sua funcionalidade.
```
int numero = 20;
bool ehPar = false;

ehPar = numero % 2 == 0;
Console.WriteLine($"O número {numero} é " + (ehPar ? "par" : "impar"));

Output:
O número 20 é par
```
No código acima iniciamos iniciamos inserindo um valor inteiro na variável `numero`, após isso criamos uma variável boleana com o nome `ehPar` com o valor falso. Em seguida verificamos se o resto da divisão da variável número é igual a zero, se for igual a zer a variável `ehPar` vai receber o valor de true e se não for igual a zero a variável boleana vai receber falso.

No método `WriteLine`realizamos uma concatenação e através do IF Ternário exibimos a mensagem "par" se a variável `ehPar` for verdadeira e exibimos a mensagem "impar" se a variável `ehPar` for falsa. 