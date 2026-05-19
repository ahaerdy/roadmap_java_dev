### Resumo de Variáveis

A linguagem de programação Java usa tanto “campos” quanto “variáveis” como parte de sua terminologia.

- **Variáveis de instância (campos não estáticos):** são únicas para cada instância de uma classe.  
- **Variáveis de classe (campos estáticos):** são campos declarados com o modificador `static`; existe exatamente uma cópia de uma variável de classe, independentemente de quantas vezes a classe tenha sido instanciada.  
- **Variáveis locais:** armazenam estado temporário dentro de um método.  
- **Parâmetros:** são variáveis que fornecem informações adicionais a um método; tanto variáveis locais quanto parâmetros são sempre classificados como “variáveis” (não “campos”).

Ao nomear seus campos ou variáveis, existem regras e convenções que você deve (ou precisa) seguir.

Os oito tipos primitivos de dados são:  
`byte`, `short`, `int`, `long`, `float`, `double`, `boolean` e `char`.

A classe `java.lang.String` representa cadeias de caracteres.

O compilador atribuirá um valor padrão razoável para campos dos tipos acima; para variáveis locais, um valor padrão nunca é atribuído.

Um **literal** é a representação no código-fonte de um valor fixo.

Um **array** é um objeto contêiner que mantém um número fixo de valores de um único tipo. O comprimento de um array é estabelecido quando o array é criado. Após a criação, seu comprimento é fixo.