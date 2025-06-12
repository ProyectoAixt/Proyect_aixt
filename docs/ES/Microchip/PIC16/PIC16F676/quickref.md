# **PIC16F676 Quick Guide**
## Reference for the PIC16 used from the MICROCHIP brand
- PIC16F676

**NOTE:** This PIC16F microcontroller only has digital outputs, digital inputs, and ADC

## Pin Names
Pin names are identified by a letter indicating the port and a number indicating the pin. For example, `a6` indicates pin 6 of port A. All names in  **Aixt** are written in lowercase, to follow [V variable naming rules.](https://github.com/vlang/v/blob/master/doc/docs.md#variables).


### PIC16F676 Pin Names
| Port   | 0 | 1 | 2 | 3 | 4 | 5 | 
|:------:|---|---|---|---|---|---|
| **A**  | a0| a1| a2| a3| a4| a5|
| **C**  | c0| c1| c2| c3| c4| c5|

In the PIC16 microcontroller families, port registers are divided into: 

- `TRIS` To configure each port pin
- `PORT` To manage pins as inputs or outputs

To simplify the implementation (and avoid generating unnecessary code) for this Aixt port, each pin's name differs based on its configuration, input, and output, as shown in the following example: 

- `a5_s` Bit name to configure the `a5` pin as input or output 
- `a5`   Bit name to read the pin as input or output `a5`

### Integrated Components 
It has eight analog pins distributed between port A and port C.

| Port   | 0 | 1 | 2 | 3 | 4 | 5 | 
|:------:|---|---|---|---|---|---|
| **A**  |AN0|AN1|AN2|-  |AN3|-  |
| **C**  |AN4|AN5|AN6|AN7|-  |-  |

### Supported Functions
The API contains functions for digital inputs or outputs and for performing analog-to-digital conversion.

name                                  | description
--------------------------------------|---------------------------------------------z-
`pin.setup(pin_name, mode)`     | Configures `PIN_NAME` to `PIN_MODE`
`pin.high(PIN_NAME)`                 | Turns ON `PIN_NAME`
`pin.low(PIN_NAME)`                  | Turns OFF `PIN_NAME`
`pin.write(PIN_NAME,VAL)`            | Writes `VAL` to `PIN_NAME`
`pin.read(PIN_NAME)`                 | Reads `PIN_NAME`
`pin.digital(PIN)`                   | Configures digital I/O for `PIN_NAME`
`pin (PIN)`                           | Configures `PIN_OUTPUT` or `PIN_INPUT`
`port`                                | Initializes `port`
`port.read(PORT_NAME)`               | Reads `PORT_NAME`
`port.setup(PORT_NAME, VALUE)`       | Configures `PORT_NAME` assigns `VALUE`
`port.write(PORT_NAME, VALUE)`       | Writes `PORT_NAME` to `VALUE`
`adc.setup()`                        | Initializes the `adc` 
`adc.read(channel)`                  | Configures the `channel` of the `adc`
`adc`                                 | Initializes the `adc` 
`time.sleep(time)`                   | Delay in `seg`
`time.sleep_us(time)`                | Delay in `microseg`
`time.sleep_ms(time)`                | Delay in `miliseg`
`time`                                | Initializes `time`

### Examples of different API functions in _Aixt_v language 

## Time

```v

time.sleep(5)	// 5 second delay
time.sleep_us(10)	// 10 microsecond delay
time.sleep_ms(500)	// 500 millisecond delay

```

## Pin Configuration

```v

pin.setup(pin.a5, pin.output)      // Function to configure the pin as output 
pin.setup(pin.c2, pin.output)      // Function to configure the pin as output
pin.setup(pin.a2, pin.input)    // Function to configure the pin as input
pin.setup(pin.c4, pin.input)    // Function to configure the pin as input

pin.high(pin.a5)    // Function to turn the pin ON           
pin.low(pin.a5)     // Function to turn the pin OFF

pin.write(pin.a2, 0)  // Function to overwrite the pin
pin.write(pin.a2, 1)  // Function to overwrite the pin

pin.read(pin.a4)      // Function to read the pin
pin.read(pin.c3)      // Function to read the pin

```

Example of turning an LED ON and OFF:

```v
      
for {

    pin.high(pin.c1);
    sleep_us(500);
    pin.low(pin.c1);
    sleep_us(500);

}

```
Example of turning an LED ON and OFF with a digital input:

```v

pin.digital(); // All pins are digital I/O

for {
    
    if(c2 == 1){        // Condition if a 1 is found on c2
        
        pin.high(pin.c1);
        pin.high(pin.c0);
    }
    
    else if(c4 == 1){   // Condition if a 1 is found on c4
        
        pin.low(pin.c1);
        pin.low(pin.c0);
    }

}
        
```

## Port Configuration

```v

port.setup(port.a, ob000000)      // Function to configure the port as output

```

Example of turning a microcontroller port ON and OFF:

```v
      
for {
        
    port.write(port.a,0b010101);
    sleep_ms(500);
    port.write(port.a,0b101010);
    sleep_ms(500);      
        
}

```

## ADC Configuration

```v

adc.setup()     // Initializes the ADC
adc.read(0)     // Selects the analog channel pin

```

Example of turning LEDs ON and OFF depending on the ADC value:

```v

unsigned int adc_result;  // Variable declaration to store the ADC value
        
for {
            
    adc_result = adc.read(0); // Stores the ADC value
    
    if ( adc_result >= 1020 ){
        
        pin.high(pin.c0);
        pin.high(pin.c1);
        pin.high(pin.c2);           
    }
    
    else if ( adc_result >= 820 ){
        
        pin.high(pin.c0);
        pin.high(pin.c1);
        pin.low(pin.c2);
    }
    
    else if ( adc_result >= 620 ){
        
        pin.high(pin.c0);
        pin.low(pin.c1);
        pin.low(pin.c2);   
    }
        
    else {
        
        pin.low(pin.c0);
        pin.low(pin.c1);
        pin.low(pin.c2);      
    }

}

```