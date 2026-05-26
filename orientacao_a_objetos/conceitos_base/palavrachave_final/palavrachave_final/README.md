# A Palavra-chave “final” em Java 

## 1. Visão Geral
Enquanto a herança nos permite reutilizar código existente, às vezes precisamos impor limitações à extensibilidade por diversos motivos; a palavra-chave `final` nos permite fazer exatamente isso.  
Neste tutorial, veremos o que a palavra-chave `final` significa para classes, métodos e variáveis.

## 2. Classes Final
Classes marcadas como `final` não podem ser estendidas.  
Se olharmos o código das bibliotecas centrais do Java, encontraremos muitas classes `final`. Um exemplo é a classe `String`.

Imagine se pudéssemos estender a classe `String`, sobrescrever qualquer um de seus métodos e substituir todas as instâncias de `String` por instâncias de nossa subclasse específica. O resultado das operações sobre objetos `String` se tornaria imprevisível. Como a classe `String` é usada em toda parte, isso seria inaceitável.  
Por isso, a classe `String` é marcada como `final`.

Qualquer tentativa de herdar de uma classe `final` causará um erro de compilação.  
Exemplo:

```java
public final class Cat {
    private int weight;
    // getter e setter padrão
}
```

Tentando estender:

```java
public class BlackCat extends Cat { }
```

Erro do compilador:  
`The type BlackCat cannot subclass the final class Cat`

> Importante: marcar uma classe como `final` não significa que seus objetos são imutáveis. Podemos alterar os campos de um objeto `Cat` livremente.

```java
Cat cat = new Cat();
cat.setWeight(1);
assertEquals(1, cat.getWeight());
```

Devemos usar cautela ao criar classes `final`. Tornar uma classe `final` significa que nenhum outro programador poderá melhorá-la. Se houver um problema em um método e não tivermos o código-fonte, não poderemos sobrescrevê-lo para corrigir. Assim, perdemos extensibilidade, um dos benefícios da programação orientada a objetos.

## 3. Métodos Final
Métodos marcados como `final` não podem ser sobrescritos.  
Quando projetamos uma classe e sentimos que um método não deve ser sobrescrito, podemos torná-lo `final`.

Exemplo: a classe `Thread`. Podemos estendê-la, mas seu método `isAlive()` é `final`. Esse método verifica se uma thread está ativa e não pode ser sobrescrito corretamente, pois é nativo.

```java
public class Dog {
    public final void sound() {
        // ...
    }
}
```

Tentando sobrescrever:

```java
public class BlackDog extends Dog {
    public void sound() { }
}
```

Erro do compilador:  
`Cannot override the final method from Dog`

Se métodos de nossa classe são chamados por outros métodos, devemos considerar torná-los `final`. Caso contrário, sobrescrevê-los pode afetar o funcionamento dos chamadores e causar resultados inesperados.  
Se nosso construtor chama outros métodos, geralmente devemos declará-los como `final`.

Diferença:  
- Tornar todos os métodos `final` → podemos estender a classe e adicionar novos métodos.  
- Tornar a classe `final` → não podemos estendê-la.

## 4. Variáveis Final
Variáveis marcadas como `final` não podem ser reatribuídas. Uma vez inicializadas, não podem ser alteradas.

#### 4.1. Variáveis Primitivas Final
```java
final int i = 1;
i = 2; // erro
```

Erro:  
`The final local variable i may already have been assigned`

#### 4.2. Variáveis de Referência Final
```java
final Cat cat = new Cat();
```

Não podemos reatribuir `cat`, mas podemos alterar suas propriedades:

```java
cat.setWeight(5);
assertEquals(5, cat.getWeight());
```

#### 4.3. Campos Final
Campos `final` podem ser constantes ou “write-once”.  
Constantes devem seguir convenções de nomenclatura em maiúsculas com underscore:

```java
static final int MAX_WIDTH = 999;
```

Campos `final` devem ser inicializados antes do término do construtor.  
- Para campos `static final`: na declaração ou em bloco inicializador estático.  
- Para campos de instância `final`: na declaração, em bloco inicializador de instância ou no construtor.

#### 4.4. Parâmetros Final
Podemos usar `final` em parâmetros de métodos. Eles não podem ser alterados dentro do método:

```java
public void methodWithFinalArguments(final int x) {
    x = 1; // erro
}
```

Erro:  
`The final local variable x cannot be assigned`

### 5. Conclusão
Neste artigo, aprendemos o que a palavra-chave `final` significa para classes, métodos e variáveis.  
Embora possamos não usar `final` com frequência em nosso código interno, pode ser uma boa solução de design.  

O código deste artigo está disponível no GitHub.  
Uma vez logado como Membro Pro do Baeldung, você pode começar a aprender e codificar no projeto.
