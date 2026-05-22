```markdown
# A Instrução switch

Diferente das instruções if-then e if-then-else, a instrução switch pode ter vários caminhos possíveis de execução. Um switch funciona com os tipos primitivos byte, short, char e int. Ele também funciona com tipos enumerados (discutidos em Tipos Enum), a classe String e algumas classes especiais que encapsulam certos tipos primitivos: Character, Byte, Short e Integer (discutidos em Números e Strings).

O exemplo de código a seguir, **SwitchDemo**, declara um int chamado `month` cujo valor representa um mês. O código exibe o nome do mês, com base no valor de `month`, usando a instrução switch.

```java
public class SwitchDemo {
    public static void main(String[] args) {
        int month = 8;
        String monthString;
        switch (month) {
            case 1:  monthString = "January"; break;
            case 2:  monthString = "February"; break;
            case 3:  monthString = "March"; break;
            case 4:  monthString = "April"; break;
            case 5:  monthString = "May"; break;
            case 6:  monthString = "June"; break;
            case 7:  monthString = "July"; break;
            case 8:  monthString = "August"; break;
            case 9:  monthString = "September"; break;
            case 10: monthString = "October"; break;
            case 11: monthString = "November"; break;
            case 12: monthString = "December"; break;
            default: monthString = "Invalid month"; break;
        }
        System.out.println(monthString);
    }
}
```

Neste caso, **August** é impresso na saída padrão.

O corpo de uma instrução switch é conhecido como **bloco switch**. Uma instrução dentro do bloco switch pode ser rotulada com um ou mais rótulos `case` ou `default`. A instrução switch avalia sua expressão e, em seguida, executa todas as instruções que seguem o rótulo `case` correspondente.

Você também poderia exibir o nome do mês com instruções if-then-else:

```java
int month = 8;
if (month == 1) {
    System.out.println("January");
} else if (month == 2) {
    System.out.println("February");
}
// ... e assim por diante
```

Decidir se deve usar instruções if-then-else ou uma instrução switch depende da legibilidade e da expressão que está sendo testada. Uma instrução if-then-else pode testar expressões baseadas em intervalos de valores ou condições, enquanto uma instrução switch testa expressões apenas com base em um único inteiro, valor enumerado ou objeto String.

Outro ponto de interesse é a instrução **break**. Cada instrução break termina a instrução switch que a contém. O fluxo de controle continua com a primeira instrução após o bloco switch. As instruções break são necessárias porque, sem elas, instruções em blocos switch caem em sequência: todas as instruções após o rótulo case correspondente são executadas em sequência, independentemente da expressão dos rótulos case subsequentes, até que uma instrução break seja encontrada.

O programa **SwitchDemoFallThrough** mostra instruções em um bloco switch que caem em sequência. O programa exibe o mês correspondente ao inteiro `month` e os meses que seguem no ano:

```java
public class SwitchDemoFallThrough {
    public static void main(String[] args) {
        java.util.ArrayList<String> futureMonths = new java.util.ArrayList<String>();
        int month = 8;
        switch (month) {
            case 1:  futureMonths.add("January");
            case 2:  futureMonths.add("February");
            case 3:  futureMonths.add("March");
            case 4:  futureMonths.add("April");
            case 5:  futureMonths.add("May");
            case 6:  futureMonths.add("June");
            case 7:  futureMonths.add("July");
            case 8:  futureMonths.add("August");
            case 9:  futureMonths.add("September");
            case 10: futureMonths.add("October");
            case 11: futureMonths.add("November");
            case 12: futureMonths.add("December");
                    break;
            default: break;
        }
        if (futureMonths.isEmpty()) {
            System.out.println("Invalid month number");
        } else {
            for (String monthName : futureMonths) {
                System.out.println(monthName);
            }
        }
    }
}
```

Saída do código:

```
August
September
October
November
December
```

Tecnicamente, o break final não é necessário porque o fluxo sai da instrução switch. Usar um break é recomendado para que modificar o código seja mais fácil e menos propenso a erros.

A seção **default** trata todos os valores que não são explicitamente tratados por uma das seções case.

O exemplo de código a seguir, **SwitchDemo2**, mostra como uma instrução pode ter múltiplos rótulos case. O exemplo calcula o número de dias em um determinado mês:

```java
class SwitchDemo2 {
    public static void main(String[] args) {
        int month = 2;
        int year = 2000;
        int numDays = 0;
        switch (month) {
            case 1: case 3: case 5: case 7:
            case 8: case 10: case 12:
                numDays = 31;
                break;
            case 4: case 6: case 9: case 11:
                numDays = 30;
                break;
            case 2:
                if (((year % 4 == 0) && !(year % 100 == 0)) || (year % 400 == 0))
                    numDays = 29;
                else
                    numDays = 28;
                break;
            default:
                System.out.println("Invalid month.");
                break;
        }
        System.out.println("Number of Days = " + numDays);
    }
}
```

Saída do código:

```
Number of Days = 29
```

## Usando Strings em Instruções switch

No Java SE 7 e posteriores, você pode usar um objeto String na expressão da instrução switch. O exemplo de código a seguir, **StringSwitchDemo**, exibe o número do mês com base no valor da String chamada `month`:

```java
public class StringSwitchDemo {
    public static int getMonthNumber(String month) {
        int monthNumber = 0;
        if (month == null) {
            return monthNumber;
        }
        switch (month.toLowerCase()) {
            case "january":   monthNumber = 1; break;
            case "february":  monthNumber = 2; break;
            case "march":     monthNumber = 3; break;
            case "april":     monthNumber = 4; break;
            case "may":       monthNumber = 5; break;
            case "june":      monthNumber = 6; break;
            case "july":      monthNumber = 7; break;
            case "august":    monthNumber = 8; break;
            case "september": monthNumber = 9; break;
            case "october":   monthNumber = 10; break;
            case "november":  monthNumber = 11; break;
            case "december":  monthNumber = 12; break;
            default:  monthNumber = 0; break;
        }
        return monthNumber;
    }

    public static void main(String[] args) {
        String month = "August";
        int returnedMonthNumber = StringSwitchDemo.getMonthNumber(month);
        if (returnedMonthNumber == 0) {
            System.out.println("Invalid month");
        } else {
            System.out.println(returnedMonthNumber);
        }
    }
}
```

Saída do código:

```
8
```

A String na expressão switch é comparada com as expressões associadas a cada rótulo case como se o método `String.equals` estivesse sendo usado. Para que o exemplo **StringSwitchDemo** aceite qualquer mês independentemente de maiúsculas ou minúsculas, `month` é convertido para minúsculas (com o método `toLowerCase`), e todas as strings associadas aos rótulos case estão em minúsculas.

**Nota:** Este exemplo verifica se a expressão na instrução switch é nula. Certifique-se de que a expressão em qualquer instrução switch não seja nula para evitar que uma **NullPointerException** seja lançada.