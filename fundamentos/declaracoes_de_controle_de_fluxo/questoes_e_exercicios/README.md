
# Perguntas e Exercícios: Declarações de Controle de Fluxo  

## Perguntas

- A declaração de controle de fluxo mais básica suportada pela linguagem de programação Java é a declaração ___.
- A declaração ___ permite qualquer número de possíveis caminhos de execução.
- A declaração ___ é semelhante à declaração while, mas avalia sua expressão no ___ do loop.
- Como você escreve um loop infinito usando a declaração for?
- Como você escreve um loop infinito usando a declaração while?

---

## Exercícios

Considere o seguinte trecho de código:

```java
if (aNumber >= 0)
    if (aNumber == 0)
        System.out.println("first string");
    else
        System.out.println("second string");

System.out.println("third string");
```

1. Qual saída você acha que o código produzirá se `aNumber` for 3?  
2. Escreva um programa de teste contendo o trecho de código anterior; defina `aNumber` como 3. Qual é a saída do programa? É o que você previu?  
3. Explique por que a saída é essa; em outras palavras, qual é o fluxo de controle para o trecho de código?  
4. Usando apenas espaços e quebras de linha, reformate o trecho de código para tornar o fluxo de controle mais fácil de entender.  
5. Use chaves `{` e `}` para esclarecer ainda mais o código.  

<details>
<summary>Verifique suas respostas (🖱️ <b><ins>clique aqui</ins></b>)</summary>

## Respostas  

- A declaração de controle de fluxo mais básica suportada pela linguagem de programação Java é a declaração if-then.  
- A declaração switch permite qualquer número de possíveis caminhos de execução.  
- A declaração do-while é semelhante à declaração while, mas avalia sua expressão no final do loop.  

**Pergunta:** Como você escreve um loop infinito usando a declaração for?  
**Resposta:**  
```java
for ( ; ; ) {
}
```

**Pergunta:** Como você escreve um loop infinito usando a declaração while?  
**Resposta:**  
```java
while (true) {
}
```

---

## Exercícios  

Considere o seguinte trecho de código:  
```java
if (aNumber >= 0)
    if (aNumber == 0)
        System.out.println("first string");
    else
        System.out.println("second string");
System.out.println("third string");
```

**Exercício:** Qual saída você acha que o código produzirá se aNumber for 3?  

**Solução:**  
```
second string
third string
```

**Exercício:** Escreva um programa de teste contendo o trecho de código anterior; faça aNumber ser 3. Qual é a saída do programa? É o que você previu? Explique por que a saída é essa. Em outras palavras, qual é o fluxo de controle para o trecho de código?  

**Solução:**  
```
NestedIf
second string
third string
```

3 é maior ou igual a 0, então a execução progride para a segunda declaração if. O teste da segunda declaração if falha porque 3 não é igual a 0. Assim, a cláusula else é executada (já que está anexada ao segundo if). Portanto, “second string” é exibido. O println final está completamente fora de qualquer declaração if, então sempre é executado, e assim “third string” sempre é exibido.  

**Exercício:** Usando apenas espaços e quebras de linha, reformate o trecho de código para tornar o fluxo de controle mais fácil de entender.  

**Solução:**  
```java
if (aNumber >= 0)
    if (aNumber == 0)
        System.out.println("first string");
    else
        System.out.println("second string");

System.out.println("third string");
```

**Exercício:** Use chaves { e } para esclarecer ainda mais o código e reduzir a possibilidade de erros por futuros mantenedores do código.  

**Solução:**  
```java
if (aNumber >= 0) {
    if (aNumber == 0) {
        System.out.println("first string");
    } else {
        System.out.println("second string");
    }
}
System.out.println("third string");
```

</details>
