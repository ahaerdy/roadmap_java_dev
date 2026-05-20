# Perguntas e Exercícios: Operadores  

## Perguntas

Considere o seguinte trecho de código:

```java
arrayOfInts[j] > arrayOfInts[j+1]
```

Quais operadores o código contém?

---

Considere o seguinte trecho de código:

```java
int i = 10;
int n = i++ % 5;
```

Quais são os valores de `i` e `n` após a execução do código?  
Quais são os valores finais de `i` e `n` se, em vez de usar o operador de incremento pós-fixado (`i++`), você usar a versão prefixada (`++i`)?

---

Para inverter o valor de um booleano, qual operador você usaria?

---

Qual operador é usado para comparar dois valores, `=` ou `==`?

---

Explique o seguinte exemplo de código:

```java
result = someCondition ? value1 : value2;
```

---

## Exercícios

Altere o seguinte programa para usar atribuições compostas:

```java
class ArithmeticDemo {
    public static void main (String[] args){
        int result = 1 + 2; // result agora é 3
        System.out.println(result);

        result = result - 1; // result agora é 2
        System.out.println(result);

        result = result * 2; // result agora é 4
        System.out.println(result);

        result = result / 2; // result agora é 2
        System.out.println(result);

        result = result + 8; // result agora é 10
        result = result % 7; // result agora é 3
        System.out.println(result);
    }
}
```

---

No programa a seguir, explique por que o valor `"6"` é impresso duas vezes seguidas:

```java
class PrePostDemo {
    public static void main(String[] args){
        int i = 3;
        i++;
        System.out.println(i);    // "4"

        ++i;
        System.out.println(i);    // "5"

        System.out.println(++i);  // "6"
        System.out.println(i++);  // "6"
        System.out.println(i);    // "7"
    }
}
```

---

<details>
<summary>Verifique suas respostas (🖱️ <b><ins>clique aqui</ins></b>)</summary>

### Respostas às Perguntas

Considere o seguinte trecho de código:

```java
arrayOfInts[j] > arrayOfInts[j+1]
```

**Pergunta:** Quais operadores o código contém?  
**Resposta:** `>`, `+`

---

Considere o seguinte trecho de código:

```java
int i = 10;
int n = i++ % 5;
```

**Pergunta:** Quais são os valores de `i` e `n` após a execução do código?  
**Resposta:** `i` é 11, e `n` é 0.

---

**Pergunta:** Quais são os valores finais de `i` e `n` se, em vez de usar o operador de incremento pós-fixado (`i++`), você usar a versão prefixada (`++i`)?  
**Resposta:** `i` é 11, e `n` é 1.

---

**Pergunta:** Para inverter o valor de um boolean, qual operador você usaria?  
**Resposta:** O operador de complemento lógico `"!"`.

---

**Pergunta:** Qual operador é usado para comparar dois valores, `=` ou `==`?  
**Resposta:** O operador `==` é usado para comparação, e `=` é usado para atribuição.

---

**Pergunta:** Explique o seguinte exemplo de código:

```java
result = someCondition ? value1 : value2;
```

**Resposta:** Este código deve ser lido como:  
“Se `someCondition` for verdadeiro, atribua o valor de `value1` a `result`. Caso contrário, atribua o valor de `value2` a `result`.”

---

### Solução dos Exercícios

Altere o seguinte programa para usar atribuições compostas:

```java
class ArithmeticDemo {
    public static void main (String[] args){
        int result = 1 + 2; // result agora é 3
        System.out.println(result);
        result = result - 1; // result agora é 2
        System.out.println(result);
        result = result * 2; // result agora é 4
        System.out.println(result);
        result = result / 2; // result agora é 2
        System.out.println(result);
        result = result + 8; // result agora é 10
        result = result % 7; // result agora é 3
        System.out.println(result);
    }
}
```

Aqui está uma solução:

```java
class ArithmeticDemo {
    public static void main (String[] args){
        int result = 3;
        System.out.println(result);
        result -= 1; // result agora é 2
        System.out.println(result);
        result *= 2; // result agora é 4
        System.out.println(result);
        result /= 2; // result agora é 2
        System.out.println(result);
        result += 8; // result agora é 10
        result %= 7; // result agora é 3
        System.out.println(result);
    }
}
```

---

No programa a seguir, explique por que o valor `"6"` é impresso duas vezes seguidas:

```java
class PrePostDemo {
    public static void main(String[] args){
        int i = 3;
        i++;
        System.out.println(i);    // "4"
        ++i;
        System.out.println(i);    // "5"
        System.out.println(++i);  // "6"
        System.out.println(i++);  // "6"
        System.out.println(i);    // "7"
    }
}
```

O código `System.out.println(++i);` avalia para 6, porque a versão prefixada de `++` avalia para o valor já incrementado.  
A linha seguinte, `System.out.println(i++);`, avalia para o valor atual (6), e só depois incrementa em um.  
Portanto, o `"7"` só é impresso na linha seguinte.

</details>