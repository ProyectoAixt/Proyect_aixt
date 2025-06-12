# **Dispositivos y placas compatibles**

Todos los dispositivos compatibles implementan estos módulos:
- `time`: Funciones de retardo
- `pin`: GPIO
- `adc`: Entradas ADC
- `pwm`: Salidas PWM
- `uart`: puerto serie

Algunos otros dispositivos como PIC16F y AT admiten la gestión de puertos pin:
- `port`: GPIO como puerto multi-bit

## Emulador para Linux, Android (Termux) y Windows
- **_Dispositivo x64-based o AArch64-based_**: x64 o AArch64 

## LEGO Mindstorms NXT
- **_Bloque inteligente NXT_**: AT91SAM7S256 (ARM7TDMI) "_nxc_ backend" 
  
## Microchip

Para el compilador XC8:
- **Familia 16F de 8-bit**
    - Familia PIC16F8x   **_(only `time`, `pin`, `port`)_**
    - PIC16F628A   **_(en proceso...)_**
    - PIC16F676   **_(only `time`, `pin`, `adc`, `port`)._**
    - PIC16F873A    
    - PIC16F886     
- **Familia 18F de 8-bit**
    - PIC18F452     
    - PIC18F2550     
- **_Explorer 16_**: PIC18F4550 **_(en proceso...)_**

Para el compilador XC16::
- **_Explorer 16_**: PIC24FJ128GA010 
- **_Explorer 16_**: dsPIC33FJ256GP710A **_(en proceso...)_**

## Atmel (Microchip)
- **_Digispark Kickstarter_**: ATtiny85 "_arduino_ backend" **_(en proceso...)_** 
- **_MH-Tiny_**: ATtiny88 "_arduino_ backend" 
- **_Arduino Uno_**: ATmega328p "_arduino_ backend"   
- **_Arduino Nano_**: ATmega328p "_arduino_ backend"  

## Estudio Seeed
- **_Seeed Studio XIAO SAMD21_**: ATSAMD21G18 (Cortex-M0+) "_arduino_ backend" 

## Cypress
Para el creador de PSoC:
- **PSoC 3**
    - **_CY8CKIT-001 + (009)_**: CY8C3866AXI-040 (8051) **_(en proceso...)_**
- **PSoC 4**
  - **_CY8CKIT-049-42xx_**: CY8C4245AXI-483 (Cortex-M0) **_(en proceso...)_**
  - **_CY8CKIT-145-40xx_**: CY8C4045AZI-S413 (Cortex-M0) **_(en proceso...)_**
- **PSoC 5LP**
    - **_CY8CKIT-059_**: CY8C5888LTI-LP097 (Cortex-M3) **_(en proceso...)_**

## LogicGreen 
- **_LQFP32 MiniEVB_**: lgt8f328p "_arduino_ backend"

## Espressif
- **ESP8266**
    - **_NodeMCU V3 Lua_**: ESP8266 (LX106) "_arduino_ backend" 
- **ESP32**
    - **_ESP32 DEVKITV1_**: ESP32 (LX6) "_arduino_ backend" **_(en proceso...)_**
    - **_D1 R32_**: ESP32 (LX6) "_arduino_ backend" _(WIP...)_**
    - **_CORE-ESP32_**: ESP32-C3 (RV32) "_arduino_ backend" **_(en proceso...)_**
    - **_ESP32-C3FH4 Core Board (WeAct Studio)_**: ESP32-C3 (RV32) "_arduino_ backend" 
    - **_LILYGO T-Watch 2020 V1_**: ESP32 (LX6) "_arduino_ backend" **_(en proceso...)_**  

## ST
- **_Blue Pill_**: STM32F103C6 (Cortex-M3) "_arduino_ backend" 
- **_STM32G431CBU6 Core Board_**: STM32G431CBU6 (Cortex-M4F) "_arduino_ backend" **_(en proceso...)_**

## LuatOS
- **_CORE-Air32F103CBT6_**: air32f103 (Cortex-M3) "_arduino_ backend" 

## Artery
- **_Black Pill_**: AT32F403ACGU7 (Cortex-M4) "_arduino_ backend" **_(en proceso...)_**

## Raspberry Pi
- **_Raspberry Pi Pico_**: RP2040 (Dual Cortex-M0+) "_arduino_ backend" 
- **_Raspberry Pi Pico W_**: RP2040 (Dual Cortex-M0+) "_arduino_ backend" 

## WCH
- **_Placa base CH552_**: CH552 (E8051) **_(en proceso...)_**
- **_Placa base CH552 (WeAct Studio)_**: CH552 (E8051) **_(en proceso...)_**
- **_Placa base CH573F_**: CH573F (RV32) **_(en proceso...)_**
- **_Placa base CH582F_**: CH582F (RV32) **_(en proceso...)_**
- **_Placa de evaluación CH32V103R8T6-EVT-R1_**: CH32V103R8T6 (RV32) **_(en proceso...)_**
- **_Placa de desarrollo CH32V003_**: CH32V003F4U6 (RV32) **_(en proceso...)_**
- **_Placa de desarrollo CH32V203_**: CH32V203C8T6 (RV32) **_(en proceso...)_** 
- **_Placa de desarrollo CH32V305_**: CH32V305RBT6 (RV32) **_(en proceso...)_** 

## WinnerMicro
- **_HLK-W801-KIT-V1.1_**: W801-C400 (XT804) "_arduino_ backend" **_(en proceso...)_**

## Sipeed
- **_Sipeed M0sense_**: BL702 (RV32) "_arduino_ backend" **_(en proceso...)_**

## Ai-Thinker
- **_Ai-WB2-32S-Kit_**: BL602 "_arduino_ backend" **_(only `time`, `pin`, `pwm`, `uart`)_**


## Dispositivos API actualizada v0.1.2

- Emulador de software para Linux, Android (Termux) and Windows     _(GCC-TCC)_
- PIC16F8x family: PIC16F83, PIC16F83A, PIC16F84, PIC16F84A     _(XC8)_
- Arduino Uno         _(arduino-cli)_
- Arduino Nano        _(arduino-cli)_
- ESP32-DevKitC       _(arduino-cli)_
- Raspberry Pi Pico   _(arduino-cli)_