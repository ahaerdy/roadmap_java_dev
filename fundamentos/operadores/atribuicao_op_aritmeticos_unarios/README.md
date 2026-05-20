
# Atribuição, Operadores Aritméticos e Unários 
## O Operador de Atribuição Simples

Um dos operadores mais comuns que você encontrará é o operador de atribuição simples `"="`. Você viu esse operador na classe `Bicycle`; ele atribui o valor à sua direita ao operando à sua esquerda:

```java
int cadence = 0;
int speed = 0;
int gear = 1;
```

Esse operador também pode ser usado em objetos para atribuir referências de objetos, conforme discutido em **Criando Objetos**.

---

## Os Operadores Aritméticos

A linguagem de programação Java fornece operadores que realizam adição, subtração, multiplicação e divisão. Há uma boa chance de você reconhecê-los por seus equivalentes na matemática básica. O único símbolo que pode parecer novo é `"%"`, que divide um operando por outro e retorna o resto como resultado.

| Operador | Descrição |
|----------|-----------|
| +        | Operador aditivo (também usado para concatenação de Strings) |
| -        | Operador de subtração |
| *        | Operador de multiplicação |
| /        | Operador de divisão |
| %        | Operador de resto |

O programa a seguir, `ArithmeticDemo`, testa os operadores aritméticos:

```java
class ArithmeticDemo {
    public static void main (String[] args) {
        int result = 1 + 2; // result agora é 3
        System.out.println("1 + 2 = " + result);

        int original_result = result;
        result = result - 1; // result agora é 2
        System.out.println(original_result + " - 1 = " + result);

        original_result = result;
        result = result * 2; // result agora é 4
        System.out.println(original_result + " * 2 = " + result);

        original_result = result;
        result = result / 2; // result agora é 2
        System.out.println(original_result + " / 2 = " + result);

        original_result = result;
        result = result + 8; // result agora é 10
        System.out.println(original_result + " + 8 = " + result);

        original_result = result;
        result = result % 7; // result agora é 3
        System.out.println(original_result + " % 7 = " + result);
    }
}
```

Este programa imprime:

```
1 + 2 = 3
3 - 1 = 2
2 * 2 = 4
4 / 2 = 2
2 + 8 = 10
10 % 7 = 3
```

Você também pode combinar os operadores aritméticos com o operador de atribuição simples para criar atribuições compostas. Por exemplo, `x+=1;` e `x=x+1;` ambos incrementam o valor de `x` em 1.

O operador `+` também pode ser usado para concatenar (juntar) duas strings, como mostrado no programa `ConcatDemo`:

```java
class ConcatDemo {
    public static void main(String[] args){
        String firstString = "This is";
        String secondString = " a concatenated string.";
        String thirdString = firstString + secondString;
        System.out.println(thirdString);
    }
}
```

Ao final deste programa, a variável `thirdString` contém `"This is a concatenated string."`, que é impressa na saída padrão.

---

## Os Operadores Unários

Os operadores unários requerem apenas um operando; eles realizam várias operações, como incrementar/decrementar um valor em um, negar uma expressão ou inverter o valor de um booleano.

| Operador | Descrição |
|----------|-----------|
| +        | Operador unário de mais; indica valor positivo (números já são positivos sem isso) |
| -        | Operador unário de menos; nega uma expressão |
| ++       | Operador de incremento; incrementa um valor em 1 |
| --       | Operador de decremento; decrementa um valor em 1 |
| !        | Operador de complemento lógico; inverte o valor de um booleano |

O programa a seguir, `UnaryDemo`, testa os operadores unários:

```java
class UnaryDemo {
    public static void main(String[] args) {
        int result = +1; // result agora é 1
        System.out.println(result);

        result--; // result agora é 0
        System.out.println(result);

        result++; // result agora é 1
        System.out.println(result);

        result = -result; // result agora é -1
        System.out.println(result);

        boolean success = false; // false
        System.out.println(success);

        // true
        System.out.println(!success);
    }
}
```

Os operadores de incremento/decremento podem ser aplicados antes (prefixo) ou depois (pós-fixo) do operando. O código `result++;` e `++result;` terminará com `result` incrementado em um. A única diferença é que a versão de prefixo (`++result`) avalia para o valor incrementado, enquanto a versão de pós-fixo (`result++`) avalia para o valor original. Se você estiver apenas realizando um incremento/decremento simples, não importa qual versão escolher. Mas se usar esse operador como parte de uma expressão maior, a escolha pode fazer uma diferença significativa.

O programa a seguir, `PrePostDemo`, ilustra o operador unário de incremento prefixo/pós-fixo:

```java
class PrePostDemo {
    public static void main(String[] args){
        int i = 3;
        i++;                // imprime 4
        System.out.println(i);

        ++i;                // imprime 5
        System.out.println(i);

        // imprime 6
        System.out.println(++i);

        // imprime 6
        System.out.println(i++);

        // imprime 7
        System.out.println(i);
    }
}
```
