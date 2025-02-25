# ¿QUÉ SON LOS SERVOMOTORES?

Los servomotores son un actuador electromecánico, el cual es ampliamente usado en el control de movimiento, esto debido a la gran cantidad de usos que se le puede dar y a la cantidad de contextos en los que se puede utilizar. Los servomotores son básicamente motores a los cuales se les controla de manera precisa una, dos o más variables, esto dependiendo del propósito que se tenga para estos. 

## Índice
 [1. Control de servomotores](#1-Control-de-servomotores)
 
 [2. ¿En qué industria se usa?](#2-en-qué-industria-se-usa)
 
 [3. Ejes de Movimiento](#3-ejes-de-movimiento)

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
  <p><b>Figura 2.</b> Robot FANUC Arc Mate 100iC</p>
</div>
  - (Velocidad) Asi como podemos controlar en donde se encuentra el rotor, podemos indicar que tan rapido queremos que este rote, es decir que tantos grados por segundo queremos que recorra el rotor, un uso para esto es el control de crucero de los automoviles tesla, donde el objetivo es que el vehiculo transite siempre a la misma velocidad.
  💡**Ejemplo 2:** Aplicación de control de velocidad
<div align="center">
  <img src="Imágenes/Clase%20%234/tesla.png" alt="Figura de prueba" width="400">
  <p><b>Figura 2.</b> Robot FANUC Arc Mate 100iC</p>
</div>
   
- **Movimiento de las tarjetas perforadas:**  
  - Se desplazaban y giraban para indicar el siguiente patrón de tejido.
  - Funcionaban como un sistema de control programable mecánico.

## 2. ¿En qué industria se usa?

A continuación, se muestra una tabla con las industrias donde se usa el control de movimiento, los tipos de máquinas que emplean esta tecnología, los países donde es más común y los beneficios clave en cada sector.

<div align="center">

| **Industria**              | **Tipos de Máquinas**                                | **Países donde más se usan**      | **Beneficios clave**                                     |
|----------------------------|-----------------------------------------------------|---------------------------------|---------------------------------------------------------|
| **Empaque**                | Máquinas de envasado, cintas transportadoras, etiquetadoras | EE.UU., Alemania, China, México | Mayor velocidad, precisión en el empaquetado y reducción de desperdicios. |
| **Ensamblaje**             | Robots ensambladores, sistemas pick & place, CNC   | Japón, Alemania, Corea del Sur  | Ensamblaje preciso, reducción de costos y automatización avanzada. |
| **Impresión**              | Impresoras industriales, máquinas flexográficas     | EE.UU., China, Alemania, Brasil | Alta resolución, sincronización del material y rapidez de producción. |
| **Productos de madera**    | Sierras automáticas, cepilladoras CNC, routers CNC  | Canadá, EE.UU., Suecia, Brasil  | Corte preciso, optimización del material y reducción de errores. |
| **Maquinaria**             | Torno CNC, fresadoras, robots industriales         | Alemania, Japón, Italia, China  | Producción eficiente, mayor seguridad y reducción de tiempo de operación. |
| **Eléctrica/Semiconductores** | Máquinas de soldadura PCB, ensambladoras SMT       | Taiwán, Corea del Sur, China, EE.UU. | Ensamblaje de componentes de alta velocidad y precisión en micras. |

</div>

> **Nota:** Esta tabla presenta solo algunos ejemplos de aplicaciones y países donde el control de movimiento es clave en la industria.

## 3. Ejes de Movimiento

Cada movimiento generado por un actuador en un sistema de control se denomina **eje de movimiento (axis)**. Un sistema puede tener múltiples ejes, y su sincronización es esencial para realizar tareas complejas con precisión y eficiencia.

## Tipos de Ejes de Movimiento
<div align="center">
 
| Tipo de Eje         | Descripción | Ejemplo |
|--------------------|-------------|---------|
| **Eje Lineal** | Movimiento en línea recta a lo largo de un solo eje (X, Y o Z). | Un torno CNC mueve el cortador en el eje X para dar forma a la pieza. |
| **Eje Rotacional** | Movimiento giratorio alrededor de un eje fijo. | Un brazo robótico de ensamblaje rota en el eje Z para ajustar una pieza. |
| **Ejes Coordinados** | Múltiples ejes que trabajan en sincronización para realizar una tarea. | En una impresora, el cartucho de tinta se mueve en el eje X, mientras que el rodillo mueve el papel en el eje Y. |
| **Ejes Interpolados** | Movimiento combinado de varios ejes para generar trayectorias complejas. | Un robot industrial realiza movimientos curvos en 3D con interpolación de sus ejes. |
 
</div>

> **Nota:** Esta tabla da una pequeña explicación de los tipos de ejes de movimiento.

## 4. ¿Qué se controla?

El control de movimiento puede regular posición, velocidad, torque y aceleración. Dependiendo de la aplicación, se pueden controlar las cuatro variables, solo tres, dos o una.

>🔑 *Posición:* Determina la ubicación exacta de un objeto en el espacio. Se controla para asegurar que un mecanismo llegue a un punto específico con precisión.
>
>🔑 *Velocidad:* Regula la rapidez con la que un objeto se mueve de un punto a otro. Es crucial para evitar vibraciones y mejorar la eficiencia del proceso.
>
>🔑 *Torque:* Es la fuerza de giro aplicada a un eje o motor. Controlarlo permite garantizar que un sistema pueda mover cargas sin sobrecargas o fallos mecánicos.
>
>🔑 *Acerleración:* Es la variación de la velocidad en el tiempo. Se controla para evitar movimientos bruscos y reducir el desgaste de los componentes.

💡**Ejemplo 2:** Controlando las 4 variables (posición, velocidad, torque y aceleración)

<div align="center">
  <img src="Imágenes/Clase%20%232/Robot FANUC Arc Mate 100iC.png" alt="Figura de prueba" width="400">
  <p><b>Figura 2.</b> Robot FANUC Arc Mate 100iC</p>
</div>


- **Posición:** El brazo robótico debe moverse con precisión milimétrica para soldar en el punto exacto.

- **Velocidad:** Se ajusta para evitar sobrecalentamiento o defectos en la soldadura.

- **Torque:** Se controla para aplicar la presión adecuada en la unión de las piezas.

- **Aceleración:** Se regula para evitar movimientos bruscos que puedan afectar la calidad de la soldadura.

💡**Ejemplo 3:** Controlando 3 variables (posición, velocidad y torque)

<div align="center">
  <img src="Imágenes/Clase%20%232/Fresadora HAAS VF-2.jpg" alt="Figura de prueba" width="400">
  <p><b>Figura 3.</b> Fresadora HAAS VF-2 </p>
</div>

- **Posición:** La herramienta debe ubicarse exactamente en la coordenada correcta para realizar cortes precisos.

- **Velocidad:** La velocidad de corte se ajusta según el material para evitar sobrecalentamiento o desgaste prematuro.

- **Torque:** Se regula para asegurar la fuerza suficiente en el mecanizado sin dañar la pieza.

- **Aceleración:** No se controla la aceleración directamente, ya que no es crítica para este proceso.

💡**Ejemplo 4:** Controlando 2 variables (posición y velocidad)

<div align="center">
  <img src="Imágenes/Clase%20%232/Cinta transportadora con parada automática ConveyLinx.avif" alt="Figura de prueba" width="400">
  <p><b>Figura 4.</b>Cinta transportadora con parada automática ConveyLinx </p>
</div>

- **Posición:** Se detiene exactamente en el punto donde debe descargarse un producto.

- **Velocidad:** Se ajusta para sincronizarse con otras máquinas de la línea de producción.

- **Torque:** No se controla el torque, porque la carga es liviana y no se requiere fuerza específica.

- **Aceleración:** No se controla la aceleración, ya que no es relevante en este tipo de movimiento

💡**Ejemplo 5:** Controlando solo 1 variable (torque)

<div align="center">
  <img src="Imágenes/Clase%20%232/Bosch GSR 18V-EC.jpg" alt="Figura de prueba" width="400">
  <p><b>Figura 5.</b> Bosch GSR 18V-EC </p>
</div>

- **Posición:** No se controla la posición, porque no necesita ubicarse en coordenadas exactas.

- **Velocidad:** No se controla la velocidad, ya que funciona a una velocidad fija o ajustable manualmente.

- **Torque:** Se regula para apretar los tornillos con la fuerza exacta sin dañar la pieza.

- **Aceleración:** No se controla la aceleración, porque el usuario decide la rapidez del movimiento.

## 5. ¿Cómo se hacia antes del control?

El control de movimiento no siempre fue electrónico. Antes de los motores y sensores modernos, los ingenieros usaban mecanismos mecánicos avanzados para lograr precisión y automatización.  

## 5.1. Primeros Métodos de Control Mecánico  

### El Mundo Antiguo: Primeras Máquinas Autónomas  

#### Herón de Alejandría (Siglo I d.C.)  
- Inventó **puertas automáticas** en templos usando contrapesos.

<div align="center">
  <img src="Imágenes/Clase%20%232/Herón de Alejandría Puertas Automaticas.jpg" alt="Figura de prueba" width="400">
  <p><b>Figura 6.</b> Herón de Alejandría Puertas Automaticas </p>
</div>

- Creó la **eolípila**, un dispositivo a vapor que anticipó las máquinas de vapor.

<div align="center">
  <img src="Imágenes/Clase%20%232/Herón de Alejandría eolípila.gif" alt="Figura de prueba" width="400">
  <p><b>Figura 7.</b> Herón de Alejandría eolípila </p>
</div>

#### Los Autómatas Islámicos (Siglos IX - XIII)  
- Al-Jazari Creó mecanismos de engranajes y poleas para automatizar procesos.

<div align="center">
  <img src="Imágenes/Clase%20%232/Al-Jazari Creó mecanismos de engranajes y poleas para automatizar procesos.jpg" alt="Figura de prueba" width="400">
  <p><b>Figura 8.</b> Herón de Alejandría eolípila </p>
</div>

## 5.2. Revolución Industrial: La Era del Control Mecánico  

<div align="center">
  <table>
    <tr>
      <th>País</th>
      <th>Industria Destacada</th>
    </tr>
    <tr>
      <td>Reino Unido</td>
      <td>Máquinas de vapor y telares</td>
    </tr>
    <tr>
      <td>Francia</td>
      <td>Industria textil y relojería</td>
    </tr>
    <tr>
      <td>Alemania</td>
      <td>Metalurgia y manufactura</td>
    </tr>
  </table>
 
</div>

 > **Nota:** Países Pioneros en la Automatización Mecánica.

## 5.3. ¿Cómo Funcionaban Sin Control?  

<div align="center">
 
| Mecanismo | Función | Ejemplo |
|-----------|---------|---------|
| **Engranajes y ruedas de levas** | Generar movimientos repetitivos | Telares mecánicos |
| **Cajas de cambio y árboles de transmisión** | Transmitir energía a varias máquinas | Fundiciones de acero |
| **Mecanismos de frenado y relojes de control** | Regular procesos en intervalos de tiempo | Molinos de viento |
| **Sistemas de tarjetas perforadas** | Programar secuencias automáticas | Máquinas textiles |

</div>

> **Nota:** Esta tabla da a conconer como funcionaba antes sin control

## 5.4. Desventajas de los Métodos Antiguos  

**Poca flexibilidad**: Modificar una máquina requería reconstruir todo el sistema.  
**Errores por desgaste**: Engranajes y levas perdían precisión con el tiempo.  
**Altos costos de mantenimiento**: Reemplazar piezas dañadas era caro.  
**Dependencia del operador**: Se necesitaban trabajadores para supervisar.  

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

