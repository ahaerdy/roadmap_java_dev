# Classes Aninhadas em Java

Em Java, classes aninhadas (nested classes) são classes definidas dentro de outra classe.

O propósito de uma classe aninhada é agrupar claramente a classe aninhada com a classe que a envolve, sinalizando que essas duas classes devem ser usadas juntas. Ou talvez que a classe aninhada só deva ser usada a partir de dentro de sua classe envolvente (proprietária).

Desenvolvedores Java frequentemente se referem a *classes aninhadas* como *classes internas* (inner classes), mas as classes internas (classes aninhadas não estáticas) são apenas um entre vários tipos diferentes de classes aninhadas em Java.

Em Java, as classes aninhadas são consideradas membros de sua classe envolvente. Assim, uma classe aninhada pode ser declarada como `public`, `package` (sem modificador de acesso), `protected` e `private` (veja modificadores de acesso para mais informações). Portanto, classes aninhadas em Java também podem ser herdadas por subclasses, conforme explicado no meu tutorial sobre herança em Java.

Você pode criar vários tipos diferentes de classes aninhadas em Java. Os tipos são:

* Classes aninhadas estáticas (Static nested classes)
* Classes aninhadas não estáticas (Non-static nested classes)
* Classes locais (Local classes)
* Classes anônimas (Anonymous classes)

Todos esses tipos de classes aninhadas serão abordados nas seções seguintes.

## Classes aninhadas estáticas (Static nested classes)

Classes aninhadas estáticas são declaradas em Java desta forma:

```java
public class Outer {

  public static class Nested {

  }

}

```

Para criar uma instância da classe `Nested`, você deve referenciá-la prefixando-a com o nome da classe `Outer`, desta forma:

```java
Outer.Nested instance = new Outer.Nested();

```

Em Java, uma classe aninhada estática é essencialmente uma classe normal que apenas foi aninhada dentro de outra classe. Sendo estática, uma classe aninhada estática só pode acessar variáveis de instância da classe envolvente por meio de uma referência a uma instância da classe envolvente.

## Classes aninhadas não estáticas (Non-static nested classes / Inner Classes)

Classes aninhadas não estáticas em Java também são chamadas de *classes internas* (inner classes). Classes internas estão associadas a uma instância da classe envolvente. Portanto, você deve primeiro criar uma instância da classe envolvente para criar uma instância de uma classe interna. Aqui está um exemplo de definição de classe interna:

```java
public class Outer {

  public class Inner {
  }

}

```

Aqui está como você cria uma instância da classe `Inner`:

```java
Outer outer = new Outer();
Outer.Inner inner = outer.new Inner();

```

Note como você coloca `new` após a referência para a classe externa a fim de criar uma instância da classe interna.

Classes aninhadas não estáticas (classes internas) têm acesso aos campos da classe envolvente, mesmo que sejam declarados como privados. Aqui está um exemplo disso:

```java
public class Outer {

    private String text = "I am private!";

    public class Inner {

        public void printText() {
            System.out.println(text);
        }
    }
}

```

Note como o método `printText()` da classe `Inner` referencia o campo privado `text` da classe `Outer`. Isso é perfeitamente possível. Aqui está como você chamaria o método `printText()`:

```java
Outer outer = new Outer();
Outer.Inner inner = outer.new Inner();
inner.printText();

```

### Inner Class Shadowing

Se uma classe interna em Java declara campos ou métodos com os mesmos nomes que campos ou métodos em sua classe envolvente, diz-se que os campos ou métodos internos causam *sombreamento* (shadow) sobre os campos ou métodos externos. Aqui está um exemplo:

```java
public class Outer {

    private String text = "I am Outer private!";

    public class Inner {

        private String text = "I am Inner private";

        public void printText() {
            System.out.println(text);
        }
    }
}

```

No exemplo acima, tanto a classe `Outer` quanto a `Inner` contêm um campo chamado `text`. Quando a classe `Inner` se refere a `text`, ela se refere ao seu próprio campo. Quando `Outer` se refere a `text`, ela também se refere ao seu próprio campo.

No entanto, o Java torna possível para a classe `Inner` se referir ao campo `text` da classe `Outer`. Para fazer isso, é necessário prefixar a referência do campo `text` com `Outer.this.` (o nome da classe externa + `.this.` + nome do campo) desta forma:

```java
public class Outer {

    private String text = "I am Outer private!";

    public class Inner {

        private String text = "I am Inner private";

        public void printText() {
            System.out.println(text);
            System.out.println(Outer.this.text);
        }
    }
}

```

Agora o método `Inner.printText()` irá imprimir tanto o campo `Inner.text` quanto o `Outer.text`.

## Classes locais (Local classes)

Classes locais em Java são como classes internas (classes aninhadas não estáticas) que são definidas dentro de um método ou bloco de escopo (`{ ... }`) dentro de um método. Aqui está um exemplo:

```java
class Outer {

    public void printText() {

        class Local {

        }

        Local local = new Local();
    }

}

```

Classes locais só podem ser acessadas de dentro do método ou bloco de escopo no qual foram definidas.

Classes locais podem acessar membros (campos e métodos) de sua classe envolvente exatamente como classes internas regulares.

Classes locais também podem acessar variáveis locais dentro do mesmo método ou bloco de escopo, desde que essas variáveis sejam declaradas como `final`.

A partir do Java 8, classes locais também podem acessar variáveis locais e parâmetros do método no qual a classe local é declarada. O parâmetro terá que ser declarado como `final` ou ser *efetivamente final* (effectually final). Efetivamente final significa que a variável nunca é alterada após ser inicializada. Parâmetros de método são frequentemente efetivamente finais.

Classes locais também podem ser declaradas dentro de métodos estáticos. Nesse caso, a classe local só tem acesso às partes estáticas da classe envolvente. Classes locais não podem conter todos os tipos de declarações estáticas (constantes são permitidas - variáveis declaradas como `static final`), porque as classes locais são não estáticas por natureza - mesmo se declaradas dentro de um método estático.

As mesmas regras de sombreamento se aplicam para classes locais e para classes internas.

## Classes anônimas (Anonymous classes)

Classes anônimas em Java são classes aninhadas sem um nome de classe. Elas são tipicamente declaradas como subclasses de uma classe existente ou como implementações de alguma interface.

Classes anônimas são definidas quando são instanciadas. Aqui está um exemplo que declara uma subclasse anônima de uma superclasse chamada `SuperClass`:

```java
public class SuperClass {

  public void doIt() {
    System.out.println("SuperClass doIt()");
  }

}

```

```java
SuperClass instance = new SuperClass() {

    public void doIt() {
        System.out.println("Anonymous class doIt()");
    }
};

instance.doIt();

```

Executar este código Java resultaria em `Anonymous class doIt()` sendo impresso no `System.out`. A classe anônima herda (estende) de `SuperClass` e sobrescreve o método `doIt()`.

Uma classe anônima em Java também pode implementar uma interface em vez de estender uma classe. Aqui está um exemplo:

```java
public interface MyInterface {

  public void doIt();

}

```

```java
MyInterface instance = new MyInterface() {

    public void doIt() {
        System.out.println("Anonymous class doIt()");
    }
};

instance.doIt();

```

Como você pode ver, uma classe anônima que implementa uma interface é bastante semelhante a uma classe anônima que estende outra classe.

Uma classe anônima pode acessar membros da classe envolvente. Ela também pode acessar variáveis locais que são declaradas como final ou efetivamente finais (desde o Java 8).

Você pode declarar campos e métodos dentro de uma classe anônima, mas não pode declarar um construtor. No entanto, você pode declarar um inicializador estático para a classe anônima. Aqui está um exemplo:

```java
final String textToPrint = "Text...";

MyInterface instance = new MyInterface() {

    private String text;

    //inicializador estático (bloco de inicialização de instância)
    {  this.text = textToPrint;  }

    public void doIt() {
        System.out.println(this.text);
    }
};

instance.doIt();

```

As mesmas regras de sombreamento se aplicam às classes anônimas e às classes internas.

## Benefits das Classes Aninhadas

Os benefícios das classes aninhadas em Java são que você pode agrupar classes que pertencem uma à outra. Você já poderia fazer isso colocando-as no mesmo pacote, mas colocar uma classe dentro de outra cria um agrupamento ainda mais forte.

Uma classe aninhada é tipicamente usada apenas *por* ou *com* sua classe envolvente. Às vezes, uma classe aninhada é visível apenas para a classe envolvente, é usada apenas internamente e, portanto, nunca é visível fora da classe envolvente. Outras vezes, a classe aninhada é visível fora de sua classe envolvente, mas só pode ser usada em conjunto com ela.

Um exemplo seria uma classe `Cache`. Dentro da classe `Cache`, você pode declarar uma classe `CacheEntry` que pode conter informações sobre uma entrada de cache específica (valor em cache, hora de inserção, número de vezes acessada, etc.). Os usuários da classe `Cache` podem nunca ver a classe `CacheEntry`, se não tiverem necessidade de obter informações sobre a própria `CacheEntry`, mas apenas o valor em cache. No entanto, a classe `Cache` pode optar por tornar a classe `CacheEntry` visível para o mundo externo, para que eles possam acessar mais do que apenas o valor em cache (por exemplo, informações sobre quando o valor foi atualizado pela última vez, etc.).

Aqui estão dois esqueletos de implementação de `Cache` que ilustram esses pontos:

```java
public class Cache {

    private Map<String, CacheEntry> cacheMap = new HashMap<String, CacheEntry>();

    private class CacheEntry {
        public long   timeInserted = 0;
        public Object value        = null;
    }

    public void store(String key, Object value){
        CacheEntry entry = new CacheEntry();
        entry.value = value;
        entry.timeInserted = System.currentTimeMillis();
        this.cacheMap.put(key, entry);
    }

    public Object get(String key) {
        CacheEntry entry = this.cacheMap.get(key);
        if(entry == null) return null;
        return entry.value;
    }

}

```

```java
public class Cache {

    private Map<String, CacheEntry> cacheMap = new HashMap<String, CacheEntry>();

    public class CacheEntry {
        public long   timeInserted = 0;
        public Object value        = null;
    }

    public void store(String key, Object value){
        CacheEntry entry = new CacheEntry();
        entry.value = value;
        entry.timeInserted = System.currentTimeMillis();
        this.cacheMap.put(key, entry);
    }

    public Object get(String key) {
        CacheEntry entry = this.cacheMap.get(key);
        if(entry == null) return null;
        return entry.value;
    }

    public CacheEntry getCacheEntry(String key) {
        return this.cacheMap.get(key);
    }

}

```

A primeira classe `Cache` esconde sua classe aninhada `CacheEntry`, enquanto a segunda classe `Cache` a expõe.

```
