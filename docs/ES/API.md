# Interfaz de Programación de Aplicaciones **_Aixt_** v0.1.2

## Digitales I/O (Pines)
requiere:
```v
import pin
```

### Configuración de pines
```v
pin.setup(name, mode)
```
- `name` podría cambiar dependiendo del microcontrolador por ejemplo `pin.b7`, `pin.gp7`, etc.
- `mode`:
  - `pin.input`
  - `pin.output`

### Salida de pin
```v
pin.high(name)
```

```v
pin.low(name)
```

```v
pin.toggle(name)    
// not available for all devices
```

```v
pin.write(name, value)
```
- `value` es un entero que se escribirá en el pin
  - `0`
  - `1`


### Entrada de pin
```v
x = pin.read(name)
```
`pin.read()` devuelve un entero (`0` o `1`)

## Convertidor Analógico a Digital (entradas ADC)
requiere:
```v
import adc
```

La sintaxis para todas las funciones ADC es: `adc.function_name()`.


### Configuración del ADC
```v
adc.setup(setup_value_1, setup_value_2, ... )   // equals to adc1_setup(...)
```

### Lectura del ADC
```v
x = adc.read(channel)
```
- `channel` es un número de identificación de la entrada del ADC, por ejemplo `adc.ch3`


## Modulación por ancho de pulso (salidas PWM)
requiere:
```v
import pwm
```

La sintaxis para todas las funciones PWM es: `pwm_function_name()`.

### Configuración de PWM
```v
pwm_setup(setup_value_1, setup_value_2, ... )  //or just pwm.setup(...)
```

### Ciclo de trabajo PWM
```v
pwm.write(channel, duty)  //or pwm1_duty(duty)
```

- `duty` es el ciclo de trabajo (número de 8 bits en la mayoría de los dispositivos)
- `channel` es el nombre de la salida o del canal, por ejemplo `pwm.ch1`


## Comunicación del serial (UART)
requiere:
```v
import uart
```

El UART predeterminado puede variar según la placa o el microcontrolador; consulte la documentación específica. La sintaxis de la mayoría de las funciones UART es:`uartx.function_name()`, donde representa `x` l número de identificación si hay varios UART. Puede omitir el `x` para referirse al primer UART, el predeterminado, o si solo tiene uno.  

### Configuración UART

```v
uart.setup(baud_rate)   // the same of uart1_setup(baud_rate)
```
- `baud_rate` configurar la velocidad de comunicación

### Recepción del serial
```v
str1 = uart.input()          // read a string from the default UART
```
```v
str2 = uart2.input()    // read a string from UART2
```
```v
str2 = uart1.read()    // read a single Byte from UART1
```

### Transmisión del Serial
```v
uart.print(message)      // print a string to the default UART
```
```v
uart.println(message)    // print a string plus a line-new character to the default UART
```
```v
uart2.print(message)    // print a string to the UART2
```
```v
uart3.println(message)  // print a string plus a line-new character to the UART3
```
```v
uart2.write(message)    // send binary data (in Bytes) to UART2
```


## Retardo
requiere:
```v
import time
```


```v
time.sleep(s)    // delay in seconds
```
```v
time.sleep_ms(ms)    // delay in milliseconds
```
```v
time.sleep_us(us)    // delay in microseconds
```


# Creación de un nuevo módulo API

### Archivo `function_name.c.v`.
Todas las funciones implementadas en cada módulo de **Aixt** tienen un archivo llamado:
`function_name.c.v` donde se realiza su implementación.

Por ejemplo, la `setup` función del modulo `adc`, que establece la resolución del ADC, debe describirse en `adc/setup.c.v`.

En los dispositivos que utilizan el _backend_ de **arduino**  la mayoría de las funcionalidades simplemente deben enmascararse en lugar de implementarse desde cero. En este caso, `setup` la función en **V** enmascara la función de **arduino** `analogReadResolution`.

Todas las funciones deben ser públicas (`pub`).

El atributo `@[inline]` es opcional y define la función creada en C como `inline`.


### Archivo `module_name.c.v`.
Todos los módulos implementados en el directorio `api`  tienen un archivo con el mismo nombre que el módulo. Por ejemplo, el modulo `pwm` debe tener un archivo `pwm.c.v` donde se creen sus definiciones básicas.

En este caso se definen las funciones a invocar desde C (arduino).

V permite el tipo de datos `any` que resulta práctico si no se conocen el tipo de datos de retorno y/o los parámetros de la función que se van a enmascarar.

En este caso la implementación puede dejarse como está.

### Inclusión de archivos en C
Los módulos API de **Aixt** pueden incluir archivos `.c` o `.h` con la directiva `#include <lib.h>` o `#include “lib.h”` Tenga en cuenta que los archivos incluidos en `"` se buscarán en el mismo directorio.


### Enmascaramiento de métodos de Arduino
En el caso del _backend_ de **arduino** , Las funciones definidas como métodos se pueden redefinir como macros en un archivo `.c` para que puedan ser `called` desde V sin problemas. 

Reemplazar el `.` con `_`.


Y cada función a implementar o enmascarar se describe en un archivo `.c.v` separado, para que pueda ser llamada independientemente de V para utilizar la menor cantidad de memoria posible si así lo desea el usuario.

En este caso debemos reemplazar `Serial1` por justo `Serial` en todas las funciones.


Eliminamos los módulos no soportados y listo

Ahora vamos a recopilar los ejemplos para corroborar el funcionamiento.

Renombramos las carpetas de ejemplos y los archivos `.v`.

Es recomendable abrir una sesión de vscode diferente solo con el archivo de proyecto de ejemplo.

debemos modificar el archivo `settings.json` en el directorio `.vscode` con el nombre del nuevo dispositivo.

En el caso del ejemplo de parpadeo, la transcompilación generó el archivo `.ino` y el archivo binario de salida en la carpeta `build`.

ahora lo probamos en el simulador **Wokwi** podemos copiar el código generado al simulador

Como podemos ver el ejemplo de las obras de parpadeo