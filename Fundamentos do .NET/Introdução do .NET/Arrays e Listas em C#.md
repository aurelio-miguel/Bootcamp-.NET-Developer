# Arrays e Listas em C#

## Arrays
O array também pode ser conhecido como matriz ou vetor. O Array é uma estrutura de dados que armazena valores do mesmo tipo com um tamanho fixo. Em alguns momentos é necessário representar diversos valores em uma variável, para isso utilizamos um array, o array possui a capacidade de armezenar diversos valores do mesmo tipo em uma única variável. Todos os itens do array precisam ter o mesmo tipo.

Segue abaixo alguns exemplos:

- Nesse primeiro exemplo temos a criação de um array de inteiros. Ele é criado primeiramente definindo a variável seguida de colchetes para representar o array. Após isso é definido o nome do array e em seguida o operador de atribuição para que possamos determinar o valor. Após o operador de atribuição é realizado a declaração do array com o comando `new int[tamanhoDoArray]`, o 4 representa o tamanho que esse arry vai ter.

```
int[] nomeDoArray = new int[4];
```

- Nesse segundo exemplo temos a criação de um array já inserindo os valores dele. Para fazer isso realizamos a criação da estrutura padrão `int[] nomeDoArray = new int[]...`, porém após os colchetes podemos já inserir os valores através das chaves, por exemplo `{2,5,8,5}`. Dessa forma teremos um array criado e com os valores já inseridos, o tamanho do array será a quantidade de itens que foram inseridos, dessa forma podemos omitir o tamanho dele. Cada item do array é separado por vírgula.

```
int[] nomeDoArray = new int[] {2,5,8,5};
```

- No terceiro exemplo foi criado um array de strings em que a declaração do array é feita apenas no momento da criação da variável. Após o operador de atribuição os valores já são inseridos entre chaves.
```
string[] nomeDoArray = {"Janeiro", "Fevereiro"};
```

### Índice
O indice é a posição de um determinado valor dentro de um array, o indice sempre começa do zero.

Na imagem abaixo podemos ver os valores de um array e o indice onde cada um dos valores estão inseridos.

![Imagem explicando o índice de um array](/imagens/array.png);

Através do indice podemos capturar o valor de um dos elementos do array e também podemos utilizar o índice para alterar o valor de um determinado indice.

Para acessar o valor de um determinado índice, basta utilizar o comando `nomeDoArray[posicao]`, a posição sempre deve ser um inteiro.

Segue abaixo um trecho de código que exemplifica esse tipo de captura e manipulação de dados do array através do índice.

```
//criação do array
int[] array = {2,5,9.3};

//Capturando a informação de um array e passando pra uma variável
int elemento0 = array[0];

//Alterando o valor de um item do array
array[1] = 56;
```

Nos exemplos acima foi possível capturar o valor do array que estava no índice zero e foi possível alterar o valor que estava inserido na posição 1 do nosso array.

Se você tentar acessar uma posição maior do que o tamanho do array o seu problema vai gerar um erro de excessão, é importante gerenciar o tamanho máximo de um array;

### Implementando um array
Vamos iniciar essa etapa declarando um array de inteiros com três posições, dentre as três forma possíveis de criação de arrays:
```
int[] arrayInteiros = new int [3];
```

Na próxima etapa, vamos inserir os valores em cada uma das posições separadamente:
```
int[] arrayInteiros = new int[3];

arrayInteiros[0] = 57;
arrayInteiros[1] = 33;
arrayInteiros[2] = 21;
```

Na próxima etapa vamos exibir o array no console através do Console.WriteLine:
```
int[] arrayInteiros = new int[3];

arrayInteiros[0] = 57;
arrayInteiros[1] = 33;
arrayInteiros[2] = 21;

Console.WriteLine($"índice 0: {arrayInteiros[0]}");
Console.WriteLine($"índice 1: {arrayInteiros[1]}");
Console.WriteLine($"índice 2: {arrayInteiros[2]}");

Output:
índice 0: 57
índice 1: 33
índice 2: 21
```

Podemos também aproveitar o for para acessar cada um dos valores e imprimir no console, conforme consta no trecho de código abaixo:
```
...

for (int indice = 0; indice < arrayInteiros.Length; indice++)
{
    Console.WriteLine($"índice {indice}: {arrayInteiros[indice]}");
}

Output:
índice 0: 57
índice 1: 33
índice 2: 21
```
Nesse trecho utilizamos o for para percorrer o array e o contador foi utilizado para indicar o índice do array que acessamos. utilizamos o comando `arrayInteiros.Length` para executar o for até o tamanho determinado do array.

### Erro de excessão
Esse erro ocorre quando você tenta acessar um indice que não faça parte do seu array. Imagine que você criou um array com 4 itens e deseja acessar a posição 4. Pelo fato do array começar com o zero, o indice máximo é o 3, se você acessar um indice inexistente vai ocorrer o erro abaixo:

`Unhandled exception. System.IndexOutOfRangeException: Index was outside the bounds of the array.`

### Percorrendo um array com FOREACH
Para percorrer um array, também podemos utilizar o **FOREACH** para percorrer um array sem a necessidade de um contador para acessar cada um dos itens.

Segue abaixo um trecho de código com o foreach:
```
...

foreach (int valor in arrayInteiros)
{
    Console.WriteLine($"Valor: {valor}");
}

Output:
Valor: 57
Valor: 33
Valor: 21
```
Dentro dos parenteses do foreach, iniciamos declarando uma variável que deve ter o mesmo tipo do array que queremos percorrer. Essa variável vai receber o elemento atual do array, por isso que ela precisa ter o mesmo tipo do array. Após isso, dentro dos parametros utilizamos o `in nomeDoArray` para que o foreach saiba que o arry que deve ser percorrido é o array em questão. Para capturar o valor foi utilizado apenas a variável criada na estrutura do FOREACH com o nome `valor`;

O FOREACH não possui o contador imbutido da mesma forma que podemos fazer através do laço de repetição FOR. Uma alternativa para ter o contador seria declarando uma variável antes do FOREACH e a cada novo loop ir incrementando um nesse contador, por exemplo:
```
...

int contador = 0;

foreach (int valor in arrayInteiros)
{
    Console.WriteLine($"Posição Nº{contador}: {valor}");
    contador++;
}

Output:
osição Nº0: 57
Posição Nº1: 33
Posição Nº2: 21
```

Com o FOREACH nós podemos evitar erros de excessão e não temos a necessidade de usar os colchetes para acessar as posições sendo gerenciados por um contator, assim como ocorre no FOR.

