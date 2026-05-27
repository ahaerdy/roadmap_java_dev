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

### Classe Main (exemplo)

```java
public class Main {
    public static void main(String[] args) {
        // 1. Criamos o primeiro objeto (c1) da classe Counter.
        // O construtor é executado e incrementa a variável estática COUNT para 1.
        Counter c1 = new Counter();

        // 2. Criamos o segundo objeto (c2) da classe Counter.
        // Como COUNT é compartilhada, o construtor incrementa o valor atual (1) para 2.
        Counter c2 = new Counter();

        // 3. Acessamos a variável estática diretamente pelo nome da classe.
        // Saída esperada: "2"
        System.out.println(Counter.COUNT);

        // 4. Demonstração adicional baseada na introdução:
        // Também é possível acessar a mesma variável estática usando qualquer objeto da classe.
        // Ambas as linhas abaixo também exibirão "2", pois apontam para a mesma variável compartilhada.
        // System.out.println(c1.COUNT);
        // System.out.println(c2.COUNT);
    }
}

```

## Explicação:

* **Compartilhamento:** A saída é `2` porque a variável `COUNT` pertence à classe e não a um objeto específico. Toda vez que `new Counter()` é chamado, o construtor mexe na mesma variável global daquela classe.
* **Formas de Acesso:** O código mostra o padrão recomendado (`Counter.COUNT`), mas a introdução ressalta que o Java também permite o acesso via instância (`c1.COUNT`), embora ambos apontem para o mesmo lugar na memória.


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

A saída é **2**, porque o valor é incrementado pelo método estático `increment()`.  
Assim como variáveis estáticas, métodos estáticos também podem ser acessados usando variáveis de instância.

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
