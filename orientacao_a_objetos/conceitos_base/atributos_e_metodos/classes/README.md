# Classes Java

Classes são alguns dos principais blocos de construção de aplicativos, toolkits, frameworks, APIs, etc e, Java. Um pequeno aplicativo pode consistir em uma única classe com um método `main()` nela, como abordado no tutorial sobre o método main. À medida que o seu aplicativo cresce, manter todo o código na mesma classe se torna cada vez mais difícil de gerenciar. Portanto, pode se tornar necessário começar a dividir o código em múltiplas partes (classes).

Uma classe é uma unidade única e coerente de código que pertence ao mesmo contexto. Ela pode conter uma mistura de dados (variáveis) e ações (métodos). Agrupar variáveis e métodos sobre essas variáveis em classes distintas facilita a estruturação do seu programa caso ele se torne grande demais para visualizar dentro de uma única classe. Uma classe deve ser armazenada em seu próprio arquivo. 

Seu aplicativo normalmente terá que conter pelo menos uma única classe, mas poderá conter quantas classes você julgar necessárias. O Java também dispõe de classes predefinidas, o que dispensa ter que escrever muitas das funções básicas essenciais típicas da programação.

## Blocos de Construção de uma Classe Java

Uma classe poderá conter os seguintes blocos de construção:

* Campos
* Construtores
* Métodos
* Classes Aninhadas

Campos são variáveis (dados) locais à classe, ou instâncias (objetos) dessa classe. Voltaremos às instâncias mais tarde. 

Construtores são métodos que inicializam uma instância da classe. Os construtores frequentemente definem os valores dos campos na instância fornecida.

Métodos são operações que a classe ou instâncias dessa classe podem executar. Por exemplo, um método pode executar uma operação em parâmetros de entrada, ou alterar o valor de campos mantidos internamente no objeto, etc. 

Classes aninhadas são classes Java definidas dentro de outra classe. As classes aninhadas são tipicamente destinadas a serem usadas apenas internamente pela classe que as contém (ou usadas em conexão com as mesmas). 

Nem todas as classes possuem campos, construtores e métodos. Às vezes, classes contêm apenas campos (dados) e, às vezes, apenas métodos (operações).

## Definindo uma Classe em Java

Tudo o que é preciso para definir uma classe em Java é isto:

```java
public class MyClass {

}

```

O código acima define uma classe Java pública chamada `MyClass`. Esta classe não possui campos, construtores ou métodos.

## Arquivos .java

A classe acima deve ser alocada em seu próprio arquivo chamado `MyClass.java`. Os arquivos devem ter o mesmo nome da classe que eles contêm, com extensão `.java`. Certifique-se de manter os mesmos caracteres em maiúsculas e minúsculas do nome da classe também no nome do arquivo.

Use apenas uma única definição de classe em cada arquivo, a menos que sua classe contenha classes internas. 

## Classe Com Campos

Como mencionado anteriormente, uma classe pode conter dados na forma de variáveis. As variáveis que pertencem à classe são tipicamente chamadas de "campos".

O próximo exemplo mostra uma classe que deve modelar um carro. A classe se chama `Car` e possui três campos. Segue o código:

```java
public class Car {
    public String brand = null;
    public String model = null;
    public String color = null;
}

```

Este código define uma classe chamada `Car`. Ela possui três campos e não possui métodos.

## Classe Com Construtor

Uma classe Java pode ter um construtor. Um construtor é um método especial que é chamado quando um objeto da classe fornecida é criado (explicado mais adiante). O propósito de um construtor é inicializar os campos na classe. Os campos também são chamados de "estado interno". segue um exemplo de uma classe Java com dois construtores:

```java
public class Car {
    public String brand = null;
    public String model = null;
    public String color = null;

    public Car() {
    }

    public Car(String theBrand, String theModel, String theColor) {
        this.brand = theBrand;
        this.model = theModel;
        this.color = theColor;
    }
}

```

Os construtores são métodos que têm o mesmo nome que a classe e que não possuem um tipo de retorno especificado. O primeiro construtor não recebe parâmetros e o segundo recebe 3 parâmetros. O construtor que recebe 3 parâmetros armazena os valores desses parâmetros nos campos do objeto criado. 

## Classe Com Métodos

Uma classe pode conter operações. Essas operações são tipicamente chamadas de métodos. Um método contém instruções que tipicamente executam operações em um campo na classe, ou nos valores dos parâmetros (também variáveis) passados para o método quando ele é chamado.

Aqui está o exemplo da classe `Car` com um método adicionado:

```java
public class Car {
    public String brand = null;
    public String model = null;
    public String color = null;

    public void setColor(String newColor) {
        this.color = newColor;
    }
}

```

Na definição da classe acima, foi adicionado o método `setColor()`. Quando chamado, este método define um novo valor para a variável interna de cor. 

## Classe Com Classe Aninhada

Exemplo de classe aninhada:

```java
public class MyClass {

    public static class MyNestedClass{

    }

}

```

No código acima, a classe externa é chamada `MyClass` e a classe aninhada é chamada `MyNestedClass`. Nenhuma das classes neste exemplo possui quaisquer campos ou métodos, mas tanto a classe externa quanto a aninhada poderiam ter tantos campos e métodos quanto necessários. 

## Classes e Objetos

Uma classe Java é um modelo para objetos dessa classe. A  classe `Car` da seção anterior é um modelo para objetos `Car`.

Para criar objetos de uma determinada classe, você usa a palavra-chave `new`. Aqui está um exemplo:

```java
Car car1 = new Car();
Car car2 = new Car();
Car car3 = new Car();

car1.setColor("red");
car2.setColor("green");
car3.setColor("blue");

```

Este exemplo cria 3 variáveis `Car` e atribui uma nova instância da classe `Car` a cada variável. Cada variável faz referência a um objeto `Car` diferente. Tais objetos também são chamados de instâncias. Se você alterar os campos de um objeto, os campos de outros objetos não serão alterados. Portanto, os campos de objetos diferentes (mesmo da mesma classe) podem variar independentemente uns dos outros.

Depois de criar os 3 objetos `Car`, o método `setColor()` é chamado em cada objeto. Agora a cor (representada como um texto) é definida individualmente para cada objeto `Car`.

Criar um objeto de uma determinada classe também é chamado de "instanciar" um objeto. O objeto é, portanto, uma "instância" da classe fornecida. 

## Mais Conceitos

O que você viu neste texto cobre apenas o básico das classes. Mais adiante verremos sobre campos, construtores, métodos, classes aninhadas, classes abstratas, herança, modificadores de acesso e interfaces. Todos serão discutidos seções próprias.


