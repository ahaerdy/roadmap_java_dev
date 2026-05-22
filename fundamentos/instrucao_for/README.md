# A Instrução for

A instrução **for** fornece uma maneira compacta de iterar sobre um intervalo de valores. Os programadores frequentemente a chamam de “laço for” por causa da forma como ela repete até que uma condição específica seja satisfeita.

A forma geral da instrução for pode ser expressa da seguinte maneira:

```java
for (initialization; termination; increment) {
    statement(s)
}
```

Ao usar esta versão da instrução for, tenha em mente que:

- A expressão de **inicialização** inicializa o laço; é executada uma vez, quando o laço começa.
- Quando a expressão de **terminação** avalia como falsa, o laço termina.
- A expressão de **incremento** é invocada após cada iteração do laço; é perfeitamente aceitável que esta expressão incremente ou decremente um valor.

O programa a seguir, `ForDemo`, usa a forma geral da instrução for para imprimir os números de 1 a 10 na saída padrão:

```java
class ForDemo {
    public static void main(String[] args){
        for(int i=1; i<11; i++){
            System.out.println("Count is: " + i);
        }
    }
}
```

A saída deste programa é:

```
Count is: 1
Count is: 2
Count is: 3
Count is: 4
Count is: 5
Count is: 6
Count is: 7
Count is: 8
Count is: 9
Count is: 10
```

Observe como o código declara uma variável dentro da expressão de inicialização. O escopo desta variável se estende desde sua declaração até o final do bloco governado pela instrução for, de modo que ela pode ser usada nas expressões de terminação e incremento também. Se a variável que controla uma instrução for não for necessária fora do laço, é melhor declará-la na expressão de inicialização. Os nomes `i`, `j` e `k` são frequentemente usados para controlar laços for; declará-los dentro da expressão de inicialização limita sua vida útil e reduz erros.

As três expressões do laço for são opcionais; um laço infinito pode ser criado da seguinte forma:

```java
// laço infinito
for ( ; ; ) {
    // seu código aqui
}
```

## O for aprimorado

A instrução for também possui outra forma projetada para iteração através de **Collections** e **arrays**. Esta forma é às vezes chamada de **for aprimorado**, e pode ser usada para tornar seus laços mais compactos e fáceis de ler.

Para demonstrar, considere o seguinte array, que contém os números de 1 a 10:

```java
int[] numbers = {1,2,3,4,5,6,7,8,9,10};
```

O programa a seguir, `EnhancedForDemo`, usa o for aprimorado para percorrer o array:

```java
class EnhancedForDemo {
    public static void main(String[] args){
        int[] numbers = {1,2,3,4,5,6,7,8,9,10};
        for (int item : numbers) {
            System.out.println("Count is: " + item);
        }
    }
}
```

Neste exemplo, a variável `item` contém o valor atual do array `numbers`. A saída deste programa é a mesma de antes:

```
Count is: 1
Count is: 2
Count is: 3
Count is: 4
Count is: 5
Count is: 6
Count is: 7
Count is: 8
Count is: 9
Count is: 10
```

Recomendamos usar esta forma da instrução for em vez da forma geral sempre que possível.
