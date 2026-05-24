# Introdução à Programação Orientada a Onjetos

## Classes Java

### Blocos de Construção de Classes Java
- Definindo uma Classe em Java
- Arquivos .java
- Classe com Campos
- Classe com Construtor
- Classe com Métodos
- Classe com Classe Aninhada
- Classes e Objetos
- Conceitos Adicionais para Classes Java
- Classes em Outras Linguagens de Programação  

Jakob Jenkov  
Última atualização: 30-07-2024  

As classes Java são alguns dos blocos de construção centrais de aplicações Java, toolkits, frameworks, APIs etc. Uma pequena aplicação Java pode consistir em uma única classe Java com um método `main()`, como abordado no tutorial sobre o método main em Java.  

À medida que sua aplicação Java cresce, manter todo o código na mesma classe torna cada vez mais difícil ter uma visão geral. Portanto, pode ser benéfico começar a dividir o código Java em várias classes.  

Uma classe Java é uma unidade única e coerente de código Java que pertence junto. Uma classe Java pode conter uma mistura de dados (variáveis) e ações (métodos). Agrupar variáveis e operações sobre essas variáveis em classes Java facilita estruturar seu programa quando ele fica grande demais para caber confortavelmente em uma única classe.  

Uma classe Java deve ser armazenada em seu próprio arquivo. Portanto, à medida que a classe cresce, o arquivo também cresce e se torna mais difícil de manter uma visão geral mental.  

Sua aplicação Java normalmente terá que conter pelo menos uma classe Java, mas pode conter quantas classes você achar adequado para dividir sua aplicação. O Java também vem com muitas classes pré-definidas, para que você não precise codificar cada pequena função desejada.  

---

## Blocos de Construção de Classes Java
Uma classe Java pode conter os seguintes blocos de construção:
- **Campos**  
- **Construtores**  
- **Métodos**  
- **Classes Aninhadas**

**Campos** são variáveis (dados) locais da classe ou instâncias (objetos) dessa classe.  

**Construtores** são métodos que inicializam uma instância da classe.  

**Métodos** são operações que a classe ou suas instâncias podem executar.  

**Classes aninhadas** são classes definidas dentro de outra classe.  

Nem todas as classes Java possuem campos, construtores e métodos. Às vezes, você tem classes que contêm apenas campos (dados) ou apenas métodos (operações).  

---

## Definindo uma Classe em Java
```java
public class MyClass {
}
```
Isso define uma classe pública chamada `MyClass`. A classe não possui campos, construtores ou métodos.  

---

## Arquivos .java
A definição acima deve ser colocada em um arquivo chamado `MyClass.java`. Os arquivos Java devem ter o mesmo nome da classe que contêm, com a extensão `.java`.  

---

## Classe com Campos
```java
public class Car {
    public String brand = null;
    public String model = null;
    public String color = null;
}
```
Essa classe `Car` possui três campos (`brand`, `model`, `color`).  

---

## Classe com Construtor
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
Aqui temos dois construtores: um sem parâmetros e outro com três parâmetros.  

---

## Classe com Métodos
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
O método `setColor()` altera o valor do campo `color`.  

---

## Classe com Classe Aninhada
```java
public class MyClass {
    public static class MyNestedClass {
    }
}
```
A classe externa é `MyClass` e a classe aninhada é `MyNestedClass`.  

---

## Classes e Objetos
```java
Car car1 = new Car();
Car car2 = new Car();
Car car3 = new Car();

car1.setColor("red");
car2.setColor("green");
car3.setColor("blue");
```
Cada variável referencia um objeto diferente da classe `Car`. Esses objetos são chamados de **instâncias**.  

---

## Conceitos Adicionais para Classes Java
Além dos conceitos básicos, você precisa aprender sobre:
- Campos
- Construtores
- Métodos
- Classes aninhadas
- Classes abstratas
- Herança
- Modificadores de acesso
- Interfaces  

---

## Classes em Outras Linguagens de Programação
Classes são um conceito comum em muitas linguagens de programação.  
- Classes em Java  
- Classes em Python  

