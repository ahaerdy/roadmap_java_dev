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

#### Métodos estáticos sendo acessados usando variáveis de instância

Assim como variáveis estáticas, métodos estáticos também podem ser acessados usando variáveis de instância. Uma variável de instância (ou objeto) é aquela que você cria usando o operador new. 

Exemplo:

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

---

Aqui está o trecho reescrito, com o código Java totalmente documentado através de comentários *inline* para explicar o papel do bloco estático e a ordem de execução:

---

## Blocos Estáticos

Blocos de código estáticos são usados para inicializar variáveis estáticas (especialmente útil para lógicas complexas ou constantes). Esses blocos são executados automaticamente apenas uma vez, no momento em que a classe é carregada na memória, logo após a declaração das variáveis estáticas e antes de qualquer objeto ser criado ou método ser chamado.

**Exemplo:**

```java
public class Saturn {
    // Declaração de uma constante estática (final). 
    // Ela não recebeu valor aqui, o que nos obriga a inicializá-la no bloco static.
    public static final int MOON_COUNT;

    // Bloco estático de inicialização.
    // É executado automaticamente assim que a classe Saturn é mencionada/carregada.
    static {
        MOON_COUNT = 62; // Inicializa a variável estática com o valor 62
    }
}

```

```java
public class Main {
    public static void main(String[]  args) {
        // Acessa a variável estática diretamente pelo nome da classe.
        // No momento em que "Saturn" é lido, o bloco static roda e define o valor como 62.
        System.out.println(Saturn.MOON_COUNT); 
    }
}
// Saída "62"

```

A saída é 62, porque a variável `MOON_COUNT` recebe esse valor dentro do bloco estático no exato momento em que a classe `Saturn` é carregada para ser utilizada no método `main`.

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
