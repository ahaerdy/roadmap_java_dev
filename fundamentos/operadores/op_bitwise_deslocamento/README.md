# Operadores Bitwise e de Deslocamento de Bits

A linguagem de programação Java também fornece operadores que realizam operações bitwise e de deslocamento de bits em tipos integrais. Os operadores discutidos nesta seção são menos usados. Portanto, sua cobertura é breve; a intenção é apenas tornar você ciente de que esses operadores existem.

- O operador unário de complemento bitwise `~` inverte um padrão de bits; pode ser aplicado a qualquer tipo integral, transformando cada “0” em “1” e cada “1” em “0”.  
  Exemplo: um `byte` contém 8 bits; aplicar este operador a um valor cujo padrão de bits seja `00000000` mudaria seu padrão para `11111111`.

- O operador de deslocamento à esquerda com sinal `<<` desloca um padrão de bits para a esquerda, e o operador de deslocamento à direita com sinal `>>` desloca um padrão de bits para a direita.  
  O padrão de bits é dado pelo operando à esquerda, e o número de posições para deslocar é dado pelo operando à direita.

- O operador de deslocamento à direita sem sinal `>>>` insere um zero na posição mais à esquerda, enquanto a posição mais à esquerda após `>>` depende da extensão de sinal.

- O operador bitwise `&` realiza uma operação AND bit a bit.  
- O operador bitwise `^` realiza uma operação OR exclusivo bit a bit.  
- O operador bitwise `|` realiza uma operação OR inclusivo bit a bit.

---

## Exemplo de Programa

O programa abaixo, **BitDemo**, usa o operador AND bitwise para imprimir o número “2” na saída padrão:

```java
class BitDemo {
    public static void main(String[] args) {
        int bitmask = 0x000F;
        int val = 0x2222;
        // imprime "2"
        System.out.println(val & bitmask);
    }
}
```
