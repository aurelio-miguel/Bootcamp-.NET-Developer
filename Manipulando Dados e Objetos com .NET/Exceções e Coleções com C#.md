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
