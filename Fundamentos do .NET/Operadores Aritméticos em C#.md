# Operadores Aritméticos em C# e a classe Math
Os operadores aritméticos são os operadores que utilizamos na matemática e também podemos utilizar na programação para realizar cálculos. 

A classe Math do C# é uma classe também voltada para a realização de cálculos de forma facilitada. Essa classe permite a realização de operações mais complexas.

## Operadores aritméticos
- **( + )**: Operador utilizado para realizar soma entre o elemento localizado na parte esquerda e o elemento da parte direita. Por exemplo: x + y;

- **( - )**: Operador utilizado para realizar subtrações, esse operador vai realizar a subtração entre o elemento localizado a esquerda do operador e o elemtno localizado a direita do operador. Por exemplo: x - y;

- **( * )**: Esse operador é utilizado para realizar multiplicação, com ele podemos multiplicar de dois valores. Por exemplo: x * y;

- **( / )**: O operador de divisão permite que possamos dividir o valor da esquerda pelo valor da direita. Por exemplo: x / y;

- **( % )**: O operador de módulo permite retorna o resto da divisão entre dois valores. Por exemplo: 5 % 2 = 1, 1 é o resto da divisão entre ao dividir o 5 por 2;

- **( ++ )**: Operador de incremento permite incrementar 1 em uma detarminada variável, esse é um operador muito utilizado com alguns laços de repetição. Por exemplo: idade++;

- **( -- )**: Diferente do operador de incremente, o operador de decremento vai remover 1 elemento por vez. Por exemplo: 1--;

## Usando a potência
Para fazer uma potência, utilizaremos a classe **Math** para realizar os cálculos mais complexos;

No trecho de código abaixo nós realizamos a criação de um método com o nome *Potência*, esse vai receber 2 valores por parâmetro e esses valores serão utilizados no método **Pow()** da classe **Math**. A classe **Math** possui vários outros métodos para cálculos mais complexos

```
public void Potencia(int x, int y)
{
    double potencia = Math.Pow(x, y);
    Console.WriteLine($"{x} ^ {y} = {potencia}");
}
```

O resultado da potência foi inserido na variável com o nome *potencia* e o seu resultado foi exibido através do método WriteLine da classe Console.

## Exemplso de código
No projeto *Aula01* eu criei uma nova classe com o nome *Calculadora* e inseri nela todos os métodos citados nessa aula. Segue abaixo a estrutura da classe Calculadora e os seus métodos:

```
namespace Aula01.Models
{
    public class Calculadora
    {
        public void Somar(int x, int y)
        {
            Console.WriteLine($"{x} + {y} = {x + y}");
        }

        public void Subtrair(int x, int y)
        {
            Console.WriteLine($"{x} - {y} = {x - y}");
        }

        public void Multiplicar(int x, int y)
        {
            Console.WriteLine($"{x} * {y} = {x * y}");
        }

        public void Dividir(int x, int y)
        {
            Console.WriteLine($"{x} / {y} = {x / y}");
        }

        public void Resto(int x, int y)
        {
            Console.WriteLine($"{x} % {y} = {x % y}");
        }

        public void Incrementa(int x)
        {
            int result = x;
            result++;
            Console.WriteLine($"{x}++ = {result}");
        }

        public void Decrementa(int x)
        {
            int result = x;
            result--;
            Console.WriteLine($"{x}-- = {result}");
        }

        public void Potencia(int x, int y)
        {
            double potencia = Math.Pow(x, y);
            Console.WriteLine($"{x} ^ {y} = {potencia}");
        }
    }
}
```

No *Program.cs* eu instanciei essa classe para utilizar os seus métodos e imprimir os resultados no console, conforme consta o código abaixo:

```
using Aula01.Models;

Calculadora c1 = new Calculadora();

c1.Somar(3, 5);
c1.Subtrair(4, 2);
c1.Multiplicar(5, 3);
c1.Resto(5, 2);
c1.Incrementa(10);
c1.Decrementa(10);
c1.Potencia(5, 2);

```