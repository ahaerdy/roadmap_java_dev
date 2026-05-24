# O que são declarações condicionais em programação?

Declarações condicionais, expressões ou simplesmente condicionais são recursos das linguagens de programação que dizem ao computador para executar certas ações, desde que certas condições sejam atendidas. Declarações condicionais são usadas através das várias linguagens de programação para instruir o computador sobre a decisão a tomar quando dadas algumas condições. Essas decisões são tomadas se e somente se as condições pré-estabelecidas forem verdadeiras ou falsas, dependendo das funções que o programador tem em mente. Todas as linguagens de programação têm sintaxe de expressão condicional (embora a sintaxe difira ligeiramente de uma linguagem para outra). 

Por exemplo, uma típica declaração condicional em C# lê assim:

```csharp
public static void Weather(string myDay)
        {
            if (myDay == "Sunny")
            {
                Console.WriteLine("Read in the Library");
            }
            else if (myDay == "Raining")
            {
                Console.WriteLine("Read at Home");
            }
            else if (myDay == "Cloudy")
            {
                Console.WriteLine("Read in the Garden");
            }
            else
            {
                Console.WriteLine("Get some Sleep");
            }
        }
```

Do exemplo acima, podemos ver como um programa pode ser usado para expressar várias decisões com base na veracidade ou falsidade das condições dadas. Testamos para `Weather("Cloudy")`. Além de `if`, `else if` e `else` declarações condicionais (como ilustrado no exemplo acima), linguagens de programação também têm `if else` (C e C++), `elif` (Python), e `switch case` (C#, Java, JavaScript, e um novo recurso na versão 3.10 do Python). As declarações condicionais são vitais no campo da programação e engenharia de software, na medida em que as condições podem ser usadas pelos programadores e engenheiros de software para permitir que uma máquina simule o comportamento de uma pessoa que tem a habilidade de fazer escolhas e executar algumas ações com base na decisão tomada. Com expressões condicionais, a linguagem de programação dá aos programadores ferramentas e recursos que eles podem manipular para colocar uma máquina para trabalhar de forma eficaz.

Para maior clareza, vamos mergulhar nos tipos de declarações condicionais. Tenha em mente que todas as declarações condicionais retornam valores booleanos, ou seja, **true** ou **false**.

## Decalaração if 

A declaração `if` é a primeira condição que um programador usa para abrir o terreno das declarações condicionais. A sintaxe do `if` é tão simples quanto escrever `if` com chaves de abertura e fechamento, seguido pela condição que o programador pretende comparar ou verificar. A expressão `if` simplesmente compara se a condição (ou condições) contida nas chaves é verdadeira ou falsa. Se for verdadeira, o bloco de código `if` é executado. Se for falsa, a execução passa para o próximo bloco para verificar.

```csharp
if (day == " Monday") // Condition
    {
        // Decision
        Console.WriteLine("Go to School");
    }
```

Verifica **se** o dia é Monday, o que pode resultar apenas em true ou false (bool).

## Decalaração else if

Enquanto a declaração `if` pode ser usada para verificar uma condição, `else if` é usada para verificar múltiplas condições. A declaração `else if` (ou `elif` em Python), tem sintaxe similar à declaração `if`, seguida pelo bloco `else if`. Por exemplo:

```csharp
if (myDay == " Sunny")
    {
        // Decision
        Console.WriteLine("Read in the Library");
    } // 2nd condition
else if (myday == "Raining")
    {
        //decision
        Console.WriteLine("Read at Home")
    } // 3rd condition
else if (MyDay == "Cloudy")
    {
        // Decision
        Console.WriteLine("Read in the Garden")
    }
```

Verificando múltiplas declarações condicionais com `if`, `else if`

Nas declarações `else if`, as condições são verificadas de cima para baixo; se o primeiro bloco retornar true, o segundo e o terceiro blocos não serão verificados, mas se o primeiro bloco `if` retornar false, o segundo bloco será verificado. Essa verificação continua até que um bloco retorne um resultado verdadeiro.

## Decalaração else

A declaração `else` é a declaração padrão de todas as expressões condicionais, em todas as linguagens de programação. Ou seja, quando todos os `if` e `else if` retornam false (de cima para baixo), então o bloco final (padrão) `else` é executado. A sintaxe da declaração `else` é simplesmente escrever `else` seguido pela declaração padrão entre chaves de abertura e fechamento.

```csharp
using namespace Conditional;

static void Main(string[] args)
 {
     // This method determines what a user should do
     // for the day based on the weather condition

 public void Weather(string myDay)
  {
      // 1st condition
      if (myDay == " Sunny")
      {
          // Decision
          Console.WriteLine("Read in the Library");
      } // 2nd condition
      else if (myday == "Raining")
      {
          //decision
          Console.WriteLine("Read at Home")
      } // 3rd condition
      else if (MyDay == "Cloudy")
      {
          // Decision
          Console.WriteLine("Read in the Garden")
      }
      else
      {
          // Default Decision
          Console.WriteLine("Get some Sleep")
      }
  }
}
```

Exemplo de declaração `else`

Encontre o exemplo executável abaixo:

```csharp
using System;
namespace Conditional {
class Program
    {
    static void Main(string[] args)
        {
        Weather("Sunny");
        Weather("Raining");
        Weather("Cloudy");
        Weather("Unknown");
        }
    public static void Weather(string myDay)
        {
        if (myDay == "Sunny")
            {
            Console.WriteLine("Read in the Library");
            }
        else if (myDay == "Raining")
            {
            Console.WriteLine("Read at Home");
            }
        else if (myDay == "Cloudy")
            {
            Console.WriteLine("Read in the Garden");
            }
        else
            {
            Console.WriteLine("Get some Sleep");
            }
        }
    }
}
```

Execute o exemplo completo para declarações `if-else`.

## switch

`switch` é outra versão da declaração condicional. Ele torna o código mais limpo e legível do que as convencionais declarações `if`, `else if` e `else`. Nas expressões `switch`, cada bloco é terminado por uma palavra-chave `break`. As declarações em `switch` são expressas com `case`s. Para clareza, vamos usar uma declaração `switch` para ilustrar nosso exemplo anterior:

```csharp
using System;
namespace Conditional {
class Program
    {
    static void Main(string[] args)
        {
        int myDay = 4; // setting the value to test
        switch (myDay)
            {
            case 1: Console.WriteLine("Read in the Library"); break;
            case 2: Console.WriteLine("Read at Home"); break;
            case 3: Console.WriteLine("Read in the Garden"); break;
            default: Console.WriteLine("Get some Sleep"); break;
            }
        }
    }
}
```

Execute o exemplo de código de declarações `switch`.

No exemplo acima fornecemos `MyDay = 4`.

Como afirmado anteriormente, a expressão condicional `switch` é uma maneira mais limpa de escrever declarações condicionais. Cada `case` é testado até que um valor verdadeiro seja retornado, então a execução do código atinge a palavra-chave `break`. Se todos os `case`s retornarem false, o bloco `default` é executado. Portanto, a partir do exemplo de código acima, o valor `default` será executado já que nenhum dos casos de teste 1, 2 e 3 retorna true. (O caso verdadeiro nesta expressão é `myDay = 4`.)
