# **Árbol de carpetas de los proyectos**
El proyecto Aixt tiene el siguiente árbol de carpetas general:
    
```
aixt/    
    ├── src
    │   ├── aixt_build
    │   :   :
    │   │   └── builder.v
    │   ├── aixt_setup
    │   :   :
    │   │   └── setup.v
    │   ├── aixt_cgen
    │   │   ├── assign.v
    │   │   ├── call.v
    │   :   :
    │   │   └── utils.v
    │   └── aixt.v
    ├── assets
    │   ├── Aixtu-ru.jpeg
    │   ├── Aixtu-ru-wide.png
    :   :
    │   └── text-logo.svg
    ├── CONTRIBUTING.md
    ├── docs
    │   ├── Aixt language.md
    │   ├── API folder tree.md
    :   :
    │   ├── Setup file.md
    │   ├── Atmel
    │   ├── Cypress
    :   :
    │   └── WCH
    ├── LICENSE
    ├── ports
    │   ├── Atmel
    │   ├── Cypress
    :   :
    │   └── WCH
    ├── prerequisites.md
    ├── README.md
    ├── TODO.md
    └── v.mod
```

- El _source code_ se encuentra en la carpeta `src`.
- La carpeta `assets/` contiene los archivos de recursos como imágenes.
- La carpeta `ports/` contiene el código de implementación para cada dispositivo o placa (principalmente el código fuente V de Aixt)
- La carpeta `docs/` contiene la documentación de cada dispositivo o placa.

Para cada implementación de dispositivo o placa, deben existir dos carpetas con el mismo nombre dentro `ports` y `docs`, para la propia implementación y la documentación correspondiente:

```
aixt/    
    :
    ├── docs
    :   :
    │   ├── Emulator
    :   :
    :
    ├── ports
    :   :
    │   ├── Emulator
    :   :
    :
```

## Carpeta `ports`
Este documento contiene la implementación en lenguaje _C_ de la API de Aixt, proyectos y ejemplos de _Aixt_ para cada dispositivo o placa. El árbol de carpetas recomendado para cada puerto es:

```
device_or_board_name/    
    ├── api
    │   ├── pin/
    :   :   
    │   └── builtin.c
    ├── examples
    │   ├── example_1.v
    │   ├── example_2.v
    :   :
    │   └── example_n.v
    └── projects
        ├── project_1
        ├── project_2
        :
        └── project_n
```

La carpeta `projects` podría contener las carpetas del proyecto y los archivos para el compilador específico y la carpeta `examples` solo debe contener los archivos fuente de _Aixt_ (_V_).

## Carpeta `docs`
Este documento contiene la documentación para cada dispositivo o implementación de placa. Debe incluir al menos una guía de referencia rápida `quickref.md`:

```
device_or_board_name/    
    ├── quickref.md
    :
    :
    └── pin_descrition.md
```

La carpeta `projects` podría contener las carpetas y los archivos del proyecto para el compilador específico y la carpeta `examples` solo debe contener archivos fuente de _Aixt_ (_V_).