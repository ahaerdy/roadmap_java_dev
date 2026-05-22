# Strings e Métodos

## Criando uma String
Strings em Java são objetos. Portanto, você precisa usar o operador `new` para criar um novo objeto String:

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

## Performance de Concatenação
Dentro de loops, use `StringBuilder` para evitar overhead:

```java
StringBuilder temp = new StringBuilder();
for(String s : strings) {
    temp.append(s);
}
String result = temp.toString();
```

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
