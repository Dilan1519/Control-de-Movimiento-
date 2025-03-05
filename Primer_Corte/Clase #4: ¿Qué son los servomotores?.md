# ¿QUÉ SON LOS SERVOMOTORES?

Los servomotores son un actuador electromecánico, el cual es ampliamente usado en el control de movimiento, esto debido a la gran cantidad de usos que se le puede dar y a la cantidad de contextos en los que se puede utilizar. Los servomotores son básicamente motores a los cuales se les controla de manera precisa una, dos o más variables, esto dependiendo del propósito que se tenga para estos. 

## Índice
 [1. Control de servomotores](#1-Control-de-servomotores)
 
 [2. Motores AC y DC](#2-Motores-AC-y-DC)
 
 [3. ¿Qué motor elegir?](#3-Qué-motor-elegir)

 [4. Caracterización](#4-Caracterización)

 [5. Ejercicio ](#5-Ejercicio)

 [6. Solución](#6-Solución)

 [7. Bibliografía](#7-Bibliografía)


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
  - (Sensor) Existen diferentes sensores tanto para los motores DC como LOS AC, sin embargo, el más comúnmente usado es el enconder, el cual consta de una rueda ranurada, la cual permite o no el paso de un haz de luz desde un emisor láser, dependiendo de cuantas ranuras tenga la rueda, depende la resolución, entre más ranuras más resolución.


## 2. Motores AC y DC

Como se había dicho antes, el motor o prácticamente el corazón del servomotor, es este actuador al cual queremos controlar sus variables. Este actuador lo podemos clasificar en dos, lo motores DC y lo AC, y estos últimos los podemos dividir en Síncronos Y asíncronos. 

>🔑 *Motor DC:* Motor que funciona por corriente continua, que está compuesto de un estator el cual contiene imanes permanentes, y un rotor el cual contiene una serie de bobinas que al recibir corriente por medio de las escobillas, genera un campo magnético que interactúa con el estator.
>
>🔑 *Motor AC síncrono:* Este motor a diferencia del anterior, opera con corriente alterna, además en este caso la bobina está ubicada en le estator lo cual evita la fricción con escobillas, y en este orden de ideas, los imanes permanentes se encuentran en el rotor.
>
>🔑 *Motor AC asíncrono:* Al igual que el motor AC síncrono, este funciona con corriente alterna, sin embargo, el motor asíncrono no tiene ningún imán permanente, tanto el rotor como el estator cuentan con bobinas, las cuales en el caso del estator generan un campo magnético, este induce una corriente en el rotor, la cual a su vez crea un campo magnético en el mismo, el cual interactúa con el campo magnético del estator. 

## 3. ¿Qué motor elegir?

Ahora que sabemos los distintos motores y cómo funcionan, se debe hacer la gran pregunta, que motor se debe elegir para que tarea, la respuesta a este tipo de presunta siempre es la misma, y es que depende, por lo tanto a continuación verán una tabla la cual tomara en cuenta ciertos parámetros a considerar, y como se desarrollan estos motores en cada caso, con una calificación de 1 a 5. 

<div align="center">
 
| **Motor**          | **Potencia** | **Mantenimiento** | **Tamaño** | **Consumo** | **Durabilidad** |
|:------------------:|:------------:|:-----------------:|:----------:|:-----------:|:---------------:|
| Motor DC           | 2 | 2 | 3 | 3 | 2 |
| Motor AC sincrono  | 4 | 5 | 4 | 5 | 3 |
| Motor AC asincrono | 5 | 5 | 4 | 4 | 4 |

</div>

## 4. Caracterización 
 Con tal de hacer más fácil para los usuarios de servomotores la tarea de caracterizar y probar los motores, los fabricantes comparten información vital del motor, en forma de gráficos torque vs velocidad y tablas de datos, las dos con información de vital importancia para los procesos de diseño y elección de hardware.

### Curvas velocidad vs Torque:
Las curvas de velocidad vs torque son un gráfico que bien interpretado, puede dar ciertos datos sobre el motor, en adición algunas graficas de este tipo también añaden un eje vertical de corriente, que también adicione ciertos datos. 

<div align="center">
  <img src="Imágenes/Clase%20%234/grafico 1.png" alt="Figura de prueba" width="400">
  <p><b>Figura 4.</b> Curva velocidad vs torque servomotor QB02302 </p>
</div>

Como se observa el grafico, tenemos dos secciones remarcadas con cirulos de colores, en cuanto al círculo de color rojo, este punto donde el motor inicia arranque y no tiene carga (torque) tenemos el valor máximo de velocidad o velocidad máxima, con el de color azul, vemos que es el punto de torque en donde el motor tiene 0 RPM’s, esto indica el stal torque o torque de parada, por ultimo si nos fijamos en el título del grafico  este después del número de modelo tiene la inscripción A00, esto se refiere a que este grafico corresponde con el motor a un voltaje de 24 V, si la inscripción fuera B00, este sería el mismo modelo, pero a 40 V, esto se ve más fácil con la tabla de datos que se verá a continuación. 

### Tablas de datos:
Con las tablas es más fácil interpretar, pues los datos están directamente listados con su nombre, si embargo, es importante fijarse en las unidades de las constantes, ya que a veces estos motores son de fabricantes estadounidenses y las unidades están en sistema imperial y no internacional.

<div align="center">
  <img src="Imágenes/Clase%20%234/tabla.png" alt="Figura de prueba" width="400">
  <p><b>Figura 4.</b> Curva velocidad vs torque servomotor QB02302 </p>
</div>

Además, podemos evidenciar lo dicho en el apartado del gráfico, este motor cuenta con tres voltajes de operación, por ejemplo, si quisiéramos el grafico de velocidad torque del motor a 130 V tendríamos que buscar el que tenga los últimos tres dígitos C00.

## 5. Ejercicio 

Segun la siguiente grafica de Velocidad VS Torque, encuenrte la mayor catidad de parametros de importancia sobre el motor.

<div align="center">
  <img src="Imágenes/Clase%20%234/grafico2.png" alt="Figura de prueba" width="400">
  <p><b>Figura 4.</b> Curva velocidad vs torque servomotor QB02300 </p>
</div>

# 6. Solución

En los fraficos de velocidad VS torque, uno puede fijarse en ciertos puntos clave que le dan datos sobre el funcionamiento del motor, el la siguiente imagen se evidencia cuales:

<div align="center">
  <img src="Imágenes/Clase%20%234/grafico3.png" alt="Figura de prueba" width="400">
  <p><b>Figura 4.</b> Curva velocidad vs torque servomotor QB02300 </p>
</div>

En orden de izquierda a derecha:

- **Velocidad maxima = 5900 RPM**  
- **Velocidad nominal = 5300 RPM**  
- **Torque de parada = 0.35 Nm**
  
# 7. Bibliografía  

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

