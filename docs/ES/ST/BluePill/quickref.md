# **Guía rápida STM32F103C**
Esta implementación de Aixt que admite la tarjeta Blue Pill STM32F103C

## Vista
**STM32F103C, se conectan un total de 44 interfaces, por ejemplo, la tabla de definición de función de pin es la definición de interfaz.**

![Alt text](./../../../assets/images/BLUE_PILL_STM32F103C.jpg)
*Imagen tomada de la hoja de datos del dispositivo*

## Datasheet
[STM32F103C](https://pdf1.alldatasheet.com/datasheet-pdf/view/201596/STMICROELECTRONICS/STM32F103C8T6.html)
Para programar la tarjeta STM32F103C se debe conectar el ST, por lo que se recomienda ver la hoja de datos:
[ST LINK-V2](https://www.waveshare.com/wiki/ST-LINK/V2_(mini))
## Identificación de puerto
A continuación se muestran los puertos utilizados y sus designaciones adecuadas para la programación:

No.| Nombre   | Función 
-- |-----     |---
1  |VBAT      | Fuente de alimentación de 3,3 V; La corriente de salida de la fuente de alimentación externa
2  |          | De forma predeterminada, está habilitado como chip y el nivel alto es efectivo.
3  |          | Empty feet 
4  |          | GPIO11/SPI_SCLK/IIC_SDA/ADC_CH10/JTAG_TDI/TDO 
7  |R         | NRST_RESET BUTTON
10 |A0        | PA0_ADC0_CTS2_T2C1E_WKUP
11 |A1        | PA1_ADC1_RTS2_T2C2
12 |A2        | PA2_ADC2_TX2_T2C3
13 |A3        | PA3_ADC3_RX2_T2C4
14 |A4        | PA4_ADC4_NSS1_CK2
15 |A5        | PA5_ADC5_SCK1 
16 |A6        | PA6_ADC6_MISO1_T3C1_T1BKIN 
17 |A7        | PA7_ADC7_MOSI1_T3C2_T1C1N  
18 |B0        | PB0_ADC8_T3C3_T1C2N
19 |B1        | PB1_ADC9_T3C4_T1C3N
20 |BOOT1     | PB2_BOOT1
21 |B10       | PB10_SCL2_TX3_T2C3N
22 |B11       | PB11_SDA2_RX3_T2C4N
25 |B12       | PB12_SMBAI2_NSS2_T1BKIN_CK3
26 |B13       | PB13_SCK2_T1C1N_CTS3
27 |B14       | PB14_MISO2_T1C2N_RTS3
28 |B15       | PB15_MOSI2_T1C3N
29 |A8        | PA8_CK1_T1C1_MCO
30 |A9        | PA9_TX1_T1C2
31 |A10       | PA10_RX1_T1C3
32 |A11       | PA11_USB-_CTS1_T1C4_CANRX
33 |A12       | PA12_USB+_RTS1_T1ETR_CANTX 
34 |SWIO      | SWIO_JTMS_PA13 
37 |SWCLK     | SWCLK_JTCK_PA14
38 |A15       | PA15_JTDI_NSS1_T2C1E
39 |B3        | PB3_JTDO_SCK1_T2C2_TRACE SWO
40 |B4        | PB4_JTRST_MISO1_T3C1
41 |B5        | PB5_SMBAI1_MOSI1_T2C2
42 |B6        | PB6_SCL1_T4C1_TX1
43 |B7        | PB7_SDA1_T4C2_RX1
44 |BOOT0     | BOOT0
45 |B8        | PB8_SCL1_T4C3_CANRX
46 |B9        | PB9_SDA1_T4C4_CANTX
   |5V        | ENTRADA 5V BLUE PILL STM32F103C
   |GND       | TARJETA DE TIERRA BLUE PILL STM32F103C
   |3.3V      | ENTRADA 3.3V BLUE PILL STM32F103C


### Entrada y salida digital

Para identificar las entradas y salidas digitales se prueban respectivamente los puertos de entrada y salida de la tarjeta, para ello se programó un código el cual permitió probar uno a uno los puertos identificados, tal como se muestra en la (imagen 1): el led está protegido por una resistencia de 330Ω.
PA0,PA1,PA2,PA3,PA4,PA5,PA6,PA7,PB0,PB1,PB10,PB11,PB12,PB13,PB14,PB15,PA8,PA9,PA10,PA11,PA12,PB5,PB6,PB7,PB8,PB9, los antes mencionados también pueden ser utilizados como salidas ya que los pines de la tarjeta permiten ambas funciones dependiendo de como se clasifiquen en la programación, la diferencia entre estos puertos o pines será que algunos soportan voltajes de exactamente 5 voltios y otros que soportan voltajes menores a 5 voltios, para poder entregar 3.3 voltios y 5 voltios a la tarjeta se utiliza un quemador ST-LINK V2 que nos permite seleccionar entre estos dos voltajes cual queremos entregar y nos permite sincronizar el programa que tenemos en la aplicación ARDUINO IDE 2.2.1 para STM32VLD a FLASH y la tarjeta STM32F103C3.

const int ledPIN1 = PA8; //salida digital al led PA3

const int intPIN = PA9; //entrada digital al led PA8
void setup() {
  Serial.begin(9600);
  // put your setup code here, to run once:
  pinMode(ledPIN1, pin.OUTput);//led conectado a salida PA9
  pinMode(intPIN, pin.INput);//interruptor conectado a entrada PA8
}
void loop() {
  // put your main code here, to run repeatedly:
  if (digitalRead(intPIN)==LOW){
    //INTERRUPTOR PRESIONADO
  digitalWrite(ledPIN1, LOW); //LED conectado a PA9  

  }
  else{
    //interruptor suelto

  digitalWrite(ledPIN1, LOW);  //LED conectado a PA9
  
  }  
 delay (1);
}

### Salida Analógica
Para reconocer las entradas analógicas se realiza el mismo proceso de prueba de puertos realizado anteriormente con la diferencia de que solo se probarán los puertos que permiten utilizarlos para recibir y transmitir señales analógicas, las cuales permiten modificar la amplitud y el periodo de la señal. Una señal para este caso se refleja cuando se utiliza un potenciómetro, el cual funciona como una resistencia variable que tiene un valor entre 0Ω y 10 kΩ que regula el nivel de voltaje que será suministrado por este dispositivo a la entrada de nuestro LED, El LED está protegido por una resistencia de 330Ω, con este circuito lo cual nos permitirá observar cómo varía la intensidad de luz del LED dependiendo del valor de Ω asignado al potenciómetro, durante la verificación se obtiene que los puertos que permiten la transferencia de señales analógicas son A8, A9, A10, B3, B4, B5, B6, B7, B12, B13, B14, B15, para esto se programa un código el cual permite identificar uno a uno los puertos previamente identificados.


### Salida PWM


Para reconocer el puerto de señal PWM de la tarjeta AIR32F103 se prueban los puertos de la tarjeta para saber cuál de ellos nos proporciona esta función, así podemos obtener una señal PWM utilizando como entrada una señal analógica modulando el ancho de los pulsos generados por los puertos de salida a través de, durante la identificación se obtiene que los pines que permiten la emisión de una señal PWM son.

Ejemplo para PWM y analógico

definir LED_BUILTIN 2

#include <PWMOutESP32.h> //https://github.com/fellipecouto/PWMOutESP32 [ http://www.efeitonerd.com.br ]

//Resolution between 1 and 16 (bits). Frequency between 1 and 40000 (Hz)
PWMOutESP32 pwm(10, 5000); //Resolution=10bits, Frequency=5000Hz

void setup() {
  Serial.begin(115200);
  pinMode(LED_BUILTIN, pin.OUTput);

  Serial.println("\nPWMOutESP32");
  Serial.println("Library for controlling ESP32 PWM outputs similar to use on Arduino");
  Serial.print("Maximum PWM value for the configured resolution: ");
  Serial.println(pwm.getMaxPWMValue());
}

void loop() {

  for (int fadeValue = 0; fadeValue <= pwm.getMaxPWMValue(); fadeValue++)  {
    pwm.analogWrite(LED_BUILTIN, fadeValue);
    delay(2);
  }
  delay(500);

  for (int fadeValue = pwm.getMaxPWMValue(); fadeValue >= 0; fadeValue--)  {
    pwm.analogWrite(LED_BUILTIN, fadeValue);
    delay(2);
  }
  delay(500);

}

### comunicación UART 

Para identificar los puertos de la tarjeta que permiten la comunicación UART, se utilizan los 3.3 V proporcionados por la tarjeta AIR32F103 como entrada. El voltaje de entrada se regula mediante un potenciómetro que, al girar su perilla y a través de la comunicación entre las tarjetas, permite encender y apagar los LED asignados a la tarjeta STM32F103C a través del puerto UART. Cuando el regulador de voltaje alcanza su valor mínimo de resistencia, el LED verde debe estar encendido. Cuando alcanza el valor promedio de resistencia, debe encenderse. el LED amarillo y cuando llegue a su valor maximo de resistencia se debe encender el LED Rojo en la entrada, se debe conectar un LED a cada puerto, para ello se conectaran estas dos tarjetas mediante el puerto UART generico, es decir conectar el puerto PA9 (TX) de la tarjeta AIR32F103C con el puerto PA10 (RX) de la tarjeta STM32F103C y el puerto PA10 (RX) de la tarjeta AIR32F103C con el puerto PA9 (TX) de la tarjeta STM32F103C.

ejemplo:

## Programación en lenguaje v
Para cada uno de estos módulos, tendrás un archivo en formato .cv con el mismo nombre del módulo y en este tendrás el texto módulo seguido del nombre del módulo, ejemplo:
* module pin
* module adc
* module pwm


### Configuración del puerto de salida
Para activar el puerto a utilizar
```v
pin.setup(pin_name, mode)
```
Para activar el puerto a utilizar
```v
pin.high(PIN_NAME)
```
* *Ejemplo: Si desea activar el puerto 17;  `pin.high(17)`.*

Para deshabilitar el puerto que se está utilizando
```v
pin.low(PIN_NAME)
```
* *Ejemplo: Si desea deshabilitar el puerto 17;  `pin.low(17)`.*

Para deshabilitar o habilitar el uso del puerto

```v
pin.write(PIN_NAME, VALUE)
```
* *Ejemplo: Si desea deshabilitar el puerto 17 `pin.write(17, 1)`,  y si desea activarlo  `pin.write(17, 0)`.*




### Puertos Analógicos a Digitales (ADC)

Para configurar uno de los puertos analógicos
```v
adc.setup(PIN_NAME, SETUP_VALUE, ... )
```
* *En PIN_NAME se ingresa el nombre del puerto analógico, en SETUP_VALUE el VALOR que se dará es dicho puerto.*

Para detectar el VALOR del puerto analógico
```v
x = adc.read(PIN_NAME)
```
* *En `PIN_NAME` el nombre del puerto analogico se ingresa, y `x` toma el VALOR de dicho puerto.*

## Modulación por Ancho de Pulso (salidas PWM)

Para configurar algún PWM
```v
pwm.setup(SETUP_VALUE, setup_VALUE_1, ... )
```
* *En pwm estableces el PWM a utilizar, y en SETUP_VALUE el VALOR al que quieres configurar dicho pwm.*


Para configurar el ciclo de trabajo de un modulador
```v
pwm.write(duty)
```
* *En PWM se fija el pwm a utilizar, y en `duty` el VALOR del ciclo (de 0 a 100) en porcentaje.*

## Comunicatción Serial  (UART)

El UART solía ser la salida de flujo estándar, por lo que las funcione `print()`, `println()` y `input()` funcionan directamente en el UART predeterminado. El UART predeterminado puede variar según la placa o el microcontrolador; consulte la documentación específica. La sintaxis de la mayoría de las funciones UART es: `uart_function_name_x()`, donde `x` es el número de identificación en caso de múltiples UART. Puede omitir `x` para referirse al primer UART o al predeterminado, o en caso de tener solo uno.  

### Configuración de UART

```v
uart.setup(BAUD_RATE)   // the same of uart.setup(BAUD_RATE)
```
Para una segunda conexión se utiliza como:
```v 
uart.setup_1(BAUD_RATE)   // the same of uart.setup_1(BAUD_RATE)
```
- `BAUD_RATE` configurar la velocidad de comunicación
### Transmisión Serial 

```v
uart.print(message)      // print a string to the default UART
```
```v
uart.println(message)    // print a string plus a line-new character to the default UART
```
```v
uart.ready // get everything ready for to UART
```
```v
uart.read // receives binary data (in Bytes) to UART
```
```v
uart.write(MESSAGE)    // send binary data (in Bytes) to second UART
```
- Para un segundo UART se utilizaría de la siguiente manera:
```v
uart.print_1(MESSAGE)    // print a string to the second UART
```
```v
uart.println_1(MESSAGE)  // print a string plus a line-new character to the second UART
```
```v
uart.write_1(MESSAGE)    // send binary data (in Bytes) to second UART
```
```v
uart.ready_1 // get everything ready for to second UART
```
```v
uart.read_1 // receives binary data (in Bytes) to second UART
```

### Retardos

* Uso de los tiempos

    * En cada expresión, el VALOR del tiempo se coloca dentro de los paréntesis.
```v
time.sleep(S) //Seconds
```
```v
time.sleep_ms(MS) //Milliseconds
```
```v
time.sleep_us(US) //Microseconds
```

* Ejemplo de LED parpadeante

```v
import pin
import time {sleep_ms}

pin.setup(14, pin.output)

for {   //infinite loop
    pin.high(14)
    sleep_ms(500)
    pin.low(14)
    sleep_ms(500)
}
```