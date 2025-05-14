# Conceptos de Transmisión Tornillo Guía

Durante las sesiones anteriores del curso, se abordaron los fundamentos del comportamiento del torque y la inercia en distintos tipos de mecanismos de transmisión. El objetivo principal ha sido entender cómo reflejar adecuadamente estas variables hacia el lado del motor, lo cual es esencial para un correcto dimensionamiento del mismo. Entre los mecanismos estudiados se encuentran los engranajes y las poleas con correas, destacando aspectos clave como la relación de transmisión, la eficiencia del sistema y la relación de inercia. Se discutió cómo estas variables afectan el rendimiento y la selección del motor, y se realizaron simulaciones en Simscape para visualizar su comportamiento.

Ahora, retomando la clase, se introducen nuevos mecanismos comúnmente utilizados en entornos industriales. Entre ellos se encuentra el tornillo guía, también conocido como tornillo sin fin, un componente ampliamente utilizado en diversos procesos mecánicos. Este mecanismo será analizado tanto desde su funcionamiento físico como desde su modelado y simulación, con el fin de ampliar el entendimiento sobre las diferentes formas de transmisión de movimiento y fuerza en sistemas industriales.

## Índice

 [10. Conclusiones](#10-Conclusiones)

 [11. Bibliografía](#11-Bibliografía)


## 1. Tornillo sin Fin

>🔑 *Tornillo sin fin:* Elemento mecánico que convierte movimiento rotacional en movimiento lineal, usado comúnmente en maquinaria para precisión y control de posición.

## 1.1 Principio de Funcionamiento

<div align="center">
  <img src="Imágenes_Corte_3/Clase%20%2311/Tornillo_Sin_Fin.gif" alt="Figura de prueba" width="300">
  <p><b>Figura 1.</b>Tornillo sin Fin</p>
</div>

- Al girar el tornillo, se genera un desplazamiento lineal en una tuerca o componente móvil acoplado a él.

- A esta parte móvil, que se desplaza a lo largo del tornillo, se le suele conectar una cama o bandeja que cumple funciones específicas en el sistema mecánico.
  
## 1.2 Rosca Cuadrada (Square Thread) vs Rosca Trapezoidal (Trapezoidal Thread)   

<div align="center">
  <img src="Imágenes_Corte_3/Clase%20%2311/Acme_Threads_Trapezoidal_Threads.png" alt="Figura de prueba" width="600">
  <p><b>Figura 2.</b>Square Thread y Trapezoidal Thread</p>
</div>

<div align="center">
 
| Característica              | Rosca Cuadrada (Square Thread)                        | Rosca Trapezoidal (Trapezoidal Thread)                          |
|----------------------------|--------------------------------------------------------|------------------------------------------------------------------|
| Forma del diente           | Perfil completamente cuadrado                          | Perfil con pendiente lateral (~29° o 30°)                        |
| Dimensiones del diente     | Todos los dientes tienen el mismo ancho y altura       | Dientes con inclinación que mejora el contacto                  |
| Costo                      | Más económica                                           | Más costosa                                                     |
| Uso recomendado            | Cargas ligeras o moderadas                             | Cargas altas                                                    |
| Resistencia estructural    | Más débil, propensa al desgaste o deformación          | Mayor robustez frente a esfuerzos mecánicos                     |
| Eficiencia de acople       | Menor eficiencia, más fricción                         | Mejor distribución de carga, acople más eficiente               |
| Durabilidad                | Menor, debido al desgaste localizado                   | Mayor, gracias a la mejor distribución de fuerzas               |

</div>

> **Nota:** La elección entre rosca cuadrada y trapezoidal depende del tipo de aplicación mecánica, considerando factores como carga, eficiencia, durabilidad y costo.


## 1.3 Rosca Directa (sin esferas) vs Tornillo con Recirculación de Bolas (Ball Screw)    

<div align="center">
  <img src="Imágenes_Corte_3/Clase%20%2311/Rosca Directa (sin esferas) y Tornillo con Recirculación de Bolas (Ball Screw).jpg" alt="Figura de prueba" width="600">
  <p><b>Figura 3.</b>Rosca Directa (sin esferas) vs Tornillo con Recirculación de Bolas (Ball Screw)  </p>
</div>

| Característica              | Rosca Directa (sin esferas)                                  | Tornillo con Recirculación de Bolas (Ball Screw)                      |
|----------------------------|---------------------------------------------------------------|------------------------------------------------------------------------|
| Mecanismo de movimiento    | Contacto directo entre rosca del tornillo y tuerca            | Movimiento asistido por esferas internas que actúan como rodamientos  |
| Fricción                   | Alta fricción                                                  | Muy baja fricción gracias a las esferas                               |
| Precisión del movimiento   | Menor precisión                                                | Alta precisión y suavidad                                             |
| Desgaste                   | Mayor desgaste debido al contacto directo                     | Menor desgaste por menor contacto directo                             |
| Capacidad de carga         | Limitada a cargas bajas o moderadas                          | Soporta cargas elevadas por mejor distribución del esfuerzo           |
| Costo                      | Más económico                                                 | Más costoso                                                           |
| Aplicaciones típicas       | Sistemas simples o de bajo costo donde la precisión no es crítica | Máquinas CNC, robótica, automatización de alta precisión          |

> **Nota:** Los tornillos con recirculación de bolas ofrecen ventajas significativas en eficiencia y precisión, siendo ideales para sistemas exigentes, aunque a un mayor costo.

## 1.4 Aplicaciones

<div align="center">

| Aplicación                          | Descripción                                                                 |
|------------------------------------|-----------------------------------------------------------------------------|
| Impresoras 3D                      | Permiten el desplazamiento preciso del cabezal o la cama de impresión.     |
| Tornos CNC                         | Guían el movimiento lineal de las herramientas para mecanizado.            |
| Prensas mecánicas                  | Transmiten fuerza para aplicar presión en procesos como embutido o corte.  |
| Sillas elevadoras                  | Convierten el giro del motor en desplazamiento vertical para elevar carga. |
| Mesas de coordenadas (fresadoras) | Desplazan con precisión la pieza en ejes X/Y para mecanizado controlado.   |
| Actuadores lineales eléctricos     | Utilizados en automatización para generar movimiento lineal controlado.    |
| Sistemas de apertura de compuertas | Controlan la apertura/cierre de compuertas en sistemas hidráulicos o mecánicos. |

</div>

> **Nota:** Todas estas aplicaciones emplean mecanismos de transmisión de movimiento lineal, fundamentales en sistemas industriales y automatizados.

💡**Ejemplo 1:**  

<div align="center">
  <img src="Imágenes_Corte_3/Clase%20%2311/maquinas-cnc-que-es-una-cortadora-laser-para-metal-sideco.jpg" alt="Figura de prueba" width="300">
  <p><b>Figura 4.</b>Máquina CNC para cortar materiales metálicos</p>
</div>

**Sistema:** Tornillo guía con recirculación de bolas y rosca trapezoidal.  

**Aplicación:** Máquina CNC para cortar materiales metálicos.  

**Objetivo:** Convertir el giro del motor en un desplazamiento lineal preciso del cabezal de corte.

**Datos:**

- Relación de transmisión: 1:5
  
- Eficiencia del sistema: 85%
  
- Torque en la carga: 10 Nm
  
- Inercia de la carga reflejada: 0.02 kg·m²  

**Cálculos:**

**1. Torque reflejado al motor:**

$$
T_{motor} = \frac{T_{carga}}{r \cdot \eta} = \frac{10}{5 \cdot 0.85} \approx 2.35 \, \text{Nm}
$$

**2. Inercia reflejada al motor:**

$$
J_{motor} = \frac{J_{carga}}{r^2} = \frac{0.02}{25} = 0.0008 \, \text{kg} \cdot \text{m}^2
$$

**3. Relación de inercia (IR):**

Si la inercia del motor es $$\( J_{motor} = 0.001 \, \text{kg} \cdot \text{m}^2 \)$$:

$$
IR = \frac{J_{reflejada}}{J_{motor}} = \frac{0.0008}{0.001} = 0.8 
$$

## 1.5 Ejercicio 1

<div align="center">
  <img src="Imágenes_Corte_3/Clase%20%2311/Imresora_3d.jpg" alt="Figura de prueba" width="300">
  <p><b>Figura 5.</b>Impresora 3D con tornillo guía de rosca cuadrada sin esferas</p>
</div>

**Sistema:** Impresora 3D con tornillo guía de rosca cuadrada sin esferas.  

**Relación de transmisión:** 1:3  

**Inercia de la carga:** 0.015 kg·m²  

**Torque en la carga:** 5 Nm  

**Eficiencia del sistema:** 70%

**Preguntas y soluciones:**

**1. ¿Cuál es el torque que debe entregar el motor?**

$$
T_{motor} = \frac{T_{carga}}{r \cdot \eta} = \frac{5}{3 \cdot 0.7} \approx \frac{5}{2.1} \approx 2.38 \, \text{Nm}
$$

**2. ¿Cuál es la inercia reflejada al motor?**

$$
J_{motor} = \frac{J_{carga}}{r^2} = \frac{0.015}{9} \approx 0.00167 \, \text{kg} \cdot \text{m}^2
$$

**3. Si la inercia del motor es 0.002 kg·m², ¿la relación de inercia es adecuada?**

$$
IR = \frac{J_{reflejada}}{J_{motor}} = \frac{0.00167}{0.002} \approx 0.835 
$$

## 2. ¿Qué es el Backlash?

<div align="center">
  <img src="Imágenes_Corte_3/Clase%20%2311/Backlash.png" alt="Figura de prueba" width="300">
  <p><b>Figura 6.</b>Backlash</p>
</div>

>🔑 *backlash:* Es el juego o pérdida de movimiento que se produce en sistemas mecánicos, especialmente en cadenas cinemáticas largas, debido a torsión o deformación elástica.

## 2.1 Consecuencias:

- El movimiento aplicado en el motor no se transmite completamente al efector final.
  
- Pérdida de precisión.
  
- Dificultad para cumplir protocolos exactos de pruebas.

💡**Ejemplo 2:**  Proyecto con la Fuerza Aérea – Control de Movimiento para Pruebas de Biocombustibles

<div align="center">
  <img src="Imágenes_Corte_3/Clase%20%2311/Fac.avif" alt="Figura de prueba" width="300">
  <p><b>Figura 7.</b>Proyecto con la Fuerza Aérea – Control de Movimiento para Pruebas de Biocombustibles</p>
</div>

- Objetivo del Proyecto

Diseñar y desarrollar un sistema de control de movimiento para un banco de pruebas de turbinas de avión, con el fin de realizar ensayos precisos con biocombustibles, cumpliendo con protocolos internacionales de certificación.

- Contexto Técnico

El banco de pruebas incluye:

- Relación entre Posición y Velocidad

  - Una turbina real de avión.

  - Una cabina de mando simulada, con palancas y controles reales como en una aeronave.

  - Instrumentación para medir variables como presión, temperatura y consumo de combustible.

- Problema Inicial

  - En la primera fase, los controles eran mecánicos: las palancas de la cabina estaban conectadas al motor mediante guayas (cables tipo *Teleflex*).

  - Uno de los mandos más críticos era el control de potencia, que regula el flujo de combustible a la turbina.

  - Debido a la longitud de las guayas y la fricción en los recodos, surgió un fenómeno severo de backlash.

- Consecuencias del Backlash

  - Movimientos pequeños de la palanca no se transmitían correctamente al actuador del motor.
  
  - El operador tenía que mover mucho la palanca para que se notara el efecto, generando una respuesta tardía y saltos en la entrega de combustible.
  
  - Esto hacía imposible seguir los protocolos de prueba, ya que se requería una variación de potencia precisa, gradual y repetible.

- Solución Desarrollada

El equipo de Mecatrónica diseñó un sistema de control de movimiento electrónico que reemplazó el enlace mecánico:

  - A la palanca de mando se le instaló un encoder rotatorio, capaz de detectar micro-movimientos con alta resolución.
  
  - En el actuador del motor se colocó un servomotor, controlado por el sistema.
  
  - Cualquier movimiento, por pequeño que fuera, detectado por el encoder, se convertía inmediatamente en una señal para el servomotor, eliminando por completo el backlash.

- Resultados

  - Se obtuvo una respuesta instantánea y precisa del motor al mover la palanca.
  
  - Se logró realizar pruebas controladas y certificables, permitiendo medir el desempeño real de los biocombustibles bajo condiciones definidas.
  
  - Se demostró la importancia del control de movimiento preciso en sistemas de prueba industrial o aeroespacial.

- Lecciones del Proyecto

  - El backlash puede arruinar incluso un sistema que, en teoría, está bien diseñado.
  
  - El control electrónico con retroalimentación (encoder + servomotor) es fundamental cuando se necesita precisión extrema.
  
  - Las soluciones mecánicas deben ser cuidadosamente evaluadas si se requiere alta fidelidad en la transmisión del movimiento.


## 3. Cabeceo (Pitch) vs Paso (Lead)

<div align="center">
  <img src="Imágenes_Corte_3/Clase%20%2311/lead-vs-pitch-5.png" alt="Figura de prueba" width="600">
  <p><b>Figura 8.</b>Cabeceo (Pitch) vs Paso (Lead)</p>
</div>

<div align="center">
 
| **Característica**        | **Cabeceo (Pitch)**                                                                 | **Paso (Lead)**                                                                 |
|--------------------------|--------------------------------------------------------------------------------------|---------------------------------------------------------------------------------|
| **Definición**           | Número de vueltas necesarias para mover la cápsula 1 unidad de longitud              | Distancia que se desplaza la cápsula por cada vuelta del tornillo              |
| **Símbolo común**        | No siempre tiene símbolo específico                                                  | `p`                                                                             |
| **Unidad típica**        | rev/m o rev/in                                                                       | m/rev o mm/rev                                                                  |
| **Interpretación**       | Entrada → ¿Cuántas vueltas se necesitan?                                             | Salida → ¿Cuánto se mueve por vuelta?                                          |
| **Usado para**           | Medir esfuerzo del motor necesario para lograr un desplazamiento                    | Medir la eficiencia de la conversión angular-lineal                            |
| **Sistema de medida**    | Métrico / imperial                                                                   | Métrico / imperial                                                              |
| **Aplicación práctica**  | Más común en estándares ingleses (rev/in)                                            | Más usado en diseño y selección de tornillos                                   |
| **Importancia en diseño**| Menor (referencial)                                                                  | Alta (define la relación de transmisión)                                        |

</div>

**Nota**: Esta es la **relación de transmisión** que caracteriza a los tornillos de potencia.  

## 3.1 Relación Movimiento Angular - Movimiento Lineal

A partir de estos parámetros, se establece la relación entre desplazamiento angular del tornillo y desplazamiento lineal de la carga:

$$
\Delta \theta = \frac{2\pi}{p} \cdot \Delta x
$$

Donde:

- $$\(\Delta \theta\)$$: Desplazamiento angular del tornillo [rad]
  
- $$\(\Delta x\)$$: Desplazamiento lineal de la cápsula [m]
  
- $$\(p\)$$: Paso del tornillo [m/rev]  

## 3.2 Relación entre Velocidades

Si derivamos con respecto al tiempo:

$$
\frac{d\theta}{dt} = \frac{2\pi}{p} \cdot \frac{dx}{dt} \quad \Rightarrow \quad \frac{\dot{\theta}}{\dot{x}} = \frac{2\pi}{p}
$$

Lo que implica que:

$$
\frac{\text{Velocidad del motor}}{\text{Velocidad de la carga}} = \frac{2\pi}{p}
$$

Donde:

- $$\(\dot{\theta}\)$$: Velocidad angular del tornillo [rad/s]
    
- $$\(\dot{x}\)$$: Velocidad lineal de la cápsula [m/s]  

##  4. Simulación de Tornillo Guía en Simscape

Simular la conversión de movimiento rotacional a lineal mediante un tornillo guía (leadscrew) usando Simscape de MATLAB/Simulink.

<div align="center">
  <img src="Imágenes_Corte_3/Clase%20%2311/Simulink_Tornillo_Sin_Fn.png" alt="Figura de prueba" width="600">
  <p><b>Figura 9.</b>Simulación de Tornillo Guía en Simscape</p>
</div>

## 4.1 Componentes del modelo

<div align="center">
 
| **Bloque**              | **Función**                                                                 |
|------------------------|------------------------------------------------------------------------------|
| **Motor (fuente de 24 V)** | Genera el movimiento rotacional.                                            |
| **Bloque "Tornillo guía"** | Realiza la conversión rotación → traslación. Se define aquí el paso (lead). |
| **Sensor θ(t)**         | Mide la posición angular del eje del motor.                                 |
| **Sensor x(t)**         | Mide la posición lineal de la cápsula desplazada por el tornillo.           |
| **Corriente i(t)**      | Monitoreo de la corriente del sistema.                                      |

</div>

> **Nota**: Cada bloque representa un componente físico del sistema electromecánico, permitiendo evaluar su comportamiento dinámico mediante simulación.

##  4.2 Parámetros clave del Tornillo

<div align="center">
  <img src="Imágenes_Corte_3/Clase%20%2311/Configuración_Tonillo_Sin_Fin.png" width="400">
  <p><b>Figura 10.</b>Parámetros clave del Tornillo</p>
</div>

<div align="center">
 
| **Parámetro**        | **Valor**   | **Descripción**                                                                        |
|---------------------|-------------|-----------------------------------------------------------------------------------------|
| **Screw lead (paso)** | 0.015 m     | La cápsula se desplaza **1.5 cm por cada vuelta completa** del tornillo.               |
| **Screw helix type** | Right-hand  | Tornillo de paso a la derecha (rotación en sentido horario produce avance lineal).     |

</div>

> **Nota**: El paso del tornillo define directamente la relación entre el desplazamiento angular y el desplazamiento lineal.

##  4.3 Cálculo del desplazamiento lineal

<div align="center">
  <img src="Imágenes_Corte_3/Clase%20%2311/Resultados_Tornillo_Sin_FIN.png" width="400">
  <p><b>Figura 11.</b>Cálculo del desplazamiento lineal</p>
</div>

Dado:

- Desplazamiento angular: 117.8 rad
  
- Paso del tornillo (lead): 0.015 m/rev

Usamos la conversión:

$$
\text{Desplazamiento lineal} = 117.8 \, \text{rad} \times \frac{1 \, \text{rev}}{2\pi \, \text{rad}} \times 0.015 \, \text{m/rev}
$$

$$
\approx 0.28 \, \text{m}
$$

## 5. Inercia Reflejada en Tornillos Guía

Cuando una masa lineal es movida por un motor rotacional a través de un tornillo guía, la inercia lineal puede reflejarse al eje del motor. Esto permite analizar el sistema en términos rotacionales para diseño y control.

## 5.1 Derivación desde la energía cinética

- Energía cinética lineal:

$$
KE = \frac{1}{2} m \dot{x}^2
$$

Donde:

- $$\( m \)$$: masa lineal (kg)
  
- $$\( \dot{x} \)$$: velocidad lineal (m/s)

- Relación entre velocidad angular y velocidad lineal:

$$
\dot{x} = \frac{p}{2\pi} \dot{\theta}
$$

Sustituyendo en $$\( KE \)$$:

$$
KE = \frac{1}{2} m \left( \frac{p}{2\pi} \dot{\theta} \right)^2 = \frac{1}{2} \left[ m \left( \frac{p}{2\pi} \right)^2 \right] \dot{\theta}^2
$$

Esto se puede reescribir como:

$$
KE = \frac{1}{2} J_\text{ref} \dot{\theta}^2
$$

Por lo tanto, la inercia reflejada es:

$$
J_\text{ref} = m \left( \frac{p}{2\pi} \right)^2
$$

- Esta inercia reflejada $$\( J_\text{ref} \)$$ actúa como si la masa estuviera directamente conectada al eje del motor.
  
- Permite reducir el sistema a un solo dominio rotacional, facilitando el análisis dinámico y el diseño de controladores.
  
- Cuanto mayor el paso $$\( p \)$$ del tornillo, menor será la inercia reflejada (respuesta más rápida).


## Conclusiones

1. La relación de transmisión en sistemas polea-correa funciona igual que en engranajes: la velocidad angular y el torque se relacionan de forma inversa según los radios, pero ambas poleas giran en el mismo sentido (salvo que se indique lo contrario en simulación).

2. Simulaciones en Simscape permiten representar de manera precisa un sistema mecánico, incluyendo parámetros como fricción, inercia, elasticidad de la correa, y configuración del sentido de giro.

3. La correcta configuración de los bloques (polea, correa, acoplamiento) es esencial para obtener resultados realistas, como velocidad de salida y tensiones en la correa, lo cual es útil para validación y predicción de fallos.


## Referencias

[1] S. Niku, Introduction to Robotics: Analysis, Control, Applications, 4th ed., Wiley, 2023.

[2] R. Kelly, D. Santibáñez, and L. F. Reyes, Control of Robot Manipulators in Joint Space, 2nd ed., Springer, 2021.

[3] M. Spong, S. Hutchinson, and M. Vidyasagar, Robot Modeling and Control, 2nd ed., Wiley, 2020.

[4] J. E. Cote B., Perfiles de Movimiento, diapositivas de clase, 9° semestre, Universidad ECCI, 2025.
