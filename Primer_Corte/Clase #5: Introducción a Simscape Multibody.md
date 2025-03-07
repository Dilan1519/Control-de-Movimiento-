# Introducción a Simscape Multibody

Los software de modelado estructural permiten simular esfuerzos, materiales y comportamiento ante fuerzas, pero no analizan la dinámica del sistema. Aunque generan animaciones basadas en la cinemática, no ofrecen curvas de posición, velocidad o aceleración en función del tiempo. Para ello, se requieren herramientas específicas de simulación dinámica.

## Índice

[1. ¿En qué consiste?](#1-en-qué-consiste)
 [4. Ejercicio Simulación de un Péndulo Simple en Simscape Multibody ](#4-Ejercicio-Simulación-de-un-Péndulo-Simple-en-Simscape-Multibody)

 [5. Solución](#9-Solución)

 [6. Bibliografía](#10-Bibliografía)
  
## 1. Características

<div align="center">

| Característica              | Descripción |
|-----------------------------|-------------|
| **Tipo de modelado**        | Basado en cuerpos rígidos y articulaciones con restricciones. |
| **Generación de ecuaciones** | Calcula automáticamente ecuaciones diferenciales y cinemáticas. |
| **Análisis en el tiempo**   | Muestra la respuesta temporal de variables dinámicas. |
| **Animación 3D**            | Visualiza el movimiento del sistema en tiempo real. |
| **Integración con otros sistemas** | Permite combinar con modelos hidráulicos, térmicos, electromecánicos y eléctricos. |
| **Uso de motores**          | Se pueden agregar modelos de motores para simular accionamientos. |

</div>

> **Nota:** Este modelo permite realizar simulaciones dinámicas avanzadas con integración de múltiples disciplinas, facilitando el análisis y diseño de sistemas complejos.

## 1.1 Simscape y sus aplicaciones en distintas industrias:

<div align="center">

| Industria         | Aplicaciones con Simscape |
|------------------|-------------------------|
| **Automotriz**    | Modelado de sistemas de suspensión, frenos, transmisión y motores eléctricos. |
| **Aeroespacial**  | Simulación de actuadores hidráulicos, controles de vuelo y trenes de aterrizaje. |
| **Robótica**      | Diseño de manipuladores, simulación de control de motores y análisis de dinámica. |
| **Manufactura**   | Modelado de líneas de producción, control de maquinaria y sistemas neumáticos. |
| **Energía**       | Simulación de turbinas eólicas, paneles solares y sistemas de almacenamiento de energía. |
| **Dispositivos médicos** | Análisis de prótesis, exoesqueletos y sistemas biomédicos electromecánicos. |

</div>

> **Nota:** Simscape es una herramienta poderosa para la simulación multidominio, permitiendo modelar y analizar sistemas físicos en diversas industrias con alta precisión y realismo.


## 1.2  Descripción de algunos bloques en Simscape Miltibody

<div align="center">

| Concepto                | ¿Qué es? | Características / Función |
|-------------------------|---------|---------------------------|
| **Solver Configuration** | Bloque necesario en Simscape para definir los parámetros del solucionador numérico. | - Establece el tipo de solver (variable o fijo).<br>- Define el paso de simulación.<br>- Maneja restricciones algebraicas y diferenciales. |
| **World Frame** | Representa el marco de referencia global para simulaciones mecánicas. | - Punto de referencia fijo en el espacio.<br>- Sirve como base para definir posiciones y orientaciones. |
| **Mechanism Configuration** | Bloque usado en Simscape Multibody para definir la configuración del mecanismo. | - Permite definir gravedad y unidades.<br>- Necesario para sistemas mecánicos en Simscape Multibody. |
| **Revolute Joint** | Una unión mecánica que permite la rotación entre dos cuerpos alrededor de un solo eje. | - Define movimiento rotacional.<br>- Puede tener restricciones y actuadores.<br>- Se puede controlar con torques o ángulos. |
| **Scope** | Bloque de Simulink que permite visualizar señales durante la simulación. | - Muestra gráficos en tiempo real.<br>- Permite múltiples entradas.<br>- Se usa para analizar señales y depuración. |
| **Sine Wave** | Generador de señal senoidal en Simulink. | - Permite definir amplitud, frecuencia y fase.<br>- Se usa como entrada para sistemas dinámicos.<br>- Puede representar fuentes de vibración o señales de control. |
| **Simulink-PS Converter** | Convierte señales de Simulink en señales físicas para Simscape. | - Necesario para conectar Simulink con Simscape.<br>- Permite definir unidades físicas.<br>- Se usa para aplicar entradas externas a modelos físicos. |
| **Brick Solid** | Bloque que representa un cuerpo rígido con forma de paralelepípedo (bloque sólido) en Simscape Multibody. | - Permite definir dimensiones, densidad y material.<br>- Se puede conectar a juntas mecánicas.<br>- Es útil para modelar estructuras, masas y elementos mecánicos. |
| **Rigid Transform** | Bloque que permite definir una transformación rígida entre dos marcos de referencia en Simscape Multibody. | - No deforma el objeto, solo cambia su posición y orientación.<br>- Se usa para ensamblar diferentes partes de un mecanismo.<br>- Permite especificar traslaciones y rotaciones en el espacio. |

</div>

> **Nota:** Esta tabla contiene una descripción de algunos bloques fundamentales en Simscape Multibody, junto con sus características y funciones principales.

## 2 Configuración de Elementos en Simscape Multibody: Guía Paso a Paso

1- Abrir el entorno de Simscape Multibody

- En la ventana de comandos de MATLAB, escribe smnew y presiona Enter. Esto abrirá un modelo base con los elementos principales de Simscape Multibody.

<div align="center">
  <img src="Imágenes/Clase%20%235/Ejemplo_Pendulo_1.jpg" alt="Figura de prueba" width="400">
  <p><b>Figura 1.</b> Abrir Smnew </p>
</div>

2- Esquema principal del modelo

- Al abrir el modelo, se muestra un esquema con los bloques esenciales para la simulación de sistemas mecánicos.

<div align="center">
  <img src="Imágenes/Clase%20%235/Ejemplo_Pendulo_2.jpg" alt="Figura de prueba" width="400">
  <p><b>Figura 2.</b> Esquema principal </p>
</div>

3- World Frame

- Este bloque representa el marco de referencia global y sirve como base para definir posiciones y orientaciones de los objetos en el espacio.

<div align="center">
  <img src="Imágenes/Clase%20%235/Ejemplo_Pendulo_3.jpg" alt="Figura de prueba" width="400">
  <p><b>Figura 3.</b> Bloque World Frame </p>
</div>

4- Mechanism Configuration

- Este bloque permite configurar parámetros fundamentales del mecanismo, como la gravedad y las unidades de medida utilizadas en la simulación.

<div align="center">
  <img src="Imágenes/Clase%20%235/Ejemplo_Pendulo_4.jpg" alt="Figura de prueba" width="400">
  <p><b>Figura 4.</b> Mechanism Configuration </p>
</div>

5- Brick Solid

- Se usa para definir las dimensiones, densidad y propiedades físicas de un objeto sólido. Es útil para representar cuerpos rígidos en el modelo.

<div align="center">
  <img src="Imágenes/Clase%20%235/Ejemplo_Pendulo_5.jpg" alt="Figura de prueba" width="400">
  <p><b>Figura 5.</b> Brick Solid </p>
</div>

6- Herramientas de visualización

- Dentro del bloque Brick Solid, hay una caja de herramientas que permite mover, rotar y cambiar la perspectiva del objeto, facilitando la visualización en tres dimensiones.

<div align="center">
  <img src="Imágenes/Clase%20%235/Ejemplo_Pendulo_6.jpg" alt="Figura de prueba" width="400">
  <p><b>Figura 6.</b> Herramienta de visualización </p>
</div>

7- Rigid Transform

- Este bloque permite cambiar la posición y orientación de un objeto sin deformarlo. Se usa para conectar diferentes componentes dentro de un mecanismo.

<div align="center">
  <img src="Imágenes/Clase%20%235/Ejemplo_Pendulo_9.jpg" alt="Figura de prueba" width="400">
  <p><b>Figura 7.</b> Rigid Transform </p>
</div>

8- Revolute Joint 

- Este bloque crea una unión rotacional entre dos objetos, permitiendo que uno de ellos gire alrededor de un eje fijo.

<div align="center">
  <img src="Imágenes/Clase%20%235/Ejemplo_Pendulo_17.png" alt="Figura de prueba" width="400">
  <p><b>Figura 8.</b> Revolute Joint </p>
</div>

9- Ctrl + D

- Nos ayudará abrir la pestaña de simulación

<div align="center">
  <img src="Imágenes/Clase%20%235/Ejemplo_Pendulo_8.jpg" alt="Figura de prueba" width="400">
  <p><b>Figura 9.</b> Diagrama Control Cascada </p>
</div>

## 3.  Ejercicio Simulación de un Péndulo Simple en Simscape Multibody

En este ejercicio, diseñaremos un péndulo simple en Simscape Multibody, siguiendo los pasos detallados a continuación:

1- Creación de los componentes del péndulo:

- Primer eslabón (masa del péndulo - cubo):
- Dimensiones: 4 cm × 4 cm × 4 cm.
- Color: rojo.
- Segundo eslabón (barra de suspensión):
- Dimensiones: 20 cm × 1 cm × 1 cm.
- Color: azul.

2- Posicionamiento de los eslabones:

- Se debe trasladar el primer eslabón (cubo) a una de las puntas del segundo eslabón (barra).
  
- Para esto, utilizaremos el bloque Rigid Transform con la siguiente configuración:
  
    - Translation Method: Standard Axis.
    - Axis: +X.
    - Offset: 10 cm.
      
3- Conexión de los componentes:

- Usaremos el bloque Revolute Joint para unir los dos eslabones y permitir la rotación del péndulo.
  
4- Aplicación de la gravedad:

- La gravedad se configurará a través del bloque Mechanism Configuration.

- Como la gravedad normalmente actúa en el eje Z, se cambiará para que actúe en el eje Y.

5- Configuración del solucionador (Solver):

- Seleccionar el solver "ode15s (stiff/NDF)".
  
- Establecer el Max Step Size en 0.01.

6- Configuración de la Revolute Joint:

- En la pestaña Actuation:
  
  - En Torque, seleccionar Provided by Input.

- En la pestaña Sensing:
  
  - Habilitar la medición de Position y Velocity.

En la pestaña State Targets:

   - Ángulo inicial: 45°.
     
   - Velocidad inicial: 1 rad/s.
     
7- Aplicación de una señal de entrada:

- La entrada de torque será una señal senoidal con:

  - Amplitud: 0.06.
    
8- Visualización de resultados:

-Colocar un bloque Scope en cada salida para analizar el comportamiento del sistema.

## 4. Solución 

- Diagrama completo del ejercico

<div align="center">
  <img src="Imágenes/Clase%20%235/Ejemplo_pendulo_13.jpg" alt="Figura de prueba" width="400">
  <p><b>Figura 10.</b> Diagrama </p>
</div>

1- Creación de los componentes del péndulo:
  
<div align="center">
  <img src="Imágenes/Clase%20%235/Ejercicio_Pendulo_1.png" alt="Figura de prueba" width="400">
  <p><b>Figura 11.</b> Cubo </p>
</div>

<div align="center">
  <img src="Imágenes/Clase%20%235/Ejercicio_Pendulo_2.png" alt="Figura de prueba" width="400">
  <p><b>Figura 12.</b>  Eslabón </p>
</div>

2- Posicionamiento de los eslabones:

<div align="center">
  <img src="Imágenes/Clase%20%235/Ejercicio_Pendulo_3.png" alt="Figura de prueba" width="400">
  <p><b>Figura 13.</b>   Posicionamiento de los eslabones </p>
</div>

4- Aplicación de la gravedad:

<div align="center">
  <img src="Imágenes/Clase%20%235/Ejercicio_Pendulo_4.png" alt="Figura de prueba" width="400">
  <p><b>Figura 14.</b>   Aplicación de la gravedad </p>
</div>

5- Configuración del solucionador (Solver):

<div align="center">
  <img src="Imágenes/Clase%20%235/Ejercicio_Pendulo_5.png" alt="Figura de prueba" width="400">
  <p><b>Figura 15.</b>   Configuración del solucionador </p>
</div>

6- Configuración de la Revolute Joint:

<div align="center">
  <img src="Imágenes/Clase%20%235/Ejercicio_Pendulo_6.png" alt="Figura de prueba" width="400">
  <p><b>Figura 16.</b>  Configuración de la Revolute Joint </p>
</div>

7- Aplicación de una señal de entrada:

<div align="center">
  <img src="Imágenes/Clase%20%235/Ejercicio_Pendulo_7.png" alt="Figura de prueba" width="400">
  <p><b>Figura 17.</b>  Aplicación de una señal de entrada </p>
</div>

8- Visualización de resultados:

<div align="center">
  <img src="Imágenes/Clase%20%235/Ejemplo_Pendulo_16.png" alt="Figura de prueba" width="400">
  <p><b>Figura 9.</b> Diagrama Control Cascada </p>
</div>

<div align="center">
  <img src="Imágenes/Clase%20%235/Pendulo_Simple.gif" alt="Figura de prueba" width="400">
  <p><b>Figura 2.</b> Diagrama Control Cascada </p>
</div>

<div align="center">
  <img src="Imágenes/Clase%20%235/Pendulo_Simple_1.gif" alt="Figura de prueba" width="400">
  <p><b>Figura 2.</b> Diagrama Control Cascada </p>
</div>

<div align="center">
  <img src="Imágenes/Clase%20%235/Pendulo_Simple_2.gif" alt="Figura de prueba" width="400">
  <p><b>Figura 2.</b> Diagrama Control Cascada </p>
</div>


## 5. Cocluisiones

- Facilita el modelado y simulación de sistemas mecánicos complejos Simscape Multibody permite representar mecanismos de múltiples cuerpos con conexiones articuladas de manera eficiente y realista. Gracias a su entorno basado en bloques, los ingenieros pueden diseñar, analizar y simular sistemas mecánicos sin necesidad de resolver manualmente ecuaciones diferenciales complejas.

- Integración fluida con Simulink y Simscape La compatibilidad de Simscape Multibody con otras herramientas de Simulink y Simscape permite combinar sistemas mecánicos con modelos eléctricos, hidráulicos y de control. Esto facilita el desarrollo de simulaciones,para aplicaciones en robótica y sistemas industriales avanzados.


