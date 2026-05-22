# As instruções while e do-while (The Java™ Tutorials - Oracle)

## A instrução while
A instrução **while** executa continuamente um bloco de instruções enquanto uma determinada condição for verdadeira. Sua sintaxe pode ser expressa como:

```java
while (expression) {
    statement(s)
}
```

A instrução **while** avalia a expressão, que deve retornar um valor booleano.  
Se a expressão for avaliada como verdadeira, a instrução **while** executa as instruções dentro do bloco.  
A instrução **while** continua testando a expressão e executando seu bloco até que a expressão seja avaliada como falsa.

Usar a instrução **while** para imprimir os valores de 1 a 10 pode ser feito como no seguinte programa *WhileDemo*:

```java
class WhileDemo {
    public static void main(String[] args){
        int count = 1;
        while (count < 11) {
            System.out.println("Count is: " + count);
            count++;
        }
    }
}
```

Você pode implementar um loop infinito usando a instrução **while** da seguinte forma:

```java
while (true){
    // seu código vai aqui
}
```

---

## A instrução do-while
A linguagem de programação Java também fornece a instrução **do-while**, que pode ser expressa da seguinte forma:

```java
do {
    statement(s)
} while (expression);
```

A diferença entre **do-while** e **while** é que **do-while** avalia sua expressão no final do loop, em vez do início.  
Portanto, as instruções dentro do bloco **do** são sempre executadas pelo menos uma vez, como mostrado no seguinte programa *DoWhileDemo*:

```java
class DoWhileDemo {
    public static void main(String[] args){
        int count = 1;
        do {
            System.out.println("Count is: " + count);
            count++;
        } while (count < 11);
    }
}
```