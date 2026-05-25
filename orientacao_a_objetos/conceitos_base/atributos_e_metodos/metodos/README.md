# Métodos em Java

Os métodos são onde você coloca as operações sobre dados (variáveis) em seu código. Em outras palavras, você agrupa operações (código) dentro de métodos. Os métodos devem estar localizados dentro de uma classe. Métodos são semelhantes ao que é chamado de funções ou procedimentos em outras linguagens de programação (por exemplo, Pascal ou JavaScript).  

Um método é um grupo de instruções que executa alguma operação sobre alguns dados e pode ou não retornar um resultado.  

Aqui está um exemplo simples de método:

```java
public MyClass{
    public void writeText(String text) {
        System.out.print(text);   // imprime o parâmetro text em System.out.
    }
}
```

O exemplo acima define um método chamado `writeText` dentro de uma classe chamada `MyClass`. O método recebe um único parâmetro chamado `text`. Esse parâmetro é usado na instrução dentro do método. O método não retorna nenhum valor.  

Nas seções seguintes explicarei o que cada um dos elementos na definição do método acima significa.

---

## Parâmetros de Método

Parâmetros de método tornam possível passar valores para o método, sobre os quais o método pode operar. Os parâmetros do método são declarados dentro dos parênteses após o nome do método.  

No exemplo abaixo os parâmetros do método estão em negrito:

```java
public void writeText(String text1, String text2) {
    System.out.print(text1);
    System.out.print(text2);
}
```

O método `writeText` no exemplo acima recebe dois parâmetros chamados `text1` e `text2`. Ambos são do tipo `String`, como escrito antes de cada nome de parâmetro. Você pode usar qualquer tipo primitivo ou classe interna do Java como tipo de dado para parâmetros. Também pode usar suas próprias classes como tipos de parâmetro.

---

## Parâmetros vs. Variáveis

Um parâmetro de método é semelhante a uma variável. Você pode ler seu valor e também alterá-lo.  

Exemplo:

```java
public MyClass{
    public void writeText(String text1, String text2) {
        System.out.print(text1);    // lê o valor de text1
        System.out.print(text2);    // lê o valor de text2
        text1 = "new value 1";      // altera o valor de text1
        text2 = "new value 2";      // altera o valor de text2
    }
}
```

⚠️ Atenção: embora seja possível alterar o valor dos parâmetros, isso pode levar a código confuso. Se não tiver certeza, crie uma variável local para armazenar o valor e deixe o parâmetro intacto.

Chamando o método `writeText()`:

```java
MyClass myClassObj = new MyClass();
myClassObj.writeText("Hello", "World");
```

---

## Parâmetros `final`

Um parâmetro de método Java pode ser declarado como `final`. O valor de um parâmetro `final` não pode ser alterado. Se o parâmetro for uma referência a um objeto, a referência não pode ser modificada, mas os valores dentro do objeto ainda podem ser alterados.

```java
public void writeText(final String text1, final String text2) {
    System.out.print(text1);
    System.out.print(text2);
}
```

---

## Variáveis Locais

Você pode declarar variáveis locais dentro de um método. Elas só são acessíveis dentro do escopo do método.

```java
public void writeText() {
    int localVariable1 = 1;
    int localVariable2 = 2;
    System.out.println(localVariable1 + localVariable2);
}
```

Variáveis locais também podem ser `final`.

---

## Tipos de Retorno de Método

Um método Java pode retornar um valor:

```java
public int sum(int value1, int value2) {
    return value1 + value2;
}
```

Esse método soma os dois parâmetros e retorna o resultado. O tipo de retorno `int` indica que o método retorna um inteiro.  

Outro exemplo:

```java
public String concat(String string1, String string2) {
    return string1 + string2;
}
```

---

## Múltiplos `return`

É possível ter mais de uma instrução `return` em um método, mas apenas uma será executada.

```java
public String concat(String string1, String string2, boolean reverseOrder){
    if(reverseOrder) {
        return string2 + string1;
    }
    return string1 + string2;
}
```

---

## Modificadores de Acesso

A palavra `public` usada nos exemplos é o modificador de acesso do método. Ele determina qual código pode chamar esse método.  

---

## Declarações de Exceção

Se ocorrer um erro dentro de um método, ele pode lançar uma exceção. Exemplo:

```java
public String concat(String string1, String string2) throws MyException {
    if(string1 == null) {
        throw new MyException("string1 was null");
    }
    if(string2 == null) {
        throw new MyException("string2 was null");
    }
    return string1 + string2;
}
```

---

## Chamando Métodos

Veja estes dois métodos:

```java
public void callSum() {
    int theSum = add(1, 3);
    System.out.print(theSum);
}

public int add(int value1, int value2) {
    return value1 + value2;
}
```

O método `callSum()` cria uma variável `theSum` e atribui a ela o valor retornado pela chamada `add(1, 3)`. Depois imprime o valor.  

Os métodos podem ser usados para dividir o código em segmentos menores, mais compreensíveis e reutilizáveis, em vez de escrever seu programa como um único método grande.
