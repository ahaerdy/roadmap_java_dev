# Tipos de Dados Primitivos em Java

Este documento resume os conceitos fundamentais sobre tipos de dados primitivos na linguagem Java, conforme abordado na documentação oficial [Primitive Data Types - The Java Tutorials](https://docs.oracle.com/javase/tutorial/java/nutsandbolts/datatypes.html).

## Introdução

Java é uma linguagem de **tipagem estática**, o que significa que todas as variáveis devem ser declaradas (definindo seu tipo e nome) antes de serem utilizadas. O tipo de dado determina os valores que a variável pode conter e as operações que podem ser realizadas sobre ela.

## Os 8 Tipos de Dados Primitivos

A linguagem Java possui oito tipos de dados primitivos pré-definidos pela própria linguagem:

1. **`byte`**: Inteiro de 8 bits (sinalizado). Faixa: -128 a 127.
2. **`short`**: Inteiro de 16 bits (sinalizado). Faixa: -32.768 a 32.767.
3. **`int`**: O padrão para números inteiros (32 bits).
4. **`long`**: Inteiro de 64 bits. Ideal para valores maiores que `int`.
5. **`float`**: Ponto flutuante de precisão simples (32 bits, IEEE 754).
6. **`double`**: Ponto flutuante de precisão dupla (64 bits, IEEE 754). É o padrão para decimais.
7. **`boolean`**: Representa apenas dois valores: `true` ou `false`.
8. **`char`**: Um único caractere Unicode de 16 bits.

> **Nota:** Embora a classe `java.lang.String` não seja um tipo primitivo, ela possui suporte especial da linguagem para manipulação de sequências de caracteres.

## Valores Padrão

Quando um campo de classe é declarado mas não inicializado, o compilador atribui valores padrão:

| Tipo de Dado | Valor Padrão (para campos) |
| --- | --- |
| `byte`, `short`, `int`, `long` | `0` |
| `float` | `0.0f` |
| `double` | `0.0d` |
| `char` | `'\u0000'` |
| `boolean` | `false` |
| `String` (ou qualquer objeto) | `null` |

*Atenção: Variáveis locais não recebem valores padrão; devem ser inicializadas manualmente antes do uso.*

## Literais

Um **literal** é a representação no código fonte de um valor fixo.

* **Inteiros:** Podem ser decimais, hexadecimais (prefixo `0x`) ou binários (prefixo `0b`).
* **Ponto Flutuante:** `double` é o padrão. Para `float`, deve-se adicionar o sufixo `f` ou `F`.
* **Caracteres e Strings:** Usam aspas simples (`'`) para `char` e aspas duplas (`"`) para `String`.

### Melhoria de Leitura (Underscores)

Desde o Java SE 7, é possível utilizar o caractere sublinhado (`_`) em literais numéricos para separar grupos de dígitos, melhorando a legibilidade (ex: `1_000_000`), desde que não estejam no início, fim ou adjacentes a pontos decimais.

---

*Fonte: [The Java™ Tutorials - Primitive Data Types*](https://docs.oracle.com/javase/tutorial/java/nutsandbolts/datatypes.html)