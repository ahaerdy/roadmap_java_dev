# Operadores Matemáticos e Classe Math em Java

## Operadores Matemáticos

### Operadores básicos
| Operador | Descrição |
|----------|-----------|
| `+`      | Adição |
| `-`      | Subtração |
| `*`      | Multiplicação |
| `/`      | Divisão |


### Adição
O operador `+` realiza a soma de dois valores.

```java
int sum1 = 10 + 20;      // soma de constantes
int sum2 = sum1 + 33;    // variável + constante
int sum3 = sum2 + sum2;  // variável + variável
```

Operador de atalho:
```java
int result = 10;
result += 20; // equivalente a result = result + 20;
```

### Subtração
O operador `-` realiza a subtração.

```java
int diff1 = 200 - 10;
int diff2 = diff1 - 5;
int diff3 = diff1 - diff2;
```

Operador de atalho:
```java
int result = 200;
result -= 10;
```

### Multiplicação
O operador `*` realiza multiplicação.

```java
int prod1 = 10 * 20;
int prod2 = prod1 * 5;
int prod3 = prod1 * prod2;
```

Operador de atalho:
```java
int result = 10;
result *= 20;
```

### Divisão
O operador `/` realiza divisão.

```java
int division1 = 100 / 10;
int division2 = division1 / 2;
int division3 = division1 / division2;
```

Operador de atalho:
```java
int result = 100;
result /= 5;
```

### Resto / Módulo
O operador `%` retorna o resto da divisão.

```java
int value    = 100;
int remainder = value % 9; // resultado = 1
```

Operador de atalho:
```java
int result = 100;
result %= 9; // resultado = 1
```

## Precedência de Operadores
Multiplicação e divisão (`*`, `/`) têm precedência sobre adição e subtração (`+`, `-`).  
Parênteses podem alterar a ordem de execução.

## Matemática com Inteiros
Operações com tipos inteiros (`byte`, `short`, `int`, `long`) descartam frações.

```java
int result = 100 / 8; // resultado = 12
```

## Matemática com Ponto Flutuante
Tipos `float` e `double` suportam frações.

```java
double result = 100D / 8D; // resultado = 12.5
```

### Precisão
Operações com ponto flutuante podem gerar imprecisões:

```java
double resultDbl3 = 0D;
for(int i=0; i<100; i++){
    resultDbl3 += 0.01D;
}
System.out.println(resultDbl3); // saída: 1.0000000000000007
```

## Classe Math em Java
A classe `java.lang.Math` fornece funções matemáticas avançadas.

### Funções básicas
- `Math.abs()` → valor absoluto
- `Math.ceil()` → arredonda para cima
- `Math.floor()` → arredonda para baixo
- `Math.floorDiv()` → divisão arredondada para baixo
- `Math.min()` → menor valor
- `Math.max()` → maior valor
- `Math.round()` → arredonda para inteiro
- `Math.random()` → número aleatório entre 0 e 1

### Funções exponenciais e logarítmicas
- `Math.exp()` → e^x
- `Math.log()` → logaritmo natural
- `Math.log10()` → logaritmo base 10
- `Math.pow()` → potência
- `Math.sqrt()` → raiz quadrada

### Funções trigonométricas
- Constante `Math.PI`
- `Math.sin()`, `Math.cos()`, `Math.tan()`
- `Math.asin()`, `Math.acos()`, `Math.atan()`, `Math.atan2()`
- `Math.sinh()`, `Math.cosh()`, `Math.tanh()`
- `Math.toDegrees()`, `Math.toRadians()`
