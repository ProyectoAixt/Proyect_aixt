# **Árbol de carpetas de la API de **_Aixt_** v0.1.2**

La API de _Aixt_ para cada puerto del microcontrolador debe estar ubicada en la carpeta:
```
aixt/ports/brand/microcontroller_or_board/api
```
```
aixt/ports/brand/brand/microcontroller_or_board/api
```
por ejemplo:
```
aixt/ports/Microchip/Explorer-16/PIC24/api
```
```
aixt/ports/Emulator/api
```
Todas las implementaciones de API deben seguir este árbol de carpetas básico:

```
ports/Microchip/Explorer-16/PIC24/api/
├── builtin.c
├──pin
│   ├── pin.c
│   ├── setup.c
:   :
│   └── high.c
:
└── time
    ├── sleep.c
    ├── sleep_ms.c
    └── sleep_us.c
```

comenzando desde la carpeta principal del proyecto _Aixt_.

La API de _Aixt_ Ase compone de varios módulos con funcionalidades específicas del microcontrolador. Todas las funciones de la API, relacionadas con el hardware interno o los periféricos disponibles de cada microcontrolador, se encuentran en el módulo correspondiente, por ejemplo, el periférico `adc`. Otras funciones, relacionadas con funcionalidades genéricas, se encuentran en el módulo correspondiente. Por ejemplo, todas las funciones relacionadas con el tiempo o el retardo se encuentran en el módulo `time`.

Para seguir las reglas sintácticas del _V language_, todos los nombres de carpetas y archivos dentro de la carpeta API deben usar **snake_case**.

## Módulos
Cada módulo de la API debe implementarse mediante archivos _C_ en la carpeta module_name/. Por ejemplo, el modulo `time` se implementa en `time/` de la siguiente manera: 
```
api
 ├── ...
 :
 └── time
      ├── sleep_ms.c
      └── sleep_us.c
```

<!-- ## Optimization levels
_Aixt_ projects uses _C_ code optimization levels according to the way of describing each API function on _C_ language. The optimization level is specified with the ending `_n`, where `n` is the optimization level starting from `0` (**WIP**).  -->

