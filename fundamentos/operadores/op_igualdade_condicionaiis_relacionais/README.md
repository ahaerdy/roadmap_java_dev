# Operadores de Igualdade, Relacionais e Condicionais

## Operadores de Igualdade e Relacionais
Os operadores de igualdade e relacionais determinam se um operando é maior, menor, igual ou diferente de outro operando. A maioria desses operadores provavelmente parecerá familiar para você. Lembre-se de que você deve usar `==`, e não `=`, ao testar se dois valores primitivos são iguais.

- `==`      igual a  
- `!=`      diferente de  
- `>`       maior que  
- `>=`      maior ou igual a  
- `<`       menor que  
- `<=`      menor ou igual a  

O programa a seguir, **ComparisonDemo**, testa os operadores de comparação:

```java
class ComparisonDemo {
    public static void main(String[] args){
        int value1 = 1;
        int value2 = 2;
        if(value1 == value2)
            System.out.println("value1 == value2");
        if(value1 != value2)
            System.out.println("value1 != value2");
        if(value1 > value2)
            System.out.println("value1 > value2");
        if(value1 < value2)
            System.out.println("value1 < value2");
        if(value1 <= value2)
            System.out.println("value1 <= value2");
    }
}
```

**Saída:**
```
value1 != value2
value1 <  value2
value1 <= value2
```

---

## Operadores Condicionais
Os operadores `&&` e `||` realizam operações de **AND condicional** e **OR condicional** em duas expressões booleanas. Esses operadores apresentam comportamento de *short-circuit*, o que significa que o segundo operando só é avaliado se necessário.

- `&&` Condicional-AND  
- `||` Condicional-OR  

O programa a seguir, **ConditionalDemo1**, testa esses operadores:

```java
class ConditionalDemo1 {
    public static void main(String[] args){
        int value1 = 1;
        int value2 = 2;
        if((value1 == 1) && (value2 == 2))
            System.out.println("value1 is 1 AND value2 is 2");
        if((value1 == 1) || (value2 == 1))
            System.out.println("value1 is 1 OR value2 is 1");
    }
}
```

Outro operador condicional é `?:`, que pode ser considerado uma forma abreviada de uma instrução **if-then-else**. Esse operador também é conhecido como **operador ternário**, pois utiliza três operandos.

No exemplo a seguir, o operador deve ser lido como:  
*"Se someCondition for verdadeiro, atribua o valor de value1 a result. Caso contrário, atribua o valor de value2 a result."*

```java
class ConditionalDemo2 {
    public static void main(String[] args){
        int value1 = 1;
        int value2 = 2;
        int result;
        boolean someCondition = true;
        result = someCondition ? value1 : value2;
        System.out.println(result);
    }
}
```

Como `someCondition` é verdadeiro, este programa imprime `1` na tela.  
Use o operador `?:` em vez de uma instrução if-then-else se isso tornar seu código mais legível, especialmente quando as expressões forem compactas e sem efeitos colaterais.

---

## 📌 Operador de Comparação de Tipo `instanceof`
O operador `instanceof` compara um objeto com um tipo especificado. Você pode usá-lo para testar se um objeto é uma instância de uma classe, de uma subclasse ou de uma classe que implementa uma determinada interface.

O programa a seguir, **InstanceofDemo**, define uma classe pai (**Parent**), uma interface simples (**MyInterface**) e uma classe filha (**Child**) que herda da classe pai e implementa a interface:

```java
class InstanceofDemo {
    public static void main(String[] args) {
        Parent obj1 = new Parent();
        Parent obj2 = new Child();
        System.out.println("obj1 instanceof Parent: " + (obj1 instanceof Parent));
        System.out.println("obj1 instanceof Child: " + (obj1 instanceof Child));
        System.out.println("obj1 instanceof MyInterface: " + (obj1 instanceof MyInterface));
        System.out.println("obj2 instanceof Parent: " + (obj2 instanceof Parent));
        System.out.println("obj2 instanceof Child: " + (obj2 instanceof Child));
        System.out.println("obj2 instanceof MyInterface: " + (obj2 instanceof MyInterface));
    }
}

class Parent {}
class Child extends Parent implements MyInterface {}
interface MyInterface {}
```

**Saída:**
```
obj1 instanceof Parent: true
obj1 instanceof Child: false
obj1 instanceof MyInterface: false
obj2 instanceof Parent: true
obj2 instanceof Child: true
obj2 instanceof MyInterface: true
```

Ao usar o operador `instanceof`, lembre-se de que **null não é instância de nada**.
