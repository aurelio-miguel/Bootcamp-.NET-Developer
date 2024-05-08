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

## Redimensionando um array
O array já é definido com o seu tamanho pré-determinado e não é possível aumentar ou diminuir o tamanho de um array no percurso do desenvolvimento. 

Existe uma alternativa para poder mudar o tamanho de um array que é utilizando a classe `Array` e a sua função `Resize()`;

Segue abaixo um trecho de código com a estrutura para o redimensionamento:
```
Array.Resize(ref nomeDoArray, nomeDoArray.Length * 2);
```
Perceba que o primeiro parâmetro da função **Resize** pede o array por referência, isso é feito pois o primeiro parâmetro da função não vai receber o valor do array e sim o endereço da memória do array. O segundo parâmetro é o novo tamanho do nosso array, o novo tamanho sempre deve ser inserido como inteiro, nesse caso utilizamos o comando `nomeDoArray.Length * 2` para pegarmos o tamanho do array através do `.Length` e multiplicar esse tamanho por 2. Dessa forma conseguimos dobrar o tamanho do array.

O mesmo processo pode ser feito para diminuir o tamano do array, ao diminuir o tamanho de um array ocorre a perda dos valores a partir da última posição.

Internamente a função **Resize()** cria uma cópia do array que você deseja alterar e insere ela em um novo array com o tamanho maior e também copia todos os valores e insere no novo array. Por isso que no primeiro parâmetro é passado a referência do local da memória onde se encontra o array previamente criado.

## Copiando um Array para outro
É possível copiar um array e inserir ele dentro de outro array, podemos fazer isso através da função array da classe resize ou podemos fazer isso manualmente. Podemos por exemplo copiar um array menor e inserir em um array maior, podemos fazer também o contrário.

Segue abaixo um trecho de código com um exemplo para isso:
```
//Criando o primeiro array e inserindo os dados
int[] array1 = new int[3];

array1[0] = 57;
array1[1] = 33;
array1[2] = 21;

//Criando o segundo array
int[] array2 = new int[array1.Length * 2];

//Copiando os dados do array1 para o array2
Array.Copy(array1, array2, array1.Length);
```

**Etapas:**
- Criando o primeiro array e inserindo os dados: Nessa etapa foi criado o primeiro array e os dados foram inseridos, conforme já ensinado nesse material.

- Criando o segundo array: Nessa etapa criamos um novo array chamado *array2* e definimos o tamanho como `array1.Length * 2`, dessa forma pegamos o tamanho do array1 com o `Length` e multiplicamos por 2. O array2 vai ter o tamanho do array 1 x 2;

- Copiando os dados do array1 para o array2: Através da função `Copy()` da classe `Array` nós inserimos como primeiro parâmetro o array de origem, no segundo parâmetro foi indicado o array que vai receber os dados e no terceiro parâmetros foi passado qual a quantidade que deveria ser copiado, nesse exemplo todos os dados do array1 foram copiados passando o comando `array1.Length`. Nessa terceiro parâmetro podemos passar apenas a quantidade que desejarmos.

## Trabalhando com Listas
Uma lista possui a capacidade de armezenar uma coleção de objetos do mesmo tipo, porém, sem toda a complexidade de um array. Por exemplo, o array obriga a definição do tamanho dele, já a lista não possui essa obrigatóriedade, além disso o redimensionamento pode ser feito de forma mais facilitada. 

A lista pode aumentar a sua capacidade conforme vamos inserindo elementos nela. Não é preciso realizar o gerenciamento de tamanho ou se preocupar com a capacidade máxima da lista, algo que era necessário nos arrays.

### Estrutura de criação da lista
Paa realizar a criação da lista, basta seguir a estrutura abaixo:
```
List<string> nomeLista = new List<string>();
```
A criação da string é iniciada com a classe `List<string>` para que possamos criar uma lista de strings, o tipo da lista é inserido dentro do sinal de maior e menos e o nome da variável é inserida após o sinal de maior, conforme o padrão de criação de variáveis. Após isso é definido o nome da variável e é inserido o operador de atribuição para realizar a declaração. Após o indicador de atribuição a lista é inmplementada através do comando `new List<string>();` nessa implementação também é passada o tipo da variável.

Não é preciso passar uma capacidade para a lista, por isso que não tem nenhum valor inserido dentro das parenteses. 

Após a implementação da lista, ela se torna uma instãncia da classe List. Dessa forma podemos trabalhar com diversas funções que essa classe possui.

### Inserindo elementos na lista
Para trabalhar com a lista podemos utilizar os métodos da classe List após a sua criação. Para inserir um novo elemento, podemos utilizar as funções *Add()* ou *AddRange* para inserir mais de um elemento.

Segue abaixo um exemplo de inserção na lista
```
List<string> listaString = new List<string>();

listaString.Add("TO");
listaString.Add("SP");
listaString.Add("BA");
```

### Percorrendo uma lista
Para percorrer uma lista podemos utilizar o FOR ou o FOREACH, da mesma forma que foi exemplificado na criação do array. A única diferença é que nas listas não temos o *.Length* para capturar o tamanho, para listas devemos utilizar o *.Count*.

Percorrendo a lista com o FOR:
```
for (int contador = 0; contador < listaString.Count; contador++)
{
    Console.WriteLine($"Posição Nº{contador}: {listaString[contador]}");
}

Output:
Posição Nº0: TO
Posição Nº1: SP
Posição Nº2: BA
```

Percorrendo a lista com o FOREACH:
```
int contador = 0;
foreach (string valor in listaString)
{
    Console.WriteLine($"Posição Nº{contador}: {valor}");
    contador++;
}

Output:
Posição Nº0: TO
Posição Nº1: SP
Posição Nº2: BA
```
A variável de contador não é obrigatória para o foreach, utilizei apenas para exemplificação.

### Removendo um elemento da lista
Para remover um elemento da lista, podemos utilizar a função `Remove(item)` da lista criada.

Segue abaixo um trecho de código que exemplifica esse processo:
```
List<string> listaString = new List<string>();

listaString.Add("TO");
listaString.Add("SP");
listaString.Add("BA");

listaString.Remove("SP");
```
Além de remover, a função também reorganiza as posições da lista e o tamanho para que o espaço removido não fique em branco