## Pacotes

---

```java
public class Package
extends Object
implements AnnotatedElement

```

Os objetos `Package` contêm informações de versão sobre a implementação e a especificação de um pacote Java. Essas informações de versionamento são recuperadas e disponibilizadas pela instância de `ClassLoader` que carregou a(s) classe(s). Normalmente, elas são armazenadas no manifesto que é distribuído com as classes.

O conjunto de classes que compõem o pacote pode implementar uma especificação específica e, se for o caso, as strings de título da especificação, número da versão e fornecedor identificam essa especificação. Uma aplicação pode perguntar se o pacote é compatível com uma versão específica; veja o método `isCompatibleWith` para mais detalhes.

Os números de versão de especificação usam uma sintaxe que consiste em números inteiros decimais não negativos separados por pontos ".", por exemplo, "2.0" ou "1.2.3.4.5.6.7". Isso permite que um número extensível seja usado para representar versões major, minor, micro, etc. A especificação da versão é descrita pela seguinte gramática formal:

> *SpecificationVersion:*
> *Digits RefinedVersion_opt_*
> *RefinedVersion:*
> `.` *Digits*
> `.` *Digits RefinedVersion*
> *Digits:*
> *Digit*
> *Digits*
> *Digit:*
> any character for which `Character.isDigit(char)` returns `true`, e.g. 0, 1, 2, ...

As strings de título de implementação, versão e fornecedor identificam uma implementação e são disponibilizadas de forma conveniente para permitir o relato preciso dos pacotes envolvidos quando ocorre um problema. O conteúdo de todas as três strings de implementação é específico do fornecedor. As strings de versão de implementação não possuem uma sintaxe especificada e devem ser comparadas apenas quanto à igualdade com os identificadores de versão desejados.

Dentro de cada instância de `ClassLoader`, todas as classes do mesmo pacote java possuem o mesmo objeto Package. Os métodos estáticos permitem que um pacote seja encontrado pelo nome ou que o conjunto de todos os pacotes conhecidos pelo carregador de classes atual seja encontrado.

Veja Também:
`ClassLoader.definePackage(java.lang.String, java.lang.String, java.lang.String, java.lang.String, java.lang.String, java.lang.String, java.lang.String, java.net.URL)`

---

### Resumo dos Métodos

| Modificador e Tipo | Método | Descrição |
| --- | --- | --- |
| `<A extends Annotation> A` | `getAnnotation(Class<A> annotationClass)` | Retorna a anotação deste elemento para o tipo especificado se tal anotação estiver *presente*, caso contrário, null. |
| `Annotation[]` | `getAnnotations()` | Retorna as anotações que estão *presentes* neste elemento. |
| `<A extends Annotation> A[]` | `getAnnotationsByType(Class<A> annotationClass)` | Retorna as anotações que estão *associadas* a este elemento. |
| `<A extends Annotation> A` | `getDeclaredAnnotation(Class<A> annotationClass)` | Retorna a anotação deste elemento para o tipo especificado se tal anotação estiver *diretamente presente*, caso contrário, null. |
| `Annotation[]` | `getDeclaredAnnotations()` | Retorna as anotações que estão *diretamente presentes* neste elemento. |
| `<A extends Annotation> A[]` | `getDeclaredAnnotationsByType(Class<A> annotationClass)` | Retorna a(s) anotação(ões) deste elemento para o tipo especificado se tais anotações estiverem *diretamente presentes* ou *indiretamente presentes*. |
| `String` | `getImplementationTitle()` | Retorna o título deste pacote. |
| `String` | `getImplementationVendor()` | Retorna o nome da organização, fornecedor ou empresa que forneceu esta implementação. |
| `String` | `getImplementationVersion()` | Retorna a versão desta implementação. |
| `String` | `getName()` | Retorna o nome deste pacote. |
| `static Package` | `getPackage(String name)` | Encontra um pacote pelo nome na instância de `ClassLoader` do chamador. |
| `static Package[]` | `getPackages()` | Obtém todos os pacotes atualmente conhecidos para a instância de `ClassLoader` do chamador. |
| `String` | `getSpecificationTitle()` | Retorna o título da especificação que este pacote implementa. |
| `String` | `getSpecificationVendor()` | Retorna o nome da organização, fornecedor ou empresa que possui e mantém a especificação das classes que implementam este pacote. |
| `String` | `getSpecificationVersion()` | Retorna o número da versão da especificação que este pacote implementa. |
| `int` | `hashCode()` | Retorna o código de hash computado a partir do nome do pacote. |
| `boolean` | `isAnnotationPresent(Class<? extends Annotation> annotationClass)` | Retorna true se uma anotação para o tipo especificado estiver *presente* neste elemento, caso contrário, false. |
| `boolean` | `isCompatibleWith(String desired)` | Compara a versão da especificação deste pacote com uma versão desejada. |
| `boolean` | `isSealed()` | Retorna true se este pacote for selado. |
| `boolean` | `isSealed(URL url)` | Retorna true se este pacote for selado em relação à URL de origem do código especificada. |
| `String` | `toString()` | Retorna a representação em string deste Package. |

#### Métodos herdados da classe java.lang.Object

`clone, equals, finalize, getClass, notify, notifyAll, wait, wait, wait`

---

### Detalhes dos Métodos

#### getName

```java
public String getName()

```

Retorna o nome deste pacote.

**Retorna:**
O nome totalmente qualificado deste pacote, conforme definido na seção 6.5.3 de *The Java™ Language Specification*, por exemplo, `java.lang`

---

#### getSpecificationTitle

```java
public String getSpecificationTitle()

```

Retorna o título da especificação que este pacote implementa.

**Retorna:**
o título da especificação, null é retornado se não for conhecido.

---

#### getSpecificationVersion

```java
public String getSpecificationVersion()

```

Retorna o número da versão da especificação que este pacote implementa. Esta string de versão deve ser uma sequência de inteiros decimais não negativos separados por "." e pode conter zeros à esquerda. Quando as strings de versão são comparadas, os números mais significativos são comparados.

**Retorna:**
a versão da especificação, null é retornado se não for conhecido.

---

#### getSpecificationVendor

```java
public String getSpecificationVendor()

```

Retorna o nome da organização, fornecedor ou empresa que possui e mantém a especificação das classes que implementam este pacote.

**Retorna:**
o fornecedor da especificação, null é retornado se não for conhecido.

---

#### getImplementationTitle

```java
public String getImplementationTitle()

```

Retorna o título deste pacote.

**Retorna:**
o título da implementação, null é retornado se não for conhecido.

---

#### getImplementationVersion

```java
public String getImplementationVersion()

```

Retorna a versão desta implementação. Ela consiste em qualquer string atribuída pelo fornecedor desta implementação e não possui nenhuma sintaxe específica definida ou esperada pelo runtime Java. Pode ser comparada quanto à igualdade com outras strings de versão de pacote usadas para esta implementação por este fornecedor para este pacote.

**Retorna:**
a versão da implementação, null é retornado se não for conhecido.

---

#### getImplementationVendor

```java
public String getImplementationVendor()

```

Retorna o nome da organização, fornecedor ou empresa que forneceu esta implementação.

**Retorna:**
o fornecedor que implementou este pacote.

---

#### isSealed

```java
public boolean isSealed()

```

Retorna true se este pacote for selado.

**Retorna:**
true se o pacote for selado, false caso contrário

---

#### isSealed

```java
public boolean isSealed(URL url)

```

Retorna true se este pacote for selado em relação à URL de origem do código especificada.

**Parâmetros:**
`url` - a URL de origem do código

**Retorna:**
true se este pacote for selado em relação à url

---

#### isCompatibleWith

```java
public boolean isCompatibleWith(String desired)
                         throws NumberFormatException

```

Compara a versão da especificação deste pacote com uma versão desejada. Retorna true se o número da versão da especificação deste pacote for maior ou igual ao número da versão desejada.

Os números de versão são comparados comparando sequencialmente os componentes correspondentes das strings desejada e de especificação. Cada componente é convertido como um número inteiro decimal e os valores são comparados. Se o valor da especificação for maior que o valor desejado, true é retornado. Se o valor for menor, false é retornado. Se os valores forem iguais, o ponto é ignorado e o próximo par de componentes é comparado.

**Parâmetros:**
`desired` - a string de versão da versão desejada.

**Retorna:**
true se o número da versão deste pacote for maior ou igual ao número da versão desejada

**Lança:**
`NumberFormatException` - se a versão desejada ou a atual não estiver no formato correto separado por pontos.

---

#### getPackage

```java
public static Package getPackage(String name)

```

Encontra um pacote pelo nome na instância de `ClassLoader` do chamador. A instância de `ClassLoader` do chamador é usada para encontrar a instância de pacote correspondente à classe nomeada. Se a instância de `ClassLoader` do chamador for null, o conjunto de pacotes carregados pela instância do `ClassLoader` do sistema será pesquisado para encontrar o pacote nomeado.

Os pacotes possuem atributos para versões e especificações apenas se o carregador de classes tiver criado a instância do pacote com os atributos apropriados. Normalmente, esses atributos são definidos nos manifestos que acompanham as classes.

**Parâmetros:**
`name` - um nome de pacote, por exemplo, java.lang.

**Retorna:**
o pacote com o nome solicitado. Pode ser null se nenhuma informação de pacote estiver disponível a partir do arquivo ou da base de código.

---

#### getPackages

```java
public static Package[] getPackages()

```

Obtém todos os pacotes atualmente conhecidos para a instância de `ClassLoader` do chamador. Se a instância de `ClassLoader` do chamador for a instância do `ClassLoader` de inicialização (bootstrap), que pode ser representada por null em algumas implementações, apenas os pacotes correspondentes às classes carregadas pela instância do `ClassLoader` de inicialização serão retornados.

**Retorna:**
um novo array de pacotes conhecidos pela instância de `ClassLoader` do chamador.

---

#### hashCode

```java
public int hashCode()

```

Retorna o código de hash computado a partir do nome do pacote.

**Substitui:**
`hashCode` na classe `Object`

**Retorna:**
um valor de código de hash para este objeto.

---

#### isAnnotationPresent

```java
public boolean isAnnotationPresent(Class<? extends Annotation> annotationClass)

```

Retorna true se uma anotação para o tipo especificado estiver presente neste elemento, caso contrário, false. Este método foi projetado principalmente para acesso conveniente a anotações de marcação (marker annotations).

**Especificado por:**
`isAnnotationPresent` na interface `AnnotatedElement`

**Parâmetros:**
`annotationClass` - o objeto Class correspondente ao tipo de anotação

**Retorna:**
true se uma anotação para o tipo de anotação especificado estiver presente neste elemento, caso contrário, false

**Lança:**
`NullPointerException` - se a classe de anotação fornecida for null

---

#### toString

```java
public String toString()

```

Retorna a representação em string deste Package. Seu valor é a string "package " e o nome do pacote. Se o título do pacote estiver definido, ele será anexado. Se a versão do pacote estiver definida, ela será anexada.

**Substitui:**
`toString` na classe `Object`

**Retorna:**
uma representação em string do objeto.
