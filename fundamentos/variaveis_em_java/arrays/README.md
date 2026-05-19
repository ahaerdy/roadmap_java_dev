## Arrays

Um array é um objeto contêiner que armazena um número fixo de valores de um único tipo. O comprimento de um array é estabelecido quando o array é criado. Após a criação, seu comprimento é fixo. Você já viu um exemplo de arrays no método `main` da aplicação "Hello World!". Esta seção discute arrays em maior detalhe.

<p align="center">
  <img src="000-Midia_e_Anexos/2026-05-19-14-05-42.png" alt="" width="480">
</p>

### Um array de 10 elementos

Cada item em um array é chamado de elemento, e cada elemento é acessado por seu índice numérico. Conforme mostrado na ilustração anterior, a numeração começa em 0. O 9º elemento, por exemplo, seria acessado no índice 8.

O programa a seguir, `ArrayDemo`, cria um array de inteiros, coloca alguns valores nele e imprime cada valor na saída padrão:

```java
class ArrayDemo {
    public static void main(String[] args) {
        // declara um array de inteiros
        int[] anArray;

        // aloca memória para 10 inteiros
        anArray = new int[10];

        // inicializa elementos
        anArray[0] = 100;
        anArray[1] = 200;
        anArray[2] = 300;
        anArray[3] = 400;
        anArray[4] = 500;
        anArray[5] = 600;
        anArray[6] = 700;
        anArray[7] = 800;
        anArray[8] = 900;
        anArray[9] = 1000;

        System.out.println("Element at index 0: " + anArray[0]);
        System.out.println("Element at index 1: " + anArray[1]);
        System.out.println("Element at index 2: " + anArray[2]);
        System.out.println("Element at index 3: " + anArray[3]);
        System.out.println("Element at index 4: " + anArray[4]);
        System.out.println("Element at index 5: " + anArray[5]);
        System.out.println("Element at index 6: " + anArray[6]);
        System.out.println("Element at index 7: " + anArray[7]);
        System.out.println("Element at index 8: " + anArray[8]);
        System.out.println("Element at index 9: " + anArray[9]);
    }
}
```

**Saída:**
```
Element at index 0: 100
Element at index 1: 200
Element at index 2: 300
Element at index 3: 400
Element at index 4: 500
Element at index 5: 600
Element at index 6: 700
Element at index 7: 800
Element at index 8: 900
Element at index 9: 1000
```

Em situações reais, você provavelmente usaria uma estrutura de repetição para percorrer cada elemento do array, em vez de escrever cada linha individualmente. No entanto, o exemplo ilustra claramente a sintaxe de arrays. Você aprenderá sobre estruturas de repetição (`for`, `while`, `do-while`) na seção **Fluxo de Controle**.

---

## Declarando uma variável para referenciar um array

O programa anterior declara um array (`anArray`) com a seguinte linha:

```java
int[] anArray;
```

Assim como declarações de variáveis de outros tipos, uma declaração de array tem dois componentes: o tipo do array e o nome do array. O tipo é escrito como `tipo[]`, onde `tipo` é o tipo dos elementos contidos. Os colchetes indicam que a variável contém um array. O tamanho não faz parte do tipo.

Você pode declarar arrays de outros tipos:

```java
byte[] anArrayOfBytes;
short[] anArrayOfShorts;
long[] anArrayOfLongs;
float[] anArrayOfFloats;
double[] anArrayOfDoubles;
boolean[] anArrayOfBooleans;
char[] anArrayOfChars;
String[] anArrayOfStrings;
```

Também é possível colocar os colchetes após o nome do array (forma desencorajada):

```java
float anArrayOfFloats[];
```

---

## Criando, inicializando e acessando um array

Uma forma de criar um array é com o operador `new`:

```java
anArray = new int[10];
```

Se essa instrução estiver ausente, o compilador gera erro:  
`Variable anArray may not have been initialized.`

Você pode inicializar elementos individualmente ou usar a sintaxe abreviada:

```java
int[] anArray = {100, 200, 300, 400, 500, 600, 700, 800, 900, 1000};
```

---

## Arrays multidimensionais

Você pode declarar arrays de arrays (multidimensionais):

```java
String[][] names;
```

Exemplo:

```java
class MultiDimArrayDemo {
    public static void main(String[] args) {
        String[][] names = {
            {"Mr. ", "Mrs. ", "Ms. "},
            {"Smith", "Jones"}
        };
        System.out.println(names[0][0] + names[1][0]); // Mr. Smith
        System.out.println(names[0][2] + names[1][1]); // Ms. Jones
    }
}
```

**Saída:**
```
Mr. Smith
Ms. Jones
```

---

## Propriedade `length`

Você pode usar `length` para determinar o tamanho de qualquer array:

```java
System.out.println(anArray.length);
```

---

## Copiando arrays

A classe `System` possui o método `arraycopy`:

```java
public static void arraycopy(Object src, int srcPos, Object dest, int destPos, int length)
```

Exemplo:

```java
class ArrayCopyDemo {
    public static void main(String[] args) {
        String[] copyFrom = {
            "Affogato", "Americano", "Cappuccino", "Corretto", "Cortado",
            "Doppio", "Espresso", "Frappucino", "Freddo", "Lungo",
            "Macchiato", "Marocchino", "Ristretto"
        };

        String[] copyTo = new String[7];
        System.arraycopy(copyFrom, 2, copyTo, 0, 7);

        for (String coffee : copyTo) {
            System.out.print(coffee + " ");
        }
    }
}
```

**Saída:**
```
Cappuccino Corretto Cortado Doppio Espresso Frappucino Freddo
```

---

## Manipulações de arrays

A classe `java.util.Arrays` fornece métodos úteis:

- `copyOfRange` – copia intervalos de arrays.
- `binarySearch` – busca valores.
- `equals` – compara arrays.
- `fill` – preenche arrays.
- `sort` / `parallelSort` – ordena arrays.
- `stream` – cria streams a partir de arrays.
- `toString` – converte arrays em string.

Exemplo com `copyOfRange`:

```java
class ArrayCopyOfDemo {
    public static void main(String[] args) {
        String[] copyFrom = {
            "Affogato", "Americano", "Cappuccino", "Corretto", "Cortado",
            "Doppio", "Espresso", "Frappucino", "Freddo", "Lungo",
            "Macchiato", "Marocchino", "Ristretto"
        };

        String[] copyTo = java.util.Arrays.copyOfRange(copyFrom, 2, 9);

        for (String coffee : copyTo) {
            System.out.print(coffee + " ");
        }
    }
}
```

**Saída:**
```
Cappuccino Corretto Cortado Doppio Espresso Frappucino Freddo
```
