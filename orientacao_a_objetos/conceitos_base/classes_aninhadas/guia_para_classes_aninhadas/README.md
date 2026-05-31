# Classes Aninhadas em Java

Última atualização: 11 de junho de 2024

Escrito por: baeldung
Revisado por: Grzegorz Piwowarek

## **1. Introdução**

Este tutorial é uma introdução rápida e direta às classes aninhadas na linguagem Java.

De forma simples, o Java nos permite definir classes dentro de outras classes. **Classes aninhadas nos permitem agrupar logicamente classes que são usadas em apenas um lugar, escrever códigos mais legíveis e fáceis de manter, além de aumentar o encapsulamento.**

Antes de começarmos, vamos dar uma olhada nos diversos tipos de classes aninhadas disponíveis na linguagem:

* [Classes aninhadas estáticas](#2-classes-aninhadas-estáticas)
* [Classes aninhadas não estáticas](#3-classes-aninhadas-não-estáticas)
* [Classes locais](#31-classes-locais)
* [Classes anônimas](#32-classes-anônimas)

Nas próximas seções, discutiremos cada uma delas detalhadamente.

## **2. Classes Aninhadas Estáticas**

Aqui estão alguns pontos a serem lembrados sobre classes aninhadas antes de começarmos:

* Assim como os membros estáticos, elas pertencem à sua classe envolvente, e não a uma instância da classe
* Elas podem ter todos os tipos de modificadores de acesso em sua declaração
* Elas só têm acesso a membros estáticos na classe envolvente
* Elas podem definir tanto membros estáticos quanto não estáticos

Vamos ver como podemos declarar uma classe aninhada estática:

```
public class Enclosing {
    
    private static int x = 1;
    
    public static class StaticNested {

        private void run() {
            // method implementation
        }
    }
    
    @Test
    public void test() {
        Enclosing.StaticNested nested = new Enclosing.StaticNested();
        nested.run();
    }
}
```

## **3. Classes Aninhadas Não Estáticas**

A seguir, aqui estão alguns pontos rápidos a serem lembrados sobre classes aninhadas não estáticas:

* Elas também são chamadas de classes internas
* Elas podem ter todos os tipos de modificadores de acesso em sua declaração
* Assim como as variáveis e métodos de instância, as classes internas estão associadas a uma instância da classe envolvente
* Elas têm acesso a todos os membros da classe envolvente, independentemente de serem estáticos ou não estáticos
* Elas só podem definir membros não estáticos

Aqui está como podemos declarar uma classe interna:

```
public class Outer {
    
    public class Inner {
        // ...
    }
}
```

Se declararmos uma classe aninhada com o modificador *static*, então ela será um membro estático. Caso contrário, será uma classe interna. Embora sintaticamente a diferença seja apenas uma única palavra-chave (ou seja, *static*), semanticamente existe uma enorme diferença entre esses tipos de classes aninhadas. Instâncias de classes internas estão vinculadas às instâncias da classe envolvente e, portanto, têm acesso aos seus membros. Devemos estar cientes disso ao escolher se tornamos uma classe aninhada em uma classe interna ou não.

**Para instanciar uma classe interna, devemos primeiro instanciar sua classe envolvente.**

Vamos ver como podemos fazer isso:

```
Outer outer = new Outer();
Outer.Inner inner = outer.new Inner();
```

Nas próximas subseções, mostraremos alguns tipos especiais de classes internas.

### **3.1. Classes Locais**

As classes locais são um tipo especial de classes internas – nas quais **a classe é definida dentro de um método** ou bloco de escopo.

Vamos ver alguns pontos a serem lembrados sobre este tipo de classe:

* Elas não podem ter modificadores de acesso em sua declaração
* Elas têm acesso tanto a membros estáticos quanto não estáticos no contexto envolvente
* Elas só podem definir membros de instância

Aqui está um exemplo rápido:

```
public class NewEnclosing {
    
    void run() {
        class Local {

            void run() {
                // method implementation
            }
        }
        Local local = new Local();
        local.run();
    }
    
    @Test
    public void test() {
        NewEnclosing newEnclosing = new NewEnclosing();
        newEnclosing.run();
    }
}
```

### **3.2. Classes Anônimas**

As classes anônimas podem ser usadas para definir uma implementação de uma interface ou de uma classe abstrata sem a necessidade de criar uma implementação reutilizável.

Vamos listar alguns pontos a serem lembrados sobre classes anônimas:

* Elas não podem ter modificadores de acesso em sua declaração
* Elas têm acesso tanto a membros estáticos quanto não estáticos no contexto envolvente
* Elas só podem definir membros de instância
* Elas são o único tipo de classes aninhadas que não podem definir construtores ou estender/implementar outras classes ou interfaces

Para definir uma classe anônima, vamos primeiro definir uma classe abstrata simples:

```
abstract class SimpleAbstractClass {
    abstract void run();
}
```

Agora vamos ver como podemos definir uma classe anônima:

```
public class AnonymousInnerUnitTest {
    
    @Test
    public void whenRunAnonymousClass_thenCorrect() {
        SimpleAbstractClass simpleAbstractClass = new SimpleAbstractClass() {
            void run() {
                // method implementation
            }
        };
        simpleAbstractClass.run();
    }
}
```

Para mais detalhes, você pode achar útil nosso tutorial sobre [Classes Anônimas em Java](/java-anonymous-classes).

## **4. Sombreamento**

**A declaração dos membros de uma classe interna sombreia os da classe envolvente** se eles tiverem o mesmo nome.

Nesse caso, a palavra-chave *this* se refere às instâncias da classe aninhada e os membros da classe externa podem ser referenciados usando o nome da classe externa.

Vamos ver um exemplo rápido:

```
public class NewOuter {

    int a = 1;
    static int b = 2;

    public class InnerClass {
        int a = 3;
        static final int b = 4;

        public void run() {
            System.out.println("a = " + a);
            System.out.println("b = " + b);
            System.out.println("NewOuterTest.this.a = " + NewOuter.this.a);
            System.out.println("NewOuterTest.b = " + NewOuter.b);
            System.out.println("NewOuterTest.this.b = " + NewOuter.this.b);
        }
    }

    @Test
    public void test() {
        NewOuter outer = new NewOuter();
        NewOuter.InnerClass inner = outer.new InnerClass();
        inner.run();

    }
}
```

## **5. Serialização**

Para evitar uma exceção *java.io.NotSerializableException* ao tentar serializar uma classe aninhada, devemos:

* Declarar a classe aninhada como *static*
* Fazer com que tanto a classe aninhada quanto a classe envolvente implementem *Serializable*

## **6. Conclusão**

Neste artigo, vimos o que são classes aninhadas e seus diferentes tipos. Também analisamos como a visibilidade de campos e modificadores de acesso diferem entre esses diferentes tipos.

O código que suporta este artigo está disponível no GitHub. Assim que você estiver **logado como um [Membro Baeldung Pro](/members/)**, comece a aprender e a codificar no projeto.
