
# Articulaciones, Rigid transformation ,sensing y entradas

Ya que en la sesión anterior vimos como modelar sólidos y cambiar sus propiedades, en esta oportunidad veremos cómo es que estos se pueden conectar entre sí, esto con el objetivo de tener la capacidad de realizar simulaciones de mecanismos, para así tener la facilidad de realizar análisis ya sea de posición, velocidad o aceleración, además de ver las limitaciones de este tipo de simulación y como poder aprovecharlas al máximo.  

## Índice

[1. Articulaciones basicas en multibody](#1-Articulaciones-basicas-en-multibody)

[1.1 Articulación revoluta](#11-Diferencia-entre-Mecánica-y-Control-de-Movimiento)

[1.2 Articulación prismática](#12-Parámetros-Principales)

[2 Propiedades generales de las articulaciones](#13-Tipos-de-Sistemas-y-su-Perfil-de-Movimiento)

[2.1 Cinemática](#2-Cinemática)

[2.2 Parámetros Fundamentales de la Cinemática](#21-Parámetros-Fundamentales-de-la-Cinemática)

[2.2 Diferenciación (Definición de velocidad y aceleración)](#22-Diferenciación-Definición-de-velocidad-y-aceleración)

[2.3 Integración (Cálculo de velocidad y posición)](#23-Integración-Cálculo-de-velocidad-y-posición)

[2.4 Ejercicio Movimiento de un Actuador Lineal](#24-Ejercicio-Movimiento-de-un-Actuador-Lineal)

[2.5 Solución Movimiento de un Actuador Lineal](#25-Solución-Movimiento-de-un-Actuador-Lineal)

[3. Reglas Geométricas](#3-Reglas-Geométricas)

[3.1 Fórmulas Fundamentales Para Aceleración Constante](#31-Fórmulas-Fundamentales-Para-Aceleración-Constante)

[3.2 Ejercicio en Matlab](#32-Ejercicio-en-Matlab)

[4 Comparación de Perfiles de Movimiento](#4-Comparación-de-Perfiles-de-Movimiento)

## 1. Articulaciones basicas en multibody

Como había mencionado antes, en multibody las articulaciones tienen la función de unir de cierta forma los sólidos, a continuación, explicare de que marea se unen estos sólidos y de formas la articulación los hace interactuar 

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

<div align="center">
  <img src="Imágenes_Corte_2/Clase%20%237/Actuador_Lineal.gif" alt="Figura de prueba" width="400">
  <p><b>Figura 7.</b>Actuador Lineal</p>
</div>

Sabemos que:

$$ a(t)=4m/s^{2} $$

- Velocidad inicial: v(0) = 0 m/s
  
- Posición inicial: s(0) = 0 m 

Preguntas:

- ¿Cuál es la velocidad v(t) en función del tiempo?

- ¿Cuál es la posición s(t) en función del tiempo?

- ¿Cuál será la posición y velocidad después de 3 segundos?

## 2.5 Solución Movimiento de un Actuador Lineal 

- Cálculo de la Velocidad

Usamos la ecuación integral:

$$ v(t)=∫a(t)dt $$

Sustituyendo $a(t) = 4t$:

$$v(t) = ∫4 , dt = 4t + C_1$$

Como $v(0) = 0$, sustituimos:

$$ 0 = 4(0) + C_1 \Rightarrow C_1 = 0 $$

Por lo tanto:

$$ v(t) = 4t $$

- Cálculo de la Posición

Usamos la ecuación integral:

$$ s(t) = ∫ v(t), dt $$

Sustituyendo $v(t) = 4t$:

$$ s(t) = ∫ 4t, dt = 2t^2 + C_2 $$

Como $s(0) = 0$, sustituimos:

$$ 0 = 2(0)^2 + C_2 \Rightarrow C_2 = 0 $$

Por lo tanto:

$$ s(t) = 2t^2 $$

- Evaluación en $t = 3$ segundos

**Velocidad:**

$$ v(3) = 4(3) = 12 \text{ m/s} $$

**Posición:**

$$ s(3) = 2(3)^2 = 18 \text{ m} $$

## 3. Reglas Geométricas  

- Relación entre Posición y Velocidad

  - La posición en un instante de tiempo es igual al área bajo la curva de velocidad hasta ese instante.

  - Esto significa que integrar la velocidad en un intervalo de tiempo nos da el desplazamiento total.

- Relación entre Velocidad y Aceleración

  - La aceleración es la pendiente de la curva de velocidad.

  - Es decir, la derivada de la velocidad con respecto al tiempo nos da la aceleración en cada instante.

## 3.1 Fórmulas Fundamentales Para Aceleración Constante

Si consideramos que la aceleración 𝑎 es constante, podemos utilizar las ecuaciones básicas del movimiento rectilíneo uniformemente acelerado:

<div align="center">
  <img src="Imágenes_Corte_2/Clase%20%237/Movimiento-rectilineo-uniformemente-acelerado.jpg" alt="Figura de prueba" width="400">
  <p><b>Figura 8.</b>Movimiento Rectilíneo Uniformemente Acelerado</p>
</div>

- Velocidad en función del tiempo

$$ v = V_{0} +a(t−t_{0}) $$

Donde:

$V_{0}$ es la velocidad inicial.

𝑎 es la aceleración.

$t_{0}$ es el tiempo inicial.

- Posición en función del tiempo

$$ s=s_{0}+v_{0}(t−t_{0})+ \frac{1}{2}a(t−t_{0})^{2} $$
 
Donde:

$s_{0}$ es la posición inicial.

💡**Ejemplo 3:**  Encuentre la posición y la aceleración en t=5s

<div align="center">
  <img src="Imágenes_Corte_2/Clase%20%237/Ejemplo_Geometría.png" alt="Figura de prueba" width="200">
  <p><b>Figura 9.</b>Ejemplo 1</p>
</div>

Solución:

- La aceleración sería la pendiente de la velocidad:

$$ a = \frac{10}{5} = 2\frac{in}{s^{2}} $$

- El área bajo la curva de velocidad es hasta t=5 s es la posición alcanzada en t=5 s

$$ s= \frac{1}{2}(10*5) = 25 \frac{in}{s} $$

💡**Ejemplo 4:** Un eje está viajando a una velocidad de 10 cm/s. En t=5s empieza a disminuir la velocidad como se ve en el perfil. Cual es la posición del eje cuando se detiene? Asumaque empieza a desacelerar a 25 cm.

<div align="center">
  <img src="Imágenes_Corte_2/Clase%20%237/Ejemplo_Geometria_2.png" alt="Figura de prueba" width="200">
  <p><b>Figura 10.</b>Ejemplo 2</p>
</div>

Solución:

- La pendiente de la velocidad es la aceleración:

$$ a=\frac{-10\frac{cm}{s}\frac{1 m}{100 cm}}{10s - 5s} =- \frac{0,1 \frac{m}{s}}{10 s} = -0,01 \frac{m}{s^{2}} $$

-  El área del perfil de velocidad triangular es la posición alcanzada en t=15s

$$ 𝑆_{o} = \frac{1}{2} ∗ (15s − 5s)∗ 0,1 \frac{m}{s} = 0,5 m $$

## 3.2 Ejercicio en Matlab

Un eje (axis) lineal comienza su movimiento desde el reposo en la posición 0, con una aceleración de 2 m/s^2. Después de moverse durante 5 s, cual es la posición del eje (axis)?

<div align="center">
  <img src="Imágenes_Corte_2/Clase%20%237/Ejercicio_Matlab.png" alt="Figura de prueba" width="400">
  <p><b>Figura 11.</b>Ejercicio Matlab 2</p>
</div>

## 4. Comparación de Perfiles de Movimiento

<div align="center">
  <img src="Imágenes_Corte_2/Clase%20%237/Ejemplo_3.png" alt="Figura de prueba" width="400">
  <p><b>Figura 13.</b>Perfil trapezoidal</p>
</div>

<div align="center">
    
| Característica             | Perfil Trapezoidal                                        | Perfil en S (Sigmoidal o Gaussiano)                     |
|----------------------------|----------------------------------------------------------|---------------------------------------------------------|
| **Forma de la curva**      | Tres fases: aceleración constante, velocidad constante y desaceleración constante. | Transiciones suaves en la aceleración y desaceleración, formando una curva en "S". |
| **Transiciones**           | Cambios bruscos entre fases.                            | Transiciones progresivas sin cambios abruptos.         |
| **Facilidad de implementación** | Fácil, requiere cálculos básicos de aceleración y velocidad. | Más complejo, requiere funciones matemáticas avanzadas. |
| **Impacto mecánico**       | Puede generar esfuerzos mecánicos elevados y vibraciones. | Reduce esfuerzos mecánicos y minimiza vibraciones.     |
| **Tiempo de movimiento**   | Más rápido en trayectos cortos.                         | Puede ser más lento debido a transiciones suaves.      |
| **Precisión del movimiento** | Adecuado para movimientos estándar.                    | Mejor precisión en sistemas que requieren estabilidad y suavidad. |
| **Aplicaciones típicas**   | Máquinas CNC, transportadores, automatización industrial. | Robótica de precisión, impresión 3D, manipulación de materiales frágiles. |

</div>

**Nota:** Esta tabla compara dos tipos de perfiles de movimiento utilizados en sistemas mecánicos y robóticos. Mientras que el perfil trapezoidal es más simple y rápido en trayectos cortos, el perfil en S ofrece mayor suavidad y precisión, reduciendo esfuerzos mecánicos y vibraciones.

## 5. Perfil de Velocidad Trapezoidal (Geométrico)

<div align="center">
  <img src="Imágenes_Corte_2/Clase%20%237/Perfil_de_velocidad_trapezoidal .png" alt="Figura de prueba" width="400">
  <p><b>Figura 14.</b>Tornillo sin Fin</p>
</div>

$$ t_a = t_d = \frac{v_m}{a} $$

- **$t_a$** : Tiempo que tarda el sistema en acelerar desde 0 hasta la velocidad máxima $v_m$.
  
- **$t_d$** : Tiempo que tarda en frenar desde la velocidad máxima $v_m$ hasta 0.
  
- **$a$** : Aceleración constante durante ese tramo.

Se usa cuando ya se conoce:

- La aceleración máxima que el sistema puede aplicar.
  
- La velocidad máxima que se desea alcanzar.

Se asume que:

$$ t_a = t_d $$

Pero esto no siempre es cierto. Por ejemplo, si el sistema puede frenar más rápido que acelerar, entonces:

$$ t_d < t_a $$

## 5.1 Tiempo Total de Movimiento

$$ t_{total} = t_a + t_m + t_d $$

Es la suma del tiempo que el sistema pasa en cada una de las tres fases:

- **$t_a$**: Aceleración
   
- **$t_m$**: Movimiento a velocidad constante
  
- **$t_d$**: Desaceleración

Nos permite saber cuánto tiempo dura todo el trayecto, como:

- Coordinando movimientos en un robot o máquina multieje.
  
- Sincronizando este eje con otros procesos.

## 5.2 Cálculo del recorrido total $L$ y del tiempo en velocidad constante $t_m$

Calcular:

- Cuánta distancia recorre el sistema en total ($L$).

- Cuánto tiempo se mantiene moviéndose a velocidad constante ($t_m$).

Esto es esencial si se quiere que el sistema llegue a un punto específico y se necesita saber cuánto tiempo debe estar en cada fase del perfil trapezoidal.


## 5.3 Cálculo Geométrico del Recorrido Total $L$

Se suman las áreas bajo la curva de velocidad, ya que:

- Área bajo $v(t)$ = posición $s(t)$

- Área del triángulo de aceleración:
  
$$ A_1 = \frac{t_a \cdot v_m}{2} $$

- Área del rectángulo (velocidad constante):

$$ A_2 = t_m \cdot v_m $$

- Área del triángulo de desaceleración:
    
$$ A_3 = \frac{t_d \cdot v_m}{2} $$

Distancia total recorrida $L$:

$$ L = \frac{t_a \cdot v_m}{2} + t_m \cdot v_m + \frac{t_d \cdot v_m}{2} $$

## 5.4 Simplificación 

Si asumimos que $t_a = t_d$, entonces:

$$ L = v_m \cdot (t_a + t_m) $$

## 5.5 Despeje del Tiempo en Velocidad Constante $t_m$

$$ t_m = \frac{L}{v_m} - t_a $$

Es el tiempo que el sistema permanece a velocidad constante durante el trayecto, o sea, la parte plana del trapecio en la gráfica de velocidad.

Si:

$$ \frac{L}{v_m} < 2t_a $$

Entonces no hay fase de velocidad constante → el perfil será triangular, no trapezoidal.

## 5.6 Enfoque Analítico del Perfil Trapezoidal (Fase de Aceleración)

Ahora, pasamos al enfoque analítico, que permite calcular la posición $s(t)$ en cualquier instante de tiempo de forma exacta.

FASE 1: Aceleración ( $0 < t < t_a$ )

En esta fase:

- El sistema parte desde reposo: $v_0 = 0$
  
- Se aplica una aceleración constante: $a$
  
- La velocidad aumenta linealmente desde 0 hasta la velocidad máxima $v_m$.

Velocidad en función del tiempo:

$$ v(t) = a \cdot t $$

## 5.7 Posición en Función del Tiempo:

Para obtener la posición, integramos la velocidad:

$$ s(t) = \int_0^t v(t) \, dt = \int_0^t a \cdot t \, dt = \frac{1}{2} a t^2 $$

Es la posición recorrida durante la fase de aceleración, y crece con una parábola.

FASE 2: $$ t_a < t < t_a + t_m $$

Sabemos que para el intervalo:

$$ t_a < t < t_a + t_m $$

la velocidad del sistema es constante:

$$ v(t) = v_m $$

Cálculo de la posición_

Para obtener la posición en esta fase, integramos la velocidad a partir de la posición alcanzada al final de la aceleración:

$$ s(t) = s(t_a) + \int_{t_a}^{t} v_m \, dt $$

Como $v_m$ es constante, podemos sacarlo fuera de la integral:

$$ s(t) = s(t_a) + v_m \int_{t_a}^{t} dt = s(t_a) + v_m (t - t_a) $$

Fórmula final para la posición en esta fase:

$$ s(t) = s(t_a) + v_m (t - t_a) $$

Desglose de los términos:

- $s(t)$ → posición actual en esta fase.
  
- $s(t_a)$ → posición al final de la fase de aceleración.
  
- $v_m$ → velocidad máxima (constante durante esta fase).
  
- $(t - t_a)$ → tiempo transcurrido desde que empezó la velocidad constante.

Sabemos que:

$$ s(t_a) = \frac{1}{2} a t_a^2 $$

Entonces, también podés expresar la posición así:

$$ s(t) = \frac{1}{2} a t_a^2 + v_m (t - t_a) $$

## Fase 3: Desaceleración (Enfoque Analítico)


## Rango de tiempo:

$$ t_a + t_m < t < t_a + t_m + t_d $$

## Velocidad en esta fase:

La aceleración es negativa ($-a$), por lo tanto:

$$ v(t) = v_m - a(t - t_a - t_m) $$

- $v_m$: velocidad máxima al inicio del frenado
  
- $t - t_a - t_m$: tiempo desde que empezó la desaceleración

##  Ejemplo – Movimiento de un eje en un robot Gantry

###  Planteamiento del problema:

Queremos mover el eje **X** de un robot con los siguientes datos:

- Distancia total:  
  $$L = 10 \,\text{cm}$$  
- Velocidad máxima:  
  $$v_m = 2 \,\text{cm/s}$$  
- Aceleración máxima:  
  $$a = 1 \,\text{cm/s}^2$$  

---

### Paso 1: Calcular el tiempo de aceleración y desaceleración

Sabemos que:

$$
t_a = t_d = \frac{v_m}{a}
$$

Sustituyendo:

$$
t_a = \frac{2\,\text{cm/s}}{1\,\text{cm/s}^2} = 2\,\text{s}
$$

> El tiempo de aceleración y desaceleración es el mismo ya que se usa la misma aceleración para frenar.

---

###  Paso 2: Calcular el tiempo a velocidad constante

Sabemos que la distancia total es la suma de:

- Aceleración (área de un triángulo):  
  $$\frac{1}{2} v_m t_a$$
- Velocidad constante (área de un rectángulo):  
  $$v_m t_m$$
- Desaceleración (igual al área de aceleración):  
  $$\frac{1}{2} v_m t_d$$

Entonces, la distancia total es:

$$
L = \frac{1}{2} v_m t_a + v_m t_m + \frac{1}{2} v_m t_d
$$

Como \( t_a = t_d \), agrupamos:

$$
L = v_m \left(t_a + \frac{t_m}{1}\right)
$$

Despejando \( t_m \):

$$
t_m = \frac{L}{v_m} - t_a
$$

Sustituyendo valores:

$$
t_m = \frac{10\,\text{cm}}{2\,\text{cm/s}} - 2\,\text{s} = 5\,\text{s} - 2\,\text{s} = 3\,\text{s}
$$

### Resultado final: Tiempo total del movimiento

$$
t_{\text{total}} = t_a + t_m + t_d = 2\,\text{s} + 3\,\text{s} + 2\,\text{s} = 7\,\text{s}
$$

**Tiempo total del movimiento trapezoidal: 7 segundos**


<div align="center">
  <img src="Imágenes_Corte_2/Clase%20%237/Ejemplo_1.png" alt="Figura de prueba" width="400">
  <p><b>Figura 15.</b>Ejemplo</p>
</div>

<div align="center">
  <img src="Imágenes_Corte_2/Clase%20%237/Ejemplo_2.png" alt="Figura de prueba" width="400">
  <p><b>Figura 16.</b>Ejemplo</p>
</div>

<div align="center">
  <img src="Imágenes_Corte_2/Clase%20%237/Ejemplo_3_Tra.png" alt="Figura de prueba" width="200">
  <p><b>Figura 17.</b>Ejercicio</p>
</div>

CONCLUSONES 1. El perfil de velocidad trapezoidal es una herramienta fundamental en el diseño de trayectorias para sistemas de movimiento, como robots o ejes lineales. Su principal ventaja es que permite planificar el desplazamiento de manera suave y controlada, dividiéndolo en tres fases: aceleración, velocidad constante y desaceleración. Esta estructura facilita un movimiento más eficiente y menos agresivo para los componentes mecánicos, al evitar cambios bruscos de velocidad.

2. A través del uso de fórmulas geométricas y analíticas, se pueden calcular con precisión todos los parámetros clave del movimiento: tiempos de aceleración y desaceleración, duración del movimiento uniforme y el desplazamiento total. Estas relaciones permiten adaptar el perfil a las restricciones físicas del sistema, como la aceleración máxima o la distancia que se debe recorrer. Además, la posibilidad de calcular la posición en cada instante del tiempo es esencial para aplicaciones que requieren alta precisión.

3. Tanto el enfoque geométrico como el analítico resultan válidos y complementarios. El primero ofrece una solución rápida e intuitiva mediante áreas bajo la curva de velocidad, mientras que el segundo brinda mayor exactitud y permite analizar el comportamiento del sistema en todo momento. La correcta aplicación de estos métodos garantiza trayectorias optimizadas, seguras y eficientes, fundamentales en sistemas automatizados modernos

Referencia 

Referencias

[1] J. J. Craig, Introduction to Robotics: Mechanics and Control, 3rd ed., Pearson Prentice Hall, 2005.

[2] L. Sciavicco y B. Siciliano, Modeling and Control of Robot Manipulators, 2nd ed., Springer, 2012.

[3] M. P. Groover, Automation, Production Systems, and Computer-Integrated Manufacturing, 4th ed., Pearson, 2015.

[4] Bosch Rexroth AG, Mechatronics and Motion Control – Application Manual, 2002.

[5] J. E. Cote B., Perfiles de Movimiento, diapositivas de clase, 9° semestre, Universidad ECCI, 2025.

