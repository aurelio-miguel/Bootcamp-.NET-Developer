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