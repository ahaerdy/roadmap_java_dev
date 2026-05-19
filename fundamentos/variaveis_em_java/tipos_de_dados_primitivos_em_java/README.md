A linguagem de programação Java é tipada estaticamente, o que significa que todas as variáveis ​​devem ser declaradas antes de serem usadas. Isso envolve especificar o tipo e o nome da variável, como você já viu:

engrenagem inteira = 1;

Ao fazer isso, você informa ao seu programa que um campo chamado "gear" existe, armazena dados numéricos e tem um valor inicial de "1". O tipo de dados de uma variável determina os valores que ela pode conter, além das operações que podem ser realizadas nela. Além de \`int\` `int`, a linguagem de programação Java suporta outros sete *tipos de dados primitivos* . Um tipo primitivo é predefinido pela linguagem e nomeado por uma palavra-chave reservada. Valores primitivos não compartilham estado com outros valores primitivos. Os oito tipos de dados primitivos suportados pela linguagem de programação Java são:

- **byte** : O `byte`tipo de dados é um inteiro de 8 bits com sinal em complemento de dois. Possui um valor mínimo de -128 e um valor máximo de 127 (inclusive). Esse `byte`tipo de dados pode ser útil para economizar memória em [arrays](arrays.html) grandes , onde a economia de memória é realmente importante. Eles também podem ser usados ​​no lugar de \` `int`int\` quando seus limites ajudam a esclarecer o código; o fato de o intervalo de uma variável ser limitado pode servir como uma forma de documentação.
- **Resumo** : O `short`tipo de dados é um inteiro de 16 bits com sinal em complemento de dois. Possui um valor mínimo de -32.768 e um valor máximo de 32.767 (inclusive). Assim como em outros `byte`tipos de dados, as mesmas diretrizes se aplicam: você pode usar um \`int\` `short`para economizar memória em arrays grandes, em situações onde a economia de memória é realmente importante.
- **int** : Por padrão, o `int`tipo de dados é um inteiro de 32 bits com sinal em complemento de dois, que tem um valor mínimo de -2^ <sup><font dir="auto" style="vertical-align: inherit;"><font dir="auto" style="vertical-align: inherit;">31</font></font></sup> e um valor máximo de 2 <sup><font dir="auto" style="vertical-align: inherit;"><font dir="auto" style="vertical-align: inherit;">^31</font></font></sup> - 1. No Java SE 8 e versões posteriores, você pode usar o `int`tipo de dados para representar um inteiro de 32 bits sem sinal, que tem um valor mínimo de 0 e um valor máximo de 2 <sup><font dir="auto" style="vertical-align: inherit;"><font dir="auto" style="vertical-align: inherit;">^32</font></font></sup> - 1. Use a classe Integer para usar `int`o tipo de dados como um inteiro sem sinal. Consulte a seção As Classes de Número para obter mais informações. Métodos estáticos como \`map\` `compareUnsigned`, \` filter\`, `divideUnsigned`etc., foram adicionados à [`Integer`](https://docs.oracle.com/javase/8/docs/api/java/lang/Integer.html)classe para suportar as operações aritméticas para inteiros sem sinal.
- **\`long\`** : O `long`tipo de dados é um inteiro de 64 bits em complemento de dois. O \`long\` com sinal tem um valor mínimo de -2<sup> <sup><font dir="auto" style="vertical-align: inherit;"><font dir="auto" style="vertical-align: inherit;">63&lt;/sup&gt;</font></font></sup> e um valor máximo de 2 <sup><font dir="auto" style="vertical-align: inherit;"><font dir="auto" style="vertical-align: inherit;">&lt;sup&gt;63</font></font></sup> </sup> - 1. No Java SE 8 e versões posteriores, você pode usar o `long`tipo de dados \`long\` para representar um \`long\` sem sinal de 64 bits, que tem um valor mínimo de 0 e um valor máximo de 2 <sup><font dir="auto" style="vertical-align: inherit;"><font dir="auto" style="vertical-align: inherit;">&lt;sup&gt;64</font></font></sup> </sup> - 1. Use este tipo de dados quando precisar de um intervalo de valores maior do que os fornecidos por \` long\` `int`. A [`Long`](https://docs.oracle.com/javase/8/docs/api/java/lang/Long.html)classe também contém métodos como `compareUnsigned`\`map\`, \` filter\`, `divideUnsigned`etc., para suportar operações aritméticas com \`long\` sem sinal.
- **float** : O `float`tipo de dados é um ponto flutuante de precisão simples de 32 bits, padrão IEEE 754. Seu intervalo de valores está além do escopo desta discussão, mas é especificado na seção [Tipos, Formatos e Valores de Ponto Flutuante](https://docs.oracle.com/javase/specs/jls/se7/html/jls-4.html#jls-4.2.3) da Especificação da Linguagem Java. Assim como nas recomendações para `byte`float e float `short`, use um float `float`(em vez de float `double`) se precisar economizar memória em grandes arrays de números de ponto flutuante. Este tipo de dados nunca deve ser usado para valores precisos, como moedas. Para isso, você precisará usar a classe [java.math.BigDecimal .](https://docs.oracle.com/javase/8/docs/api/java/math/BigDecimal.html) [Números e Strings](../data/index.html) abordam float `BigDecimal`e outras classes úteis fornecidas pela plataforma Java.
- **\`double\`** : O `double`tipo de dados é um ponto flutuante de dupla precisão de 64 bits, padrão IEEE 754. Seu intervalo de valores está além do escopo desta discussão, mas é especificado na seção [Tipos, Formatos e Valores de Ponto Flutuante](https://docs.oracle.com/javase/specs/jls/se7/html/jls-4.html#jls-4.2.3) da Especificação da Linguagem Java. Para valores decimais, este tipo de dados é geralmente a escolha padrão. Como mencionado acima, este tipo de dados nunca deve ser usado para valores exatos, como moedas.
- **boolean** : Este `boolean`tipo de dado possui apenas dois valores possíveis: verdadeiro `true`e falso `false`. Use este tipo de dado para indicadores simples que rastreiam condições verdadeiras/falsas. Este tipo de dado representa um bit de informação, mas seu "tamanho" não é algo precisamente definido.
- **char** : O `char`tipo de dados é um único caractere Unicode de 16 bits. Possui um valor mínimo de `'\u0000'`(ou 0) e um valor máximo de `'\uffff'`(ou 65.535, inclusive).

Além dos oito tipos de dados primitivos listados acima, a linguagem de programação Java também oferece suporte especial para strings de caracteres por meio da classe [\`java.lang.String\`](https://docs.oracle.com/javase/8/docs/api/java/lang/String.html) . Colocar sua string de caracteres entre aspas duplas criará automaticamente um novo `String`objeto; por exemplo, \`"string" `String s = "this is a string";`\`. `String`Objetos \`string\` são *imutáveis* , o que significa que, uma vez criados, seus valores não podem ser alterados. A `String`classe \`String\` não é tecnicamente um tipo de dado primitivo, mas considerando o suporte especial que a linguagem lhe oferece, você provavelmente tenderá a considerá-la como tal. Você aprenderá mais sobre a `String`classe \`String\` em [Objetos de Dados Simples.](../data/index.html)

## Valores padrão

Nem sempre é necessário atribuir um valor quando um campo é declarado. Campos declarados, mas não inicializados, receberão um valor padrão razoável do compilador. De modo geral, esse valor padrão será zero ou nulo `null`, dependendo do tipo de dado. No entanto, confiar nesses valores padrão é geralmente considerado uma má prática de programação.

O gráfico a seguir resume os valores padrão para os tipos de dados acima.

| **Tipo de dados** | **Valor padrão (para campos)** |
| --- | --- |
| byte | 0 |
| curto | 0 |
| inteiro | 0 |
| longo | 0L |
| flutuador | 0,0f |
| dobro | 0,0d |
| personagem | '\\u0000' |
| String (ou qualquer objeto) | nulo |
| booleano | falso |

  

As variáveis ​​locais são ligeiramente diferentes; o compilador nunca atribui um valor padrão a uma variável local não inicializada. Se você não puder inicializar sua variável local onde ela foi declarada, certifique-se de atribuir um valor a ela antes de tentar usá-la. Acessar uma variável local não inicializada resultará em um erro de compilação.

### Literais

Você deve ter notado que a `new`palavra-chave \`new\` não é usada ao inicializar uma variável de um tipo primitivo. Tipos primitivos são tipos de dados especiais, inerentes à linguagem; eles não são objetos criados a partir de uma classe. Um *literal* é a representação em código-fonte de um valor fixo; literais são representados diretamente no seu código, sem a necessidade de cálculos. Como mostrado abaixo, é possível atribuir um literal a uma variável de um tipo primitivo:

resultado booleano = verdadeiro;
char capitalC = 'C';
byte b = 100;
curto s = 10000;
int i = 100000;

#### Literais inteiros

Um literal inteiro é do tipo `long`se terminar com a letra `L`ou `l`; caso contrário, é do tipo `int`. Recomenda-se o uso da letra maiúscula, `L`pois a letra minúscula `l`é difícil de distinguir do dígito `1`.

Valores dos tipos inteiros `byte`, `short`, `int`, e `long`podem ser criados a partir de `int`literais. Valores do tipo `long`que excedem o intervalo de `int`podem ser criados a partir de `long`literais. Literais inteiros podem ser expressos pelos seguintes sistemas numéricos:

- Decimal: Base 10, cujos dígitos consistem nos números de 0 a 9; este é o sistema numérico que você usa todos os dias.
- Hexadecimal: Base 16, cujos dígitos consistem nos números de 0 a 9 e nas letras de A a F.
- Binário: Base 2, cujos dígitos consistem nos números 0 e 1 (você pode criar literais binários no Java SE 7 e versões posteriores).

Para programação de propósito geral, o sistema decimal provavelmente será o único sistema numérico que você usará. No entanto, se precisar usar outro sistema numérico, o exemplo a seguir mostra a sintaxe correta. O prefixo `0x`indica hexadecimal e `0b`indica binário:

// O número 26, em decimal
int decVal = 26;
// O número 26, em hexadecimal
int hexVal = 0x1a;
// O número 26, em binário
int binVal = 0b11010;

#### Literais de ponto flutuante

Um literal de ponto flutuante é do tipo `float`se terminar com a letra `F`ou `f`; caso contrário, seu tipo é `double`e pode opcionalmente terminar com a letra `D`ou `d`.

Os tipos de ponto flutuante ( `float`e `double`) também podem ser expressos usando E ou e (para notação científica), F ou f (literal float de 32 bits) e D ou d (literal double de 64 bits; este é o padrão e, por convenção, é omitido).

duplo d1 = 123,4;
// mesmo valor que d1, mas em notação científica
duplo d2 = 1,234e2;
float f1 = 123.4f;

#### Literais de caracteres e strings

Literais de tipos \`int\` `char`e `String`\`string\` podem conter quaisquer caracteres Unicode (UTF-16). Se o seu editor e sistema de arquivos permitirem, você pode usar esses caracteres diretamente no seu código. Caso contrário, você pode usar uma sequência de escape Unicode, como `'\u0108'`\`\\c\` (C maiúsculo com acento circunflexo) ou `"S\u00ED Se\u00F1or"`\`\\sí Señor\` (Sí Señor em espanhol). Sempre use aspas simples para `char`literais e aspas duplas para `String`literais de tipos \`int\` e \`string\`. Sequências de escape Unicode podem ser usadas em outras partes do programa (como em nomes de campos, por exemplo), não apenas em literais de tipos \`int\` `char`ou \` `String`string\`.

A linguagem de programação Java também suporta algumas sequências de escape especiais para `char`literais `String`: `\b`(backspace), `\t`(tab), `\n`(line feed), `\f`(form feed), `\r`(carriage return), `\"`(double quote), `\'`(single quote) e `\\`(backslash).

Existe também um `null`literal especial que pode ser usado como valor para qualquer tipo de referência. `null`Ele pode ser atribuído a qualquer variável, exceto variáveis ​​de tipos primitivos. Há pouco que se possa fazer com um `null`valor além de verificar sua presença. Portanto, `null`ele é frequentemente usado em programas como um marcador para indicar que algum objeto está indisponível.

Finalmente, existe também um tipo especial de literal chamado *literal de classe* , formado pegando um nome de tipo e acrescentando " `.class"`; por exemplo, `String.class`. Isso se refere ao objeto (do tipo `Class`) que representa o próprio tipo.

## Utilizando caracteres de sublinhado em literais numéricos

No Java SE 7 e versões posteriores, qualquer número de caracteres de sublinhado (\_ `_`) pode aparecer em qualquer lugar entre os dígitos em um literal numérico. Esse recurso permite, por exemplo, separar grupos de dígitos em literais numéricos, o que pode melhorar a legibilidade do seu código.

Por exemplo, se o seu código contiver números com muitos dígitos, você pode usar um caractere de sublinhado para separar os dígitos em grupos de três, de forma semelhante a como você usaria um sinal de pontuação, como uma vírgula, ou um espaço, como separador.

O exemplo a seguir mostra outras maneiras de usar o sublinhado em literais numéricos:

Número longo do cartão de crédito = 1234\_5678\_9012\_3456L;
long socialSecurityNumber = 999\_99\_9999L;
float pi = 3.14\_15F;
long hexBytes = 0xFF\_EC\_DE\_5E;
palavras hexadecimais longas = 0xCAFE\_BABE;
longo maxLong = 0x7fff\_ffff\_ffff\_ffffL;
byte nibbles = 0b0010\_0101;
bytes longos = 0b11010010\_01101001\_10010100\_10010010;

Você só pode usar sublinhados entre dígitos; não é possível usar sublinhados nos seguintes locais:

- No início ou no fim de um número
- Adjacente a um ponto decimal em um literal de ponto flutuante
- Antes de um sufixo `F`ou`L`
- Em posições onde se espera uma sequência de dígitos.

Os exemplos a seguir demonstram posicionamentos válidos e inválidos de sublinhados (que estão destacados) em literais numéricos:

// **Inválido: não é possível colocar sublinhados** 
// **adjacentes a um ponto decimal**
float pi1 = 3\_.1415F;
// **Inválido: não é possível colocar sublinhados**  
// **adjacentes a um ponto decimal**
float pi2 = 3.\_1415F;
// **Inválido: não é possível colocar sublinhados**  
// **antes do sufixo L**
long socialSecurityNumber1 = 999\_99\_9999\_L;
// OK (literal decimal)
int x1 = 5\_2;
// **Inválido: não é possível colocar sublinhados** 
// **No final de um literal**
int x2 = 52\_;
// OK (literal decimal)
int x3 = 5\_\_\_\_\_\_\_2;
// **Inválido: não é possível inserir sublinhados** 
// **no prefixo de base 0x**
int x4 = 0\_x52;
// **Inválido: não é possível colocar sublinhados** 
// **no início de um número**
int x5 = 0x\_52;
// OK (literal hexadecimal)
int x6 = 0x5\_2;
// **Inválido: não é possível colocar sublinhados** 
// **no final de um número**
int x7 = 0x52\_;