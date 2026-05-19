# Criando Variáveis e Nomeando-as

> 📍 `01-Fundamentos` › `Sintaxe_Basica` › `01-criando-variaveis`  
> 🔗 Fonte: [dev.java — Creating Variables and Naming Them](https://dev.java/learn/language-basics/variables/)

---

## Variáveis

Um objeto armazena seu estado em **campos** (*fields*). Na linguagem Java, os termos "campo" e "variável" são ambos utilizados — o que é uma fonte comum de confusão entre novos desenvolvedores, já que ambos frequentemente parecem se referir à mesma coisa.

O Java define os seguintes tipos de variáveis:

### Variáveis de Instância (Campos Não-Estáticos)

Objetos armazenam seus estados individuais em campos declarados **sem** a palavra-chave `static`. São chamadas de variáveis de instância porque seus valores são únicos para cada instância de uma classe — a `velocidadeAtual` de uma bicicleta é independente da `velocidadeAtual` de outra.

### Variáveis de Classe (Campos Estáticos)

Qualquer campo declarado com o modificador `static`. Isso informa ao compilador que existe exatamente **uma única cópia** dessa variável, independentemente de quantas vezes a classe foi instanciada.

```java
static int numMarchas = 6;
```

A palavra-chave `final` pode ser adicionada para indicar que o valor nunca mudará.

### Variáveis Locais

Assim como um objeto armazena seu estado em campos, um método frequentemente armazena seu estado temporário em variáveis locais. A sintaxe de declaração é similar à de um campo:

```java
int contador = 0;
```

Não há palavra-chave especial que designe uma variável como local — isso é determinado exclusivamente pela **localização** em que ela é declarada: entre as chaves de abertura e fechamento de um método. Portanto, variáveis locais são visíveis apenas dentro do método em que foram declaradas.

### Parâmetros

Já vistos anteriormente, por exemplo na assinatura do método principal:

```java
public static void main(String[] args)
```

Aqui, `args` é o parâmetro do método. O ponto importante é que parâmetros são sempre classificados como **variáveis**, não como campos. Isso vale também para construtores e tratadores de exceção.

> 💡 **Resumindo a terminologia:**
> - **Campos** → variáveis de instância e estáticas (excluindo locais e parâmetros)
> - **Variáveis** → termo geral que engloba todos os tipos acima
> - **Membros** → campos, métodos e tipos aninhados de uma classe, coletivamente

---

## Nomeando Variáveis

As regras e convenções para nomear variáveis em Java podem ser resumidas da seguinte forma:

- **Nomes de variáveis são sensíveis a maiúsculas e minúsculas.** O nome pode ser qualquer identificador legal — uma sequência de comprimento ilimitado de letras e dígitos Unicode, começando com uma letra, o cifrão `$` ou o caractere de sublinhado `_`.

- **Por convenção, sempre comece o nome com uma letra**, nunca com `$` ou `_`. O cifrão, por convenção, nunca é usado. O sublinhado no início, embora tecnicamente legal, é uma prática desestimulada.

- **Espaços em branco não são permitidos.**

- **Caracteres subsequentes** podem ser letras, dígitos, cifrões ou sublinhados. Prefira palavras completas a abreviações crípticas — nomes como `cadencia`, `velocidade` e `marcha` são muito mais intuitivos do que `c`, `v` e `m`. O nome escolhido não pode ser uma palavra-chave ou palavra reservada do Java.

- **Convenção de capitalização:**

| Situação | Convenção | Exemplo |
|---|---|---|
| Nome com uma única palavra | Tudo em minúsculas | `marcha` |
| Nome com múltiplas palavras | *camelCase* | `relacaoDeMarcha`, `marchaAtual` |
| Constante (`static final`) | Tudo maiúsculo com `_` | `NUM_MARCHAS` |

```java
// Variável de instância
int velocidadeAtual;

// Variável estática
static int numMarchas = 6;

// Constante
static final int NUM_MARCHAS = 6;

// Variável local
int contador = 0;
```

---

## Navegação

| | |
|---|---|
| ← Anterior | [Sintaxe Básica](../README.md) |
| → Próximo | [Criando Variáveis de Tipo Primitivo](../02-tipos-primitivos/README.md) |