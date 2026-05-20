# Operadores

Agora que você aprendeu a declarar e inicializar variáveis, provavelmente quer saber como fazer algo com elas. Aprender os operadores da linguagem de programação Java é um bom ponto de partida.  

**Operadores** são símbolos especiais que executam operações específicas em um, dois ou três operandos e retornam um resultado.

À medida que exploramos os operadores da linguagem Java, pode ser útil saber de antemão quais operadores têm maior precedência. Os operadores na tabela a seguir estão listados de acordo com a ordem de precedência. Quanto mais próximo do topo da tabela um operador aparece, maior sua precedência. Operadores com maior precedência são avaliados antes dos operadores com precedência relativamente menor. Operadores na mesma linha têm precedência igual.  

Quando operadores de mesma precedência aparecem na mesma expressão, uma regra deve determinar qual é avaliado primeiro. **Todos os operadores binários, exceto os operadores de atribuição, são avaliados da esquerda para a direita; operadores de atribuição são avaliados da direita para a esquerda.**

---

## Precedência de Operadores

| Operadores | Precedência |
|------------|-------------|
| pós-fixo | `expr++  expr--` |
| unário | `++expr  --expr  +expr  -expr  ~ !` |
| multiplicativo | `* / %` |
| aditivo | `+ -` |
| deslocamento | `<< >> >>>` |
| relacional | `< > <= >= instanceof` |
| igualdade | `== !=` |
| AND bit a bit | `&` |
| OR exclusivo bit a bit | `^` |
| OR inclusivo bit a bit | `|` |
| AND lógico | `&&` |
| OR lógico | `||` |
| ternário | `? :` |
| atribuição | `= += -= *= /= %= &= ^= |= <<= >>= >>>=` |

---

## Observações

Na programação de uso geral, certos operadores tendem a aparecer com mais frequência que outros; por exemplo, o operador de atribuição `"="` é muito mais comum que o operador de deslocamento à direita sem sinal `">>>"`.  

Com isso em mente, a discussão a seguir foca primeiro nos operadores que você provavelmente usará regularmente e termina com aqueles menos comuns.  

Cada explicação é acompanhada por **código de exemplo** que você pode compilar e executar. Estudar sua saída ajudará a reforçar o que você acabou de aprender.
