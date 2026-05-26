# Modificadores de Acesso em Java

Um modificador de acesso em Java especifica quais classes podem acessar uma determinada classe e seus campos, construtores e métodos. Eles são às vezes chamados informalmente de especificadores de acesso, mas o nome correto é **modificadores de acesso**.

Classes, campos, construtores e métodos podem ter um dos quatro modificadores de acesso:

- **private**
- **default (package)**
- **protected**
- **public**

A tabela a seguir resume em quais construções cada modificador pode ser aplicado:

|               | private | default | protected | public |
|---------------|---------|---------|-----------|--------|
| Classe        | Não     | ✅     | Não       | ✅    |
| Classe Interna| Sim     | Sim     | Sim       | Sim    |
| Construtor    | Sim     | Sim     | Sim       | Sim    |
| Método        | Sim     | Sim     | Sim       | Sim    |
| Campo         | Sim     | Sim     | Sim       | Sim    |

Atribuir um modificador de acesso a uma classe, construtor, campo ou método também é chamado de “marcar” esse elemento como público, privado, etc.

---

## Modificador **private**

Se um método ou variável for marcado como **private**, apenas o código dentro da mesma classe pode acessá-lo. Subclasses ou classes externas não têm acesso. Classes não podem ser marcadas como privadas.

Exemplo:

```java
public class Clock {
    private long time = 0;
}
```

O campo `time` não pode ser acessado fora da classe `Clock`.

### Acessando campos privados via métodos acessores

Campos privados geralmente são acessados por meio de métodos **getters** e **setters**:

```java
public class Clock {
    private long time = 0;

    public long getTime() {
        return this.time;
    }

    public void setTime(long theTime) {
        this.time = theTime;
    }
}
```

### Construtores privados

Um construtor privado não pode ser chamado fora da classe, mas pode ser usado dentro dela:

```java
public class Clock {
    private long time = 0;

    private Clock(long time) {
        this.time = time;
    }

    public Clock(long time, long timeOffset) {
        this(time);
        this.time += timeOffset;
    }

    public static Clock newClock() {
        return new Clock(System.currentTimeMillis());
    }
}
```

---

## Modificador **default (package)**

O modificador **default** é aplicado quando nenhum modificador é escrito. Ele permite acesso dentro da mesma classe e dentro de classes do mesmo pacote. Por isso, também é chamado de **package access modifier**.

Exemplo:

```java
public class Clock {
    long time = 0;
}

public class ClockReader {
    Clock clock = new Clock();

    public long readClock() {
        return clock.time;
    }
}
```

---

## Modificador **protected**

O modificador **protected** funciona como o **default**, mas também permite que subclasses acessem métodos e campos da superclasse, mesmo que estejam em pacotes diferentes.

Exemplo:

```java
public class Clock {
    protected long time = 0; // tempo em milissegundos
}

public class SmartClock extends Clock {
    public long getTimeInSeconds() {
        return this.time / 1000;
    }
}
```

---

## Modificador **public**

O modificador **public** permite acesso de qualquer código, em qualquer classe ou pacote.

Exemplo:

```java
public class Clock {
    public long time = 0;
}

public class ClockReader {
    Clock clock = new Clock();

    public long readClock() {
        return clock.time;
    }
}
```

---

## Modificadores de Classe

O modificador de acesso aplicado a uma classe tem precedência sobre os modificadores de seus membros. Classes só podem ser **default** ou **public**. Não podem ser **private** ou **protected**.

---

## Modificadores de Interface

Interfaces em Java definem métodos e campos que devem ser públicos. Portanto, não é permitido usar **private**, **protected** ou mesmo o **default**. Todos os membros de uma interface são implicitamente **public**.

---

## Modificadores e Herança

Ao sobrescrever métodos em subclasses, não é permitido reduzir o nível de acesso.  
- Se um método na superclasse é **public**, ele deve continuar sendo **public** na subclasse.  
- Se for **protected**, pode ser **protected** ou **public** na subclasse.  
- É permitido aumentar o nível de acesso (por exemplo, de **default** para **public**).
