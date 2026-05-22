# Strings e Métodos

## Criando uma String
Strings em Java são objetos. Portanto, você precisa usar o operador `new` para criar um novo objeto String:

>  Em Java, Strings são instâncias da classe java.lang.String, não tipos primitivos, e representam sequências imutáveis de caracteres. Isso significa que, uma vez criada, uma String não pode ser alterada — qualquer modificação gera um novo objeto.

```java
String myString = new String("Hello World");
```

## Literais de String
Forma mais curta de criar uma String:

```java
String myString = "Hello World";
```

Isso é chamado de **literal de String**.

## Caracteres de Escape
Literais de String aceitam caracteres de escape:

| Esc. Char | Descrição |
|-----------|------------|
| `\\`      | Um único caractere barra invertida |
| `\t`      | Tabulação |
| `\r`      | Retorno de carro |
| `\n`      | Nova linha |

Exemplo:

```java
String text = "\tThis text is one tab in.\r\n";
```

## Literais como Constantes ou Singletons
Strings literais iguais podem compartilhar a mesma instância na **String pool** da JVM:

```java
String myString1 = "Hello World";
String myString2 = "Hello World";
```

Ambas apontam para o mesmo objeto.

## Text Blocks
Introduzido no **Java 13**, permite criar Strings multilinha:

```java
String textblock = """
This is a text inside a text block
""";
```

Permite incluir aspas sem escape:

```java
String textblock = """
You can use "quotes" here
""";
```

## Indentação em Text Blocks
A JVM remove indentação com base na posição dos delimitadores finais.

## Concatenação de Strings
Strings são imutáveis. Concatenar cria uma nova String:

```java
String one = "Hello";
String two = "World";
String three = one + " " + two;
```

## ⭐️ Performance de Concatenação
Dentro de loops, use `StringBuilder` para evitar overhead:

### O problema
Strings em Java são **imutáveis**. Se você fizer:

```java
String result = "";
for (int i = 0; i < strings.length; i++) {
    result += strings[i];
}
```

- Cada vez que o operador `+` é usado, uma **nova String** é criada na memória, copiando o conteúdo anterior e adicionando o novo.  
- Em loops grandes, isso gera **muitos objetos temporários**, causando **overhead** (uso excessivo de CPU e memória).

### A solução com StringBuilder

O `StringBuilder` é uma classe **mutável**, projetada para construir Strings de forma eficiente. Usando o `for` tradicional:

```java
StringBuilder temp = new StringBuilder();
for (int i = 0; i < strings.length; i++) {
    temp.append(strings[i]);
}
String result = temp.toString();
```

- `new StringBuilder()` → cria um buffer interno que pode ser modificado.  
- `append(strings[i])` → adiciona cada String ao buffer sem criar novos objetos.  
- `toString()` → converte o resultado final em uma String imutável.

### Vantagens
- **Performance**: evita a criação de múltiplos objetos temporários.  
- **Eficiência em loops**: ideal para concatenação repetitiva.  
- **Flexibilidade**: possui métodos como `insert`, `delete`, `replace`, além de `append`.

### Comparação rápida

| Abordagem | Funcionamento | Performance |
|-----------|---------------|-------------|
| **String +** | Cria nova String a cada concatenação | Lento em loops grandes |
| **StringBuilder** | Usa buffer mutável, concatena sem recriar | Muito mais rápido |
| **StringBuffer** | Igual ao StringBuilder, mas sincronizado (thread-safe) | Mais lento que StringBuilder |


## Comprimento da String
```java
String string = "Hello World";
int length = string.length();
```

## Substrings
```java
String substring = string1.substring(0,5); // "Hello"
```

## Busca em Strings
```java
int index = string1.indexOf("World"); // 6
```

## Comparação de Strings
- `equals()` → compara igualdade exata
- `equalsIgnoreCase()` → ignora maiúsculas/minúsculas
- `startsWith()` / `endsWith()` → verifica prefixo/sufixo
- `compareTo()` → ordem lexicográfica

## Trim
Remove espaços em branco no início e fim:

```java
String trimmed = text.trim();
```

## Replace
```java
String replaced = source.replace('a','@');
```

## replaceFirst / replaceAll
```java
String s = text.replaceFirst("two","five");
String t = text.replaceAll("two","five");
```

## Split
```java
String[] parts = source.split("a");
```

## Conversão de Números para String
```java
String intStr = String.valueOf(10);
```

## Conversão de Objetos para String
```java
Integer integer = new Integer(123);
String intStr = integer.toString();
```

## Obter Caracteres e Bytes
```java
char c = theString.charAt(0);
byte[] bytes = theString.getBytes(Charset.forName("UTF-8"));
```

## Maiúsculas e Minúsculas
```java
String upper = theString.toUpperCase();
String lower = theString.toLowerCase();
```

## Formatação
```java
String input = "Hello %s";
String output = input.formatted("World");
```

## stripIndent
Remove indentação de Strings multilinha.

## translateEscapes
Interpreta códigos de escape dentro da String:

```java
String output = input.translateEscapes();
```
