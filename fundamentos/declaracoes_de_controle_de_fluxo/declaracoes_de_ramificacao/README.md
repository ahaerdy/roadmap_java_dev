# Declarações de Ramificação

## A declaração break

A declaração `break` possui duas formas: rotulada e não rotulada. Você viu a forma não rotulada na discussão anterior sobre a declaração `switch`. Você também pode usar um `break` não rotulado para encerrar um loop `for`, `while` ou `do-while`, como mostrado no seguinte programa BreakDemo:

```java
class BreakDemo {
    public static void main(String[] args) {
        int[] arrayOfInts =  { 32, 87, 3, 589, 12, 1076, 2000, 8, 622, 127 };
        int searchfor = 12;
        int i;
        boolean foundIt = false;

        for (i = 0; i < arrayOfInts.length; i++) {
            if (arrayOfInts[i] == searchfor) {
                foundIt = true;
                break;
            }
        }

        if (foundIt) {
            System.out.println("Found " + searchfor + " at index " + i);
        } else {
            System.out.println(searchfor + " not in the array");
        }
    }
}
```

Este programa procura pelo número 12 em um array. A declaração `break`, mostrada em negrito, encerra o loop `for` quando esse valor é encontrado. O fluxo de controle então é transferido para a declaração após o loop `for`. A saída deste programa é:

```
Found 12 at index 4
```

Um `break` não rotulado encerra o `switch`, `for`, `while` ou `do-while` mais interno, mas um `break` rotulado encerra uma declaração externa. O programa a seguir, BreakWithLabelDemo, é semelhante ao anterior, mas usa loops `for` aninhados para procurar um valor em um array bidimensional. Quando o valor é encontrado, um `break` rotulado encerra o loop externo (rotulado como "search"):

```java
class BreakWithLabelDemo {
    public static void main(String[] args) {
        int[][] arrayOfInts = {
            { 32, 87, 3, 589 },
            { 12, 1076, 2000, 8 },
            { 622, 127, 77, 955 }
        };
        int searchfor = 12;
        int i;
        int j = 0;
        boolean foundIt = false;

        search:
        for (i = 0; i < arrayOfInts.length; i++) {
            for (j = 0; j < arrayOfInts[i].length; j++) {
                if (arrayOfInts[i][j] == searchfor) {
                    foundIt = true;
                    break search;
                }
            }
        }

        if (foundIt) {
            System.out.println("Found " + searchfor + " at " + i + ", " + j);
        } else {
            System.out.println(searchfor + " not in the array");
        }
    }
}
```

Saída do programa:

```
Found 12 at 1, 0
```

A declaração `break` encerra a declaração rotulada; ela não transfere o fluxo de controle para o rótulo. O fluxo de controle é transferido para a declaração imediatamente após a declaração rotulada (encerrada).

## A declaração continue

A declaração `continue` pula a iteração atual de um loop `for`, `while` ou `do-while`. A forma não rotulada pula para o fim do corpo do loop mais interno e avalia a expressão booleana que controla o loop. O programa a seguir, ContinueDemo, percorre uma `String`, contando as ocorrências da letra "p". Se o caractere atual não for um "p", a declaração `continue` pula o restante do loop e prossegue para o próximo caractere. Se for um "p", o programa incrementa a contagem de letras.

```java
class ContinueDemo {
    public static void main(String[] args) {
        String searchMe = "peter piper picked a " + "peck of pickled peppers";
        int max = searchMe.length();
        int numPs = 0;

        for (int i = 0; i < max; i++) {
            // interessado apenas em 'p's
            if (searchMe.charAt(i) != 'p')
                continue;

            // processa 'p's
            numPs++;
        }
        System.out.println("Found " + numPs + " p's in the string.");
    }
}
```

Saída do programa:

```
Found 9 p's in the string.
```

Para ver esse efeito mais claramente, tente remover a declaração `continue` e recompilar. Ao executar o programa novamente, a contagem estará incorreta, dizendo que encontrou 35 "p's" em vez de 9.

Um `continue` rotulado pula a iteração atual de um loop externo marcado com o rótulo fornecido. O programa a seguir, ContinueWithLabelDemo, usa loops aninhados para procurar uma substring dentro de outra string. São necessários dois loops aninhados: um para iterar sobre a substring e outro para iterar sobre a string sendo pesquisada. O programa usa a forma rotulada de `continue` para pular uma iteração no loop externo.

```java
class ContinueWithLabelDemo {
    public static void main(String[] args) {
        String searchMe = "Look for a substring in me";
        String substring = "sub";
        boolean foundIt = false;
        int max = searchMe.length() - substring.length();

        test:
        for (int i = 0; i <= max; i++) {
            int n = substring.length();
            int j = i;
            int k = 0;
            while (n-- != 0) {
                if (searchMe.charAt(j++) != substring.charAt(k++)) {
                    continue test;
                }
            }
            foundIt = true;
            break test;
        }
        System.out.println(foundIt ? "Found it" : "Didn't find it");
    }
}
```

Saída do programa:

```
Found it
```

## A declaração return

A última das declarações de ramificação é a declaração `return`. A declaração `return` sai do método atual, e o fluxo de controle retorna para onde o método foi invocado. A declaração `return` possui duas formas: uma que retorna um valor e outra que não retorna. Para retornar um valor, basta colocar o valor (ou uma expressão que calcula o valor) após a palavra-chave `return`.

```java
return ++count;
```

O tipo de dado do valor retornado deve corresponder ao tipo do valor de retorno declarado do método. Quando um método é declarado `void`, use a forma de `return` que não retorna valor.

```java
return;
```

A lição sobre Classes e Objetos cobrirá tudo o que você precisa saber sobre escrever métodos.
