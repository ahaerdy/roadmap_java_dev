# Criando Variáveis e Nomeando-as

> 📍 `01-Fundamentos` › `Sintaxe_Basica` › `01-criando-variaveis`  
> 🔗 Fonte: [dev.java — Creating Variables and Naming Them](https://dev.java/learn/language-basics/variables/)

# Criando Variáveis e Nomeando-as

## Variáveis

Como você aprendeu na seção anterior, um objeto armazena seu estado em campos:

```java
int cadence = 0;
int speed = 0;
int gear = 1;
```

A discussão sobre *O que é um Objeto?* apresentou os campos, mas você provavelmente ainda tem algumas dúvidas, como:

- Quais são as regras e convenções para nomear um campo?
- Além de `int`, quais outros tipos de dados existem?
- Os campos precisam ser inicializados quando são declarados?
- Os campos recebem um valor padrão se não forem explicitamente inicializados?

Vamos explorar essas questões nesta seção. Antes disso, é importante entender algumas distinções técnicas.

Na linguagem de programação Java, os termos **campo** e **variável** são usados, o que pode gerar confusão entre novos desenvolvedores, já que muitas vezes parecem se referir à mesma coisa. A linguagem Java define os seguintes tipos de variáveis:

### Variáveis de Instância (Campos Não-Estáticos)

Tecnicamente, os objetos armazenam seus estados individuais em **campos não-estáticos**, ou seja, campos declarados sem a palavra-chave `static`. Esses campos também são chamados de variáveis de instância porque seus valores são únicos para cada instância de uma classe. Por exemplo, a `currentSpeed` de uma bicicleta é independente da `currentSpeed` de outra.

### Variáveis de Classe (Campos Estáticos)

Uma variável de classe é qualquer campo declarado com o modificador `static`. Isso indica ao compilador que existe exatamente uma cópia dessa variável, independentemente de quantas vezes a classe seja instanciada. 

Por exemplo:

```java
static int numGears = 6;
```

Esse campo define o número de marchas de um tipo específico de bicicleta. Se adicionarmos `final`, indicamos que esse valor nunca mudará:

```java
static final int NUM_GEARS = 6;
```

### Variáveis Locais

Assim como um objeto armazena seu estado em campos, um método frequentemente armazena seu estado temporário em variáveis locais. A sintaxe é semelhante à de um campo:

```java
int count = 0;
```

Não existe palavra-chave especial para designar uma variável como local; isso é determinado pelo local onde ela é declarada — dentro das chaves de um método. Portanto, variáveis locais só são visíveis dentro do método em que foram declaradas.

### Parâmetros

Você já viu exemplos de parâmetros, tanto na classe `Bicycle` quanto no método `main` da aplicação *Hello World!*:

```java
public static void main(String[] args)
```

Aqui, `args` é o parâmetro do método. É importante lembrar que parâmetros são sempre classificados como **variáveis**, não como campos. Isso também se aplica a construtores e manipuladores de exceções.

---

## Nomeando Variáveis

Toda linguagem de programação possui regras e convenções para nomes de variáveis, e Java não é diferente. As principais regras e convenções são:

- **Sensibilidade a maiúsculas/minúsculas**: `speed` e `Speed` são nomes diferentes.
- **Identificadores válidos**: podem conter letras Unicode, dígitos, `$` ou `_`, mas devem começar com uma letra, `$` ou `_`.
- **Convenções**:
  - Sempre comece nomes de variáveis com uma letra (não use `$` ou `_`).
  - Evite usar `$` e `_` no início — embora permitido, é desencorajado.
  - Não use espaços.
  - Prefira palavras completas em vez de abreviações enigmáticas. Exemplo: `cadence`, `speed`, `gear` são melhores que `c`, `s`, `g`.
  - Não utilize palavras reservadas da linguagem.
  - Para nomes de uma palavra, use letras minúsculas: `gear`.
  - Para nomes compostos, capitalize a primeira letra de cada palavra subsequente: `gearRatio`, `currentGear`.
  - Para constantes (`static final`), use todas as letras maiúsculas e separe palavras com `_`: `NUM_GEARS`.

---

📌 **Última atualização: 23 de setembro de 2021**


---

Quer que eu também traduza e adapte as próximas páginas da seção **Java Language Basics** (variáveis, expressões, controle_de_fluxo) para manter a documentação completa em português?

## Navegação

| | |
|---|---|
| ← Anterior | [Sintaxe Básica](../README.md) |
| → Próximo | [Criando Variáveis de Tipo Primitivo](../02-tipos-primitivos/README.md) |