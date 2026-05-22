# casting (Conversão) de Tipos em Java

Antes de aprender sobre Conversão de Tipos em Java, certifique-se de conhecer os Tipos de Dados em Java.

## Conversão de Tipos
O processo de converter o valor de um tipo de dado (int, float, double, etc.) para outro tipo de dado é conhecido como **conversão de tipos** (typecasting).

Em Java, existem 13 tipos de conversão de tipos. No entanto, neste tutorial, vamos focar apenas nos 2 principais tipos:

1. Conversão de Tipos Ampliada (Widening Type Casting)  
2. Conversão de Tipos Reduzida (Narrowing Type Casting)

Para aprender sobre outros tipos de conversão, visite **Java Type Conversion** (documentação oficial do Java).

---

## Conversão de Tipos Ampliada

Na Conversão de Tipos Ampliada, o Java converte automaticamente um tipo de dado em outro tipo de dado.

### Exemplo: Convertendo int para double
```java
class Main {
  public static void main(String[] args) {
    // criar variável do tipo int
    int num = 10;
    System.out.println("O valor inteiro: " + num);

    // converter para tipo double
    double data = num;
    System.out.println("O valor double: " + data);
  }
}
```

**Saída:**
```
O valor inteiro: 10
O valor double: 10.0
```

No exemplo acima, estamos atribuindo a variável do tipo int chamada `num` a uma variável do tipo double chamada `data`.  
Aqui, o Java primeiro converte o dado do tipo int em double e, em seguida, o atribui à variável double.

Na Conversão de Tipos Ampliada, o tipo de dado menor (com tamanho menor) é convertido em um tipo de dado maior (com tamanho maior).  
Portanto, **não há perda de dados**. É por isso que esse tipo de conversão acontece automaticamente.

**Nota:** Isso também é conhecido como **Conversão Implícita de Tipos**.

---

## Conversão de Tipos Reduzida

Na Conversão de Tipos Reduzida, nós **manualmente** convertemos um tipo de dado em outro usando parênteses.

### Exemplo: Convertendo double em int
```java
class Main {
  public static void main(String[] args) {
    // criar variável do tipo double
    double num = 10.99;
    System.out.println("O valor double: " + num);

    // converter para tipo int
    int data = (int)num;
    System.out.println("O valor inteiro: " + data);
  }
}
```

**Saída:**
```
O valor double: 10.99
O valor inteiro: 10
```

No exemplo acima, estamos atribuindo a variável do tipo double chamada `num` a uma variável do tipo int chamada `data`.

Observe a linha:
```java
int data = (int)num;
```
Aqui, a palavra-chave `int` dentro dos parênteses indica que a variável `num` foi convertida para o tipo int.

Na Conversão de Tipos Reduzida, os tipos de dados maiores (com tamanho maior) são convertidos em tipos de dados menores (com tamanho menor).  
Portanto, **há perda de dados**. É por isso que esse tipo de conversão não acontece automaticamente.

**Nota:** Isso também é conhecido como **Conversão Explícita de Tipos**.

---

## Outros Exemplos de Conversão de Tipos em Java

### Exemplo 1: Conversão de int para String
```java
class Main {
  public static void main(String[] args) {
    // criar variável do tipo int
    int num = 10;
    System.out.println("O valor inteiro é: " + num);

    // converter int para string
    String data = String.valueOf(num);
    System.out.println("O valor string é: " + data);
  }
}
```

**Saída:**
```
O valor inteiro é: 10
O valor string é: 10
```

No programa acima, observe a linha:
```java
String data = String.valueOf(num);
```
Aqui, usamos o método `valueOf()` da classe String do Java para converter a variável do tipo int em uma string.

---

### Exemplo 2: Conversão de String para int
```java
class Main {
  public static void main(String[] args) {
    // criar variável do tipo string
    String data = "10";
    System.out.println("O valor string é: " + data);

    // converter string para int
    int num = Integer.parseInt(data);
    System.out.println("O valor inteiro é: " + num);
  }
}
```

**Saída:**
```
O valor string é: 10
O valor inteiro é: 10
```

No exemplo acima, observe a linha:
```java
int num = Integer.parseInt(data);
```
Aqui, usamos o método `parseInt()` da classe Integer do Java para converter uma variável do tipo string em uma variável int.

**Nota:** Se a variável string não puder ser convertida em uma variável inteira, ocorre uma exceção chamada **NumberFormatException**.

