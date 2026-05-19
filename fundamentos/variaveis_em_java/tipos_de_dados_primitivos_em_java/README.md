# Tipos de Dados Primitivos

A linguagem de programação Java é de tipagem estática, o que significa que todas as variáveis devem ser declaradas antes de serem usadas. Isso envolve definir o tipo e o nome da variável, como você já viu:

```java
int gear = 1;

```

Fazer isso diz ao seu programa que um campo chamado "gear" existe, armazena dados numéricos e tem um valor inicial de "1". O tipo de dado de uma variável determina os valores que ela pode conter, além das operações que podem ser realizadas sobre ela. Além do `int`, a linguagem de programação Java suporta outros sete tipos de dados primitivos. Um tipo primitivo é predefinido pela linguagem e é nomeado por uma palavra-chave reservada. Valores primitivos não compartilham estado com outros valores primitivos. Os oito tipos de dados primitivos suportados pela linguagem de programação Java são:

* **byte**: O tipo de dado `byte` é um inteiro de 8 bits sinalizado (complemento de dois). Ele tem um valor mínimo de -128 e um valor máximo de 127 (inclusive). O tipo de dado `byte` pode ser útil para economizar memória em grandes arrays, onde a economia de memória realmente importa. Eles também podem ser usados no lugar de `int` onde seus limites ajudam a esclarecer seu código; o fato de o intervalo de uma variável ser limitado pode servir como uma forma de documentação.
* **short**: O tipo de dado `short` é um inteiro de 16 bits sinalizado (complemento de dois). Ele tem um valor mínimo de -32.768 e um valor máximo de 32.767 (inclusive). Como acontece com o `byte`, as mesmas diretrizes se aplicam: você pode usar um `short` para economizar memória em grandes arrays, em situações onde a economia de memória realmente importa.
* **int**: Por padrão, o tipo de dado `int` é um inteiro de 32 bits sinalizado (complemento de dois), que tem um valor mínimo de -2^31 e um valor máximo de 2^31-1. No Java SE 8 e posteriores, você pode usar o tipo de dado `int` para representar um inteiro não sinalizado de 32 bits, que tem um valor mínimo de 0 e um valor máximo de 2^32-1. Use a classe `Integer` para usar o tipo de dado `int` como um inteiro não sinalizado.
* **long**: O tipo de dado `long` é um inteiro de 64 bits (complemento de dois). O `long` sinalizado tem um valor mínimo de -2^63 e um valor máximo de 2^63-1. No Java SE 8 e posteriores, você pode usar o tipo de dado `long` para representar um `long` não sinalizado de 64 bits, que tem um valor mínimo de 0 e um valor máximo de 2^64-1. Use este tipo de dado quando precisar de um intervalo de valores mais amplo do que o fornecido pelo `int`.
* **float**: O tipo de dado `float` é um ponto flutuante de precisão simples de 32 bits IEEE 754. Use um `float` (em vez de `double`) se precisar economizar memória em grandes arrays de números de ponto flutuante. Este tipo de dado nunca deve ser usado para valores precisos, como moeda. Para isso, você precisará usar a classe `java.math.BigDecimal`.
* **double**: O tipo de dado `double` é um ponto flutuante de precisão dupla de 64 bits IEEE 754. Para valores decimais, este tipo de dado é geralmente a escolha padrão. Como mencionado acima, este tipo de dado nunca deve ser usado para valores precisos, como moeda.
* **boolean**: O tipo de dado `boolean` tem apenas dois valores possíveis: `true` e `false`. Use este tipo de dado para sinalizadores simples que rastreiam condições verdadeiras/falsas. Este tipo de dado representa um bit de informação, mas seu "tamanho" não é algo que seja precisamente definido.
* **char**: O tipo de dado `char` é um caractere Unicode único de 16 bits. Ele tem um valor mínimo de '\u0000' (ou 0) e um valor máximo de '\uffff' (ou 65.535 inclusive).

Além dos oito tipos de dados primitivos listados acima, a linguagem de programação Java também oferece suporte especial para cadeias de caracteres através da classe `java.lang.String`. Envolver sua cadeia de caracteres entre aspas duplas criará automaticamente um novo objeto `String`; por exemplo, `String s = "this is a string";`. Objetos `String` são imutáveis, o que significa que, uma vez criados, seus valores não podem ser alterados.

## Valores Padrão

Nem sempre é necessário atribuir um valor quando um campo é declarado. Campos que são declarados, mas não inicializados, serão definidos com um padrão razoável pelo compilador. Geralmente, esse padrão será zero ou `null`, dependendo do tipo de dado. Contudo, confiar nesses valores padrão é geralmente considerado um estilo de programação ruim.

A tabela a seguir resume os valores padrão para os tipos de dados acima.

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

Variáveis locais são ligeiramente diferentes; o compilador nunca atribui um valor padrão a uma variável local não inicializada. Se você não puder inicializar sua variável local onde ela é declarada, certifique-se de atribuir um valor a ela antes de tentar usá-la. Acessar uma variável local não inicializada resultará em um erro em tempo de compilação.

## Literais

Você deve ter notado que a palavra-chave `new` não é usada ao inicializar uma variável de um tipo primitivo. Tipos primitivos são tipos de dados especiais integrados à linguagem; eles não são objetos criados a partir de uma classe. Um literal é a representação no código-fonte de um valor fixo; literais são representados diretamente em seu código sem exigir computação.

### Literais Inteiros

Um literal inteiro é do tipo `long` se terminar com a letra `L` ou `l`; caso contrário, é do tipo `int`. Recomenda-se que você use a letra maiúscula `L` porque a letra minúscula `l` é difícil de distinguir do dígito `1`.

Os sistemas numéricos podem ser expressos por:

* **Decimal**: Base 10.
* **Hexadecimal**: Base 16, prefixo `0x`.
* **Binário**: Base 2, prefixo `0b`.

### Literais de Ponto Flutuante

Um literal de ponto flutuante é do tipo `float` se terminar com a letra `F` ou `f`; caso contrário, seu tipo é `double` e pode opcionalmente terminar com a letra `D` ou `d`.

### Literais de Caractere e String

Literais dos tipos `char` e `String` podem conter quaisquer caracteres Unicode (UTF-16). Use sempre 'aspas simples' para literais `char` e "aspas duplas" para literais `String`.

Existe também um literal especial `null` que pode ser usado como valor para qualquer tipo de referência.

### Uso de Caracteres de Sublinhado em Literais Numéricos

No Java SE 7 e posteriores, qualquer número de caracteres de sublinhado (`_`) pode aparecer em qualquer lugar entre dígitos em um literal numérico. Este recurso permite, por exemplo, separar grupos de dígitos em literais numéricos, o que pode melhorar a legibilidade do seu código.

Você pode colocar sublinhados apenas entre dígitos; você não pode colocar sublinhados nos seguintes lugares:

* No início ou no final de um número
* Adjacente a um ponto decimal em um literal de ponto flutuante
* Antes de um sufixo `F` ou `L`
* Em posições onde uma string de dígitos é esperada