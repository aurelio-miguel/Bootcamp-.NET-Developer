# Introdução a estrutura de repetição
As estruturas de repetição são conhecidas também como laço de repetição. Essa estrutura possibilidade que um determinado trecho de código seja executado uma quantidade de vezes pré-determinada ou enquanto uma determinada condição não for atingida.

Essa estrutura está presente em todas as principais linguagens de programação e é uma estrutura muito útil.

No diagrama abaixo, imagine que queremos fazer a tabuada de um determinado número:

![Laços de repetição](/imagens/laco_de_repeticao.png)

No diagrama acima é possível visualizar que ocorre uma multiplicação do valor de x pelo contador. O contador inicia no zero e após fazer a multiplicação, é incrementado mais um no contador e após isso ele retorna para a condição para verificar se ela ainda é true.

O contador vai iniciar do zero e a cada novo ciclo ele vai ter o valor dele + 1; Esse contador vai ser utilizado para a multiplicação e também para a condição de continuidade do laço de repetição. Assim que o contador for maior do que 10, o laço de repetição vai terminar.

### Etapas do laço de repetição acima
**1º -** Verifica se a condição é verdadeira ou não. Assim que a condição for falsa o programa termina.
**2º -** O sistema vai utilizar o contador que foi iniciado do zero para ser base de cálculo par a multiplicação. No primeiro ciclo ele vai realizar o cálculo `X * 0`, por exemplo.
**3º -** Nessa etapa o sistema vai incrementar +1 na variável contador. 

Após a última etapa, o sistema vai voltar para a condição e verificar se ela segue sendo verdadeira, agora o contador vai ter o valor maior e esse valor seguirá sendo utilizado na multiplicação e também na condição.

## Introdução ao FOR
O FOR é um tipo de laço de repetição que nos permite executar um comando com base em uma condição. No geral o FOR é muito utilizado quando temos o interesse em executar um trecho de código X vezes.

Com esse laço de repetição podemos determinar que um trecho de código deve ser executado X vezes. O contador, a condição e o incremento é todo feito dentro da estrutura FOR.

### Estrutura de um FOR
No FOR temos primeiro a declaração dele com a estrutura `for(){}`. Dentro dos parenteses vamos começar criando a variável que será o contador, após isso criaremos a condição para a repetição e por último vamos incrementar no nosso contador o valor +1. Cada um dos três elementos são separados entre ele por ponto e vírgula

```
for(criação do contador; condição de parada; incremento do contador)
{
    //comandos a serem executados
}
```
O incremento é realizado após a execução dos comandos inseridos dentro das chaves.

No trecho de código abaixo realizaremos a criação da tabuada do diagrama da primeira imagem desse conteúdo:
```
int numero = 10;

for(int contador = 0; contador <= 10; contador++)
{
    Console.WriteLine($"{numero} x {contador} = {numero * contador}");
}

Output:
10 x 0 = 0
10 x 1 = 10
10 x 2 = 20
10 x 3 = 30
10 x 4 = 40
10 x 5 = 50
10 x 6 = 60
10 x 7 = 70
10 x 8 = 80
10 x 9 = 90
10 x 10 = 100
```
No código acima realizamos a criação do contador iniciando do zero, após isso determinamos a condição de repetir o trecho dentro das chavez até que o valor do contador fosse menor ou igual a 10, no terceiro elemento inserimos o incremento para inserir +1 no contador.

Perceba que nós utilizamos o contador para auxiliar na multiplicação da nossa tabuada e utilizamos o valor dele também para exibir o texto na saída.

O trecho `Console.WriteLine($"{numero} x {contador})` vai apenas exibir o valor do número que definimos anteriormente na variável e vai exibir também o valor atual do nosso contador

## Introdução ao WHILE
Em português, while significa enquanto. Esse laço de repetição é muito utilizado quando não sabemos previamente quantas vezes queremos que um trecho de código seja repetido, enquanto a condição for verdadeira o while seguirá sendo executado. Diferente do FOR que é inserido a quantidade de vezes que ele deve ser executado com base na condição e no contador, o while vai continuar sendo executado enquanto uma condição for verdadeira.

É preciso compreender que a estrutura do while precisa ter um momento em que a condição será falsa, caso contrário o código vai ficar em um loop infinito. 

Caso necessário, o contador deve ser criado e incrementado manualmente pelo sistema.

### Estrutura while
O While tem um padrão bem simples, ele possui apenas a condição em sua estrutura de repetição.

```
while(true){
    ...
}
```
Enquando a condição for verdadeira, ele vai seguir repetindo os comandos que estão entre as chaves. 

Criando o diagrama de tabuada desse material com o While:
```
int numero = 10;
int contador = 0;

while (contador <= 10)
{
    Console.WriteLine($"{numero} x {contador} = {numero * contador}");
    contador++;
}

Output:
10 x 0 = 0
10 x 1 = 10
10 x 2 = 20
10 x 3 = 30
10 x 4 = 40
10 x 5 = 50
10 x 6 = 60
10 x 7 = 70
10 x 8 = 80
10 x 9 = 90
10 x 10 = 100
```

No trecho de código acima é possível ver que foi necessário implementar o contador e fazer o gerenciamento dele incrementando + 1 na etapa final do nosso laço de repetição. Diferente do FOR, no WHILE esse gerenciamento deve ser implementado por nós.

Nesse código foi possível inserir uma condição para que o código entre chaves fosse executado, esse código é executado enquanto a condição for verdadeira.

## Interrompendo um fluxo de execução
Para interromper o fluxo do loop, basta utilizar o comando `break;`. O break é utilizado para que podemos para a execução do while ou for quando desejado. 

Imagine que temos um if dentro do while que faz uma validação e caso essa validação seja verdadeira, queremos para o while por algum motivo. Com o `break` podemos fazer isso.

Segue abaixo um exemplo de um código com o break:
```
int numero = 10;
int contador = 0;

while (contador <= 10)
{
    Console.WriteLine($"{numero} x {contador} = {numero * contador}");
    if (contador == 7)
    {
        break;
    }
    contador++;
}
```

No código acima foi inserido um `break` para que a execução do loop terminasse se o contador fosse igual a 7. A partir do momento que o break é executado, o loop é finalizado.

## Introdução ao DO WHILE
O laço de repetição DO WHILE é uma extensão do laço de repetição WHILE, porém, a verificação é feita no final do código.

Segue abaixo como funciona a estrutura do DO WHILE
```
do{

}while(condica);
```
Iniciamos a estrutura com o **DO** e após a abertura e fechamento das chaves vai ser inserido o while com a condição para continuidade da repetição.

Com o WHILE padrão, a condição é verificada antes do inicio da repetição, se a verificação for verdadeira o escopo entre as chaves é executado. Com o DO, o código entre chaves será vai iniciar a sua execução independente da condição expressa no WHILE. Após percorrer ele vai verificar se a condição do WHILE segue sendo verdadeira, caso seja verdadeira ele vai percorrer novamente, caso seja false ele vai parar de percorer laço de repeição.

No geral a diferente entre o WHILE e o DO WHILE, é que o WHILE vai verificar a condição antes de executar os comandos e o DO WHILE vai verificar após executar os comandos.

Segue abaixo um código que exemplifica a estrutura do DO WHILE em um sistema de soma interativo
```
int soma = 0;
int numero = 0;

do
{
    Console.WriteLine("Digite um número (0 para parar): ");
    numero = Convert.ToInt32(Console.ReadLine());
    soma += numero;

} while (numero != 0);

Console.WriteLine($"Total da soma dos números é: {soma}");
```
Nesse comando o sistema vai pedir para que o usuário digite um número no console e informa que se o número zero for digitado, o cálculo vai parar. Esse código começa pedindo para o cliente o número, após o cliente digitar o sistema realiza a conversão do texto digitado no console para inteiro e realiza a soma, após a soma ele verifica se o número digitado é diferente de zero, se essa informação for verdadeira o código entre as chaves será executado novamente até que o usuário digite o zero.