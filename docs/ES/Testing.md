# **Plan de Pruebas del Proyecto Aixt**

- Para ayudar a la uniformidad, calidad y confiabilidad en el desarrollo del propio proyecto Aixt con el soporte de sistemas basados en microcontroladores, se agrega la carpeta "prueba".

- Esta carpeta contiene dos tipos de pruebas: pruebas de Smoke y pruebas funcionales. A continuación, se explica el contenido de cada carpeta y cómo usar sus conjuntos de pruebas.

## Carpeta de Prueba de Smoke

La carpeta de pruebas de Smoke incluye pruebas que permiten una comprobación rápida para garantizar que la funcionalidad básica del código funcione correctamente. Estas pruebas no son exhaustivas, pero están diseñadas para detectar problemas críticos de forma temprana.

#### Objetivo: 
Para verificar las características esenciales y funcionalidades básicas de la aplicación.

#### Modo de Empleo: 
Simplemente siga el conjunto de pruebas de esta carpeta para garantizar que las funciones principales del código funcionen correctamente. Esto suele hacerse después de una nueva compilación o actualización para garantizar que las funciones principales no se hayan dañado.

## Carpetas de Pruebas Funcionales

La carpeta de pruebas funcionales contiene pruebas más completas que validan la funcionalidad completa del código según los requisitos. Estas pruebas son más detalladas y garantizan que el código se comporte como se espera en diversas condiciones.

#### Objetivo: 
Para validar que el código funciona según los requisitos especificados y realiza correctamente todas las funciones previstas.

#### Modo de Empleo: 
Sigue el conjunto de pruebas de esta carpeta para realizar pruebas exhaustivas de las características del código. Esto incluye probar funciones individuales, integraciones y flujos de trabajo para garantizar que todo funcione correctamente.

**Nota:** *Todos los casos de prueba de Smoke deben aprobarse antes de ejecutar los casos de prueba funcionales.*