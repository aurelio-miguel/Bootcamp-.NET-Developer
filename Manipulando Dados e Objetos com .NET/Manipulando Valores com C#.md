# Manipulando Valores com C#
Nessa etapa veremos como podemos manipular valores no C#, aprenderemos a transformar dados de um tipo para uma outra representação mais amigável. Aprenderemos a representar o mesmo tipo de dados em uma outra representação

## Contatenação de strings
Podemos formatar valores em diversas representações. Essa formação de valores é conhecida como interpolação. Com a concatenação podemos unir strings, nós podemos unir dois textos por exemplo através da concatenação. Esse processo de união é conhecido como concatenação ou interpolação.

### Concatenando Strings
Para trazer uma maior clareza nos conceitos de concatenação, utilizaremos o nosso método **ListarAlunos()** da nossa classe Curso como um exemplo.

O nosso objetivo vai ser exibir os alunos por ordem numérica, para isso vamos contatenar a posição do aluno na lista com o nome completo dele. Segue abaixo o trecho de código onde realizamos essa concatenação:
```
public void ListarAlunos()
{
    for (int i = 0; i < Alunos.Count; i++)
    {
        string texto = "Nº " + i + " - " + Alunos[i].NomeCompleto;
        Console.WriteLine(texto);
    }
}
```
No trecho de código acima foi feito a concatenação entre Strings utilizando o **+** o texto foi unido através do operador de soma. Criamos uma variável do tipo string para armazenar o texto contendo aposição de um aluno na lista e o nome completo dele, as duas inforações foram concatenadas com o operador de soma. Após realizar a contatenação, realizamos a exibição da variável com o texto contatenado através do método WriteLine.



Segue abaixo o output quando executamos o método ListarAlunos da classe Curso:
```
Nº 0 - AURÉLIO Miguel
Nº 1 - LEONARDO Campos
```

## Interpolação de Strings
Existe também uma outra forma de unir strings que é através da interpolação. A interpolação consiste em unir as strings sem a necessidade do operador de soma. Para interpolar, basta iniciar a string com o cifrão e as aspas duplas que vai conter toda a string. Cada valor que iremos interpolar será inserido dentro de chaves.

Segue abaixo o mesmo exemplo do método listar alunos utilizando a interpolação:

```
public void ListarAlunos()
{
    for (int i = 0; i < Alunos.Count; i++)
    {
        tring texto = $"Nº {i} - {Alunos[i].NomeCompleto}";
        Console.WriteLine(texto);
    }
}
```
Com a interpolação podemos ter uma string um pouco mais fluída no sentido da leitura. Os elementos interpolados estão entre as { } dentro da string. A string sempre inicia com o cifrão para que o C# consiga identificar que nessa string vai ter uma interpolação.

## Fromatando valores monetários
Agora veremos como podemos formatar valores monetários para que possamos representar uma moeda e o seu valor. Podemos fazer isso de forma dinâmica através do C#.

Para tratar de valores monetários, utilizaremos o tipo decimal. Segue abaixo um trecho de código com um exemplo dessa utilização:
```
decimal valorMonetario = 82.40M;
Console.WriteLine(valorMonetario);

Output:
82,40
```
Ao declarar uma variável do tipo decimal, precisamos que o seu valor tenha a letra "M" no final. 

Para que possamos especificar qual é a moeda, podemos utilizar a interpolação de string para representar esse valor em uma determinada moeda, conforme abaixo:
```
decimal valorMonetario = 82.40M;
Console.WriteLine($"{valorMonetario:C}");

Output:
R$ 82,40
```
Nesse código utilizamos a interpolação de string e dentro das chaves, logo após a variável foi inserido o código `:C`. Os dois pontos significa que queremos realizar uma formatação na variável, a formatação em questão foi a `C` que significa currency. Por conta disso ele vai formatar com o R$ e inserir a vírgula de forma automática. 

O sistema identifica que é real pois no sistema operacional existe a localização e cultura do sistema que consegue identificar a formatação e configuração do sistema é do Brasil. O sistema vai pegar as configurações de moeda do sistema operacional em que o programa está rodando.

## Alterando a localização do código
Para alterar a configuração de nosso programa para formatos específicos de uma localização, podemos importar o namespace `System.Globalization` conforme consta abaixo:
```
using System.Globalization;
```

Segue abaixo o trecho de código com a importação do namespace e também o ajuste na cultura:
```
using System.Globalization;

CultureInfo.DefaultThreadCurrentCulture = new CultureInfo("en-US");

decimal valorMonetario = 82.40M;
Console.WriteLine($"{valorMonetario:C}");

Output:
$82.40
```
Ao instânciar o `CultureInfo()` é realizado a inserção do formato que queremos trabalhar. 

## Formatando o tipo DateTime
O tipo DateTime é utilizado para que possamos trabalhar com datas e horários. Esse tipo de dados permite diversas formatações diferentes.

O primeiro passo será realizar a declaração de uma variável do tipo DateTime, conforme o código abaixo:
```
DateTime data = DateTime.Now;
Console.WriteLine(data);

Output:
12/05/2024 18:11:56
```
O comando `.Now` significa que teremos a data e hora do computador em que o programa vai estar rodando, o programa sempre vai definir o horário com o padrão do próprio computador. 

- Removendo os segundos
```
DateTime data = DateTime.Now;
Console.WriteLine(data.ToString("dd/MM/yyyy HH:mm"));

Output:
12/05/2024 18:29
```

## Formatando data e hora
Através do DateTime também podemos representar apenas as datas e as horas.

- Representando apenas a data:
```
DateTime data = DateTime.Now;
Console.WriteLine(data.ToString("dd/MM/yyyy"));

Output:
12/05/2024
```
Uma outra alternativa seria utilizando o método `ToShortDateString()` na nossa variável do tipo data. Ele será utilizado da seguinte forma `data.ToShortDateString()`, dessa forma ele vai retornar apenas as datas.

- Representando a hora:
```
DateTime data = DateTime.Now;
Console.WriteLine(data.ToString("HH:mm"));
```
Uma outra alternativa para capturar apenas a hora seria utilizar o método `ToShortTimeString`, conforme o comando a seguir `data.ToShortDateString()`.

### Convertendo uma data
Nem sempre teremos a data no formado padrão do C#, dessa forma temos formas para poder realizar a conversão de uma string para o formato DateTime. Para isso podemos utilizar o `DateTime.Parse("17/04/2022 18:00")`, através do `.Parse()` poderemos inserir uma string que desejamos converter para o formato DateTime.

Segue abaixo como a nossa string inserida no Parse será convertida para o formato do C#:
```
DateTime data = DateTime.Parse("12/05/2024 18:00");
Console.WriteLine(data);

Output:
12/05/2024 18:00:00
```

## DateTime com o TryParseExact
Anteriormente trabalhamos com método Parse para realizar a conversão de uma string para o tipo DateTime, porém, se o Parse der um erro, ele vai gerar uma excessão e vai encerrar o programa. Dessa forma, precisamos fazer uma conversão de forma mais segura, caso ocorra alguma falha poderemos controlar isso para que o programa não seja encerrado. Para isso utilizaremos o método TryParseExact().

Segue abaixo um exemplo de como podemos utilizar o TryParse para realizar a conversão de uma string para o formato DateTime de forma mais segura:
```
using System.Globalization;

string dataString = "2022-13-17 18:00";

DateTime.TryParseExact(dataString,
    "yyyy-MM-dd HH:mm",
    CultureInfo.InvariantCulture,
    DateTimeStyles.None,
    out DateTime data);

Console.WriteLine(data);

Output:
01/01/0001 00:00:00
```
No primeiro parâmetro do TryParsefoi passado a string que queremos converter, no segundo parâmetro passaremos o formato que a string est, no terceiro parâmetro vamos escolher a cultura, o outro parâmetro será o estilo do dateTime e por último é inserido o parâmetro de saída. A variável criara após o `out` poderá ser utilizada para que possamos exibir posteriormente a sua conversão.

Conforme consta no Output, o programa rodou até o final sem excessões. Porém, ele não conseguiu converter corretamente pelo fato de na string constar o mês como 13. O TryParseExact tentou converter e não deu certo retornando o Output em questão. Se inserir um mês válido a conversão será realizada corretamente.

## Validando o retorno do TryParseExact
Podemos incrementar o TryParseExact com um **IF** para que possamos validar a conversão. Podemos inserir estruturar condicionais para que ele exiba uma mensagem se foi possível converter ou não a data. 

O TryParseExact retorna um boleano. Dessa forma podemos inserir essa boleano na condição. Se o TryParseExact conseguir converter ele retornará true, se ele não conseguir converter o retorno será false.

Segue abaixo o trecho de código completo onde podemos realizar essa verificação:
```
using System.Globalization;

string dataString = "2022-13-17 18:00";

bool conversao = DateTime.TryParseExact(dataString,
    "yyyy-MM-dd HH:mm",
    CultureInfo.InvariantCulture,
    DateTimeStyles.None,
    out DateTime data);

if (conversao)
{
    Console.WriteLine($"Conversão realizada. {data}");
}
else
{
    Console.WriteLine("Erro ao converte, data inválida");
}

Output:
Erro ao converter
```

Neste exemplo criamos a variável `conversao` do tipo boleano para armazenar o retorno do TryParseExact(). Após isso criamos um if para verificar se a variavel conversão tinha o valor de verdadeiro ou falso. O retorno foi false por conta do mês incorreto na string da variável `dataString`. Se realizar a corrreção do mês da variável o programa vai retornar que a conversão foi bem sucedida. 