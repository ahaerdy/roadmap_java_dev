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
| Classe        | ❌     | ✅     | ❌       | ✅    |
| Classe Interna| ✅     | ✅     | ✅       | ✅    |
| Construtor    | ✅     | ✅     | ✅       | ✅    |
| Método        | ✅     | ✅     | ✅       | ✅    |
| Campo         | ✅     | ✅     | ✅       | ✅    |

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

<details>
<summary> 💡 Exemplos práticos (🖱️ <b><ins>clique aqui</ins></b>)</summary>
</br>
Aqui estão os exemplos práticos de onde a variável `private` <strong>pode</strong> e <strong>não pode</strong> ser acessada, seguindo a mesma estrutura:</br>
</br>
🟩 Onde PODE ser acessada (Apenas dentro da mesma classe)

O modificador `private` restringe o acesso exclusivamente ao escopo da própria classe onde a variável foi declarada.

```java
/**
 * A classe Clock demonstra o conceito de ocultamento de dados (Data Hiding).
 */
public class Clock {

    // O modificador 'private' restringe o acesso diretamente a esta classe.
    // Nenhuma classe externa (nem mesmo a Main) pode ler ou alterar 
    // 'time' diretamente, protegendo o estado interno do objeto.
    // O valor 1000 aqui representa 10:00 em um formato simplificado (HHmm).
    private long time = 1000;

    /**
     * Este é um método 'getter'. Ele é public, o que significa que 
     * serve como a interface oficial para o mundo exterior.
     *
     * FUNCIONA: O método 'readClock' está DENTRO da classe Clock,
     * então ele tem permissão total para acessar a variável 'private time'.
     */
    public long readClock() {
        // O uso do 'this' referencia o atributo da própria instância.
        return this.time;
    }
}
```

---

### 🔴 Onde NÃO PODE ser acessada (Classes externas ou Subclasses)

Nenhuma outra classe no universo do seu código — mesmo que seja uma herança (subclasse) ou que esteja no mesmo pacote — conseguirá tocar nessa variável diretamente.

#### Cenário 1: Uma classe externa tentando acessar

```java
public class ClockReader {
    void exibir() {
        Clock clock = new Clock();
        // ERRO DE COMPILAÇÃO: 'time' tem acesso privado em 'Clock'.
        // Você não pode acessá-lo diretamente a partir de outra classe.
        System.out.println(clock.time); 
    }
}

```

#### Cenário 2: Uma subclasse (Herança) tentando acessar

```java
// SmartClock herda tudo de Clock, mas...
public class SmartClock extends Clock {
    void resetar() {
        // ERRO DE COMPILAÇÃO: Mesmo sendo uma "filha" da classe Clock,
        // o atributo 'time' é privado da mãe e não é herdado diretamente.
        this.time = 0; 
    }
}

```

---

### 💡 O "Macete" para permitir o acesso

Para que as classes de fora consigam interagir com uma variável `private`, a boa prática de orientação a objetos dita que você deve criar métodos públicos de acesso (os famosos **Getters e Setters**):

```java
public class Clock {
    private long time = 0;

    // Método Getter público: permite que o mundo externo LEIA o valor de forma controlada
    public long getTime() {
        return this.time;
    }
}

```

</details>

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
// Primeira classe do arquivo. 
// Nota: Em Java, você só pode ter uma classe 'public' por arquivo .java, 
// e o nome do arquivo deve ser exatamente o nome dessa classe (Clock.java).
public class Clock {
    // Atributo do tipo long inicializado em 0.
    // Como nenhum modificador (public, private, protected) foi especificado,
    // ele usa o modificador "default" (também conhecido como package-private).
    // Isso significa que apenas classes dentro do MESMO pacote podem acessá-lo diretamente.
    long time = 0; 
}

// Segunda classe. Para que o código compile no mesmo arquivo, 
// esta classe não pode ser declarada como 'public'.
class ClockReader {
    // Instancia um novo objeto da classe Clock.
    // Isso é permitido desde que ClockReader esteja no mesmo pacote que Clock,
    // ou que Clock seja public (como é o caso).
    Clock clock = new Clock();

    // Método público que retorna o valor do tempo.
    public long readClock() {
        // Acessa diretamente o atributo 'time' do objeto 'clock'.
        // Isso só funciona porque ClockReader está no mesmo pacote que Clock,
        // respeitando o modificador "default" da variável 'time'.
        return clock.time;
    }
}
```

Como não há nenhum modificador explícito (`private`, `protected` ou `public`), o Java aplica automaticamente o modificador **default**. Isso significa que o campo `time` pode ser acessado por qualquer classe que esteja no **mesmo pacote** da classe `Clock`, como a classe `ClockReader` no exemplo.  

Portanto, o acesso `clock.time` dentro de `ClockReader` funciona porque ambas as classes estão no mesmo pacote e o campo `time` foi declarado com acesso **default**.

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

No exemplo do **modificador protected**, o campo `time` da classe `Clock` foi declarado como:

```java
protected long time = 0; // tempo em milissegundos
```

Isso significa que:

- Assim como no **default**, o campo pode ser acessado por qualquer classe dentro do mesmo pacote.  
- A diferença é que, com **protected**, **subclasses** também podem acessar esse campo, mesmo que estejam em pacotes diferentes.  

Na prática, a classe `SmartClock`, que **herda** de `Clock`, consegue acessar diretamente o campo `time` porque ele está marcado como **protected**:

```java
public class SmartClock extends Clock {
    public long getTimeInSeconds() {
        return this.time / 1000; // acesso permitido por ser protected
    }
}
```

Se `time` fosse apenas **default**, `SmartClock` só teria acesso se estivesse no mesmo pacote. Como está marcado como **protected**, o acesso é garantido pela relação de herança, independentemente do pacote.  

👉 Em resumo: o modificador **protected** amplia o alcance do **default**, permitindo acesso também por subclasses fora do pacote.

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
