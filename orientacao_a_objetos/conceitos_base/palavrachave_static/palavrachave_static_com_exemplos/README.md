# Palavra-chave Static em Java Explicada com Exemplos

## O que significa *static*?
Quando você declara uma variável ou um método como *static*, ele pertence à classe, em vez de a uma instância específica. Isso significa que apenas uma instância de um membro estático existe, mesmo que você crie múltiplos objetos da classe, ou mesmo que não crie nenhum. Ele será compartilhado por todos os objetos.

A palavra-chave *static* pode ser usada com variáveis, métodos, blocos de código e classes aninhadas.

---

## Variáveis Estáticas

**Exemplo:**
```java
public class Counter {
    public static int COUNT = 0;
    Counter() {
        COUNT++;
    }
}
```

A variável `COUNT` será compartilhada por todos os objetos dessa classe.  
Quando criamos objetos da classe `Counter` em `main` e acessamos a variável estática:

```java
public class MyClass {
    public static void main(String[]  args) {
        Counter c1 = new Counter();
        Counter c2 = new Counter();
        System.out.println(Counter.COUNT);
    }
}
// Saída "2"
```

A saída é **2**, porque a variável `COUNT` é estática e é incrementada em um a cada vez que um novo objeto da classe `Counter` é criado.  
Você também pode acessar a variável estática usando qualquer objeto dessa classe, como `c1.COUNT`.

---

## Métodos Estáticos

Um método estático pertence à classe em vez das instâncias. Assim, pode ser chamado sem criar uma instância da classe. Ele é usado para alterar conteúdos estáticos da classe.

**Restrições dos métodos estáticos:**
- Não podem usar membros não estáticos (variáveis ou funções) da classe.
- Não podem usar as palavras-chave `this` ou `super`.

**Exemplo:**
```java
public class Counter {
    public static int COUNT = 0;
    Counter() {
        COUNT++;
    }
    public static void increment(){
        COUNT++;
    }
}
```

Métodos estáticos também podem ser chamados a partir de uma instância da classe:

```java
public class MyClass {
    public static void main(String[]  args) {
        Counter.increment();
        Counter.increment();
        System.out.println(Counter.COUNT);
    }
}
// Saída "2"
```

A saída é **2**, porque o valor é incrementado pelo método estático `increment()`. O método estático foi acessado diretamente pelo nome da classe (`Counter.increment()`).

Assim como variáveis estáticas, métodos estáticos também podem ser acessados usando variáveis de instância. Uma variável de instância (ou objeto) é aquela que você cria usando o operador new. No contexto do seu código anterior, `c1` e `c2` são as variáveis de instância.

Se fôssemos aplicar o que o texto afirmou, o código dentro do main seria escrito assim:

```java
public class MyClass {
    public static void main(String[] args) {
        // Criamos uma variável de instância (objeto) chamada c1
        Counter c1 = new Counter(); 
        
        // Acessando o método estático usando a variável de instância c1:
        c1.increment(); 
        
        // Acessando o método estático usando outra variável de instância:
        Counter c2 = new Counter();
        c2.increment();

        System.out.println(Counter.COUNT); // O resultado ainda seria influenciado
    }
}
```

Apesar de o método ser estático, "por trás dos panos" o compilador Java olha para o tipo da variável c1 (que é Counter) e substitui o código internamente por Counter.increment().

---

## Blocos Estáticos

Blocos de código estáticos são usados para inicializar variáveis estáticas. Esses blocos são executados imediatamente após a declaração das variáveis estáticas.

**Exemplo:**
```java
public class Saturn {
    public static final int MOON_COUNT;
    static {
        MOON_COUNT = 62;
    }
}

public class Main {
    public static void main(String[]  args) {
        System.out.println(Saturn.MOON_COUNT);
    }
}
// Saída "62"
```

A saída é **62**, porque a variável `MOON_COUNT` recebe esse valor no bloco estático.

---

## Classes Aninhadas Estáticas

Uma classe pode ter uma classe aninhada estática que pode ser acessada usando o nome da classe externa.

**Exemplo:**
```java
public class Outer {
    public Outer() { }
    public static class Inner {
        public Inner() { }
    }
}
```

No exemplo acima, a classe `Inner` pode ser acessada diretamente como um membro estático da classe `Outer`.

```java
public class Main {
    public static void main(String[]  args) {
        Outer.Inner inner = new Outer.Inner();
    }
}
```

Um dos casos de uso das classes aninhadas estáticas é no **Builder Pattern**, amplamente utilizado em Java.
