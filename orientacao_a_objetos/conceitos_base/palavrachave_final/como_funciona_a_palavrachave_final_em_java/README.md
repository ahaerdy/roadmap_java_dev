# Como funciona a palavra-chave `final` em Java? (detalhamento)

Em Java usamos a palavra-chave `final` com variáveis para especificar que seus valores não devem ser alterados. Mas perceba que você pode mudar o valor no construtor/métodos da classe. Se a variável for `static`, então ocorre um erro de compilação.  

Aqui está o código:

```java
import java.util.ArrayList;
import java.util.List;

class Test {
    private final List foo;

    public Test() {
        foo = new ArrayList();
        foo.add("foo");  // Modificação-1
    }

    public static void main(String[] args) {
        Test t = new Test();
        t.foo.add("bar");  // Modificação-2
        System.out.println("print - " + t.foo);
    }
}
```

O código acima funciona bem e não gera erros.  
Agora, altere a variável para `static`:

```java
private static final List foo;
```

Agora ocorre um erro de compilação.  
Como esse `final` realmente funciona?

---

Essa é uma pergunta favorita em entrevistas. O entrevistador tenta descobrir o quanto você entende o comportamento de objetos em relação a construtores, métodos, variáveis de classe (`static`) e variáveis de instância.  

### Exemplo:

```java
import java.util.ArrayList;
import java.util.List;

class Test {
    private final List foo;  

    public Test() {
        foo = new ArrayList();  
        foo.add("foo");  // Modificação-1 
    }

    public void setFoo(List foo) {
        // this.foo = foo; // resulta em erro de compilação
    }
}
```

### Sobre construtor:
- O construtor pode ser invocado apenas uma vez por criação de objeto usando `new`.
- Não pode ser chamado múltiplas vezes.

### Sobre método:
- Um método pode ser chamado quantas vezes quiser (inclusive nunca).
- O compilador sabe disso.

---

### Cenário 1
```java
private final List foo;
```
- `foo` é uma variável de instância.  
- Ao criar um objeto da classe `Test`, a variável `foo` é copiada para dentro do objeto.  
- Se atribuirmos `final foo` dentro do construtor, o compilador sabe que o construtor será chamado apenas uma vez, então não há problema.  
- Se atribuirmos dentro de um método, o compilador sabe que o método pode ser chamado várias vezes, o que exigiria mudar o valor várias vezes — não permitido para variáveis `final`.

---

### Cenário 2
```java
private static final List foo = new ArrayList();
```
- `foo` agora é uma variável estática.  
- Não é copiada para cada objeto, mas compartilhada entre todos.  
- O compilador impede que variáveis `final static` sejam inicializadas dentro do construtor.  
- Devemos declarar e definir o objeto `final List` no mesmo local da declaração.

---

### Regras
- Uma variável `final` inicializada não pode ser alterada para referenciar outro objeto.  
- Classes `final` não podem ser estendidas.  
- Métodos `final` não podem ser sobrescritos.  
- Métodos `final` podem sobrescrever métodos da superclasse.

