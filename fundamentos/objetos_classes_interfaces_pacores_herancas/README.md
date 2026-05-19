# Programação Orientada a Objetos em Java

Este guia apresenta os conceitos fundamentais da **Programação Orientada a Objetos (POO)** em Java: objetos, classes, herança, interfaces e pacotes. Cada seção conecta os conceitos ao mundo real e mostra como eles se traduzem na sintaxe da linguagem.

---

## O que é um Objeto?

Um **objeto** é um conjunto de **estado** e **comportamento** relacionados.

- **Estado**: armazenado em **campos** (variáveis).
- **Comportamento**: exposto por **métodos** (funções).

Exemplos:
- Um **cachorro** tem estado (nome, cor, raça, fome) e comportamento (latir, buscar, abanar o rabo).
- Uma **bicicleta** tem estado (marcha atual, cadência do pedal, velocidade) e comportamento (mudar marcha, alterar cadência, frear).

👉 Esse conceito é chamado de **encapsulamento de dados**: o objeto controla como seu estado interno pode ser acessado ou modificado.

### Benefícios de usar objetos
- **Modularidade**: código independente e reutilizável.
- **Ocultação de informação**: detalhes internos escondidos, interação apenas via métodos.
- **Reuso de código**: objetos prontos podem ser usados em novos programas.
- **Facilidade de manutenção**: substituição de componentes problemáticos sem afetar o sistema inteiro.

---

## O que é uma Classe?

Uma **classe** é o **projeto (blueprint)** a partir do qual objetos são criados.

Exemplo de classe `Bicycle`:

```java
class Bicycle {
    int cadence = 0;
    int speed = 0;
    int gear = 1;

    void changeCadence(int newValue) { cadence = newValue; }
    void changeGear(int newValue) { gear = newValue; }
    void speedUp(int increment) { speed += increment; }
    void applyBrakes(int decrement) { speed -= decrement; }

    void printStates() {
        System.out.println("cadence:" + cadence + " speed:" + speed + " gear:" + gear);
    }
}
```

Exemplo de uso (`BicycleDemo`):

```java
class BicycleDemo {
    public static void main(String[] args) {
        Bicycle bike1 = new Bicycle();
        Bicycle bike2 = new Bicycle();

        bike1.changeCadence(50);
        bike1.speedUp(10);
        bike1.changeGear(2);
        bike1.printStates();

        bike2.changeCadence(50);
        bike2.speedUp(10);
        bike2.changeGear(2);
        bike2.changeCadence(40);
        bike2.speedUp(10);
        bike2.changeGear(3);
        bike2.printStates();
    }
}
```

---

## O que é Herança?

A **herança** permite que classes compartilhem estado e comportamento comuns.

Exemplo:
- `Bicycle` é a **superclasse**.
- `MountainBike`, `RoadBike` e `TandemBike` são **subclasses** que herdam os atributos e métodos de `Bicycle`.

Sintaxe:

```java
class MountainBike extends Bicycle {
    // código específico da MountainBike
}
```

---

## O que é uma Interface?

Uma **interface** define um contrato de métodos que uma classe deve implementar.

Exemplo de interface:

```java
interface Bicycle {
    void changeCadence(int newValue);
    void changeGear(int newValue);
    void speedUp(int increment);
    void applyBrakes(int decrement);
}
```

Implementação:

```java
class ACMEBicycle implements Bicycle {
    int cadence = 0;
    int speed = 0;
    int gear = 1;

    public void changeCadence(int newValue) { cadence = newValue; }
    public void changeGear(int newValue) { gear = newValue; }
    public void speedUp(int increment) { speed += increment; }
    public void applyBrakes(int decrement) { speed -= decrement; }
}
```

As **interfaces** em Java são úteis porque permitem definir um contrato claro de métodos que diferentes classes podem implementar, mesmo que não estejam relacionadas por herança. Isso promove flexibilidade e desacoplamento, já que **uma interface descreve apenas o que deve ser feito, sem impor como será feito**. Assim, diferentes classes podem compartilhar a mesma interface e oferecer implementações distintas, facilitando a substituição de componentes, a integração de sistemas e a criação de código mais modular e reutilizável.

---

## O que é um Pacote?

Um **pacote** é um espaço de nomes que organiza classes e interfaces relacionadas.  
Exemplo: o **Java API** fornece milhares de classes organizadas em pacotes, como:

- `String` (manipulação de texto)
- `File` (operações em arquivos)
- `Socket` (comunicação em rede)
- Classes de GUI (interfaces gráficas)

👉 Pacotes ajudam a manter grandes projetos organizados e reutilizáveis.

