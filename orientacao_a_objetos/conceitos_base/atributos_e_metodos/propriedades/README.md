# Propriedades em Java

A classe Java Properties, `java.util.Properties`, é como um `Map` de pares chave e valor do tipo `String`. A classe Java Properties pode escrever os pares chave-valor em um arquivo de propriedades no disco e ler novamente esses valores. Este é um mecanismo frequentemente usado para armazenar propriedades simples de configuração em aplicações Java.

## Criar uma Instância de Properties
Para usar a classe Java Properties, você deve primeiro criar uma instância de `Properties`. Isso é feito via seu construtor e a instrução `new` do Java.  
Exemplo:

```java
Properties properties = new Properties();
```

## Definir Propriedades
Para definir propriedades em uma instância de `Properties`, use o método `setProperty()`.  
Exemplo:

```java
properties.setProperty("email", "john@doe.com");
```

Este exemplo define a propriedade com a chave `email` para o valor `john@doe.com`.

## Obter Propriedades
Para obter propriedades de um objeto `Properties`, use o método `getProperty()`, passando a chave como parâmetro.  
Exemplo:

```java
String email = properties.getProperty("email");
```

## Remover Propriedades
Você pode remover uma propriedade usando o método `remove()`, passando a chave como parâmetro.  
Exemplo:

```java
properties.remove("email");
```

## Iterar Propriedades
Você pode iterar pelas chaves de uma instância de `Properties` obtendo o conjunto de chaves e percorrendo-o.  
Exemplo:

```java
Properties properties = new Properties();
properties.setProperty("key1", "value1");
properties.setProperty("key2", "value2");
properties.setProperty("key3", "value3");

Iterator keyIterator = properties.keySet().iterator();
while(keyIterator.hasNext()){
    String key   = (String) keyIterator.next();
    String value = properties.getProperty(key);
    System.out.println(key + " = " + value );
}
```

Saída:
```
key1 = value1
key2 = value2
key3 = value3
```

## Armazenar Propriedades em Arquivo
Você pode armazenar pares chave-valor em um arquivo `.properties` usando o método `store()`.  
Exemplo:

```java
Properties properties = new Properties();
properties.setProperty("property1", "value1");
properties.setProperty("property2", "value2");
properties.setProperty("property3", "value3");

try(FileWriter output = new FileWriter("data/props.properties")){
    properties.store(output, "These are properties");
} catch (IOException e) {
    e.printStackTrace();
}
```

## Codificação de Arquivo de Propriedades
Por padrão, o encoding é **ISO-8859-1 (Latin-1)**. É comum usar UTF-8.  
Exemplo:

```java
try(FileWriter output = new FileWriter("data/props.properties", Charset.forName("UTF-8"))){
    properties.store(output, "These are properties");
} catch (IOException e) {
    e.printStackTrace();
}
```

## Formato de Arquivo de Propriedades
Um arquivo `.properties` consiste em linhas com `key=value`.  
Exemplo:

```
#These are properties
#Thu Jul 04 21:29:20 CEST 2019
property2=value2
property1=value1
property3=value3
```

Linhas iniciadas com `#` são comentários.

## Carregar Propriedades de Arquivo
Você pode carregar propriedades de um arquivo usando `load()`.  
Exemplo:

```java
Properties properties = new Properties();
try(FileReader fileReader = new FileReader("data/props.properties")){
    properties.load(fileReader);
} catch (IOException e) {
    e.printStackTrace();
}
```

## Armazenar Propriedades em XML
A classe `Properties` também pode armazenar pares chave-valor em XML via `storeToXML()`.  
Exemplo:

```java
Properties properties = new Properties();
properties.setProperty("property1", "value1");
properties.setProperty("property2", "value2");
properties.setProperty("property3", "value3");

try(FileOutputStream output = new FileOutputStream("data/props.xml")){
    properties.storeToXML(output, "These are properties");
} catch (IOException e) {
    e.printStackTrace();
}
```

## Carregar Propriedades de XML
Você pode carregar propriedades de um arquivo XML usando `loadFromXML()`.  
Exemplo:

```java
Properties properties = new Properties();
try(FileInputStream fileInputStream = new FileInputStream("data/props.xml")){
    properties.loadFromXML(fileInputStream);
} catch(IOException e){
    e.printStackTrace();
}
```

## Propriedades Padrão
A classe `Properties` permite valores padrão:
- Passando um valor padrão ao `getProperty()`.
- Criando uma instância com outra `Properties` como padrão.

Exemplo com valor padrão:

```java
Properties properties = new Properties();
String preferredLanguage = properties.getProperty("preferredLanguage", "Danish");
```

Exemplo com instância padrão:

```java
Properties defaultProperties = new Properties();
defaultProperties.setProperty("preferredLanguage", "Danish");

Properties newProperties = new Properties(defaultProperties);
String language = newProperties.getProperty("preferredLanguage");
System.out.println("Preferred language: " + language);
```

## Propriedades do Sistema
O Java possui propriedades do sistema acessíveis via `System.getProperties()`.  
Exemplo:

```java
Properties systemProperties = System.getProperties();
```

Você pode definir propriedades do sistema pela linha de comando com `-D`.  
Exemplo:

```
java -Dkey1=value -cp . com.jenkov.MyApp
```

## Properties é Subclasse de Hashtable (Erro de Design)
A classe `Properties` é subclasse de `Hashtable`, permitindo `put()` e `get()` com valores não-String, o que quebra o propósito da classe.  
Exemplo problemático:

```java
Properties asProperties = new Properties();
asProperties.put("abc", 999);
String abc = asProperties.getProperty("abc");
System.out.println(abc); // retorna null
```
