# Classes Java

As classes Java são alguns dos principais blocos de construção de aplicativos, toolkits, frameworks, APIs Java, etc. Um pequeno aplicativo Java pode consistir em uma única classe Java com um método `main()` nela, como abordado no tutorial sobre o método main em Java. À medida que o seu aplicativo Java cresce, manter todo o código na mesma classe torna cada vez mais difícil manter uma visão geral do código. Portanto, pode ser benéfico começar a dividir o código Java em múltiplas classes.

Uma classe é uma unidade única e coerente de código que pertence ao mesmo contexto. Uma classe pode conter uma mistura de dados (variáveis) e ações (métodos). Agrupar variáveis e operações sobre essas variáveis em classes facilita a estruturação do seu programa quando ele se torna grande demais para caber confortavelmente dentro de uma única classe. Uma classe deve ser armazenada em seu próprio arquivo. Portanto, à medida que a classe cresce, o arquivo que você está editando também cresce e se torna mais difícil de manter uma visão geral na sua mente.

Seu aplicativo normalmente terá que conter pelo menos uma única classe, mas pode conter quantas classes julgar adequado para dividir o seu aplicativo. O Java também vem com muitas classes predefinidas, para que você não precise codificar funções básicas essenciais.

## Blocos de Construção de uma Classe Java

Uma classe Java pode conter os seguintes blocos de construção:

* Campos
* Construtores
* Métodos
* Classes Aninhadas

Campos são variáveis (dados) que são locais à classe, ou instâncias (objetos) dessa classe. Voltarei às instâncias mais tarde. Os campos são abordados em mais detalhes no meu tutorial sobre campos em Java.

Construtores são métodos que inicializam uma instância da classe. Os construtores frequentemente definem os valores dos campos na instância fornecida. Os construtores são abordados em mais detalhes no meu tutorial sobre construtores em Java.

Métodos são operações que a classe ou instâncias dessa classe podem executar. Por exemplo, um método pode executar uma operação em parâmetros de entrada, ou alterar o valor de campos mantidos internamente no objeto, etc. Os métodos são abordados em mais detalhes no meu tutorial sobre métodos em Java.

Classes aninhadas são classes Java que são definidas dentro de outra classe. As classes aninhadas são tipicamente destinadas a serem usadas apenas internamente pela classe Java que as contém, ou a serem usadas em conexão com a classe que as contém. As classes aninhadas são abordadas em mais detalhes no meu tutorial sobre classes aninhadas em Java.

Nem todas as classes Java possuem campos, construtores e métodos. Às vezes, você tem classes que contêm apenas campos (dados) e, às vezes, você tem classes que contêm apenas métodos (operações). Depende do que a classe Java deve fazer.

## Definindo uma Classe em Java

Tudo o que é preciso para definir uma classe em Java é isto:

```java
public class MyClass {

}

```

Isso define uma classe Java pública chamada `MyClass`. A classe não possui campos, construtores ou métodos.

## Arquivos .java

A definição da classe acima deve ser colocada em seu próprio arquivo chamado `MyClass.java`. Os arquivos Java devem ter o mesmo nome da classe que eles contêm, com a extensão de arquivo `.java`. Certifique-se de manter os mesmos caracteres em maiúsculas e minúsculas do nome da classe também no nome do arquivo.

Coloque apenas uma única definição de classe em cada arquivo Java, a menos que sua classe contenha classes internas de algum tipo. As classes internas são abordadas no meu tutorial sobre classes aninhadas em Java.

## Classe Com Campos

Como mencionado anteriormente, uma classe Java pode conter dados na forma de variáveis. As variáveis que pertencem à classe são tipicamente chamadas de "campos".

O próximo exemplo mostra uma classe Java que deve modelar um carro. Portanto, a classe se chama `Car` e possui três campos. Aqui está a classe Java em código:

```java
public class Car {
    public String brand = null;
    public String model = null;
    public String color = null;
}

```

Este código define uma classe Java chamada `Car`. A classe `Car` possui três campos. A classe `Car` não possui métodos. Apenas declarações de campo. Os campos são descritos em mais detalhes no texto sobre campos em Java.

## Classe Com Construtor

Uma classe Java pode ter um construtor. Um construtor é um método especial que é chamado quando um objeto da classe fornecida é criado (explicado mais adiante). O propósito de um construtor é inicializar os campos na classe. Os campos também são chamados de "estado interno". Aqui está um exemplo de uma classe Java com dois construtores:

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

Os construtores são os dois métodos que têm o mesmo nome que a classe e que não possuem um tipo de retorno especificado. O primeiro construtor não recebe parâmetros e o segundo recebe 3 parâmetros. O construtor que recebe 3 parâmetros armazena os valores desses parâmetros nos campos do objeto criado. Os construtores são abordados em mais detalhes no meu tutorial sobre construtores em Java.

## Classe Com Métodos

Uma classe Java também pode conter operações. Essas operações são tipicamente chamadas de métodos. Um método Java contém instruções Java que tipicamente executam algumas operações em um campo na classe, ou nos valores de um dos parâmetros (também variáveis) passados para o método quando ele foi chamado.

Aqui está o exemplo da classe Java `Car` da seção anterior com um método adicionado:

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

Na definição da classe acima, adicionei um método `setColor()`. Quando chamado, este método define a variável interna de cor (campo) para um novo valor. Os métodos são descritos em mais detalhes no texto sobre métodos.

## Classe Com Classe Aninhada

Como mencionado anteriormente, você pode definir uma classe aninhada dentro de outra classe Java. Aqui está um exemplo da definição de uma classe aninhada dentro de uma classe Java:

```java
public class MyClass {

    public static class MyNestedClass{

    }

}

```

No exemplo acima, a classe externa é chamada `MyClass` e a classe aninhada é chamada `MyNestedClass`. Nenhuma das classes neste exemplo possui quaisquer campos ou métodos, mas tanto a classe externa quanto a aninhada poderiam ter tantos campos e métodos quanto você julgasse adequado. Você pode ler mais sobre classes aninhadas no meu tutorial sobre classes aninhadas em Java.

## Classes e Objetos

Uma classe Java é um modelo para a aparência de objetos dessa classe. Em outras palavras, a classe `Car` na seção anterior é um modelo para a aparência dos objetos `Car`.

Para criar objetos de uma determinada classe, você usa a palavra-chave `new`. Aqui está um exemplo:

```java
Car car1 = new Car();
Car car2 = new Car();
Car car3 = new Car();

car1.setColor("red");
car2.setColor("green");
car3.setColor("blue");

```

Este exemplo cria 3 variáveis `Car` e atribui uma nova instância da classe `Car` a cada variável. Cada variável agora faz referência a um objeto `Car`. Cada variável faz referência a um objeto `Car` diferente. Tais objetos também são chamados de instâncias. Se você alterar os campos de um objeto, os campos de outros objetos não serão alterados. Portanto, os campos de objetos diferentes (mesmo da mesma classe) podem variar independentemente uns dos outros.

Depois de criar os 3 objetos `Car`, o método `setColor()` é chamado em cada objeto. Agora a cor (representada como um texto) é definida individualmente para cada objeto `Car`.

Criar um objeto de uma determinada classe também é chamado de "instanciar" um objeto. O objeto é, portanto, também chamado de uma "instância" da classe fornecida. Por exemplo, cada um dos objetos `Car` acima também é chamado de uma instância da classe `Car`, ou simplesmente "instâncias de Car".

## Mais Conceitos sobre Classes Java

O que você viu neste texto cobre apenas o básico das classes Java. Você precisa aprender sobre campos, construtores, métodos, classes aninhadas, classes abstratas, herança, modificadores de acesso e interfaces também. Todos esses conceitos são discutidos em seus próprios textos.

## Classes em Outras Linguagens de Programação

Classes são um conceito comum em muitas linguagens de programação. Aqui estão os links para os tutoriais sobre classes nas linguagens de programação abordadas neste site:

* Classes em Java
* Classes em Python

