# Variáveis em Java

## O que são Variáveis?

Em Java, usamos o termo **variável** para nos referirmos a diferentes formas de armazenar dados. Quando declaradas **dentro de uma classe, mas fora de métodos, construtores ou blocos**, essas variáveis são chamadas de **campos (fields)**. Já variáveis locais e parâmetros não são considerados campos, embora também sejam variáveis.

### Tipos de variáveis em Java

- **Variáveis de Instância (CAMPOS não estáticos):** cada objeto possui sua própria cópia.  
- **Variáveis de Classe (CAMPOS estáticos):** declaradas com o modificador `static`; existe exatamente uma cópia compartilhada por toda a classe, independentemente de quantas instâncias existam.  
- **Variáveis Locais:** armazenam estados temporários dentro de um método, construtor ou bloco.  
- **Parâmetros:** variáveis que fornecem informações adicionais a um método ou construtor, declaradas entre os parênteses da assinatura.  

## Regras e Convenções de Nomenclatura

A escolha de nomes para variáveis deve seguir estas diretrizes:

- **Case-sensitive:** Nomes de variáveis diferenciam maiúsculas de minúsculas.
- **Caracteres Permitidos:** Podem ser sequências de letras e dígitos Unicode, começando com uma letra, cifrão (`$`) ou sublinhado (`_`).
- **Convenções:**
   - Sempre inicie nomes com uma **letra**.
   - Evite o uso de `$` e `_` no início de nomes.
   - Não utilize palavras-chave (*keywords*) ou palavras reservadas da linguagem.
   - Use palavras completas em vez de abreviações crípticas para tornar o código autoexplicativo (ex: `speed` é melhor que `s`).
   - **Camel Case:** Se o nome consistir em uma única palavra, use minúsculas. Se houver mais de uma, capitalize a primeira letra de cada palavra subsequente (ex: `currentGear`).
   - **Constantes:** Se a variável for uma constante (ex: `static final`), capitalize todas as letras e separe as palavras com sublinhado (`NUM_GEARS`).

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