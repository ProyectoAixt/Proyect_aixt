# **Referencia Rápida para la Tarjeta Arduino Nano**


## Retrazo
Utilice el módulo `time`:

```v
import time

time.sleep(2)            // sleep for 2 seconds
time.sleep_ms(50)        // sleep for 50 milliseconds
time.sleep_us(100)       // sleep for 100 microseconds
```

### Funciones
nombre                | descripción
----------------------|----------------------
`time.sleep(time)`    | Retraso en segundos
`time.sleep_us(time)` | Retraso en microsegundos
`time.sleep_ms(time)` | Retraso en milisegundos


## LEDs internos
El LED integrado se llama `led_0` 

```v
import pin

pin.setup(led_0, pin.output)
pin.high(led_0)
```


## Pins
Utilice el módulo `pin`: 

```v
import pin

pin.setup(pin.d0, pin.input)
pin.high(pin.d13)
pin.low(pin.d3)
pin.write(pin.d8, pin.read(pin.d0)) // pin echo
```

### Functions
nombre                  | descripción
------------------------|--------------------------
`pin.setup(pin, mode)`  | Configure `pin` as `mode`
`pin.high(pin)`         | Turn On `pin`
`pin.low(pin)`          | Turn Off `pin`
`pin.write(pin, value)` | Write `value` in `pin`
`pin.read(pin)`         | Return the state of `pin`


### Nombres de Pines Digitales
Los nombres de los pines digitales se nombran de `d0` a `d21`.


## PWM (Pulse Width Modulation)
Utilice el módulo `pwm`:

```v
import pwm

pwm.write(pwm.pin.gp7, 40)       // set the duty cycle for gp7 pin
pwm.write(pwm.pin.gp8, 60)       // set the duty cycle for gp8 pin
```

### Functions
nombre                      | descripción
----------------------------|-----------------------------------
`pwm.write(channel, value)` | Escribe `value` en el PWM `channel`

### Nombres de los Pines PWM
Todos los pines digitales se pueden utilizar como canales PWM.


## ADC (convertidor analógico a digital)
Utilice el módulo `adc`:

```v
import adc

val1 := adc.read(ch0)       // read de ADC channel 0
val2 := adc.read(ch1)       // read de ADC channel 1
```

### Functions
nombre              | descripción
--------------------|--------------------------------------
`adc.read(channel)` | Devuelve el valor del ADC en `channel`

### Canales Analógicos
Los canales PWM se nombran de `ch0` a `ch2`.


## UART (puerto serial)
Utilice el módulo `uart` a `uart2`:

```v
import uart

uart.print('Hello ')
uart.println('World...')
```

### Funciones
nombre                   | descripción
-------------------------|---------------------------------------------------------------
`uart.setup(baud_rate)`  | Configure the `baud_rate` of the UART
`uart.read()`            | Return one character received by UART
`uart.input(message)`    | Send the `message` and then return the string received by UART
`uart.write(character)`  | Send one character by UART
`uart.print(message)`    | Send the `message` by UART
`uart.println(message)`  | Send the `message` plus a new line by UART
`uart.any()`             | Return the number uf characters in the UART's buffer
`uart2.setup(baud_rate)` | Configure the `baud_rate` of the UART 2
`uart2.read()`           | Return one character received by UART 2
`uart2.input(message)`   | Send the `message` and then return the string received by UART 2
`uart2.write(character)` | Send one character by UART 2
`uart2.print(message)`   | Send the `message` by UART 2
`uart2.println(message)` | Send the `message` plus a new line by UART 2
`uart2.any()`            | Return the number uf characters in the UART2's buffer


## USB UART (puerto serial por USB)
Utilice el módulo `usb_uart`:

```v
import usb_uart

usb_uart.print('Hello ')
usb_uart.println('World...')
```

### Functions
nombre                   | descripción
-------------------------|---------------------------------------------------------------
`uart.read()`            | Return one character received by USB-UART
`uart.input(message)`    | Send the `message` and then return the string received by USB-UART
`uart.write(character)`  | Send one character by USB-UART
`uart.print(message)`    | Send the `message` by USB-UART
`uart.println(message)`  | Send the `message` plus a new line by USB-UART
`uart.any()`             | Return the number uf characters in the USB-UART's buffer

