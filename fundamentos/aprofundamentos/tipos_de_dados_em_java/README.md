# Tipos de Dados em Java

Como explicado no texto sobre variáveis em Java, cada variável em Java possui um **tipo de dado**. Os tipos de dados se dividem em dois grupos:

- Tipos de dados primitivos  
- Referências a objetos  

Uma variável ocupa uma certa quantidade de espaço na memória. A quantidade depende do tipo de dado.  

Uma variável de tipo primitivo contém diretamente o valor na memória alocada para ela (por exemplo, um número ou um caractere).  

Já uma variável de referência a objeto é diferente: ela não contém o objeto em si, mas sim uma **referência** ao objeto. Essa referência aponta para outro lugar na memória onde o objeto completo está armazenado. Através dessa referência, é possível acessar campos e métodos do objeto.  

É possível que várias variáveis diferentes referenciem o mesmo objeto — algo que não ocorre com tipos primitivos.

## Tipos de Dados Primitivos

A linguagem Java contém os seguintes tipos de dados primitivos:

| Tipo   | Descrição |
|--------|-----------|
| boolean | Valor binário: `true` ou `false` |
| byte    | Valor assinado de 8 bits, de -128 a 127 |
| short   | Valor assinado de 16 bits, de -32.768 a 32.767 |
| char    | Caractere Unicode de 16 bits |
| int     | Valor assinado de 32 bits, de -2.147.483.648 a 2.147.483.647 |
| long    | Valor assinado de 64 bits, de -9.223.372.036.854.775.808 a 9.223.372.036.854.775.808 |
| float   | Valor de ponto flutuante de 32 bits |
| double  | Valor de ponto flutuante de 64 bits |

Esses tipos são **primitivos**, ou seja, não são objetos nem referências a objetos.

Exemplo de declaração:

```java
int myInt;
```

## Tipos de Objetos

Os tipos primitivos também possuem versões como objetos completos.  
Isso significa que podem ser referenciados, ter múltiplas referências ao mesmo valor e métodos podem ser chamados sobre eles.

Lista de tipos de objetos principais:

| Tipo      | Descrição |
|-----------|-----------|
| Boolean   | Valor binário: `true` ou `false` |
| Byte      | Valor assinado de 8 bits |
| Short     | Valor assinado de 16 bits |
| Character | Caractere Unicode de 16 bits |
| Integer   | Valor assinado de 32 bits |
| Long      | Valor assinado de 64 bits |
| Float     | Valor de ponto flutuante de 32 bits |
| Double    | Valor de ponto flutuante de 64 bits |
| String    | Cadeia Unicode de N bytes (texto). Imutável |

Note que os tipos objetos começam com letra maiúscula, enquanto os primitivos são escritos em minúsculas (ex.: `int` vs. `Integer`, `char` vs. `Character`).

Exemplo de declaração:

```java
Integer myInteger;
```

Para instanciar:

```java
Integer myInteger;
myInteger = new Integer(45);
```

Ou diretamente:

```java
Integer myInteger = new Integer(45);
```

## Imutabilidade

As versões objeto dos tipos primitivos são **imutáveis**.  
Isso significa que o valor armazenado não pode ser alterado após a criação do objeto.  
A variável pode apontar para outro objeto, mas o valor interno de um objeto não muda.

Exemplo:

```java
Integer myInteger = new Integer(45);
myInteger = new Integer(33);
```

## Auto Boxing

Antes do Java 5, era necessário chamar métodos para converter objetos em tipos primitivos:

```java
Integer myInteger = new Integer(45);
int myInt = myInteger.intValue();
```

A partir do Java 5, surgiu o conceito de **auto boxing**, que permite conversões automáticas entre tipos primitivos e suas versões objeto.

Exemplo:

```java
Integer myInteger = new Integer(45);
int myInt = myInteger; // unboxing automático
```

E também:

```java
int myInt = 45;
Integer myInteger = myInt; // boxing automático
```

### Atenção:

Uma referência de objeto pode ser `null`.  
Se tentar converter (`unbox`) um objeto `null` para primitivo, ocorrerá um **NullPointerException**.

Exemplo:

```java
Integer myInteger = null;
int myInt = myInteger; // Erro em tempo de execução
```
