# Classes e Objetos em Java

## Classes e Objetos em Java
Java é uma linguagem de programação orientada a objetos. O conceito central da abordagem orientada a objetos é dividir problemas complexos em objetos menores.

Um objeto é qualquer entidade que possui estado e comportamento. Por exemplo, uma bicicleta é um objeto.  

Ela possui:
- **Estados**: parada, primeira marcha, etc.  
- **Comportamentos**: frear, acelerar, etc.

Antes de aprendermos sobre objetos, vamos primeiro conhecer as classes em Java.

---

## Classe em Java
Uma classe é um **modelo** para o objeto. Antes de criar um objeto, precisamos definir a classe.

Podemos pensar na classe como um esboço (protótipo) de uma casa. Ela contém todos os detalhes sobre os andares, portas, janelas, etc. Com base nessas descrições, construímos a casa. A casa é o objeto. Como muitas casas podem ser feitas a partir da mesma descrição, podemos criar muitos objetos a partir de uma classe.

### Criar uma classe em Java
Podemos criar uma classe em Java usando a palavra-chave `class`.

```java
class ClassName {
  // fields
  // methods
}
```

Aqui:
- **fields (campos)** representam o estado do objeto.  
- **methods (métodos)** representam o comportamento do objeto.  

Exemplo para o objeto bicicleta:

```java
class Bicycle {
  // estado ou campo
  private int gear = 5;

  // comportamento ou método
  public void braking() {
    System.out.println("Working of Braking");
  }
}
```

No exemplo acima, criamos uma classe chamada `Bicycle`.  
Ela contém um campo chamado `gear` e um método chamado `braking()`.  
`Bicycle` é um protótipo. Agora podemos criar qualquer número de bicicletas usando esse protótipo.  
Todas as bicicletas compartilharão os campos e métodos do protótipo.

**Nota:** Usamos as palavras-chave `private` e `public`. Elas são chamadas de **modificadores de acesso**.

---

## Objetos em Java
Um objeto é chamado de **instância de uma classe**.  
Por exemplo, suponha que `Bicycle` seja uma classe, então `MountainBicycle`, `SportsBicycle`, `TouringBicycle`, etc. podem ser considerados objetos da classe.

### Criando um objeto em Java
```java
className object = new className();

// para a classe Bicycle
Bicycle sportsBicycle = new Bicycle();
Bicycle touringBicycle = new Bicycle();
```

Usamos a palavra-chave `new` junto com o **construtor** da classe para criar um objeto.  
Construtores são semelhantes a métodos e têm o mesmo nome da classe.  
Por exemplo, `Bicycle()` é o construtor da classe `Bicycle`.

Aqui, `sportsBicycle` e `touringBicycle` são os nomes dos objetos. Podemos usá-los para acessar campos e métodos da classe.  
Podemos criar múltiplos objetos de uma única classe em Java.

**Nota:** Campos e métodos de uma classe também são chamados de **membros da classe**.

---

## Acessando membros de uma classe
Podemos usar o nome dos objetos junto com o operador `.` para acessar membros de uma classe.

```java
class Bicycle {
  // campo da classe
  int gear = 5;

  // método da classe
  void braking() { ... }
}

// criar objeto
Bicycle sportsBicycle = new Bicycle();

// acessar campo e método
sportsBicycle.gear;
sportsBicycle.braking();
```

Aqui, criamos um objeto `sportsBicycle` da classe `Bicycle`.  
Usamos o objeto para acessar o campo `gear` e o método `braking()`.

---

## Exemplo: Classe e Objetos em Java
```java
class Lamp {
  // armazena o valor da luz
  // true se a luz estiver ligada
  // false se a luz estiver desligada
  boolean isOn;

  // método para ligar a luz
  void turnOn() {
    isOn = true;
    System.out.println("Light on? " + isOn);
  }

  // método para desligar a luz
  void turnOff() {
    isOn = false;
    System.out.println("Light on? " + isOn);
  }
}

public class Main {
  public static void main(String[] args) {
    // criar objetos led e halogen
    Lamp led = new Lamp();
    Lamp halogen = new Lamp();

    // ligar a luz chamando turnOn()
    led.turnOn();

    // desligar a luz chamando turnOff()
    halogen.turnOff();
  }
}
```

**Saída:**
```
Light on? true
Light on? false
```

Neste programa, criamos uma classe chamada `Lamp`.  
Ela contém uma variável `isOn` e dois métodos: `turnOn()` e `turnOff()`.  
Na classe `Main`, criamos dois objetos: `led` e `halogen`.  
Usamos os objetos para chamar os métodos da classe.

- `led.turnOn()` → define `isOn` como `true` e imprime a saída.  
- `halogen.turnOff()` → define `isOn` como `false` e imprime a saída.  

A variável `isOn` definida dentro da classe também é chamada de **variável de instância**, pois cada objeto terá sua própria cópia da variável.

---

## Exemplo: Criar objetos dentro da mesma classe
No exemplo anterior, criamos objetos dentro de outra classe.  
Mas também podemos criar objetos dentro da mesma classe:

```java
class Lamp {
  boolean isOn;

  void turnOn() {
    isOn = true;
    System.out.println("Light on? " + isOn);
  }

  public static void main(String[] args) {
    // criar objeto da classe Lamp
    Lamp led = new Lamp();

    // acessar método usando objeto
    led.turnOn();
  }
}
```

**Saída:**
```
Light on? true
```

Aqui, criamos o objeto dentro do método `main()` da mesma classe.