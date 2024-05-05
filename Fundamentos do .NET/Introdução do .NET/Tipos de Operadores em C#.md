# Tipos de Operadores em C# 

## Operadores de atribuição
Esse operador é utilizado para que possamos atribuir um valor a uma determinada variável. Podemos mudar o valor ou inserir o valor de uma variável utilizando o sinal `=`. O valor a ser atribuido em uma variável deve ser do mesmo tipo da variável na qual a atribuição será realizada. 

```
string informacao = "C# é legal!";
```
No trecho acima nós realizamos a atribuição da string "C# é legal!" na variável *informacao*;

## Combinando operadores
Tambem existe a possibilidade de combinar operadores de atribuição com outros operadores aritméticos (+, -, *, / e etc). 

```
int valor = 5;
valor += 5
//Poderiamos utilizar também o *=, -=, /=
Console.WriteLine(valor);

Output: 10
```
Utilizando o comando `+=` podemos somar o valor de 5 ao valor já existente nessa variável. Dessa forma iremos incrementar no valor já inserido inicialmente nessa variável. Com esse operador realizamos basicamente a operação de pegar o valor da variável, somar junto ao valor da variável e inserir nela novamente. Esse comando seria similar ao comandao `valor = valor +5;`

## Convertendo tipos de variáveis
A conversão de tipos pode ser utilizada para várias finalidades, dentre elas converter um valor para que ele se adeque ao tipo específico de uma variável.

```
int a = "5"; //Isso gera um erro pois a variável é int e o texto é uma string.
```
### Casting
O proceddo de conversão é conhecido como *Cast* ou *Casting*. Para isso podemos utilizar a classe *Convert* e os seus métodos de conversão. Por exemplo, `Convert.ToInt32(valor)`

```
int a = Convert.ToInt32("5"); //Dessa forma é realizada a conversão.
```
Utilizando o método *Convert*, podemos realizar diversos tipos de conversões através de seus métodos, no código acima foi utilizado o método *ToInt32* para converter uma string em um inteiro de 32 bits.

### Parse
Uma outra alternativa é utilizando o parse. Para isso podemos utilizar o comando `int.Parse(valor)`. O Parse vai converter o valor para o tipo inteiro de 32 bits;
```
int a = int.Parse("5");
```
O mesmo procedimento pode ser feito para os outros tipos de dados, basta substituír o `int` para o tipo que você deseja.

#### Diferenças entre o Convert e o Parse
A diferença principal entre os dois é o tratamento de valores nulos. Se eu utilizar o **Convert**, se passar um valor *null*, o Convert vai retornar o valor zero;
```
int a = Convert.ToInt32(null);
Console.WriteLine(a):

Output: 0
```

Já com o **Parse**, o programa vai exibir um erro pois o programa vai informar que o valor não pode ser nulo. O Parse não aceita valores nulos

## Conversão para string
O método *Parse* não é disponível para o string. Para converter valores para string podemos utilizar o comando `variavel.ToString();`.
```
int inteiro = 5;
string a = inteiro.ToString();
```
Todos os tipos de dados podem ser representados como string, basta utilizar o método *ToString()* para poder utiliza-lo.

## Cast Implícito
Cast Implícito é basicamente uma conversão de diferentes tipos sem precisar utilizar um método para conversão, o processo de conversão é feita de forma automática.

```
int a = 5;
double b = a;
```
Como vimos anteriormente, nós não podemos passar valores para uma variável que tenha um tipo de valor diferente. No caso descrito no código acima, foi feito um casting implícito, internamente o valor da variável *A* foi convertido para double.

Esse casting implícito foi possível pois um número inteiro cabe na variável double, o double suporte valores inteiros. O contrário disso não seria possível, tendo em vista que o int não suporte valores double;

## Ordem dos operadores
A ordem dos operadores pode afetar as operações no C#. No C# os operadores seguem a mesma rdem das operações matemáticas. Primeiro é resolvido o que está entre parenteses, após isso expoentes, seguido por divisão e multiplicação, sem seguida adição e subtração.

## Operadores condicionais
O operador condicional possibilita mudar o fluxo de execução do código, indicando um caminho que ele deve percorrer.

Imagine que você está em um ponto de ônibus para ir para a faculdade. A partir do momento em que esse ônibus demora para passar, você pode criar uma condição de qual atitude você devo tomar com base nessa situação.

![Imagem de um operador condicional](/imagens/operador_condicional.png)

As condições são boleanas, a condição pode ser verdadeira ou falsa.
Os operadores condicionais permitem que possamos escolher qual trecho de código deve ser executado com base em condições determinadas.

### Operador condicional na prática
No exemplo abaixo utilizaremos dois operadores condicionais, um deles é o **IF ou se**, ou outro operador condicional utilizado foi o **ELSE ou se não**;

```
int quantidadeEmEstoque = 10;
int quantidadeCompra = 2;

if (quantidadeEmEstoque >= quantidadeCompra)
{
    Console.WriteLine("A compra pode ser realizada.");
}
else
{
    Console.WriteLine("Desculpe. Não temos essa quantidade em estoque.");
}
```
No código acima foi armazenado a quantidade de itens em estoque na variável *quantidadeEmEstoque* e a quantidade de itens que uma pessoa deseja comprar foi armazenado na variável *quantidadeCompra*. Através dos operadores condicionais conseguimos imprimir mensagens diferentes com base na condição de ter a desejada em estoque.

Através do **if** foi verificado se a quantidade em estoque era maior que a quantidade de compra, caso essa condição não fosse atendida (false) a mensagem dentro das chaves não era executada. O **else** permite executar os comandos do seu escopo se a condição anterior não for verdadeira. Se a condição do **if** fosse verdadeira, o comando do escopo **else** não seria executado.

Se o bloco a condição do if for verdadeira, ele vai executar o código do escopo do if e vai ignorar a condição do else. Se a condição do if for falso, ele vai ignorar o escopo do if e vai executar o código do else. 

### IF aninhado
Com o if aninhado podemos ter várias condições que são possíveis de percorrer.

Imagina que você tenha um terceiro caminho, sendo eles um **if(se)**, um **else if(se não se)** e um **else(se não)**. Essa estrutura pode ser utilizada para quando precisamos realizar mais de uma verificação.

Neste caso, se a primeira condição for verdadeira, todo o fluxo das próximas condições não é executado, apenas o primeiro. Se o primeiro for falso, ele verifica se o segundo é verdadeiro, caso seja verdadeiro, será executado os códigos do escopo do **else if**. Se o **else if** também for falso, é executado o comando do **else**

Dessa forma podemos inserir novas camadas de verificações onde podemos criar condições mais complexas para que comandos sejam executados

```
int quantidadeEmEstoque = 10;
int quantidadeCompra = 2;

if (quantidadeCompra == 0)
{
    Console.WriteLine("Venda inválida");
}
else if (quantidadeEmEstoque >= quantidadeCompra)
{
    Console.WriteLine("A compra pode ser realizada.");
}
else
{
    Console.WriteLine("Desculpe. Não temos essa quantidade em estoque.");
}
```

No código acima foi possível criar uma terceira possibilidade. O nosso programa inicia verificando se a variável *quantidadeCompra* é igual a zero, se não for igual a zero ele segue para as próximas condições. O **else** será executado se as duas condições anteriores falharem.

Esse tipo de estrutura permite que apenas um dos caminhos sejam executados. Caso a primeira condição seja falsa e a segunda também, o else é executado.

### Aprendendo o switch case
O Switch case é uma estrutura condicional utilizada para realizar verificações com muitos caminhos possíveis ou muitas condições possíveis. 

No código abaixo foi feito um código para solicitar uma letra para o usuário e o programa deve determinar se a letra é uma vogal ou não. 

```
Console.WriteLine("Digite uma letra:");
string letra = Console.ReadLine();

switch (letra)
{
    case "a":
    case "e":
    case "i":
    case "o":
    case "u":
        Console.WriteLine("Vogal");
        break;
    default:
        Console.WriteLine("Não é uma vogal");
        break;
}
```

Com o switch podemos criar as verificações com base em uma determinada variável ou valor que é passado através do do comando `switch(valor)`. O `case` vai funcionar de forma similar ao if, ele vai realizar uma verificação e se for verdadeiro o código do seu escopo será executado. Nesse caso o escopo vai estar entre o **:** e o `break`.

Com o switch podemos criar a estrutura condicional, se nenhuma condição for atendida, ele executa o escopo do `default`, o default vai funcionar de forma similar ao **else**.

No switch é necessário inserir o `break;` para que a execução seja finalizada, caso contrário o switch vai seguir em funcionamento. 

## Introdução aos operadores lógicos
Esses operadores são muito utilizados em estruturas condicionais e são operadores que nos permitem criar a lógica das condições. Imagine que eu queira imprimir a idade de uma pessoa se ela tiver uma idade maior que 18 anos e estiver na faculdade, para criar condição eu precisarei usar um operador lógico para unir essa condição

### Operador OR (Pipe, ||)
Esse operador vai fazer com que uma condição seja verdade de uma das premissas da condição forem verdadeiras. Por exemplo: Só vai entrar na piscina se tiver + de 18 anos ou estiver com os pais. Esse **ou** permite que o exemplo anterior retorne como verdadeiro se pelo menos uma das premissas for verdadeira.

Segue abaixo mais um exemplo:

![Imagem com o operador ou](/imagens/operador%20or.png)

Na imagem acima podemos notar que a entrada do usuário pode ocorrer se ele for maior que 18 anos ou se ele possuir autorização do responsável. Nós podemos representar essa condição atração do ou. Textualmente essa exemplificação ficaria da sequinte forma:
```
if(maior que 18 anos || possui autorização dos pais){
    //Entrada liberada
}
else{
    //Entrada não permitida.
}
```

Segue abaixo o código que implementa o diagrama da imagem deste tópico
```
int idade = 15;
bool autorizacaoResponsavel = false;

if (idade > 18 || autorizacaoResponsavel)
{
    Console.WriteLine("Entrada liberada");
}
else
{
    Console.WriteLine("Entrada não permitida");
}
```
No **if** foi possível implementar o operador **OR** através do pipe(||).

### Operador AND (&&)
Esse operador é um pouco mais restritivo em relação ao operador OR. Quando utilizado, o condicional só será todas as condições forem verdadeiras. Independente da quantidade de condições, todas precisam ser verdadeiras.

Imagine que para ser aprovado, o aluno precisa ter a quantidade mínima de presença e também ter a média maior ou igual a 7. Nesse caso, o aluno só será aprovado se as duas condições forem satisfeitas.

![Imagem com o operador AND](/imagens/operador%20and.png)

Segue abaixo a implementação do diagrama acima
```
bool presencaMinima = true;
double media = 7.5;

if (presencaMinima && media >= 7)
{
    Console.WriteLine("Aprovado");
}
else
{
    Console.WriteLine("Reprovado");
}
```
Para realizar a verificação das condições, foi utilizado o **&&** que é a representação do AND. 

### Operador NOT (!)
Esse operador também é conhecido como operador de negação, o objetivo desse valor é negar um operador boleano. Esse operador está ligado a uma negação, o nosso objetivo é verificar se uma condição é falsa. 

![Operador NOT](/imagens/operador_not.png)

Segue abaixo um trecho de código onde coloco em prática o diagrama acima:

```
bool choveu = false;
bool estaTarde = false;

if (!choveu && !estaTarde)
{
    Console.WriteLine("Vou pedalar");
}

else
{
    Console.WriteLine("Vou pedalar outro dia");
}
```
o IF espera que a condição seja verdadeira, porém, utilizando o NOT é possível inverter isso para que possamos esperar que a condição seja falsa.

Com base no diagrama, queremos o cenário onde NÃO choveu e NÃO está tarde. Utilizando o NOT podemos validar se a variável **choveu** e falsa e também a variável **estaTarde** é falsa.

Utilizando o operador NOT nós negamos as duas variáveis para poder verificar se não estava chovendo e se não estava tarde. Dessa forma o nosso fluxo inicial de condição vai verificar se os boleanos estão em conformidade para a execução do trecho `Console.WriteLine("Vou pedalar");`.

O sinal de negação permite que eu consiga entrar no fluxo do IF, mesmo com as condições sendo falsas. Como sinal de negação é possível inverter o valor da variável para que possamos acessar o escopo dessa condição.

Através do operador **&&** nós fizemos a verificação para confirmar se as duas condições estavam em conformidade.