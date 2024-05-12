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
