# **GUÍA RÁPIDA LIBRERIA OLED**

Esta es una implementación de una libreria dedicada a pantallas OLED, que proporciona soporte para varios microcontroladores.

##  RESUMEN

Una pantalla OLED (diodo orgánico emisor de luz) es un tipo de pantalla que utiliza diodos orgánicos para emitir luz al aplicar una corriente eléctrica. A diferencia de las pantallas LCD, las OLED no requieren retroiluminación, ya que cada píxel se ilumina de forma independiente..

El dispositivo compatible con esta libreria se basa en el controlador SSD1316, diseñado para controlar pantallas OLED monocromáticas, generalmente de tamaño pequeño. Sus principales características son:

*  Resolución admitida hasta 128x64 píxeles.  
*  Modo de color: Monocromático (blanco, azul o amarillo, según el modelo del panel OLED). 
*  Interfaz de comunicación: Compatible con I2C y SPI, permitiendo una comunicación flexible con varios microcontroladores. 
*  Bajo consumo de energía.  
*  Controlador gráfico integrado: Permite dibujar texto e imágenes sin necesidad de memoria externa. 

## USOS

Las pantallas OLED con el controlador SSD1316 son ampliamente utilizadas en proyectos electrónicos y sistemas integrados debido a su bajo consumo de energía, alta legibilidad y facilidad de integración.

**Dispositivos IoT (Internet of Things)**  
* Visualización de datos en sensores de temperatura, humedad, presión, etc.
* Monitores de consumo energético en hogares inteligentes.  
* Paneles de control en sistemas de automatización.  

**Sistemas Integrados y Microcontroladores**  
* Indicadores en Arduino, ESP32, Raspberry Pi, STM32, etc.  
* Interfaces gráficas para proyectos DIY o industriales. 
* Monitores de estado en robots y drones.  

**Dispositivos Portátiles y Wearables**  
* Relojes inteligentes con pantallas monocromáticas de bajo consumo.  
* Dispositivos de monitorización de la salud (frecuencia cardíaca, oxígeno en sangre, etc.).

**Equipos Industriales y de Medición**  
* Visualización de información en osciloscopios, multímetros y analizadores de señales.
* Indicadores de funcionamiento en impresoras 3D. 
* Interfaces en sistemas de control de maquinaria.  

**Electrodomésticos y Aparatos**  
* Se muestra en cafeteras, purificadores de aire y hornos inteligentes.  
* Controles de audio en amplificadores y ecualizadores.
* Consolas de juegos retro con pantallas OLED monocromáticas.  

## **FUNCIONES COMPATIBLES CON LA TRANSPILACIÓN**

| Funciones in C                   | Funciones in V                   |
|----------------------------------|----------------------------------|
| `display.begin (TYPE, ADDRESS)`    | `DISPLAY_SETUP (TYPE, ADDRESS)`    |
| `display.clearDisplay ()`          | `DISPLAY_CLEARDISPLAY ()`          |
| `display.setTextSize (NUMBERS)`    | `DISPLAY_SETTEXTSIZE (NUMBERS)`    |
| `display.setTextColor (CHARACTER)` | `DISPLAY_SETTEXTCOLOR(CHARACTER)`  |
| `display.println (MESASAGE)`       | `DISPLAY_PRINTLN (MESSAGE)`        |
| `display.display ()`               | `DISPLAY_DISPLAY ()`               | 
| `display.DrawPixel (X,Y,COLOR)`    | `DISPLAY_DRAWPIXEL(X,Y,COLOR)`     |
| `display.drawRect(X,Y,WIDTH,HEIGHT,COLOR)` | `DISPLAY_DRAWRECT(X,Y,WIDTH,HEIGHT,COLOR)`   |
| `display.fillRect(X,Y,WIDTH,HEIGHT,COLOR)` | `DISPLAY_FILLRECT(X,Y,WIDTH,HEIGHT,COLOR)` | 
| `display.drawCircle(X,Y,RADIO,COLOR)` | `DISPLAY_DRAWCICRLE(X,Y,RADIO,COLOR)` | 
| `display.fillCircle(X,Y,RADIO,COLOR)` | `DISPLAY_FILLCIRCLE(X,Y,RADIO,COLOR)` | 
| `display.drawBitmap(X,Y,ARRAY_IMAGE,WIDTH,HEIGHT,COLOR)` | `DISPLAY_DRAWBITMAP(X,Y,ARRAY_IMAGE,WIDTH,HEIGHT,COLOR)` |

## **Código de Soporte para Funciones en Lenguaje V** 

```v

    fn C.DISPLAY_BEGIN(type_ any , address any) bool
    fn C.DISPLAY_CLEARDISPLAY(any) 
    fn C.DISPLAY_SETTEXTSIZE(number any)
    fn C.DISPLAY_TEXTCOLOR(character any)
    fn C.DISPLAY_SETCURSOR(x any , y any)
    fn C.DISPLAY_PRINTLN(message any)
    fn C.DISPLAY_DISPLAY(any) 
    fn C.DISPLAY_DRAWPIXEL(x any , y any , color any)
    fn C.DISPLAY_DRAWRECT(x any , y any , width any , height any , color any)
    fn C.DISPLAY_FILLRECT(x any , y any , width any , height any , color any)
    fn C.DISPLAY_DRAWCIRCLE(x any , y any , radio any , color any)
    fn C.DISPLAY_FILLCIRCLE(x any , y any , radio any , color any) 
    fn C.DISPLAY_DRAWBITMAP(x any , y any , array_image any , width any , height any , color any)  

```
