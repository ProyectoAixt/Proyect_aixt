# **Archivos de Configuración**

El proyecto **_Aixt_** utiliza archivos de configuración para cada microcontrolador y compilador compatible. Estos archivos configuran los parámetros específicos de la placa o dispositivo, como la frecuencia de reloj, los módulos de hardware predeterminados, los archivos de cabecera, etc., así como otros parámetros del transpilador, como la correspondencia entre tipos de variables. Los archivos de configuración se encuentran en la carpeta `setup`.

TLos archivos de configuración utilizan este `.json` formato debido a su ubicuidad. El siguiente código de ejemplo muestra el contenido de `setup/PIC16F8x.json`:

```json
{
    "port":      "PIC16F8x",
    "board":     "---",
    "backend":   "c",

    "cc_linux":			"",             
    "cc_windows":		"",
    "cc_make_flags":	"PART=@{device}",

    "flasher_linux":    "arduino-cli",
    "flasher_windows":  "arduino-cli.exe",
	"flasher_flags":	"upload @{file_dir_name} -p @{port} -b esp32:esp32:esp32",

    "api_paths": [
        "Microchip/PIC16F8x",
        "Microchip/xc8-generic",
        "Microchip/PIC12F-16F-generic"
    ],
    "v_defines": [
    ],

    "default_cpu_freq": 4000000,
    "default_string_len": 20,

    "compiler_setup_path": "setup/xc8.json"
}
```

El archivo de configuración de cada dispositivo `port_name.json` incluye también el archivo de configuración del compilador correspondiente `compiler.json` ien el parámetro: `"compiler_setup_path":`. En este caso `setup/xc8.json`, su contenido es el siguiente:

```json
{
    "main_ret_type": "void",
    "main_params":   "void",
    "compiler_types": {
        "void":     "void",
        "bool":     "bool",
        "i8":       "int8_t",
        "i16":      "int16_t",
        "int":      "int32_t",
        "i64":      "NOT SUPPORTED",
        "isize":    "int8_t",
        "int_literal": "int32_t",
        "u8":       "uint8_t",
        "u16":      "uint16_t",
        "u32":      "uint32_t",
        "u64":      "NOT SUPPORTED",
        "usize":    "uint8_t",
        "f32":      "float",
        "f64":      "NOT SUPPORTED",
        "float_literal": "float",
        "rune":     "char"
    }
}
```

En transpilador **_Aixt_** lee el `port_name.json` y  `compiler.json` y realiza la traducción en función de los parámetros escritos en él, además de agregar los parámetros específicos del microcontrolador o la placa en el archivo de salida `C`. 


## Backend
 
**_Aixt_** puede generar código para 3 backends diferentes:

Nombre del Backend| Objetivo
------------------|-------------------------------------------------
c                 | for the native _C_ compiler of the device
arduino           | for the ports that use _Arduino_ API
nxc               | for LEGO Mindstorms NXT robots on _NXC_ language  


