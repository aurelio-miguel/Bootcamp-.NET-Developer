# Exceções
Os recursos de manipulação de exceção da linguagem C# ajudam você a lidar com quaisuqer situações excepcionais ou inesperadas que ocorram quando um programa for executado.

Existem algumas situações inesperadas que podem não estar sob controle do programa ou não estarem previstas para ocorrer, as excessões vão nos auxiliar nesses momentos

## Lendo um arquivo e trabalhando com exceções
Para que possamos entender mais sobre as exceções, vamos utilizar o arquivo **Program.cs** do nosso projeto para realizar a leitura de um arquivo, dessa forma poderemos trabalhar com o disparo e tratamento de exceções.

O primeiro passo vai ser realizar a criação de uma nova pasta na raiz do seu projeto, criarei uma pasta com o nome **Arquivos**. Dentro dessa pasta eu realizarei a criação de um novo arquivo .txt com o nome **arquivoLeitura**. Nesse arquivo escreveremos algumas linhas com textos aleatórios.

Para realizar a leitura do arquivo, basta inserir o trecho de código no arquivo principal do projeto, no arquivo **Program.cs**:
```
string[] linhas = File.ReadAllLines("Arquivos/arquivoLeitura.txt");

string[] linhas = File.ReadAllLines("Arquivos/arquivoLeitura.txt");

foreach (string linha in linhas)
{
    Console.WriteLine(linha);
}

Output:
Linha 1 do arquivo de leitura
Linha 2 do arquivo de leitura - textos aleatórios
```
Quando realizamos a leitura de um arquivo, cada uma das linhas do aquivo pode ser retornada em uma string. Por conta disso, criamos uma lista do tipo string para armazenar todas as linhas na lista. Para realizar a leitura utilizamos o método `ReadAllLines(caminho_do_arquivo)` da classe `File`. Como parâmetro desse método deve ser inserido o caminho para o arquivo.

Após a leitura dos arquivos cada uma das linhas foi armazenada como uma string no array `linhas`. Para percorrer esse array foi utilizado o `foreach()` e utilizamos o método `WriteLine()` da classe `Console` para exibir cada uma das strings da lista.

### Disparando uma exceção
Anteriormente realizamos a leitura de um arquivo existente. Agora vamos começar a simular alguns erros possíveis para que possamos tratar as exceções.

- Caminho errado do arquivo:
Ao passar um caminho errado do arquivo .txt e executar o nosso projeto através do `dotnet run`, o programa retornará um erro bem extenso e de difícil leitura no console. Dentre todas as mensagens que serão exibidas, a primeira mensagem será similar a mensagem abaixo:
```
Unhandled exception. System.IO.FileNotFoundException: Could not find file 'caminho errado do arquivo'
```
Esse mensagem descreve que ocorreu uma exceção onde o arquivo não pode ser encontrado no caminho indicado. As exceções ocorrem quando o programa não pode mais executar as suas funções por conta de algum inesperado

### Tratando uma exceção
Em algumas situações, podemos criar gatilhos para prever possíveis erros. Em casos similares ao indicado acima, podemos utilizar o **Try Catch** para "prever" esses erros, evitar a ocorrência, continuar o fluxo ou até mesmo realizar algum tratamento.

No script abaixo iremos englobar a etapa do nosso código que pode gerar a exceção com o `try{ }`:
```
try
{
    string[] linhas = File.ReadAllLines("Arquivos/arquivo_Leitura.txt");

    foreach (string linha in linhas)
    {
        Console.WriteLine(linha);
    }
}

```

Após o escopo do `try`, iremos inserir o `catch()` com o parâmetro do tipo`Exception`, conforme consta no código abaixo:
```
try
{
    string[] linhas = File.ReadAllLines("Arquivos/arquivo_Leitura.txt");

    foreach (string linha in linhas)
    {
        Console.WriteLine(linha);
    }
}
catch (Exception ex)
{

}
```
Agora ao executar o programa ele vai realizar a tentativa de leitura através do `try`, caso ocorra uma exceção será executado o `catch`. Para exemplificar, vamos inserir uma mensagem no console, caso ocorra o programa entre no `catch`:

```

try
{
    string[] linhas = File.ReadAllLines("Arquivos/arquivo_Leitura.txt");

    foreach (string linha in linhas)
    {
        Console.WriteLine(linha);
    }
}
catch (Exception ex)
{
    Console.WriteLine($"Ocorreu uma genérica: {ex.Message}");
}

Output:
Ocorreu uma genérica: System.IO.FileNotFoundException: Could not find file 'caminho_do_arquivo'...
```
A variável `ex` do tipo Exception vai armazenar qual foi a exceção que ocorreu. Dessa forma através do catch podemos exibir o erro e prosseguir com o programa, caso seja possível. Através da variável do tipo Exception podemos pegar o `.Message` que vai retornar uma mensagem que descreve a exceção ocorrida, isso possibilita ter acesso a uma mensagem de exceção mais simplificada. 

Sem o Try e Catch assim que ocorrer o erro na leitura do arquivo o programa será finalizado e não conseguirá executar qualquer outro script. Com o Try e Cath podemos prever esses erros e prosseguir com a execução do programa, se fizer sentido para o programa.

## Exceção genérica e exceção específica
No exemplo anterior utilizamos um parâmetro do tipo Exception no catch para tratarmos de uma exceção genérica, uma exceção em que não sabemos qual é o seu tipo especificamente. Porém, existem casos em que podemos tratar uma exceção baseado no que ocorreu. 

O método ReadAllLines() da classe File possui diversos tipos de exceções que podem ocorrer ao utilizar esse método, segue abaixo uma lista das exceções que o método ReadAllLines pode retornar, essas exceções são as exceções específicas e elas retornam propriedades específicas do erro que ocorreu:
- ArgumentException
- ArgumentNullException
- PathTooLongException
- DirectoryNotFoundException
- IOException
- UnauthorizedAccessException
- FileNotFoundException
- NotSupportedException
- System.Security.SecurityException

Nós podemos ter vários blocos `cath` para que podermos tratar diferentes exceções. Segue abaixo alguns exemplos dessa ideia com base no exemplo de leitura de arquivo tratado anteriormente:
```
try
{
    ...
}
catch (FileNotFoundException ex)
{
    Console.WriteLine($"Ocorreu um erro na leitura do arquivo. Arquivo não encontrado. {ex.Message}");
}
catch (DirectoryNotFoundException ex)
{
    Console.WriteLine($"Ocorreu um erro na leitura do arquivo. Caminho da pasta não encontrado. {ex.Message}");
}
catch (Exception ex)
{
    Console.WriteLine($"Ocorreu uma exceção genérica. {ex.Message}");
}
```
No **Catch** poderemos passar variáveis como parâmetro com o tipo de cada uma das exceções, dessa forma apenas o catch da exceção em específica será executado e dessa forma poderemos ter um tratamento mais adequado ou uma resposta mais específica e exata. Dessa forma podemos específicar as exceções que podem ocorrer e tratar da melhor forma possível. 

No exemplo acima tentamos acessar um arquivo com um nome inexistente, por conta disso vai ocorrer uma exceção do tipo `FileNotFoundException`. O retorno no console será o retorno que está dentro do escopo do `cath(FileNotFoundException ex){ ... }`. No exemplo acima o retorno foi:
```
Ocorreu um erro na leitura do arquivo. Arquivo não encontrado. Could not find file 'caminho_do_arquivo'...
```

Tudo que está dentro do escopo de um `catch` é considerado um tratamento.

## Entendendo o bloco finally
O bloco Finally também será utilizado em conjunto com o Try e Catch. O finally deverá ser inserido após o catch e o objetivo dele é executar um bloco de comandos sempre que ocorrer o final de execução das exceções. Esse bloco será executado independente se ocorreu uma exceção ou não.

Segue abaixo um exemplo do finally:
```
try
{
    ...
}
catch(Exception ex)
{

}
finally
{
    Console.WriteLine("Finally executado após a tentativa de leitura do arquivo");
}
```
Independente se ocorreu uma exceção ou não, os comandos do escopo do finally serão executados. O Finally é importante pois em algumas situações podemos querer executar algum comando após finalizar o try e o cath, independente do resultado. Por exemplo ao fazer uma consulta em um banco de dados, ao iniciar a consulta é realizado a abertura de conexão e essa conexão deve ser fechada, podemos fechar essa conexão através do finally.

## Usando o Throw
O throw no C# permite que criemos uma exceção e utilizando ele podemos exibir um erro. Essa funcionalidade é muito utilizada para os momentos em que dependendo da situação queremos criar uma exceção para interromper ou tratar um erro. 

Para que possamos exemplificar a utilização do throw, criaremos uma nova classe dentro da pasta Models com o nome de ExemploExcecao.

```
public class ExemploExcecao
{

    public void Metodo1()
    {
        Metodo2();
    }

    public void Metodo2()
    {
        Metodo3();
    }

    public void Metodo3()
    {
        Metodo4();
    }

    public void Metodo4()
    {
        throw new Exception("Ocorreu uma exceção");
    }
}
```
Na classe ExemploExcecao realizamos a criação de 4 métodos, fizemos um sistema de cascata onde cada um dos métodos executa o próximo método e no quarto método inserimos uma exceção utilizando o throw. A estrutura básica do throw é `throw new Exception("Mensagem de erro que será exibida no console");`.

Para visualizar o exemplo acima, vamos instânciar a classe ExemploExcecao no nosso arquivo **Program.cs**:
```
using projeto1.Models;


new ExemploExcecao().Metodo1();

Output:
Unhandled exception. System.Exception: Ocorreu uma exceção...
at projeto1.Models.ExemploExcecao.Metodo4()...
at projeto1.Models.ExemploExcecao.Metodo3()
at projeto1.Models.ExemploExcecao.Metodo2()
at projeto1.Models.ExemploExcecao.Metodo1()
```

Ao chamar o método `Metodo1()` foi executado as outras funções em cascata até chegar no método `Metodo4()` que foi onde criamos a nossa exceção. A leitura da exceção que está no output é feita de baixo para cima. Com a estrutura que criamos podemos identificar que ele executou cara um dos métodos em cascata que criamos e após o 4 que a exceção ocorreu. 

Aliado a isso, também podemos tratar a exceção com o try e catch normalmente.

## Introdução a Filas/Queue
Anteriormente vimos estruturas de coleções como arrays e listas. Agora vamos falar um pouco mais sobre as filas. Uma coleção do tipo fila só pode ter elementos do mesmo tipo e obdece algumas regras, o primeiro elemento a entrar na fila será o primeiro a sair, o último elemento inserido vai para a última posição e sempre segue a sequência de avanço de posições, da mesma forma que uma fila na vida real.

A fila é muito utilizada quando temos uma estrutura em que ela precisa processar elementos em ordem, a fila vai nos auxiliar nesses casos. 

### Adição e remoção de um elemento da fila
Na imagem abaixo você poderá visualizar uma fila de inteiros onde o primeiro elemento foi o 61 e em sequência os outros elementos também foram inseridos seguindo a mesma sequência se inserção. A saída exemplifica que a saída dos elementos é com base na ordem de entrada na fila

![Imagem de uma fila](/imagens/fila.png)

Essa dinãmica onde o primeiro que entrar na fila será o primeiro a sair é conhecida também como FIFO. First In, First Out.

### Fila na prática
Agora iremos implementar uma fila no C# para que possamos explorar mais esse tipo de estrutura.

Para criar a fila utilizaremos a classe `Queue`, segue abaixo a estrutura básica:
```
//Exemplo de estrutura
Queue<tipo_de_dados> nome = new Queue<tipo_de_dados>();
//Exemplo prático
Queue<int> fila = new Queue<int>();
```

- **Inserindo elementos na fila:**
Para inserir elementos na fila utilizaremos o método `.Enqueue(valor)` do nosso novo elemento de fila criado
```
fila.Enqueue(3);
```
Como parâmetro desse método iremos inserir o elemento que queremos colocar na fila, nesse caso foi o número inteiro 3.

- **Percorrendo a fila:**
Para percorrer a fila podemos utilizar os mesmos elementos de laço de repetição que utilizamos para as listas e arrays. Segue abaixo um exemplo 
```
Queue<int> fila = new Queue<int>();
fila.Enqueue(3);
fila.Enqueue(7);
fila.Enqueue(9);
fila.Enqueue(1);

foreach(int item in fila)
{
    Console.WriteLine(item);
}

Output:
3
7
9
1
```
Perceba que o primeiro elemento que foi inserido na fila foi o primeiro elemento que foi exibido no console após o laço de repetição para percorrer a fila.

- **Removendo um elemento da fila:**
Para remover um elemento da fila, podemos utilizar o método `.Dequeue()`, com esse método não iremos passar o valor que queremos remover como parâmetro e também não passaremos a posição na fila. Isso ocorre pois a fila possui as suas próprias regras, conforme foi citado anteriormente. Ao executar esse método, as regras serão seguidas e os elementos serão removidos por orden de inserção, conforme consta no exemplo de código abaixo
```
Queue<int> fila = new Queue<int>();
fila.Enqueue(3);
fila.Enqueue(7);
fila.Enqueue(9);
fila.Enqueue(1);

Console.WriteLine("Itens inseridos:");
foreach (int item in fila)
{
    Console.WriteLine(item);
}

fila.Dequeue();
Console.WriteLine("Lista após remover 1 item");
foreach (int item in fila)
{
    Console.WriteLine(item);
}

Output:
Itens inseridos:
3
7
9
1
Lista após remover 1 item
7
9
1
```
Cada vez que o método `.Dequeue` é utilizado, um elemento da fila é removido por vez e sempre seguindo a sequência FIFO.

## Introdução a Pilhas/Stack
As pilhas também são coleções de elementos do mesmo tipo, assim como os arrays, listas e filas. A pilha também obedece algumas regras de inserção e remoção de elementos. Nessa coleção de dados é seguem a estrutura do LIFO(Last In, Firs Out), nessa estrutura o último elemento a ser inserido será o primeiro elemento a ser removido, é basicamente o contrário de uma fila.

O processo de inserção e remoção de elementos funciona de forma similar a vida real. Em uma pilha o primeiro elemento a ser removido é sempre o última a ser inserido na pilha

![Imagem para exemplificar uma pilha](/imagens/pilha_exempl.png)

### Implementando a pilha
Agora iremos implementar uma pilha, para isso utilizaremos a classe `Stack`, conforme o código abaixo:
```
Stack<tipo_de_dados> nome = new Stack<tipo_de_dados>();
```
No código acima declaramos uma nova variável do tipo pilha utilizando a classe `Stack` e passando o tipo de dados que a nossa pilha vai conter.

- Criando a pilha e inserindo elementos:
```
Stack<int> pilha = new Stack<int>();

pilha.Push(2);
```
No código acima foi criada a pilha através da classe Stack e após isso foi inserido um elemento no tipo da pilha utilizando o método `Push(elemento_inserido);`.

- Percorrendo a pilha:
```
Stack<int> pilha = new Stack<int>();

pilha.Push(2);
pilha.Push(9);
pilha.Push(4);
pilha.Push(10);
pilha.Push(1);

foreach (int item in pilha)
{
    Console.WriteLine(item);
}

Output:
1
10
4
9
2
```
Para percorrer a pilha foi utilizado o foreach e exibimos no console cada um dos elementos separadamente. Perceba que ele exibiu os dados conforme uma pilha, o primeiro item inserido está na parte inferior do output e o última item inserido está na parte superior do output.

- Removendo um objeto da pilha:
Um objeto pode ser removido da nossa pilha utilizando o método `.Pop()`, pela fato da estrutura da pilha ser LIFO, sempre será removido a partir do último elemento que foi inserido, que será o do topo da pilha.
```
Stack<int> pilha = new Stack<int>();

pilha.Push(2);
pilha.Push(9);
pilha.Push(4);
pilha.Push(10);
pilha.Push(1);

Console.WriteLine("Pilha cadastrada:");
foreach (int item in pilha)
{
    Console.WriteLine(item);
}

pilha.Pop();
Console.WriteLine("1 item foi removido:");
foreach (int item in pilha)
{
    Console.WriteLine(item);
}

Output:
Pilha cadastrada:
1
10
4
9
2
1 item foi removido:
10
4
9
2
```
O `.Pop()` não recebe parâmetros pois na pilha não é possível determinar a remoção de um item em específico, sempre é removido do topo. Se quiser remover mais itens vai ser preciso utilizar o `.Pop` novamente. No output do código acima foi possível visualizar que o item que foi removido foi o último que foi inserido. o trecho `pilha.Pop()` também remove o elemento e também retorna o elemento que foi removido, dessa forma podemos armazenar essa informação para exibir ao usuário ou algo do tipo. 

## Dictionary
Um dictionary é uma coleção de cave-valor para armezenar valores únicos sem uma ordem específica. 

No trecho abaixo você conseguirá visualizar como um dictionary é declarado:
```
Dictionary<string, string> estados = new Dictionary<string, string>();
```
No dictionary é necessário inserir dois tipos para a nossa coleção.O primeiro tipo é o tipo da chave e o segundo tipo é o tipo do valor.

Nessa estrutura a chave sempre deve ser única, se a chave se repetir o programa será encerrado com uma exceção.

- Inserindo um elemento:
```
Dictionary<string, string> estados = new Dictionary<string, string>();

estados.Add("TO", "Palmas");
estados.Add("RJ", "Rio de Janeiro");
estados.Add("SP", "São Paulo");
```
Para inserir um novo elemento na coleção foi utilizado o método `.Add(chave, valor)`. Por parâmetro foi passado dois elementos, o primeiro elemento é a chave e o segundo elemento será o valor. No exemplo acima a cigla do estado foi utilizada como chave e o nome do estado foi utilizado como valor. A chave e o valor estão como strings pois foi esse o tipo de valor que escolhemos ao criar o dictionary.

- Percorrendo o dictionary:
Aqui temos uma estrutura um pouco diferente, o tipo de elemento que vai representar a nova chave será o `KeyValuePair<tipo_chave, tipo_valor>`, conforme consta no exemplo abaixo:
```
Dictionary<string, string> estados = new Dictionary<string, string>();

estados.Add("TO", "Palmas");
estados.Add("RJ", "Rio de Janeiro");
estados.Add("SP", "São Paulo");

foreach (KeyValuePair<string, string> item in estados)
{
    Console.WriteLine(item.Key);
}


Output:
TO
RJ
SP
```
Perceba que no método `WriteLine()` foi passado como parâmetro o elemento que estava sendo percorrido no foreach `.Key`, esse `.Key` é para que ele capture apenas a chave do determinado elemento do dictionary.

Esse `.Key` poderia ser alterado para `.Value` caso tivessemos interesse em passar apenas os valores. Ele poderia também ser removido deixando apenas o item, dessa foram seria exibido tanto a chave quando o valor também.

Segue abaixo um exemplo com a exibição separadamente dessas informações no foreach e o seu output:
```
...
foreach(KeyValuePair<string, string> item in estados)
{
    Console.WriteLine($"Chave: {item.Key}, Valor: {item.Value}");
}

Output:
Chave: TO, Valor: Palmas
Chave: RJ, Valor: Rio de Janeiro
Chave: SP, Valor: São Paulo
```

### Removendo e alterando elementos

- Removendo elementos do Dictionary
Para remover um elemento utilizaremos a função `.Remove(chave_do_elemento)`, conforme o exemplo abaixo:
```
Dictionary<string, string> estados = new Dictionary<string, string>();

estados.Add("TO", "Palmas");
estados.Add("RJ", "Rio de Janeiro");
estados.Add("SP", "São Paulo");

Console.WriteLine("Itens inseridos no Dictionary:");
foreach (KeyValuePair<string, string> item in estados)
{
    Console.WriteLine($"Chave: {item.Key}, Valor: {item.Value}");
}

estados.Remove("SP");
Console.WriteLine("Dictionary Após a remoção do item:");
foreach (KeyValuePair<string, string> item in estados)
{
    Console.WriteLine($"Chave: {item.Key}, Valor: {item.Value}");
}

Output:
Itens inseridos no Dictionary:
Chave: TO, Valor: Palmas
Chave: RJ, Valor: Rio de Janeiro
Chave: SP, Valor: São Paulo

Dictionary Após a remoção do item:
Chave: TO, Valor: Palmas
Chave: RJ, Valor: Rio de Janeiro
```
Perceba que no Output é possível visualizar que o item que tinha a chave "SP" foi removido do Dictionary através do método `.Remove()`. Praticamente tudo que é feito no Dictionary, teremos como referência a chave do elemento.

- Alterando um valor:
Um ponto importante a se lembrar é que não é possível alterar uma chave, a chave só pode ser removida após a sua inserção. Para alterar um valor do Dictionary, basta seguir utilizar a estrutura `dictionary[chave] = "novo_valor";`:
```
Dictionary<string, string> estados = new Dictionary<string, string>();

estados.Add("TO", "Palmas");
estados.Add("RJ", "Rio de Janeiro");
estados.Add("SP", "São Paulo");

Console.WriteLine("Itens inseridos no Dictionary:");
foreach (KeyValuePair<string, string> item in estados)
{
    Console.WriteLine($"Chave: {item.Key}, Valor: {item.Value}");
}

estados["SP"] = "São Paulo - valor alterado";
Console.WriteLine("Dictionary após alterar o valor de um item:");
foreach (KeyValuePair<string, string> item in estados)
{
    Console.WriteLine($"Chave: {item.Key}, Valor: {item.Value}");
}

Output:
Itens inseridos no Dictionary:
Chave: TO, Valor: Palmas
Chave: RJ, Valor: Rio de Janeiro
Chave: SP, Valor: São Paulo

Dictionary após alterar o valor de um item:
Chave: TO, Valor: Palmas
Chave: RJ, Valor: Rio de Janeiro
Chave: SP, Valor: São Paulo - valor alterado
```

- Verificando se o Dictionary já possui uma chave inserida:

No Dictionary se tentarmos inserir dois elementos com a mesma chave vai ocorrer uma exceção e o programa será finalizado. Por conta disso, podemos implementar uma funcionalidade para realizar essa verificação. 

Utilizando o método `.ContainsKey(nova_chave)` receberemos um boleano com o verdadeiro se o Dictionary já tiver um elemento com essa nova chave ou receberemos um boleano com falso se ainda não existir no Dictionary. A partir disso podemos inserir essa verificação dentro de um if para inserir apenas se o retorno desse método for falso. Conforme consta no exemplo abaixo:
```
if (estados.ContainsKey("TO"))
{
    Console.WriteLine("O elemento não pode ser inserido pois a chave já está cadastrada");
}
else
{
    estados.Add("TO", "Tocantinstão");
}

```

- Obtendo o valor de uma chave em específico:
Para isso, podemos utilizar a estrutura `dictionary[chave];`. Esse comando permite que possamos exibir o valor a partir de uma chave, por exemplo:
```
Console.WriteLine($"O estado é {estados["TO"]}");

Output:
O estado é Tocantins
```