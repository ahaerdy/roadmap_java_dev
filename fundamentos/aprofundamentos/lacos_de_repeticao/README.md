# Laços de Repetição

Em programação de computadores, **loops** são usados para repetir um bloco de código. Por exemplo, se você quiser mostrar uma mensagem 100 vezes, em vez de digitar o mesmo código 100 vezes, você pode usar um loop. Em Java, existem três tipos de loops:

- **loops for**
- **loops while**
- **loops do...while**

Este tutorial foca no **floop for**. Você aprenderá sobre os outros tipos de loops nos próximos tutoriais.

### Loop for

O **loop for** em Java é usado para executar um bloco de código por um certo número de vezes. A sintaxe do loop for é:

```
for  (initialExpression; testExpression; updateExpression) {
  // body of the loop
}
```

Aqui,

- **initialExpression** inicializa e/ou declara variáveis e é executado apenas uma vez.
- **testExpression** é avaliada. Se a condição for verdadeira, o corpo do for loop é executado.
- **updateExpression** atualiza o valor de initialExpression.
- A condição é avaliada novamente. O processo continua até que a condição seja falsa.

#### Exemplo 1: Exibir um Texto Cinco Vezes

```java
// Program to print a text 5 times
class Main {
  public static void main(String[] args) {
    int  n =  5;

    // for loop
    for  (int  i =  1; i \u003C= n; \u002B\u002Bi) {
      System.out.println(\u0022Java is fun\u0022);
    }
  }
}
```

**Saída:**

```
Java is fun
Java is fun
Java is fun
Java is fun
Java is fun
```

Como o programa funciona:

| Iteração | Variável | Condição: i | Ação |
|---|---:|---|---|
| 1ª | i = 1 | n = 5 true | **Java is fun** é impresso. i é incrementado para 2. |
| 2ª | i = 2 | n = 5 true | **Java is fun** é impresso. i é incrementado para 3. |
| 3ª | i = 3 | n = 5 true | **Java is fun** é impresso. i é incrementado para 4. |
| 4ª | i = 4 | n = 5 true | **Java is fun** é impresso. i é incrementado para 5. |
| 5ª | i = 5 | n = 5 true | **Java is fun** é impresso. i é incrementado para 6. |
| 6ª | i = 6 | n = 5 false | O loop é terminado. |

#### Exemplo 2: Exibir números de 1 a 5

```java
// Program to print numbers from 1 to 5
class Main {
  public static void main(String[] args) {
    int  n =  5;

    // for loop
    for  (int  i =  1; i \u003C= n; \u002B\u002Bi) {
      System.out.println(i);
    }
  }
}
```

**Saída:**

```
1
2
3
4
5
```

Como o programa funciona:

| Iteração | Variável | Condição: i | Ação |
|---|---:|---|---|
| 1ª | i = 1 | n = 5 true | **1** é impresso. i é incrementado para 2. |
| 2ª | i = 2 | n = 5 true | **2** é impresso. i é incrementado para 3. |
| 3ª | i = 3 | n = 5 true | **3** é impresso. i é incrementado para 4. |
| 4ª | i = 4 | n = 5 true | **4** é impresso. i é incrementado para 5. |
| 5ª | i = 5 | n = 5 true | **5** é impresso. i é incrementado para 6. |
| 6ª | i = 6 | n = 5 false | O loop é terminado. |

#### Exemplo 3: Exibir a Soma dos primeiros n Números Naturais

```java
// Program to find the sum of natural numbers from 1 to 1000.
class Main {
  public static void main(String[] args) {
    int  sum =  0;
    int  n =  1000;

    // for loop
    for  (int  i =  1; i \u003C= n; \u002B\u002Bi) {
      // body inside for loop
      sum \u002B= i;      // sum = sum \u002B i
    }

    System.out.println(\u0022Sum = \u0022  \u002B sum);
  }
}
```

**Saída:**

```
Sum = 500500
```

Aqui, o valor de **sum** é 0 inicialmente. Então, o for loop é iterado de **i = 1** até **1000**. Em cada iteração, **i** é adicionado a **sum** e seu valor é incrementado em 1. Quando **i** se torna **1001**, a condição de teste é falsa e **sum** será igual a **0 + 1 + 2 + ... + 1000**.

O programa acima para somar números naturais também pode ser escrito como:

```java
// Program to find the sum of natural numbers from 1 to 1000.
class Main {
  public static void main(String[] args) {
    int  sum =  0;
    int  n =  1000;

    // for loop
    for  (int  i = n; i \u003E=  1; --i) {
      // body inside for loop
      sum \u002B= i;      // sum = sum \u002B i
    }

    System.out.println(\u0022Sum = \u0022  \u002B sum);
  }
}
```

A Saída: deste programa é a mesma do Exemplo 3.

### Loop for-each

O loop **for** em Java tem uma sintaxe alternativa que facilita iterar por arrays e coleções. Por exemplo,

```java
// print array elements
class Main {
  public static void main(String[] args) {
    // create an array
    int[] numbers = {3,  7,  5, -5};

    // iterating through the array
    for  (int  number: numbers) {
      System.out.println(number);
    }
  }
}
```

**Saída:**

```
3
7
5
-5
```

Aqui, usamos o **for-each loop** para imprimir cada elemento do array **numbers** um por um. Na primeira iteração do loop, **number** será **3**, **number** será **7** na segunda iteração e assim por diante.

Para aprender mais, visite **Java for-each Loop**.

### Loop for Infinito

Se definirmos a expressão de teste de forma que ela nunca avalie para falsa, o for loop executará para sempre. Isso é chamado de **infinite for loop**. Por exemplo,

```java
// Infinite for Loop
class Infinite {
  public static void main(String[] args) {
    int  sum =  0;
    for  (int  i =  1; i \u003C=  10; --i) {
      System.out.println(\u0022Hello\u0022);
    }
  }
}
```

Aqui, a expressão de teste, **i \u003C= 10**, nunca é falsa e **Hello** é impresso repetidamente até que a memória se esgote.

