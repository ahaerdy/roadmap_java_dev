# Variáveis em Java

Este documento resume os conceitos fundamentais sobre variáveis na linguagem de programação Java, conforme abordado na documentação oficial [Variables - The Java Tutorials](https://docs.oracle.com/javase/tutorial/java/nutsandbolts/variables.html).

## O que são Variáveis?

Em Java, embora utilizemos o termo "variável", objetos armazenam seu estado em **campos** (*fields*). A linguagem utiliza os dois termos de forma relacionada:

* **Variáveis de Instância (campos não-estáticos):** Únicas para cada instância de uma classe.
* **Variáveis de Classe (campos estáticos):** Declaradas com o modificador `static`; existe exatamente uma cópia para toda a classe, independentemente de quantas instâncias existam.
* **Variáveis Locais:** Armazenam estados temporários dentro de um método.
* **Parâmetros:** Variáveis que fornecem informações adicionais a um método ou construtor.

## Regras e Convenções de Nomenclatura

A escolha de nomes para variáveis deve seguir estas diretrizes:

* **Case-sensitive:** Nomes de variáveis diferenciam maiúsculas de minúsculas.
* **Caracteres Permitidos:** Podem ser sequências de letras e dígitos Unicode, começando com uma letra, cifrão (`$`) ou sublinhado (`_`).
* **Convenções:**
* Sempre inicie nomes com uma **letra**.
* Evite o uso de `$` e `_` no início de nomes.
* Não utilize palavras-chave (*keywords*) ou palavras reservadas da linguagem.
* Use palavras completas em vez de abreviações crípticas para tornar o código autoexplicativo (ex: `speed` é melhor que `s`).
* **Camel Case:** Se o nome consistir em uma única palavra, use minúsculas. Se houver mais de uma, capitalize a primeira letra de cada palavra subsequente (ex: `currentGear`).
* **Constantes:** Se a variável for uma constante (ex: `static final`), capitalize todas as letras e separe as palavras com sublinhado (`NUM_GEARS`).



## Tipos de Dados Primitivos

Java suporta oito tipos de dados primitivos:

1. `byte`
2. `short`
3. `int`
4. `long`
5. `float`
6. `double`
7. `boolean`
8. `char`

> **Nota:** Cadeias de caracteres (*strings*) são representadas pela classe `java.lang.String`.

## Valores Padrão

O compilador Java atribui valores padrão para campos de tipos primitivos. No entanto, **variáveis locais nunca recebem um valor padrão automático**; elas devem ser inicializadas antes do uso para evitar erros de compilação.

## Outros Conceitos

* **Literais:** É a representação no código fonte de um valor fixo.
* **Arrays:** Objetos contêineres que mantêm um número fixo de valores de um único tipo. O tamanho do array é definido no momento de sua criação e permanece fixo.

---

*Fonte: [The Java™ Tutorials - Variables*](https://docs.oracle.com/javase/tutorial/java/nutsandbolts/variables.html)