# Campos estáticos e não estáticos em Java

Um campo Java é uma variável dentro de uma classe. Por exemplo, em uma classe que representa um funcionário, a classe `Employee` pode conter os seguintes campos:

- name  
- position  
- salary  
- hiredDate  

A classe Java correspondente poderia ser definida assim:

```java
public class Employee {
    String  name     ;
    String  position ;
    int     salary   ;
    Date    hiredDate;
}
```

## Sintaxe de Declaração de Campo

Um campo Java é declarado usando a seguinte sintaxe:

```
[access_modifier] [static] [final] type name [= initial value] ;
```

Os colchetes [ ] em torno de algumas palavras-chave significam que essa opção é opcional. Apenas `type` e `name` são obrigatórios.

1. Um modificador de acesso pode ser declarado para um campo Java. O modificador de acesso determina quais classes podem acessar o campo.  
2. Um tipo de dado para o campo deve ser atribuído. No exemplo acima, foram usados `String`, `int` e `Date`.  
3. O campo pode ser declarado `static`. Em Java, campos estáticos pertencem à classe, não às instâncias. Assim, todas as instâncias de qualquer classe acessarão o mesmo campo estático. Um campo não estático pode ter valores diferentes para cada objeto.  
4. O campo pode ser declarado `final` ou não. Um campo `final` não pode ter seu valor alterado. Ele deve ter um valor inicial atribuído e, uma vez definido, não pode ser mudado. Um campo `final` é frequentemente também declarado `static`. Um campo `static final` é chamado de “constante”.  
5. O campo recebe um nome. Esse nome pode ser escolhido livremente, mas há restrições quanto aos caracteres permitidos.  
6. Opcionalmente, pode-se definir um valor inicial para o campo.  

## Modificadores de Acesso de Campos Java

O modificador de acesso determina se o campo pode ser acessado por classes além da classe que o possui. Existem quatro possíveis modificadores:

- **private**  
- **package**  
- **protected**  
- **public**

Exemplo:

```java
public class Customer {
    private    String email;
               String position;   // sem modificador = acesso de pacote
    protected  String name;
    public     String city;
}
```

Normalmente, usa-se `private` e `protected`. Para classes simples que apenas carregam dados, pode-se declarar todos os campos como `public`.

## Campos Estáticos e Não Estáticos

Um campo Java pode ser estático ou não estático.

- **Campos estáticos** pertencem à classe. Não importa quantos objetos sejam criados, existirá apenas um campo na classe, compartilhado por todos.  

```java
public class Customer {
    static String staticField1;
}
Customer.staticField1 = "value";
System.out.println(Customer.staticField1);
```

- **Campos não estáticos** pertencem às instâncias da classe. Cada objeto pode ter seus próprios valores.  

```java
public class Customer {
    String field1;
}
Customer customer = new Customer();
customer.field1 = "value";
System.out.println(customer.field1);
```

## Campos `final`

Um campo `final` não pode ter seu valor alterado após atribuição.

```java
public class Customer {
    final String field1 = "Fixed Value";
}
```

Muitas vezes, faz sentido também declarar o campo como `static final`, tornando-o uma constante:

```java
public class Customer {
    static final String CONSTANT_1 = "Fixed Value";
}
```

Por convenção, nomes de constantes são escritos em **maiúsculas** e palavras separadas por **underscore**.

## Nomeando Campos Java

O nome de um campo é usado para referenciá-lo no código:

```java
Customer customer = new Customer();
customer.city = "New York";
System.out.println(customer.city);
```

As restrições e convenções de nomenclatura são as mesmas que para qualquer outra variável.

## Valor Inicial de Campo

Um campo pode receber um valor inicial quando criado na JVM.

- Campos estáticos são criados quando a classe é carregada.  
- Campos não estáticos são criados quando o objeto é instanciado.  

Exemplo:

```java
public class Customer {
    String customerType = "OnlineCustomer";
}
```

Inicializar campos com valores padrão é opcional, mas pode ser uma boa prática.
