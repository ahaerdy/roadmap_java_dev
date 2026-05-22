# Escopo de Variáveis em Java 

## 1. Visão Geral

Em Java, assim como em qualquer linguagem de programação, cada variável possui um escopo. Este é o segmento do programa onde uma variável pode ser usada e é válida. Neste tutorial, vamos apresentar os escopos disponíveis em Java e discutir as diferenças entre eles.

## 2. Escopo de Classe

Cada variável declarada dentro das chaves (`{}`) de uma classe com modificador de acesso `private`, mas fora de qualquer método, possui escopo de classe. Como resultado, essas variáveis podem ser usadas em qualquer lugar dentro da classe, mas não fora dela:

```java
public class ClassScopeExample {
    private Integer amount = 0;

    public void exampleMethod() {
        amount++;
    }

    public void anotherExampleMethod() {
        Integer anotherAmount = amount + 4;
    }
}
```

Podemos ver que `ClassScopeExample` possui uma variável de classe `amount` que pode ser acessada dentro dos métodos da classe. Se não usarmos `private`, ela será acessível em todo o pacote. Consulte o artigo sobre modificadores de acesso para mais informações.

## 3. Escopo de Método

Quando uma variável é declarada dentro de um método, ela possui escopo de método e será válida apenas dentro do mesmo método:

```java
public class MethodScopeExample {
    public void methodA() {
        Integer area = 2;
    }

    public void methodB() {
        // erro de compilação, area não pode ser resolvida como variável
        area = area + 2;
    }
}
```

Em `methodA`, criamos uma variável de método chamada `area`. Por essa razão, podemos usar `area` dentro de `methodA`, mas não em nenhum outro lugar.

## 4. Escopo de Loop

Se declararmos uma variável dentro de um loop, ela terá escopo de loop e estará disponível apenas dentro do loop:

```java
public class LoopScopeExample {
    List<String> listOfNames = Arrays.asList("Joe", "Susan", "Pattrick");

    public void iterationOfNames() {
        String allNames = "";
        for (String name : listOfNames) {
            allNames = allNames + " " + name;
        }
        // erro de compilação, name não pode ser resolvida como variável
        String lastNameUsed = name;
    }
}
```

Podemos ver que o método `iterationOfNames` possui uma variável de método chamada `name`. Essa variável pode ser usada apenas dentro do loop e não é válida fora dele.

## 5. Escopo de Bloco

Podemos definir escopos adicionais em qualquer lugar usando chaves (`{}`):

```java
public class BracketScopeExample {
    public void mathOperationExample() {
        Integer sum = 0;
        {
            Integer number = 2;
            sum = sum + number;
        }
        // erro de compilação, number não pode ser resolvida como variável
        number++;
    }
}
```

A variável `number` é válida apenas dentro das chaves.

## 6. Escopos e Sombras de Variáveis

Imagine que temos uma variável de classe e queremos declarar uma variável de método com o mesmo nome:

```java
public class NestedScopesExample {
    String title = "Baeldung";

    public void printTitle() {
        System.out.println(title);
        String title = "John Doe";
        System.out.println(title);
    }
}
```

Na primeira vez que imprimimos `title`, será exibido “Baeldung”. Depois disso, declaramos uma variável de método com o mesmo nome e atribuímos a ela o valor “John Doe”. A variável de método `title` sobrescreve a possibilidade de acessar novamente a variável de classe `title`. Por isso, na segunda vez, será impresso “John Doe”.

Confuso, não? Isso é chamado de **sombras de variáveis** (*variable shadowing*) e não é uma boa prática. É melhor usar o prefixo `this` para acessar a variável de classe `title`, como `this.title`.
