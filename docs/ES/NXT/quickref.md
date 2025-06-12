# **Referencia Rápida para el Bloque Mindstorms NXT**
## (transpilado al lenguaje NXC)

Esta adaptación de **Aixt** funciona como un contenedor de lenguaje **NXC**. La mayoría de las funciones de nombre conservan los mismos nombres, pero usan snake_case en lugar de CamelCase . Sin embargo, algunas han cambiado por completo. Por ejemplo, este código **Aixt**:
```v
forward(motor_a, 75)    
forward(motor_c, 75)
time.sleep(4000)          
reverse(motors_ac, 75)  
time.sleep(4000)
off(motors_ac)
```

se transpilará a:
```c
task main()
{
    OnFwd(OUT_A, 75);
    OnFwd(OUT_C, 75);
    Wait(4000);
    OnRev(OUT_AC, 75);
    Wait(4000);
    Off(OUT_AC);
}
```

## Multitarea
La versión de **Aixt** para el lenguaje **NXC** admite _tasks_ mediante atributos y tipos de variables especiales. En este caso, el tipo especial `mutex` se utiliza para implementar variables mutex y el atributo `[task]` para implementar funciones de tarea. Por ejemplo, el siguiente código: 
```v
@[task] fn move_square() {
    for {
        acquire(move_mutex)
        forward(motors_ac, 75)
        sleep(1000)
        reverse(motor_c, 75)
        sleep(500)
        release(move_mutex)
    }
}

@[task] fn check_sensors() {
    for {
        if sensor_1 == 1 {
            acquire(move_mutex)
            reverse(motors_ac, 75)
            sleep(500)
            forward(motor_a, 75)
            sleep(500)
            release(move_mutex)
        }
    }
}

move_mutex := mutex('') //initialization value is necesary but will be ingnored

task.priority(move_square, check_sensors)
set_sensor_touch(in_1)
```

se transpilará a:
```c
mutex move_mutex;

task move_square()
{
    while (true)
    {
        Acquire(move_mutex);
        OnFwd(OUT_AC, 75); 
        Wait(1000);
        OnRev(OUT_C, 75); 
        Wait(500);
        Release(move_mutex);
    }
}

task check_sensors()
{
    while (true)
    {
        if (SENSOR_1 == 1)
        {
            Acquire(move_mutex);
            OnRev(OUT_AC, 75); 
            Wait(500);
            OnFwd(OUT_A, 75); 
            Wait(500);
            Release(move_mutex);
        }
    }
}

task main()
{
    Precedes(move_square, check_sensors);
    SetSensorTouch(IN_1);
}
```

La lista completa de equivalencias está en el archivo [NXT.toml](ports/setup/NXT.toml) en el diccionario llamado `aliases`.

El puerto NXC de **Aixt** puede usarse en modo _script_ (sin la función principa). En ese caso, las variables _mutex_ deben declararse después de definir las funciones _task_, como se muestra en el ejemplo anterior.

## Instalación
 El proyecto `Aixt` incluye el `nbc` compilador para _Windows_ y _Linux_,  pero hay que instalar manualmente los controladores USB.

### Para Windows
Descargue el software _NXT_ desde (https://education.lego.com/en-us/downloads/retiredproducts/nxt/software)[https://education.lego.com/en-us/downloads/retiredproducts/nxt/software], and install only the drivers.


### Para Linux
Instala la última versión del paquete `libusb-dev` según tu distribución. Por ejemplo, en una distribución _Debian-based_ puedes escribir en una terminal:
```
apt-get install libusb-1.0-0-dev
```
o
```
apt-get install libusb-dev
```