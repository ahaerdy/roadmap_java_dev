
# As instruções if-then e if-then-else
## A instrução if-then

A instrução **if-then** é a mais básica de todas as instruções de fluxo de controle. Ela diz ao seu programa para executar uma determinada seção de código apenas se um teste específico for avaliado como verdadeiro.

Por exemplo, a classe `Bicycle` poderia permitir que os freios diminuíssem a velocidade da bicicleta apenas se ela já estivesse em movimento. Uma possível implementação do método `applyBrakes` poderia ser a seguinte:

```java
void applyBrakes() {
    // a cláusula "if": a bicicleta deve estar em movimento
    if (isMoving){
        // a cláusula "then": diminuir a velocidade atual
        currentSpeed--;
    }
}
```

Se este teste for avaliado como falso (significando que a bicicleta não está em movimento), o controle salta para o fim da instrução if-then.

Além disso, as chaves de abertura e fechamento são opcionais, desde que a cláusula "then" contenha apenas uma instrução:

```java
void applyBrakes() {
    // igual ao acima, mas sem chaves
    if (isMoving)
        currentSpeed--;
}
```

Decidir quando omitir as chaves é uma questão de gosto pessoal. Omiti-las pode tornar o código mais frágil. Se uma segunda instrução for adicionada posteriormente à cláusula "then", um erro comum seria esquecer de adicionar as chaves agora necessárias. O compilador não consegue detectar esse tipo de erro; você apenas obterá resultados incorretos.

---

## A instrução if-then-else

A instrução **if-then-else** fornece um caminho secundário de execução quando uma cláusula "if" é avaliada como falsa.

Você poderia usar uma instrução if-then-else no método `applyBrakes` para realizar alguma ação caso os freios sejam aplicados quando a bicicleta não está em movimento. Nesse caso, a ação é simplesmente imprimir uma mensagem de erro informando que a bicicleta já está parada.

```java
void applyBrakes() {
    if (isMoving) {
        currentSpeed--;
    } else {
        System.err.println("The bicycle has already stopped!");
    }
}
```

O programa a seguir, `IfElseDemo`, atribui uma nota com base no valor de uma pontuação de teste: um A para uma pontuação de 90% ou mais, um B para 80% ou mais, e assim por diante.

```java
class IfElseDemo {
    public static void main(String[] args) {
        int testscore = 76;
        char grade;

        if (testscore >= 90) {
            grade = 'A';
        } else if (testscore >= 80) {
            grade = 'B';
        } else if (testscore >= 70) {
            grade = 'C';
        } else if (testscore >= 60) {
            grade = 'D';
        } else {
            grade = 'F';
        }

        System.out.println("Grade = " + grade);
    }
}
```

A saída do programa é:

```
Grade = C
```

Você pode ter notado que o valor de `testscore` pode satisfazer mais de uma expressão na instrução composta: `76 >= 70` e `76 >= 60`. No entanto, uma vez que uma condição é satisfeita, as instruções apropriadas são executadas (`grade = 'C';`) e as condições restantes não são avaliadas.
