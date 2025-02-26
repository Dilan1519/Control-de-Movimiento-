# ¿QUÉ SON LOS SERVOMOTORES?

Los servomotores son un actuador electromecánico, el cual es ampliamente usado en el control de movimiento, esto debido a la gran cantidad de usos que se le puede dar y a la cantidad de contextos en los que se puede utilizar. Los servomotores son básicamente motores a los cuales se les controla de manera precisa una, dos o más variables, esto dependiendo del propósito que se tenga para estos. 

## Índice
 [1. Control de servomotores](#1-Control-de-servomotores)
 
 [2. Motores AC y DC](#2-Motores-AC-y-DC)
 
 [3. ¿Qué motor elegir?](#3-Qué-motor-elegir)

 [4. ¿Qué se controla?](#4-qué-se-controla)
 
 [5. ¿Cómo se hacia antes del control?](#5-cómo-se-hacia-antes-del-control)

 [6. ¿Componentes?](#6-componentes)

 [7. Control de cascada ](#7-control-de-cascada)

 [8. Ejercicio ](#8-Ejercicio)

 [9. Solución](#9-Solución)

 [10. Bibliografía](#10-Bibliografía)


## 1. Control de servomotores

Para hacer uso de un servomotor, debemos saber que varibles se pueden controlar en este y como se hace este control.

- **Variables a controlar:**  
  - (Posición) en un motor podemos controlar su posición es decir en que Angulo especifico queremos que se encuentre el rotor del motor, el controlar esta variable es especialmente útil en brazos robóticos por ejemplo, donde las articulaciones deben estar en la posición que se les indique.

💡**Ejemplo 1:** Aplicación de control de posición
<div align="center">
  <img src="Imágenes/Clase%20%232/Robot FANUC Arc Mate 100iC.png" alt="Figura de prueba" width="400">
  <p><b>Figura 1.</b> Robot FANUC Arc Mate 100iC</p>
</div>
  - (Velocidad) Así como podemos controlar en donde se encuentra el rotor, podemos indicar que tan rápido queremos que este rote, es decir que tantos grados por segundo queremos que recorra el rotor, un uso para esto es el control de crucero de los automóviles tesla, donde el objetivo es que el vehículo transite siempre a la misma velocidad.
  
  
💡**Ejemplo 2:** Aplicación de control de velocidad
  
<div align="center">
  <img src="Imágenes/Clase%20%234/tesla.png" alt="Figura de prueba" width="400">
  <p><b>Figura 2.</b> Automóvil tesla con control de crucero </p>
</div>

   - (Torque) También se puede hacer control de la fuerza con la cual rota un motor, es decir cuanto esfuerzo realiza un motor con tal de lograr un movimiento, Un ejemplo de esto en una bobinadora de transformadores, la cual debe girar con una fuerza controlada, lo suficiente para enrollar el alambre con buena tensión, pero no demasiada como para romper el alambre de cobre.

💡**Ejemplo 3:** Aplicación de control de torque
  
<div align="center">
  <img src="Imágenes/Clase%20%234/bobina.jpg" alt="Figura de prueba" width="400">
  <p><b>Figura 3.</b> Planta embobinadora de transformadores</p>
</div>
   
- **Elementos para realizar control:**  
  - (Controlador) Sistema embebido o computadora que ejecuta el algoritmo de control
  - (Driver) Circuito que recibe la señal del controlador y la traduce para que así el actuador actúe de acuerdo a este, ya sea un puente H para el caso de motores DC o un ESC (Electronic Speed Controler) para motores AC Síncronos
  - (Actuador) Motor ya sea AC (síncrono o asíncrono) o DC que recibe la señal del driver y realiza una acción. 


## 2. Motores AC y DC

Como se había dicho antes, el motor o prácticamente el corazón del servomotor, es este actuador al cual queremos controlar sus variables. Este actuador lo podemos clasificar en dos, lo motores DC y lo AC, y estos últimos los podemos dividir en Síncronos Y asíncronos. 

>🔑 *Motor DC:* Motor que funciona por corriente continua, que está compuesto de un estator el cual contiene imanes permanentes, y un rotor el cual contiene una serie de bobinas que al recibir corriente por medio de las escobillas, genera un campo magnético que interactúa con el estator.
>
>🔑 *Motor AC síncrono:* Este motor a diferencia del anterior, opera con corriente alterna, además en este caso la bobina está ubicada en le estator lo cual evita la fricción con escobillas, y en este orden de ideas, los imanes permanentes se encuentran en el rotor.
>
>🔑 *Motor AC asíncrono:* Al igual que el motor AC síncrono, este funciona con corriente alterna, sin embargo, el motor asíncrono no tiene ningún imán permanente, tanto el rotor como el estator cuentan con bobinas, las cuales en el caso del estator generan un campo magnético, este induce una corriente en el rotor, la cual a su vez crea un campo magnético en el mismo, el cual interactúa con el campo magnético del estator. 

## 3. ¿Qué motor elegir?

Ahora que sabemos los distintos motores y cómo funcionan, se debe hacer la gran pregunta, que motor se debe elegir para que tarea, la respuesta a este tipo de presunta siempre es la misma, y es que depende, por lo tanto a continuación verán una tabla la cual tomara en cuenta ciertos parámetros a considerar, y como se desarrollan estos motores en cada caso, con una calificacion de 1 a 5.

<div align="center">
 
| **Motor**          | **Potencia** | **Mantenimiento** | **Tamaño** | **Consumo** |
|:------------------:|:------------:|:-----------------:|:----------:|:-----------:|
| Motor DC           | 2 | 2 | 3 | 3 |
| Motor AC sincrono  | 4 | 5 | 4 | 5 |
| Motor AC asincrono | 5 | 5 | 4 | 4 |

</div>


## 6. Componentes

El control de movimiento está compuesto por varios elementos fundamentales que trabajan en conjunto para lograr un desplazamiento preciso y eficiente en sistemas mecatrónicos. Estos componentes incluyen:

>🔑Human-Machine Interfaces (HMI): Permiten la interacción entre el usuario y el sistema de control, facilitando la configuración y supervisión del movimiento.
>
>🔑Control de Movimiento: Se encarga de generar las señales necesarias para regular la posición, velocidad y trayectoria del sistema.
>
>🔑Drivers (Potencia): Proveen la energía necesaria para accionar los actuadores de acuerdo con las señales del controlador.
>
>🔑Actuadores: Dispositivos que convierten la energía eléctrica en movimiento, como motores eléctricos o servomotores.
>
>🔑Mecanismos de Transmisión: Elementos mecánicos, como engranajes, correas o husillos, que transfieren el movimiento desde los actuadores hasta la carga final.
>
>🔑Retroalimentación (Sensores): Proveen información en tiempo real sobre la posición y velocidad del sistema, permitiendo ajustes y correcciones en el control del movimiento.

## 6.1 Componentes y Ejemplos en Control de Movimiento

<div align="center">
 
| **Componente**                     | **Ejemplos**                                                                      |
|:----------------------------------:|:--------------------------------------------------------------------------------:|
| Human-Machine Interfaces (HMI)     | Pantallas táctiles, botones, paneles de control, software SCADA                  |
| Control de Movimiento              | PLCs, controladores PID, controladores de servomotores, control por lazo abierto/cerrado |
| Drivers (Potencia)                  | Drivers de motores paso a paso, drivers de servomotores, variadores de frecuencia (VFD) |
| Actuadores                          | Motores eléctricos (DC, AC, paso a paso, servomotores), cilindros neumáticos, cilindros hidráulicos |
| Mecanismos de Transmisión           | Engranajes, correas, poleas, husillos de bolas, cremalleras y piñones            |
| Retroalimentación (Sensores)        | Encoders, tacómetros, sensores de proximidad, giroscopios, acelerómetros, sensores de corriente |

</div>

> **Nota:** Esta tabla da a conconer algunos componentes que puede tener un control en movimiento.

💡**Ejemplo 5:** Componentes de una Máquina CNC y sus Ejemplos

<div align="center">  

| **Componente**                     | **Ejemplo en la Máquina CNC** |
|:----------------------------------:|:--------------------------------------------------------------------------------:|
| **HMI (Interfaz Hombre-Máquina)**  | Pantalla táctil o software donde el operador carga el diseño y configura parámetros de corte. |
| **Control de Movimiento**          | Un controlador CNC que interpreta el código G y genera las señales para mover los ejes. |
| **Drivers (Potencia)**             | Drivers de servomotores o motores paso a paso que controlan la velocidad y el torque de los motores. |
| **Actuadores**                     | Motores paso a paso o servomotores que mueven la herramienta de corte en los ejes X, Y y Z. |
| **Mecanismos de Transmisión**       | Husillos de bolas y guías lineales que convierten el movimiento rotatorio de los motores en desplazamientos precisos. |
| **Retroalimentación (Sensores)**    | Encoders para medir la posición de los ejes, sensores de límite para evitar sobrecargas y sensores de vibración para detectar fallos. |

</div>

> **Nota:** Cada uno de estos componentes es fundamental para garantizar la precisión, eficiencia y seguridad en el control de movimiento de una máquina CNC.

### **Funcionamiento de la Máquina CNC**  

- El operador carga el diseño CAD/CAM y configura los parámetros de corte a través de la HMI.  
- El controlador CNC traduce el código G en instrucciones para los motores y envía las señales de control.  
- Los drivers regulan la potencia suministrada a los actuadores (motores paso a paso o servomotores).  
- Los motores mueven la herramienta de corte en los ejes X, Y y Z mediante husillos de bolas y guías lineales.  
- Los sensores de retroalimentación, como encoders, monitorean la posición y velocidad de los ejes, enviando datos al controlador para realizar correcciones en tiempo real.  
- La máquina ejecuta el corte con alta precisión, garantizando la calidad de la pieza terminada.  

## 7. Control de cascada

En un diagrama de cascada en control de movimiento, el orden posición → velocidad → torque se debe a la forma en que los sistemas de control gestionan el movimiento de un actuador.

### **¿Por qué este orden?**

El torque es lo que realmente mueve el sistema, pero no se puede controlar directamente la posición con torque, ya que otros factores como la inercia y la fricción influyen.
La velocidad actúa como un intermediario, asegurando que el motor no se descontrole ni se sobrecargue.
Finalmente, la posición es el objetivo final, pero necesita de los otros dos niveles para alcanzarse con precisión y estabilidad.

💡**Ejemplo 6:** ¿Donde quiero estacionarme?

<div align="center">
  <img src="Imágenes/Clase%20%232/¿Dónde quiero estacionarme”.png" alt="Figura de prueba" width="400">
  <p><b>Figura 9.</b> Control de cascada </p>
</div>

## **Control de Posición (Nivel más alto)**  
**● Referencia (Setpoint):**  
  - La posición deseada (ejemplo: destino del GPS o posición final del auto).  

 **● Retroalimentación (Feedback):**  
  - Sensor de posición: GPS, encoder de ruedas, sensores de odometría (LIDAR o cámaras en autos autónomos).  

 **● Señal de control:**  
  - Genera un setpoint de velocidad para el siguiente nivel.  

## **Control de Velocidad (Nivel intermedio)**  
**● Referencia (Setpoint):**  
  - La velocidad deseada (por ejemplo, 60 km/h en un control de crucero).  

 **● Retroalimentación (Feedback):**  
  - Sensor de velocidad: Encoder en ruedas, velocímetro, radar de control adaptativo.  

  **● Señal de control:**  
  - Genera un setpoint de torque para el siguiente nivel.  

## **Control de Torque (Nivel más bajo)**  
- **● Referencia (Setpoint):**  
  - El torque requerido por el motor para mantener la velocidad.  

  **● Retroalimentación (Feedback):**  
  - Sensor de corriente del motor eléctrico o sensor de presión en motores de combustión.  

 **● Señal de control:**  
  - **PWM** (Modulación por Ancho de Pulso) controla la energía enviada al motor eléctrico.  
  - En motores de combustión, la señal es el control del acelerador o la inyección de combustible.  

## 8. Ejercicio 

## Configuración de un Sistema de Control de Movimiento

## **Instrucciones**  

**●** Selecciona un sistema en el que se aplique el control de movimiento.  
**●** Identifica y describe los componentes del sistema:  
  - **HMI (Interfaz Humano-Máquina)**  
  - **Controladores**  
  - **Drivers**  
  - **Actuadores**  
  - **Mecanismos de transmisión**  
  - **Sensores**

**●** Explica el funcionamiento del sistema en pasos detallados.  
**●** Propón una mejora en el sistema. 

# 9. Solución

## Impresora 3D  

## Identificación de Componentes  

<div align="center">  
 
| Componente                     | Ejemplo en la Impresora 3D |
|---------------------------------|--------------------------------|
| HMI (Interfaz Hombre-Máquina)   | Pantalla táctil o software en PC (PrusaSlicer, Cura) donde el usuario configura la impresión. |
| Control de Movimiento           | Controlador 32 bits (Marlin, Klipper) que interpreta el código G y genera las señales para los motores. |
| Drivers (Potencia)              | Drivers de motores paso a paso (A4988, TMC2209) que regulan la corriente y el movimiento de los motores. |
| Actuadores                      | Motores paso a paso para mover los ejes X, Y y Z, y un extrusor que empuja el filamento. |
| Mecanismos de Transmisión        | Husillos de bolas, correas dentadas y rodamientos que convierten el giro de los motores en desplazamientos precisos. |
| Retroalimentación (Sensores)     | Endstops para detectar límites de los ejes, sensor de nivelación automática (BLTouch), termistores para monitorear temperatura. |

</div>

> **Nota:** La precisión de la impresión depende del correcto ajuste de los motores, drivers y sensores.

**Funcionamiento del Sistema**

- El usuario carga el modelo 3D en el software y configura parámetros como temperatura, velocidad y altura de capa.
- La HMI envía el código G al controlador de la impresora.
- El controlador procesa las instrucciones y envía señales a los drivers.
- Los drivers controlan la corriente de los motores paso a paso.
- Los motores mueven la boquilla de impresión en los ejes X, Y y Z mediante correas y husillos.
- El extrusor empuja el filamento hacia el hotend, donde se funde y se deposita en la cama de impresión.
- Los sensores de temperatura y nivelación ajustan el sistema en tiempo real para mejorar la calidad de la impresión.

## Mejora Propuesta

Agregar un sensor de flujo de filamento para detectar atascos o falta de material.

# 10. Bibliografía  

[1] Siciliano, B., & Khatib, O. (2016). *Springer Handbook of Robotics*. Springer.  
    Explica los principios del control de movimiento en robótica y automatización.  

[2] Nof, S. Y. (2009). *Springer Handbook of Automation*. Springer.  
    Cubre sistemas de automatización, incluyendo control de motores y sensores.  

[3] Gibson, I., Rosen, D. W., & Stucker, B. (2021). *Additive Manufacturing Technologies*. Springer.  
    Libro clave sobre impresión 3D y control de movimiento en fabricación aditiva.  

[4] Chua, C. K., & Leong, K. F. (2017). *3D Printing and Additive Manufacturing: Principles and Applications*. World Scientific.  
    Explica los sistemas de impresión 3D, componentes y control de movimiento.  

[5] Documentation of Marlin Firmware (2024). *Marlin 3D Printer Firmware*.  
    Documentación oficial del firmware Marlin, usado en muchas impresoras 3D.  
    Disponible en: [https://marlinfw.org/](https://marlinfw.org/)  

[6] RepRap Wiki (2024). *RepRap: The Open-Source 3D Printer Community*.  
    Información sobre hardware y software de impresoras 3D.  
    Disponible en: [https://reprap.org/wiki/Main_Page](https://reprap.org/wiki/Main_Page)  

