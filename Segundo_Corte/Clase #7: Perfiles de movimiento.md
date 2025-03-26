# ¿QUÉ SON PERFILES DE MOVIMIENTO?

El perfil de movimiento es una representación matemática y gráfica que describe cómo varían la posición, la velocidad y la aceleración de un sistema en función del tiempo. Su estudio es fundamental en el control de movimiento para garantizar transiciones suaves y eficientes en sistemas mecánicos y robóticos. Para comprenderlo, es esencial conocer los principios básicos de la cinemática, las reglas geométricas involucradas y los diferentes tipos de perfiles utilizados. Entre los más comunes se encuentran el perfil trapezoidal y la curva en S, cada uno con aplicaciones específicas según los requerimientos de suavidad, precisión y tiempo de ejecución.

## Índice

[1. ¿En qué Consiste?](#1-en-qué-Consiste)

[1.1 Diferencia entre Mecánica y Control de Movimiento](#11-Diferencia-entre-Mecánica-y-Control-de-Movimiento)

[1.2 Parámetros Principales](#12-Parámetros-Principales)

[1.3 Tipos de Sistemas y su Perfil de Movimiento](#13-Tipos-de-Sistemas-y-su-Perfil-de-Movimiento)

[2 Cinemática](#2-Cinemática)

[2.1 Parámetros Fundamentales de la Cinemática](#21-Parámetros-Fundamentales-de-la-Cinemática)

[2.2 Diferenciación (Definición de velocidad y aceleración)](#22-Diferenciación-Definición-de-velocidad-y-aceleración)

[2.3 Integración (Cálculo de velocidad y posición)](#23-Integración-Cálculo-de-velocidad-y-posición)

[2.4 Ejercicio Movimiento de un Actuador Lineal)](#24-Ejercicio-Movimiento-de-un-Actuador-Lineal)

## 1. ¿En qué Consiste?

- Es la trayectoria planificada para que una carga llegue a su destino cumpliendo restricciones de posición, velocidad y aceleración.

- Se emplea en control de movimiento para garantizar transiciones suaves y predecibles.

## 1.1 Diferencia entre Mecánica y Control de Movimiento

<div align="center">

| Aspecto          | Mecánica | Control de Movimiento |
|-----------------|----------|----------------------|
| **Enfoque**     | Se centra en la cinemática del mecanismo. | Se basa en el control preciso de posición, velocidad y aceleración. |
| **Objetivo**    | Garantizar que el diseño del mecanismo permita el movimiento deseado. | Planificar los parámetros para que la carga llegue al punto deseado de manera eficiente. |
| **Consideraciones** | Se enfoca en la estructura y comportamiento físico del sistema. | Considera la sincronización con otros procesos y la estabilidad del movimiento. |

</div>

> **Nota:** En mecánica, el perfil de movimiento se diseña pensando en cómo debe moverse el mecanismo, mientras que en control de movimiento se ajustan parámetros específicos para ejecutar el desplazamiento de manera óptima.

💡**Ejemplo 1:** Ejemplo en Mecánica: Diseño de un sistema de leva y seguidor en una máquina industrial.

- **Situación:** Se necesita diseñar un mecanismo que convierta el movimiento rotacional de un motor en un movimiento lineal para accionar una prensa.

- **Solución desde la Mecánica:**

    - Se diseña una leva con una forma específica que garantice el desplazamiento adecuado del seguidor.
  
    - Se analizan las ecuaciones de la cinemática para asegurar un movimiento suave sin impactos bruscos.
      
    - Se verifica que los materiales soporten las fuerzas y momentos generados.

- **Resultado:** Un sistema mecánico correctamente diseñado que permite que el seguidor se mueva de manera precisa cuando la leva gira.

<div align="center">
  <img src="Imágenes_Corte_2/Clase%20%237/Leva_(mecánica).gif" alt="Figura de prueba" width="300">
  <p><b>Figura 1.</b>Leva mecánica</p>
</div>

💡**Ejemplo 2:** Ejemplo en Control de Movimiento: Movimiento de un brazo robótico para soldadura automatizada.

Situación: Un brazo robótico debe mover su herramienta de soldadura de un punto A a un punto B con precisión, asegurando que la velocidad y aceleración sean adecuadas para una soldadura uniforme.

- **Solución desde el Control de Movimiento:**

    - Se definen los perfiles de movimiento (por ejemplo, un perfil trapezoidal para suavizar el arranque y frenado).

    - Se programan los controladores del motor para cumplir con las restricciones de posición, velocidad y aceleración.  

    - Se sincroniza el movimiento con otros robots en la línea de producción para evitar interferencias.

- **Resultado:** El brazo robótico realiza el movimiento de manera precisa y en el tiempo adecuado, asegurando una soldadura de calidad sin interrupciones en la producción.

<div align="center">
  <img src="Imágenes_Corte_2/Clase%20%237/Soldadura_robotizada.jpg" alt="Figura de prueba" width="300">
  <p><b>Figura 2.</b>Soldadura robotizada</p>
</div>

## 1.2 Parámetros Principales

- **Posición:** Punto inicial y final del desplazamiento.
  
<div align="center">
  <img src="Imágenes_Corte_2/Clase%20%237/Posición.png" alt="Figura de prueba" width="300">
  <p><b>Figura 3.</b>Posición</p>
</div>

- **Velocidad:** Ritmo al que se mueve la carga.

<div align="center">
  <img src="Imágenes_Corte_2/Clase%20%237/Velocidad.jpg" alt="Figura de prueba" width="300">
  <p><b>Figura 4.</b>Velocidad</p>
</div>

- **Aceleración:** Cambio en la velocidad durante el movimiento.

<div align="center">
  <img src="Imágenes_Corte_2/Clase%20%237/Aceleración.jpg" alt="Figura de prueba" width="300">
  <p><b>Figura 5.</b>Aceleración</p>
</div>

- **Tiempo:** Duración en la que se debe realizar el movimiento.

<div align="center">
  <img src="Imágenes_Corte_2/Clase%20%237/Tiempo.png" alt="Figura de prueba" width="300">
  <p><b>Figura 6.</b>Tiempo</p>
</div>

## 1.3 Tipos de Sistemas y su Perfil de Movimiento

<div align="center">
    
| Sistema | Descripción | Ejemplo |
|---------|-------------|---------|
| **Sistema de un solo eje** | El perfil de movimiento suele ser una línea recta, ya que el desplazamiento ocurre en una única dirección. | Un actuador lineal mueve un objeto de un punto A a un punto B en una cinta transportadora. |
| **Sistema multieje** | Se generan trayectorias más complejas al combinar movimientos de varios ejes. | Un brazo robótico mueve una pieza siguiendo una trayectoria curva en 3D. |
| **Sincronización con otros procesos** | Es fundamental coordinar el perfil de movimiento con el resto del sistema para evitar acumulaciones o retrasos. | En una línea de ensamblaje, un robot debe esperar a que una pieza esté lista antes de continuar su tarea. |

</div>

> **Nota:** La elección del sistema adecuado depende de la complejidad del movimiento requerido y de la necesidad de sincronización con otros procesos en el entorno de trabajo.

## 2 Cinemática

>🔑 *Cinemática:* La cinemática es la rama de la mecánica clásica que describe el movimiento de puntos, objetos y sistemas de grupos de objetos, sin referencia a las causas del movimiento (es decir, las fuerzas). El estudio de la cinemática a menudo se conoce como la 'geometría del movimiento'.

## 2.1 Parámetros Fundamentales de la Cinemática

En un sistema donde un eje se mueve de un punto A a un punto B, su movimiento se describe con tres parámetros esenciales:

<div align="center">
    
| Parámetro    | Símbolo    | Definición                                  | Expresión Matemática        |
|-------------|-----------|--------------------------------|-----------------------------|
| **Posición**  | \( s(t) \)  | Ubicación del objeto en un instante de tiempo. | \( s(t) \) |
| **Velocidad** | \( v(t) \)  | Cambio de la posición con respecto al tiempo.  | $$ v(t) = ( \frac{ds}{dt} ) $$ |
| **Aceleración** | \( a(t) \)  | Cambio de la velocidad con respecto al tiempo.  | \( a(t) = \frac{dv}{dt} \) |

</div>

> **Nota:** Estos parámetros son fundamentales en el análisis del movimiento, ya que permiten describir cómo varía la ubicación, velocidad y aceleración de un objeto en función del tiempo, proporcionando información clave para el diseño y control de sistemas mecánicos.

## 2.2 Diferenciación (Definición de velocidad y aceleración)

Las ecuaciones básicas del movimiento se obtienen mediante derivación:

- Velocidad instantánea como la derivada de la posición:

$$ v(t) = ( \frac{ds}{dt} ) $$

- Aceleración instantánea como la derivada de la velocidad:

$$ a(t) = ( \frac{dv}{dt} ) $$

## 2.3 Integración (Cálculo de velocidad y posición)

Si se conoce la aceleración, se pueden obtener la velocidad y la posición mediante integración:

- Velocidad a partir de la aceleración:

$$ v(t) = \int a(t) \, dt $$

- Posición a partir de la velocidad:

$$ s(t) = \int v(t) \, dt $$

## 2.4 Ejercicio Movimiento de un Actuador Lineal

Un actuador lineal mueve una carga desde el punto A hasta el punto B en un sistema de un solo eje. La aceleración del actuador está dada por la función:
