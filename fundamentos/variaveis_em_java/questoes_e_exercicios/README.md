# Questões e Exercícios: Variáveis  

## Questões

- O termo "variável de instância" é outro nome para ___.
- O termo "variável de classe" é outro nome para ___.
- Uma variável local armazena estado temporário; ela é declarada dentro de um ___.
- Uma variável declarada dentro dos parênteses de abertura e fechamento da assinatura de um método é chamada de ____.
- Quais são os oito tipos primitivos de dados suportados pela linguagem de programação Java?
- Cadeias de caracteres são representadas pela classe ___.
- Um ___ é um objeto contêiner que guarda um número fixo de valores de um único tipo.

---

<details>
<summary> Verifique suas respostas🔻</summary>
</br>

- O termo "variável de instância" é outro nome para `campo não estático`.  
    - Detalhamento: uma “variável de classe” em Java é uma variável declarada com o modificador static dentro da classe, mas fora dos métodos. Ela pertence à classe em si e não a uma instância específica, sendo compartilhada por todos os objetos criados a partir dessa classe.
    - Exemplo prático:
        ```java
        public class ContaBancaria {
            // Variável de classe (compartilhada por todas as contas)
            private static int totalContas = 0;

            // Variável de instância (cada objeto tem a sua)
            private String titular;

            public ContaBancaria(String titular) {
                this.titular = titular;
                totalContas++; // incrementa sempre que uma nova conta é criada
            }

            public String getTitular() {
                return titular;
            }

            // Método de classe (acessa variável estática)
            public static int getTotalContas() {
                return totalContas;
            }
        }

        public class Main {
            public static void main(String[] args) {
                ContaBancaria c1 = new ContaBancaria("Maria");
                ContaBancaria c2 = new ContaBancaria("João");

                System.out.println("Total de contas criadas: " + ContaBancaria.getTotalContas());
                // Saída: Total de contas criadas: 2
            }
        }
        ```
- O termo "variável de classe" é outro nome para `campo estático`.  
- Uma variável local armazena estado temporário; ela é declarada dentro de um `método`.  
- Uma variável declarada dentro dos parênteses de abertura e fechamento de um método é chamada de `parâmetro`.  
- Oito tipos primitivos de dados suportados pela linguagem de programação Java são: `byte`, `short`, `int`, `long`, `float`, `double`, `boolean` e `char`.
- Cadeias de caracteres são representadas pela classe `java.lang.String`.  
- Um `array` é um objeto contêiner que mantém um número fixo de valores de um único tipo.  

</details>

---

## Exercícios

1. Crie um pequeno programa que defina alguns campos. Tente criar alguns nomes de campos ilegais e veja que tipo de erro o compilador produz. Use as regras e convenções de nomenclatura como guia.

2. No programa que você criou no Exercício 1, tente deixar os campos não inicializados e imprima seus valores. Tente o mesmo com uma variável local e veja que tipo de erros de compilador você consegue produzir. Familiarizar-se com erros comuns de compilador tornará mais fácil reconhecer bugs em seu código.

---

# Recordando

Nem todas as variáveis em Java são chamadas de “campo”. O termo “campo” é usado especificamente para variáveis declaradas dentro de uma classe, mas fora de métodos, construtores ou blocos. Já variáveis locais e parâmetros não são considerados campos.

## 📌 Tipos de variáveis em Java

### Campos (fields)
- Declarados dentro da classe, mas fora de métodos.  
- Podem ser **de instância** (cada objeto tem sua cópia) ou **de classe** (quando declarados com `static`, compartilhados por todos os objetos).  

**Exemplo:**
```java
public class Pessoa {
    String nome;           // campo de instância
    static int contador;   // campo de classe
}
```

### Variáveis locais
- Declaradas dentro de métodos, construtores ou blocos.  
- Só existem durante a execução do método.  

**Exemplo:**
```java
public void calcularIdade() {
    int anoNascimento = 2000; // variável local
}
```

### Parâmetros
- Variáveis declaradas entre os parênteses de um método ou construtor.  
- Recebem valores quando o método é chamado.  

**Exemplo:**
```java
public void setNome(String novoNome) { // parâmetro
    this.nome = novoNome;
}
```

## 🔎 Diferença importante
- **Campos** = variáveis associadas à classe ou ao objeto.  
- **Variáveis locais** = usadas apenas dentro de métodos.  
- **Parâmetros** = valores passados para métodos ou construtores.  

