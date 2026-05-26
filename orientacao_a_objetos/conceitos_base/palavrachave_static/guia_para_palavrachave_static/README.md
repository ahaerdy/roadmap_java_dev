# Um Guia para a Palavra-chave Static em Java | Baeldung

## 1. Visão Geral
Neste tutorial, exploraremos em detalhes a palavra-chave **static** da linguagem Java.  
A palavra-chave *static* significa que um membro – como um campo ou método – pertence à classe em si, em vez de a qualquer instância específica dessa classe.  
Como resultado, podemos acessar membros estáticos sem a necessidade de criar uma instância de um objeto.  

Começaremos discutindo as diferenças entre campos e métodos estáticos e não estáticos. Em seguida, cobriremos classes e blocos de código estáticos e explicaremos por que componentes não estáticos não podem ser acessados a partir de um contexto estático.

---

## 2. Os Campos static (Ou Variáveis de Classe)
Em Java, quando declaramos um campo como *static*, exatamente uma única cópia desse campo é criada e compartilhada entre todas as instâncias dessa classe.  
Não importa quantas vezes instanciamos uma classe: sempre haverá apenas uma cópia do campo estático pertencente a ela.  

O valor desse campo estático é compartilhado entre todos os objetos da mesma classe.  
Do ponto de vista da memória, variáveis estáticas são armazenadas na memória heap.

Imagine uma classe com várias variáveis de instância, onde cada novo objeto criado dessa classe tem sua própria cópia dessas variáveis.  
No entanto, se quisermos que uma variável rastreie o número de objetos criados, usamos uma variável estática. Isso permite que o contador seja incrementado a cada novo objeto:

```java
public class Car {
    private String name;
    private String engine;
    public static int numberOfCars;

    public Car(String name, String engine) {
        this.name = name;
        this.engine = engine;
        numberOfCars++;
    }
    // getters e setters
}
```

Como resultado, a variável estática `numberOfCars` será incrementada cada vez que instanciarmos a classe `Car`.  

```java
@Test
public void whenNumberOfCarObjectsInitialized_thenStaticCounterIncreases() {
    new Car("Jaguar", "V8");
    new Car("Bugatti", "W16");
    assertEquals(2, Car.numberOfCars);
}
```

Campos estáticos são úteis quando:
- O valor da variável é independente dos objetos.
- O valor deve ser compartilhado entre todos os objetos.

Por fim, é importante saber que campos estáticos podem ser acessados por meio de uma instância (`ford.numberOfCars++`) ou diretamente pela classe (`Car.numberOfCars++`).  
A segunda forma é preferida, pois indica claramente que se trata de uma variável de classe.

---

## 3. Os Métodos static (Ou Métodos de Classe)
Assim como os campos estáticos, métodos estáticos também pertencem a uma classe em vez de a um objeto.  
Portanto, podemos invocá-los sem instanciar a classe.  

Geralmente, usamos métodos estáticos para realizar operações que não dependem da criação de instâncias.  
Por exemplo, podemos usar um método estático para compartilhar código entre todas as instâncias da classe:

```java
static void setNumberOfCars(int numberOfCars) {
    Car.numberOfCars = numberOfCars;
}
```

Além disso, podemos usar métodos estáticos para criar classes utilitárias ou auxiliares. Exemplos populares são as classes `Collections` ou `Math` do JDK, `StringUtils` do Apache e `CollectionUtils` do Spring Framework.

Assim como os campos estáticos, métodos estáticos **não podem ser sobrescritos**.  
Isso ocorre porque métodos estáticos em Java são resolvidos em tempo de compilação, enquanto a sobrescrita de métodos faz parte do polimorfismo em tempo de execução.

Combinações válidas:
- Métodos de instância podem acessar diretamente métodos e variáveis de instância.
- Métodos de instância também podem acessar variáveis e métodos estáticos diretamente.
- Métodos estáticos podem acessar todas as variáveis e métodos estáticos.
- Métodos estáticos **não podem** acessar variáveis e métodos de instância diretamente. Eles precisam de uma referência de objeto para isso.

---

## 4. Os Blocos de Código static
Normalmente, inicializamos variáveis estáticas diretamente durante a declaração.  
No entanto, se as variáveis estáticas exigirem lógica de múltiplas instruções durante a inicialização, podemos usar um bloco estático.

Exemplo:

```java
public class StaticBlockDemo {
    public static List<String> ranks = new LinkedList<>();

    static {
        ranks.add("Lieutenant");
        ranks.add("Captain");
        ranks.add("Major");
    }

    static {
        ranks.add("Colonel");
        ranks.add("General");
    }
}
```

A JVM resolve os campos e blocos estáticos na ordem em que são declarados.  
Principais razões para usar blocos estáticos:
- Inicializar variáveis estáticas com lógica adicional além da atribuição.
- Inicializar variáveis estáticas com tratamento de exceções personalizado.

---

## 5. As Classes Internas static
O Java permite criar uma classe dentro de outra. Isso ajuda a organizar melhor o código.  

Tipos:
- Classes aninhadas declaradas como *static* → chamadas de **classes aninhadas estáticas**.
- Classes aninhadas não estáticas → chamadas de **inner classes**.

Diferença principal:
- Inner classes têm acesso a todos os membros da classe externa (inclusive privados).
- Classes aninhadas estáticas têm acesso apenas a membros estáticos da classe externa.

Exemplo de uso em padrão Singleton:

```java
public class Singleton {
    private Singleton() {}
    private static class SingletonHolder {
        public static final Singleton instance = new Singleton();
    }
    public static Singleton getInstance() {
        return SingletonHolder.instance;
    }
}
```

---

## 6. Entendendo o Erro “Non-static variable cannot be referenced from a static context”
Esse erro ocorre quando uma variável não estática é usada dentro de um contexto estático.  

Exemplo:

```java
public class MyClass {
    int instanceVariable = 0;

    public static void staticMethod() {
        System.out.println(instanceVariable);
    }

    public static void main(String[] args) {
        MyClass.staticMethod();
    }
}
```

Resultado: **Non-static variable cannot be referenced from a static context**.

---

## 7. Conclusão
Neste artigo, vimos a palavra-chave *static* em ação e discutimos os principais motivos para usar campos, métodos, blocos e classes internas estáticas.  
Por fim, aprendemos o que causa o erro **“Non-static variable cannot be referenced from a static context”**.  