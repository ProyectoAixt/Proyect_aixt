# **El lenguaje V de Aixt**
El lenguaje **Aixt** _V_ se basa en [The V programming language](https://vlang.io/).

La gramática V fue tomada de estas fuentes (ordenadas por importancia):
- Documentación del árbol de sintaxis abstracta V: [https://modules.vlang.io/v.ast.html](https://modules.vlang.io/v.ast.html)
- Definición de gramática _V_ en Antlr-v4:     [https://github.com/antlr/grammars-v4/blob/master/v/V.g4](https://github.com/antlr/grammars-v4/blob/master/v/V.g4)
- Definición de gramática _V_ en lark:         [(https://github.com/Itay2805/Vork/blob/master/v.lark](https://github.com/Itay2805/Vork/blob/master/v.lark)

##  Diferencias entre Aixt's V and standard V
<!-- - **Aixt** supports the semicolon `;` by separating statements in the same line -->
- Al igual que _V_, **Aixt** admite atributos de función como `[inline]`, pero estos atributos incluyen otros como `[task]`  que brindan soporte para la multitarea en la transpilación al lenguaje _NXC_ y `[as_macro]` para implementarlos como macros C (dispositivos de baja memoria).
- `mutex`  Variables para dar soporte a la multitarea en la transcompilación _NXC_

Las principales diferencias entre **Aixt** y **V** se muestran a continuación:

característica                   | V                                        | Aixt's V
---------------------------------|------------------------------------------|-------------------------------------------------------------
instrumentos de cuerda           | de tamaño dinámico                       | De tamaño fijo y de tamaño dinámico si es compatible
matrices                         | de tamaño dinámico                       | De tamaño fijo y de tamaño dinámico si es compatible
tamaño de enteros predeterminados| 32 bits                                  | depende del dispositivo
estructuras                      | permitir funciones (orientadas a objetos)| 	no permitir funciones (solo programación estructurada)
funciones                        | múltiples valores de retorno             | solo un valor de retorno
macros de texto                  | no permitido                             | permitido mediante el uso del atributo '@[as_macro]', para funciones y constantes
acceso a variables `C`           | no permitido                             | Permitido mediante el uso de la sintaxis 'C.var_name'
variables globales               | deshabilitado por defecto                | habilitado por defecto


##  Palabras clave admitidas por V
Las palabras clave admitidas por V se enumeran en texto en negrita de la siguiente manera.
- as
- asm
- assert
- atomic
- **break**
- **const**
- defer
- **else**
- **enum**
- **false**
- **fn**
- **for**
- go
- goto
- **if**
- **import**
- **in**
- interface
- is
- isreftype
- lock
- **match**
- **module**
- **mut**
- none
- or
- **pub**
- **return**
- rlock
- select
- shared
- sizeof
- spawn
- static
- **struct**
- **true**
- **type**
- typeof
- union
- **unsafe**
- volatile
- **__global**
- __offsetof

## Características del lenguaje V de Aixt
- Todas las variables son locales por defecto
- Palabra clave en caso de necesitar variables globales `__global`
- Literales enteros en notación binaria, octal, hexadecimal y decimal
- Punto flotante, `rune`, `string` y literales _boolean_ 
- Los literales numéricos se pueden incluir `_`  para una mejor legibilidad
- Declaración de variables enteras con y sin signo de 8, 16, 32 y 64 bits (también `isize` y `usize` )
- Declaración de variables de punto flotante de 32 y 64 bits incluyendo notación científica
- Declaración y asignación múltiple en una sola línea
- Declaración por inferencia de tipos predeterminada para variables escalares y de matriz
- Conversión de variables en caso de necesidad de especificar el tipo de variable o el número de bits
- Atributos de función utilizando la sintaxis:
  
``` v
@[attribute] 
fn <name>(<params>) {
    <statements>
}```

- Loops with `for` through arrays and integer ranges:

``` v
arr := [3,5,7,9]
for a in arr {
    a = 0
}
```    
``` v
for i in 1..11 {
    x += i
}
``` 
