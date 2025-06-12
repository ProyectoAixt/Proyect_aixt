# **Referencia Rápida para el Emulador de Software**
Emulador de CLI de software que funciona en _Linux_, _Windows_ y _Android (Termux)_.


## Retardo
Utilice el módulo `time`:

```v
import time

time.sleep(2)            // sleep for 2 seconds
time.sleep_ms(50)        // sleep for 50 milliseconds
time.sleep_us(100)       // sleep for 100 microseconds
```

### Functions
nombre                | descripción
----------------------|-----------------------
`time.sleep(time)`    | retraso en segundos
`time.sleep_us(time)` | retraso en microsegundos
`time.sleep_ms(time)` | retraso en milisegundos


## Pines emulados
Utilice el módulo `pin`:

```v
import pin

pin.high(pin.x)
pin.low(pin.y)
pin.write(pin.z, pin.read(pin.a))   // pin echo
```

### Functions
nombre                  | descripción
------------------------|---------------------------
`pin.high(pin)`         | Turn ON `pin`
`pin.low(pin)`          | Turn OFF `pin`
`pin.write(pin, value)` | Write `value` in `pin`
`pin.read(pin)`         | Return the state of `pin`

### Nombres de Pines Digitales
Las funciones para emular pines digitales de entrada/salida en el terminal utilizan 8 pines emulados denominados: `a`, `b`, `c`, `d`, `w`, `x`, `y` y `z`, se muestran en el terminal después de cualquier cambio, de la siguiente manera:

_**Después de llamar a una función de escritura**_
```
 Aixt virtual pins     [#] = ON   [ ] = OFF
 _____ _____ _____ _____ _____ _____ _____ _____
|  a  |  b  |  c  |  d  |  w  |  x  |  y  |  z  |
| [#] | [ ] | [ ] | [ ] | [ ] | [#] | [ ] | [ ] |
'-----'-----'-----'-----'-----'-----'-----'-----'
```
_**Después de llamar a una función de lectura**_
```
 Aixt virtual pins     Input z : 1
```

_Nota: al utilizarlo, `pin.read()` el usuario debe escribir el valor en la terminal manualmente._


## PWM emulado(Pulse Width Modulation)
Utilice el módulo `pwm`:

```v
import pwm

pwm.write(pwm.ch0, 40)       // set the duty cycle for PWM channel 0
pwm.write(pwm.ch1, 60)       // set the duty cycle for PWM channel 1
```

Salida del terminal:
```
 Aixt virtual PWM outputs
                                    PWM 0 :  40 %
||||||||||||||||||||______________________________
                                    PWM 1 :  60 %
||||||||||||||||||||||||||||||____________________
```

### Funciones
nombre                      | descripción
----------------------------|-----------------------------------
`pwm.write(channel, value)` | Write `value` in the PWM `channel`

### Nombres de los pines PWM
Hay 2 canales PWM emulados llamados: `ch0` y `ch1`.


## ADC emulado (convertidor analógico a digital)
Utilice el módulo `adc`:

```v
import adc

val1 := adc.read(ch0)       // read de ADC channel 0
val2 := adc.read(ch1)       // read de ADC channel 1
```

Salida del terminal:
```
Aixt virtual ADC input     ADC 0 : 23
```
```
Aixt virtual ADC input     ADC 1 : 56
```

### Funciones
nombre              | descripción
--------------------|----------------------------------
`adc.read(channel)` | Return the ADC value in `channel`

### Canales analógicos
Hay 2 canales ADC emulados llamados: `ch0` y `ch1`.


## UART emulado (puerto serial)
Este emulador de software tiene 3 UART virtuales denominados `UART`, `UART2` y `UART3`.

Utilice el módulo `uart` o `uartx`:

```v
import uart

uart.print('Hello ')
uart.println('World...')
```

Salida del terminal:
```
 Aixt virtual UART
Hello world!
```

### Funciones
nombre                      | descripción
----------------------------|-------------------------------------------------------------------------------------
`uart.print(message)`       | Imprima el `message` en el UART virtual
`uart.println(message)`     | Imprima la `message` nueva línea más en el UART virtual
`uart.input(message)`       | Imprime `message` y devuelve la cadena ingresada por el usuario en el UART virtual
`uart2.print(message)`      | Imprima el `message` en el UART virtual 2
`uart2.println(message)`    | Imprima la `message` nueva línea más en el UART virtual 2
`uart2.input(message)`      | Imprime `message` y devuelve la cadena ingresada por el usuario en el UART virtual 2
`uart3.print(message)`      | Imprima el `message` en el UART virtual 3
`uart3.println(message)`    | Imprima la `message` nueva línea más en el UART virtual 3
`uart3.input(message)`      | Imprime `message` y devuelve la cadena ingresada por el usuario en el UART virtual 3

### Función de entrada
Las cadenas de entrada que capturará la `uart.input()` función tienen un tamaño fijo de 30 caracteres.