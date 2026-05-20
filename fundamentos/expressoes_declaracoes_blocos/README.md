# Expressões, Declarações e Blocos

## Expressões
Uma expressão é uma construção composta de variáveis, operadores e invocações de métodos, que são construídas de acordo com a sintaxe da linguagem, e que resulta em um único valor. Você já viu exemplos de expressões, ilustrados em negrito abaixo:

```java
int cadence = 0;
anArray[0] = 100;
System.out.println("Element 1 at index 0: " + anArray[0]);
int result = 1 + 2; // result agora é 3
if (value1 == value2)
    System.out.println("value1 == value2");
```

O tipo de dado do valor retornado por uma expressão depende dos elementos usados na expressão. A expressão `cadence = 0` retorna um `int` porque o operador de atribuição retorna um valor do mesmo tipo de dado que seu operando à esquerda; neste caso, `cadence` é um `int`. Como você pode ver em outras expressões, uma expressão pode retornar outros tipos de valores também, como `boolean` ou `String`.

A linguagem de programação Java permite construir expressões compostas a partir de várias expressões menores, desde que o tipo de dado exigido por uma parte da expressão corresponda ao tipo de dado da outra. Aqui está um exemplo de expressão composta:

```java
1 * 2 * 3
```

Neste exemplo específico, a ordem em que a expressão é avaliada não importa porque o resultado da multiplicação é independente da ordem; o resultado é sempre o mesmo, não importa em que ordem você aplique as multiplicações. No entanto, isso não é verdade para todas as expressões. Por exemplo, a seguinte expressão dá resultados diferentes, dependendo de você realizar a adição ou a divisão primeiro:

```java
x + y / 100    // ambíguo
```

Você pode especificar exatamente como uma expressão será avaliada usando parênteses balanceados: `(` e `)`. Por exemplo, para tornar a expressão anterior não ambígua, você poderia escrever:

```java
(x + y) / 100  // não ambíguo, recomendado
```

Se você não indicar explicitamente a ordem das operações a serem realizadas, a ordem é determinada pela precedência atribuída aos operadores usados na expressão. Operadores com maior precedência são avaliados primeiro. Por exemplo, o operador de divisão tem maior precedência do que o operador de adição. Portanto, as duas instruções seguintes são equivalentes:

```java
x + y / 100
x + (y / 100) // não ambíguo, recomendado
```

Ao escrever expressões compostas, seja explícito e indique com parênteses quais operadores devem ser avaliados primeiro. Essa prática torna o código mais fácil de ler e manter.

---

## Declarações
Declarações são aproximadamente equivalentes a sentenças em linguagens naturais. Uma declaração forma uma unidade completa de execução. Os seguintes tipos de expressões podem se tornar uma declaração ao terminar a expressão com um ponto e vírgula (`;`):

- Expressões de atribuição  
- Qualquer uso de `++` ou `--`  
- Invocações de métodos  
- Expressões de criação de objetos  

Tais declarações são chamadas de **declarações de expressão**. Aqui estão alguns exemplos:

```java
// declaração de atribuição
aValue = 8933.234;

// declaração de incremento
aValue++;

// declaração de invocação de método
System.out.println("Hello World!");

// declaração de criação de objeto
Bicycle myBike = new Bicycle();
```

Além das declarações de expressão, existem dois outros tipos de declarações: **declarações de variável** e **declarações de controle de fluxo**.

Uma declaração de variável declara uma variável. Você já viu muitos exemplos:

```java
// declaração de variável
double aValue = 8933.234;
```

Finalmente, as declarações de controle de fluxo regulam a ordem em que as declarações são executadas. Você aprenderá sobre elas na próxima seção, **Declarações de Controle de Fluxo**.

---

## 💡 Diferença entre `Declaração` e `Expressão` 

A diferença essencial entre **expressão** e **declaração** em Java está no papel que cada uma desempenha dentro do código:

- **Expressão**:  
  - É uma combinação de variáveis, operadores e chamadas de métodos que resulta em um **valor único**.  
  - Exemplo: `1 + 2`, `x * y`, `System.out.println("Olá")`.  
  - Uma expressão pode ser parte de uma declaração, mas por si só não é considerada uma unidade completa de execução.

- **Declaração**:  
  - É uma **unidade completa de execução** no programa.  
  - Pode ser formada por uma expressão seguida de ponto e vírgula (como `aValue++ ;`), ou por outros tipos como declarações de variável (`int x = 5;`) e declarações de controle de fluxo (`if`, `for`, `while`).  
  - Uma declaração pode conter uma ou mais expressões, mas vai além delas, pois define uma ação completa que o programa executa.

👉 Quando você escreve `cadence = 0`; **com ponto e vírgula**, ela deixa de ser apenas uma expressão e passa a ser uma declaração de expressão — ou seja, uma instrução completa que o programa executa.

👉 Em resumo: a **expressão** calcula ou retorna um valor, enquanto a **declaração** representa uma instrução completa que o programa executa.

---

## Blocos
Um bloco é um grupo de zero ou mais declarações entre chaves balanceadas e pode ser usado em qualquer lugar onde uma única declaração é permitida. O exemplo a seguir, **BlockDemo**, ilustra o uso de blocos:

```java
class BlockDemo {
    public static void main(String[] args) {
        boolean condition = true;
        if (condition) {  // início do bloco 1
            System.out.println("Condition is true.");
        }  // fim do bloco 1
        else {  // início do bloco 2
            System.out.println("Condition is false.");
        }  // fim do bloco 2
    }
}
```