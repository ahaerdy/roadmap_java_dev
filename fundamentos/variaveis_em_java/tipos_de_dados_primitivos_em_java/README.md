# Tipos de Dados Primitivos

A linguagem de programação Java é de tipagem estática, o que significa que todas as variáveis devem primeiro ser declaradas antes de poderem ser usadas. Isso envolve definir o tipo e o nome da variável, como você já viu:

```java
int gear = 1;

```

Fazer isso informa ao seu programa que existe um campo chamado "gear", que contém dados numéricos e tem um valor inicial de "1". O tipo de dado de uma variável determina os valores que ela pode conter, além das operações que podem ser realizadas nela. Além do `int`, a linguagem de programação Java suporta sete outros tipos de dados primitivos. Um tipo primitivo é predefinido pela linguagem e nomeado por uma palavra-chave reservada. Valores primitivos não compartilham estado com outros valores primitivos. Os oito tipos de dados primitivos suportados pela linguagem de programação Java são:

* **byte**: O tipo de dado `byte` é um inteiro de 8 bits com sinal, usando complemento de dois. Tem um valor mínimo de -128 e um valor máximo de 127 (inclusive). O tipo de dado `byte` pode ser útil para economizar memória em grandes arrays, onde a economia de memória realmente importa. Eles também podem ser usados no lugar de `int` onde seus limites ajudam a esclarecer seu código; o fato de o intervalo de uma variável ser limitado pode servir como uma forma de documentação.
* **short**: O tipo de dado `short` é um inteiro de 16 bits com sinal, usando complemento de dois. Tem um valor mínimo de -32.768 e um valor máximo de 32.767 (inclusive). Como acontece com o `byte`, aplicam-se as mesmas diretrizes: você pode usar um `short` para economizar memória em grandes arrays, em situações onde a economia de memória realmente importa.
* **int**: Por padrão, o tipo de dado `int` é um inteiro de 32 bits com sinal, usando complemento de dois, que tem um valor mínimo de -2^31 e um valor máximo de 2^31-1. No Java SE 8 e posteriores, você pode usar o tipo de dado `int` para representar um inteiro de 32 bits sem sinal, que tem um valor mínimo de 0 e um valor máximo de 2^32-1. Use a classe `Integer` para usar o tipo de dado `int` como um inteiro sem sinal. Consulte a seção *The Number Classes* para obter mais informações. Métodos estáticos como `compareUnsigned`, `divideUnsigned`, etc., foram adicionados à classe `Integer` para oferecer suporte às operações aritméticas para inteiros sem sinal.
* **long**: O tipo de dado `long` é um inteiro de 64 bits, usando complemento de dois. O `long` com sinal tem um valor mínimo de -2^63 e um valor máximo de 2^63-1. No Java SE 8 e posteriores, você pode usar o tipo de dado `long` para representar um `long` sem sinal de 64 bits, que tem um valor mínimo de 0 e um valor máximo de 2^64-1. Use este tipo de dado quando precisar de um intervalo de valores mais amplo do que o fornecido pelo `int`. A classe `Long` também contém métodos como `compareUnsigned`, `divideUnsigned`, etc., para oferecer suporte a operações aritméticas para `long` sem sinal.
* **float**: O tipo de dado `float` é um ponto flutuante de precisão simples de 32 bits IEEE 754. O intervalo de seus valores está além do escopo desta discussão, mas é especificado na seção *Floating-Point Types, Formats, and Values* da *Java Language Specification*. Como acontece com as recomendações para `byte` e `short`, use um `float` (em vez de `double`) se precisar economizar memória em grandes arrays de números de ponto flutuante. Este tipo de dado nunca deve ser usado para valores precisos, como moeda. Para isso, você precisará usar a classe `java.math.BigDecimal` em vez disso. *Numbers and Strings* cobre `BigDecimal` e outras classes úteis fornecidas pela plataforma Java.
* **double**: O tipo de dado `double` é um ponto flutuante de dupla precisão de 64 bits IEEE 754. O intervalo de seus valores está além do escopo desta discussão, mas é especificado na seção *Floating-Point Types, Formats, and Values* da *Java Language Specification*. Para valores decimais, este tipo de dado é geralmente a escolha padrão. Como mencionado acima, este tipo de dado nunca deve ser usado para valores precisos, como moeda.
* **boolean**: O tipo de dado `boolean` tem apenas dois valores possíveis: `true` e `false`. Use este tipo de dado para flags simples que rastreiam condições `true`/`false`. Este tipo de dado representa um bit de informação, mas seu "tamanho" não é algo que seja definido precisamente.
* **char**: O tipo de dado `char` é um caractere Unicode de 16 bits único. Tem um valor mínimo de `'\u0000'` (ou 0) e um valor máximo de `'\uffff'` (ou 65.535 inclusive).

Além dos oito tipos de dados primitivos listados acima, a linguagem de programação Java também oferece suporte especial para sequências de caracteres por meio da classe `java.lang.String`. Colocar sua sequência de caracteres entre aspas duplas criará automaticamente um novo objeto `String`; por exemplo: `String s = "this is a string";`. Objetos `String` são imutáveis, o que significa que, uma vez criados, seus valores não podem ser alterados. A classe `String` não é tecnicamente um tipo de dado primitivo, mas considerando o suporte especial dado a ela pela linguagem, você provavelmente tenderá a pensar nela como tal. Você aprenderá mais sobre a classe `String` em *Simple Data Objects*.

## Valores Padrão

Nem sempre é necessário atribuir um valor quando um campo é declarado. Campos declarados, mas não inicializados, serão definidos com um padrão razoável pelo compilador. De modo geral, esse padrão será zero ou `null`, dependendo do tipo de dado. No entanto, confiar nesses valores padrão é geralmente considerado um estilo de programação ruim.

O gráfico a seguir resume os valores padrão para os tipos de dados acima.

| Tipo de Dado | Valor Padrão (para campos) |
| --- | --- |
| byte | 0 |
| short | 0 |
| int | 0 |
| long | 0L |
| float | 0.0f |
| double | 0.0d |
| char | '\u0000' |
| String (ou qualquer objeto) | null |
| boolean | false |

Variáveis locais são ligeiramente diferentes; o compilador nunca atribui um valor padrão a uma variável local não inicializada. Se você não puder inicializar sua variável local onde ela é declarada, certifique-se de atribuir-lhe um valor antes de tentar usá-la. Acessar uma variável local não inicializada resultará em um erro em tempo de compilação.

## Literais

Você deve ter notado que a palavra-chave `new` não é usada ao inicializar uma variável de um tipo primitivo. Tipos primitivos são tipos de dados especiais integrados à linguagem; eles não são objetos criados a partir de uma classe. Um literal é a representação em código-fonte de um valor fixo; literais são representados diretamente em seu código. Como mostrado abaixo, é possível atribuir um literal a uma variável de um tipo primitivo:

```java
boolean result = true;
char capitalC = 'C';
byte b = 100;
short s = 10000;
int i = 100000;

```

### Literais Inteiros

Um literal inteiro é do tipo `long` se terminar com a letra `L` ou `l`; caso contrário, é do tipo `int`. Recomenda-se que você use a letra maiúscula `L` porque a letra minúscula `l` é difícil de distinguir do dígito `1`.

Valores dos tipos integrais `byte`, `short`, `int` e `long` podem ser criados a partir de literais `int`. Valores do tipo `long` que excedem o intervalo do `int` podem ser criados a partir de literais `long`. Literais inteiros podem ser expressos por estes sistemas numéricos:

* **Decimal**: Base 10, cujos dígitos consistem nos números 0 a 9; este é o sistema numérico que você usa todos os dias.
* **Hexadecimal**: Base 16, cujos dígitos consistem nos números 0 a 9 e nas letras A a F.
* **Binário**: Base 2, cujos dígitos consistem nos números 0 e 1 (você pode criar literais binários no Java SE 7 e posteriores).

Para programação de uso geral, o sistema decimal provavelmente será o único sistema numérico que você usará. No entanto, se precisar usar outro sistema numérico, o exemplo a seguir mostra a sintaxe correta. O prefixo `0x` indica hexadecimal e `0b` indica binário:

```java
// The number 26, in decimal
int decVal = 26;
// The number 26, in hexadecimal
int hexVal = 0x1a;
// The number 26, in binary
int binVal = 0b11010;

```

### Literais de Ponto Flutuante

Um literal de ponto flutuante é do tipo `float` se terminar com a letra `F` ou `f`; caso contrário, seu tipo é `double` e pode opcionalmente terminar com a letra `D` ou `d`.

Os tipos de ponto flutuante (`float` e `double`) também podem ser expressos usando `E` ou `e` (para notação científica), `F` ou `f` (literal `float` de 32 bits) e `D` ou `d` (literal `double` de 64 bits; este é o padrão e, por convenção, é omitido).

```java
double d1 = 123.4;
// same value as d1, but in scientific notation
double d2 = 1.234e2;
float f1 = 123.4f;

```

### Literais de Caractere e String

Literais dos tipos `char` e `String` podem conter quaisquer caracteres Unicode (UTF-16). Se seu editor e sistema de arquivos permitirem, você pode usar tais caracteres diretamente em seu código. Se não, você pode usar um "escape Unicode" como `'\u0108'` (C maiúsculo com acento circunflexo), ou `"S\u00ED Se\u00F1or"` (Sí Señor em espanhol). Sempre use 'aspas simples' para literais `char` e "aspas duplas" para literais `String`. Sequências de escape Unicode podem ser usadas em outros lugares de um programa (como em nomes de campos, por exemplo), não apenas em literais `char` ou `String`.

A linguagem de programação Java também oferece suporte a algumas sequências de escape especiais para literais `char` e `String`: `\b` (backspace), `\t` (tab), `\n` (line feed), `\f` (form feed), `\r` (carriage return), `\"` (aspas duplas), `\'` (aspas simples) e `\\` (barra invertida).

Há também um literal `null` especial que pode ser usado como um valor para qualquer tipo de referência. `null` pode ser atribuído a qualquer variável, exceto variáveis de tipos primitivos. Há pouco que você possa fazer com um valor `null` além de testar sua presença. Portanto, `null` é frequentemente usado em programas como um marcador para indicar que algum objeto está indisponível.

Finalmente, há também um tipo especial de literal chamado literal de classe, formado pegando um nome de tipo e acrescentando `.class`; por exemplo, `String.class`. Isso se refere ao objeto (do tipo `Class`) que representa o próprio tipo.

## Usando Caracteres de Sublinhado em Literais Numéricos

No Java SE 7 e posteriores, qualquer número de caracteres de sublinhado (`_`) pode aparecer em qualquer lugar entre dígitos em um literal numérico. Esse recurso permite, por exemplo, separar grupos de dígitos em literais numéricos, o que pode melhorar a legibilidade do seu código.

Por exemplo, se o seu código contém números com muitos dígitos, você pode usar um caractere de sublinhado para separar dígitos em grupos de três, semelhante a como você usaria um sinal de pontuação como uma vírgula ou um espaço como separador.

O exemplo a seguir mostra outras maneiras de usar o sublinhado em literais numéricos:

```java
long creditCardNumber = 1234_5678_9012_3456L;
long socialSecurityNumber = 999_99_9999L;
float pi = 3.14_15F;
long hexBytes = 0xFF_EC_DE_5E;
long hexWords = 0xCAFE_BABE;
long maxLong = 0x7fff_ffff_ffff_ffffL;
byte nybbles = 0b0010_0101;
long bytes = 0b11010010_01101001_10010100_10010010;

```

Você pode colocar sublinhados apenas entre dígitos; você não pode colocar sublinhados nos seguintes lugares:

* No início ou no fim de um número
* Adjacente a um ponto decimal em um literal de ponto flutuante
* Antes de um sufixo `F` ou `L`
* Em posições onde uma sequência de dígitos é esperada

Os exemplos a seguir demonstram colocações válidas e inválidas de sublinhados em literais numéricos:

```java
// Invalid: cannot put underscores 
// adjacent to a decimal point
float pi1 = 3_.1415F;

// Invalid: cannot put underscores 
// adjacent to a decimal point
float pi2 = 3._1415F;

// Invalid: cannot put underscores 
// prior to an L suffix
long socialSecurityNumber1 = 999_99_9999_L;

// OK (decimal literal)
int x1 = 5_2;

// Invalid: cannot put underscores 
// At the end of a literal
int x2 = 52_;

// OK (decimal literal)
int x3 = 5_______2;

// Invalid: cannot put underscores 
// in the 0x radix prefix
int x4 = 0_x52;

// Invalid: cannot put underscores 
// at the beginning of a number
int x5 = 0x_52;

// OK (hexadecimal literal)
int x6 = 0x5_2;

// Invalid: cannot put underscores 
// at the end of a number
int x7 = 0x52_;

```