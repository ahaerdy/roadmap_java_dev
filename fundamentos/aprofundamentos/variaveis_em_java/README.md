# Variáveis em Java

Uma variável em Java é um pedaço de memória que pode conter um valor de dado. Assim, uma variável possui um tipo de dado. Tipos de dados são abordados em mais detalhes no texto sobre tipos de dados em Java. Variáveis são tipicamente usadas para armazenar informações que seu programa Java precisa para executar sua tarefa. Isso pode ser qualquer tipo de informação, desde textos, códigos (por exemplo, códigos de país, códigos de moeda etc.) até números, resultados temporários de cálculos de múltiplas etapas etc.

No exemplo de código abaixo, o método `main()` contém a declaração de uma única variável inteira chamada `number`. O valor da variável inteira é primeiro definido como 10, e depois 20 é adicionado à variável.

```java
public class MyClass {
    public static void main(String[] args) {
        int number = 10;
        number = number + 20;
    }
}
```

## Tipos de Variáveis em Java

Em Java existem quatro tipos de variáveis:

- Campos não estáticos  
- Campos estáticos  
- Variáveis locais  
- Parâmetros  

Um campo não estático é uma variável que pertence a um objeto. Objetos mantêm seu estado interno em campos não estáticos. Campos não estáticos também são chamados de variáveis de instância, porque pertencem a instâncias (objetos) de uma classe. Campos não estáticos são abordados em mais detalhes no texto sobre campos em Java.

Um campo estático é uma variável que pertence a uma classe. Um campo estático tem o mesmo valor para todos os objetos que o acessam. Campos estáticos também são chamados de variáveis de classe. Campos estáticos também são abordados em mais detalhes no texto sobre campos em Java.

Uma variável local é uma variável declarada dentro de um método. Uma variável local só é acessível dentro do método que a declarou. Variáveis locais são abordadas em mais detalhes no texto sobre métodos em Java.

Um parâmetro é uma variável passada para um método quando o método é chamado. Parâmetros também só são acessíveis dentro do método que os declara, embora um valor seja atribuído a eles quando o método é chamado. Parâmetros também são abordados em mais detalhes no texto sobre métodos em Java.

## Declaração de Variáveis em Java

A forma exata como uma variável é declarada depende do tipo de variável (não estática, estática, local, parâmetro). No entanto, existem certas similaridades. Em Java você declara uma variável assim:

```
type name;
```

Em vez da palavra `type`, você escreve o tipo de dado da variável. Similarmente, em vez da palavra `name` você escreve o nome que deseja dar à variável.

Exemplo declarando uma variável chamada `myVariable` do tipo `int`:

```java
int myVariable;
```

Exemplos de como declarar variáveis de todos os tipos primitivos em Java:

```java
byte    myByte;
short   myShort;
char    myChar;
int     myInt;
long    myLong;
float   myFloat;
double  myDouble;
```

Exemplos de como declarar variáveis de tipos objeto em Java:

```java
Byte       myByte;
Short      myShort;
Character  myChar;
Integer    myInt;
Long       myLong;
Float      myFloat;
Double     myDouble;
String     myString;
```

Note a letra maiúscula inicial dos tipos objeto. Quando uma variável aponta para um objeto, a variável é chamada de “referência” a um objeto. Voltarei à diferença entre valores de variáveis primitivas e referências de objetos em um texto posterior.

As regras e convenções para escolher nomes de variáveis são abordadas mais adiante neste texto.

## Atribuição de Variáveis em Java

Atribuir um valor a uma variável em Java segue este padrão:

```
variableName = value;
```

Exemplos concretos:

```java
myByte   = 127;
myFloat  = 199.99;
myString = "This is a text";
```

A primeira linha atribui o valor `127` à variável `myByte`.  
A segunda linha atribui o valor `199.99` à variável `myFloat`.  
A terceira linha atribui o valor `"This is a text"` à variável `myString`.

Você também pode atribuir um valor a uma variável já no momento da declaração:

```java
byte   myByte   = 127;
float  myFloat  = 199.99;
String myString = "string value";
```

## Leitura de Variáveis em Java

Você pode ler o valor de uma variável Java escrevendo seu nome em qualquer lugar onde uma variável ou constante possa ser usada no código. Por exemplo, no lado direito de uma atribuição, como parâmetro em uma chamada de método ou dentro de uma expressão aritmética.

```java
float myFloat1 = 199.99;
float myFloat2 = myFloat1;           // lado direito em atribuição
float myFloat3 = myFloat2 + 123.45;  // parte de expressão aritmética
System.out.println(myFloat3);        // parâmetro em chamada de método
```

## Convenções de Nomenclatura de Variáveis em Java

Existem algumas regras e convenções relacionadas à nomenclatura de variáveis:

**Regras:**
- Nomes de variáveis em Java são sensíveis a maiúsculas/minúsculas. `money` não é o mesmo que `Money` ou `MONEY`.  
- Nomes de variáveis devem começar com uma letra, ou os caracteres `$` ou `_`.  
- Após o primeiro caractere, o nome pode conter números, além de letras, `$` e `_`.  
- Nomes de variáveis não podem ser iguais a palavras reservadas em Java (por exemplo, `int`, `for`).  

Exemplos válidos de nomes de variáveis:

```
myvar
myVar
MYVAR
_myVar
$myVar
myVar1
myVar_1
```

**Convenções:**
- Nomes de variáveis são escritos em minúsculas (ex.: `variable`, `apple`).  
- Se o nome tiver múltiplas palavras, cada palavra após a primeira começa com letra maiúscula (ex.: `variableName`, `bigApple`).  
- Embora permitido, normalmente não se inicia nomes de variáveis com `$` ou `_`.  
- Campos `static final` (constantes) são escritos em maiúsculas, com `_` separando palavras (ex.: `EXCHANGE_RATE`, `COEFFICIENT`).  

## Inferência de Tipo de Variável Local em Java

A partir do Java 10 é possível que o compilador infira o tipo de uma variável local a partir do valor atribuído a ela na declaração. Essa melhoria é restrita a variáveis locais, índices em loops `for-each` e variáveis locais declaradas em `for-loops`.

Exemplo antes do Java 10:

```java
String myVar = "A string!";
```

Exemplo a partir do Java 10 usando inferência de tipo:

```java
var myVar = "A string!";
```

Note o uso da palavra-chave `var` em vez do tipo `String`. O compilador deduz que o tipo da variável deve ser `String`.

Mais exemplos:

```java
var list = new ArrayList();
var myNum = new Integer(123);
var myClassObj = new MyClass();
```

---

**Próximo:** Variáveis em Java contêm dados primitivos (por exemplo, inteiros, chars, floats, boolean etc.) ou referências a objetos Java. Este tutorial explica como declarar, ler e escrever valores de variáveis em Java.
