# Usando el proyecto **Aixt**

## Corre **Aixt**
En una terminal dentro de la carpeta **_Aixt_** compila y ejecuta el archivo `aixt.v`:

```
v run aixt.v <command> <device_or_board> <source_file>
```
Ejemplos:
```
v run aixt.v -t Emulator ports/PC/projects/blinking/blinking.v
```
```
v run aixt.v -c Exp16-PIC24 common_test/17_for_in_range.v
```

## Compilar **Aixt**
Para mejorar la transcompilación de _Aixt_ a _C_ puedes compilar primero `aixt.v`: 
```
v aixt.v
```
Y ejecutar:
```
./aixt <command> <device_or_board> <source_file>
```
Ejemplos:
```
./aixt -t Emulator common_test/02_casting.v
```
```
./aixt -b NXT ports/NXT/projects/1_motor.write.v
```

## Comandos de Aixt
_**Aixt**_ admite los siguientes comandos:

Comando          | Funcionamiento
-----------------|----------------------------------------------------
transpilar, -t   | Transpilar a C un programa Aixt.
compilar, -c     | Compila el archivo C generado previamente.
Correr, -r       | Ejecute el archivo ejecutable generado previamente.
construir, -b    | Construir (transpilar, compilar y ejecutar) un programa Aixt.
limpiar, -cl     | Limpia todos los archivos generados (C y ejecutables).
ayuda, --help, -h| Llama a ayuda
versión          | Imprima el número de versión de Aixt