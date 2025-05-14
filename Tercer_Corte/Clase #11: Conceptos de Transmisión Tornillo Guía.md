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


## 6. Inercia Reflejada Total – Sistema con Tornillo de Bola

Se determinar la inercia total reflejada al eje del motor, considerando todos los componentes que afectan el esfuerzo dinámico del sistema.

<div align="center">
  <img src="Imágenes_Corte_3/Clase%20%2311/Inercia_Reflejada_Total.png" width="400">
  <p><b>Figura 12.</b>Inercia Reflejada Total</p>
</div>

## 6.1 Componentes Considerados

- Inercia del tornillo

Se puede estimar como un cilindro sólido rotante:

$$
J_\text{screw} \approx \frac{1}{2} M R^2
$$

O usar el valor provisto por el **fabricante**.

- Masa total de carga útil + carro $$\(m\)$$

$$
m = \frac{W_L + W_C}{g}
$$

Donde:

  - $$\( W_L \)$$: peso de la carga (N)
  
  - $$\( W_C \)$$: peso del carro o cama (N)
  
  - $$\( g \)$$: aceleración gravitacional (9.81 m/s²)

  - Reflejo de inercia lineal al motor (`J_\text{load→in}`)

- Usando la relación de conversión rotacional-lineal del tornillo:

$$
N_S = \frac{2\pi}{p}
$$

$$
J_{\text{load→in}} = \frac{1}{\eta N_S^2} \cdot m = \frac{1}{\eta \left( \frac{2\pi}{p} \right)^2} \cdot m
$$

Donde:

  - $$\( p \)$$: paso del tornillo (m/rev)
  
  - $$\( \eta \)$$: eficiencia del tornillo (valor típico entre 0.8–0.95)

- Ecuación completa de inercia reflejada

$$
J_{\text{ref,trans}} = J_\text{screw} + \frac{1}{\eta N_S^2} \cdot \left( \frac{W_L + W_C}{g} \right)
$$

## Ejerjcico #2: Cálculo de Inercia Reflejada – Tornillo de Bola

<div align="center">
 
| Parámetro              | Valor                | Descripción                           |
|------------------------|----------------------|---------------------------------------|
| Peso de la carga       | $$\( W_L = 150\ \text{N} \)$$   | Fuerza gravitacional sobre la carga  |
| Peso del carro         | $$\( W_C = 100\ \text{N} \)$$   | Peso de la cama o estructura móvil   |
| Paso del tornillo      | $$\( p = 0.005\ \text{m/rev} \)$$ | Conversión rotación → desplazamiento |
| Eficiencia del tornillo| $$\( \eta = 0.9 \)$$             | Eficiencia mecánica                  |
| Inercia del tornillo   | $$\( J_{\text{screw}} = 3 \times 10^{-5}\ \text{kg·m}^2 \)$$ | Propiedad del eje                   |
| Gravedad               | $$\( g = 9.81\ \text{m/s}^2 \)$$ | Aceleración estándar                 |

</div>

- Paso 1: Cálculo de la Masa Total

$$
m = \frac{W_L + W_C}{g} = \frac{150 + 100}{9.81} = \frac{250}{9.81} \approx 25.48\ \text{kg}
$$

- Paso 2: Relación de Transmisión

$$
N_S = \frac{2\pi}{p} = \frac{2\pi}{0.005} \approx 1256.64\ \text{rad/m}
$$

- Paso 3: Inercia Reflejada de la Masa

$$
J_{\text{masa→in}} = \frac{1}{\eta N_S^2} \cdot m
$$

$$
J_{\text{masa→in}} = \frac{1}{0.9 \cdot (1256.64)^2} \cdot 25.48 \approx 1.792 \times 10^{-5}\ \text{kg·m}^2
$$

- Paso 4: Inercia Total Reflejada al Motor

$$
J_{\text{ref,trans}} = J_{\text{screw}} + J_{\text{masa→in}} = 3 \times 10^{-5} + 1.792 \times 10^{-5}
$$

$$
\boxed{J_{\text{ref,trans}} \approx 4.79 \times 10^{-5}\ \text{kg·m}^2}
$$

## 7. Torque de Carga Reflejado al Motor – Tornillo de Potencia Inclinado

<div align="center">
  <img src="Imágenes_Corte_3/Clase%20%2311/Torque_de_Carga.png" width="400">
  <p><b>Figura 13.</b>Torque de Carga</p>
</div>

Cuando un tornillo de potencia está inclinado respecto a la horizontal, se deben considerar los siguientes parámetros para calcular el torque reflejado al motor:

  - Ángulo de inclinación: $$\( \beta \)$$
  
  - Peso total: $$\( W_L + W_C \)$$
  
  - Coeficiente de fricción: $$\( \mu \)$$
  
  - Eficiencia mecánica: $$\( \eta \)$$

- Fuerzas Involucradas

- Fuerza de fricción: $$F_f = \mu (W_L + W_C) \cos\beta$$

### - Componente del peso a lo largo del tornillo (gravedad):
$$
F_g = (W_L + W_C) \sin\beta
$$

### - Fuerza externa total que el motor debe vencer:
$$
F_{\text{ext}} = F_p + (W_L + W_C)(\sin\beta + \mu \cos\beta)
$$

Si el tornillo está horizontal $$(\( \beta = 0^\circ \))$$, entonces:

$$
F_g = 0,\quad F_{\text{ext}} = F_p + \mu(W_L + W_C)
$$

### - Relación de Transmisión Lineal-Rotacional

$$
N_S = \frac{2\pi}{p}
$$

Donde $$\( p \)$$ es el paso del tornillo (en metros por revolución).

### - Torque Reflejado al Motor

Se igualan los trabajos:

$$
\text{Trabajo} = F_{\text{ext}} \cdot \Delta x = T_{\text{load→in}} \cdot \Delta\theta
$$

Despejando el torque reflejado:

$$
T_{\text{load→in}} = \frac{F_{\text{ext}}}{\eta N_S}
$$

- Si el sistema está inclinado, siempre descomponer las fuerzas usando $$\( \sin\beta \)$$ y $$\( \cos\beta \)$$.
  
- Modelo de reflejo sigue la estructura:
  
  - Para inercia:

$$J_{\text{ref}} = \frac{1}{\eta N_S^2} \cdot m$$
    
  - Para torque;
    
$$T_{\text{ref}} = \frac{F_{\text{ext}}}{\eta N_S}$$
   
- La eficiencia $$\( \eta \)$$ siempre se aplica tanto para torque como para inercia.
  
- En muchos casos prácticos, no hay una fuerza adicional $$\( F_p \)$$, y solo se consideran fricción y peso.

💡**Ejemplo 3:** 

Una carga de 50 kg debe ser posicionada usando un **tornillo esferado de acero** con las siguientes características:

- Densidad: $$\( \rho = 0.14 \, \text{kg/cm}^3 \)$$
  
- Diámetro: $$\( d = 0.182 \, \text{cm} \)$$
  
- Longitud: $$\( L = 36 \, \text{cm} \)$$
  
- Paso del tornillo: $$\( p = 0.75 \, \text{cm/rev} \)$$
  
- Eficiencia: $$\( \eta = 0.90 \)$$

Además, el carro pesa 0.23 kg.


### - Paso 1: Relación de Transmisión

$$
N_s = \frac{2\pi}{p} = \frac{2\pi}{0.0075} \approx 837.76 \, \text{rad/m}
$$

### - Paso 2: Momento de Inercia del Tornillo

$$
J_{\text{screw}} = \frac{\pi L \rho D^4}{32}
$$

Sustituyendo:

$$
J_{\text{screw}} = \frac{\pi \cdot 0.36 \cdot 140{,}000 \cdot (0.00182)^4}{32} \approx 5.42 \times 10^{-8} \, \text{kg}\cdot\text{m}^2
$$

### - Paso 3: Masa Total

$$
m = W_L + W_C = 50 + 0.23 = 50.23 \, \text{kg}
$$

### - Paso 4: Cálculo de Inercia Reflejada de la Masa

$$
J_{\text{load} \rightarrow \text{in}} = \frac{1}{\eta N_s^2} \cdot m
$$

$$
J_{\text{load} \rightarrow \text{in}} = \frac{50.23}{0.9 \cdot (837.76)^2} \approx 8.10 \, \text{kg}\cdot\text{m}^2
$$

### - Paso 5: Inercia Total Reflejada

$$
J_{\text{ref trans}} = J_{\text{screw}} + J_{\text{load} \rightarrow \text{in}} \approx 5.42 \times 10^{-8} + 8.10 \approx 8.10 \, \text{kg}\cdot\text{m}^2
$$

# 8. Modelo en Simscape Multibody: Tornillo Guía (Lead Screw)

<div align="center">
  <img src="Imágenes_Corte_3/Clase%20%2311/Simulación simscape Multibody.png" width="600">
  <p><b>Figura 14.</b>Simulación simscape Multibody</p>
</div>

### Componentes del modelo

### - Transformación rígida

  - Se usa para fijar la longitud Z del sistema.
  
  - No permite movimiento entre las partes conectadas.

### - Junta de revolución (Revolute Joint)

- Permite la rotación alrededor del eje Z.
  
- Representa el giro del tornillo.

### - Bloque de soldadura (Weld Joint)

- Une el cabezal con el tornillo.
  
- No permite ni rotación ni traslación entre los sólidos.
  
- Útil para “pegar” componentes y crear un cuerpo rígido único (como si fuera un sólido más grande).

### - Articulación prismática (Prismatic Joint)

- Permite que el carro se desplace linealmente sobre el tornillo.
  
- Restringe cualquier otro tipo de movimiento.

### - Bloque de tornillo guía (Lead Screw)
- Se configura con el paso (pitch) y el sentido del avance.
  
- Relaciona la rotación del tornillo con el desplazamiento lineal del carro.
  
- Transforma la entrada rotacional (desde la junta de revolución) en un movimiento lineal equivalente.

1. El motor o entrada rotacional se conecta a una junta de revolución que gira el tornillo.
   
3. El bloque de Lead Screw convierte este giro en movimiento lineal del carro.
   
5. El carro está restringido a solo moverse linealmente gracias a la junta prismática.
   
7. Los componentes están firmemente unidos con bloques de soldadura, simulando el ensamblaje físico real.


## 8.1 Configuración del bloque Lead Screw en Simscape

<div align="center">
  <img src="Imágenes_Corte_3/Clase%20%2311/Simluacion_Tornillo.png" width="600">
  <p><b>Figura 15.</b>Simulación simscape Multibody</p>
</div>

### - Dirección

- En el ejemplo se seleccionó Left-Hand (rosca izquierda).
  
- Esto determina el **sentido del desplazamiento lineal respecto al giro** del tornillo.

###  - Lead (Paso)

- Valor configurado: 7.5 mm/rev
  
- Indica que por cada revolución completa del tornillo, el carro se desplazará 7.5 mm a lo largo del eje.

### - Interpretación del modelo simulado

<div align="center">
  <img src="Imágenes_Corte_3/Clase%20%2311/Tonillo_sin_fin.gif" width="400">
  <p><b>Figura 16.</b>Simulación simscape Multibody</p>
</div>

- 🔴 **Cubo rojo** = Carro móvil que se traslada linealmente.
  
- 🔵 **Cilindro azul** = Tornillo que gira para accionar el sistema.
  
- 🟩 **Cubo verde** = Cabezal del tornillo (agregado visualmente para facilitar la identificación del giro).
  
- 🔁 **Ejes de coordenadas visibles** ayudan a verificar el movimiento angular y lineal.


# 8.2 Resultados de la Simulación

### - Gráfica:

<div align="center">
  <img src="Imágenes_Corte_3/Clase%20%2311/Resultados_Tornillo_.png" width="600">
  <p><b>Figura 17.</b>Resultados</p>
</div>

### - Articulación Rotacional (Tornillo)

- Muestra el número de revoluciones del tornillo guía a lo largo del tiempo.

### - Articulación Prismática (Carro)

- Refleja el desplazamiento lineal del carro sobre el eje del tornillo.

- Ambos valores aumentan de forma proporcional con el tiempo.
  
- La articulación prismática no inicia en cero, ya que se configuró una posición inicial distinta para evitar que comenzara en el mismo punto que el cabezal del tornillo.
  
- Desde esa posición, el desplazamiento lineal avanza correctamente, manteniendo la relación esperada por el paso del tornillo (7.5 mm/rev).

### - Resultados de Velocidad

<div align="center">
  <img src="Imágenes_Corte_3/Clase%20%2311/Resultados_Tornillo_Velocidad.png" width="600">
  <p><b>Figura 17.</b>Resultados Tornillo Velocidad</p>
</div>

### - Velocidad Rotacional (rad/s)

- Corresponde al eje de rotación del tornillo.

### - Velocidad Lineal (mm/s)

- Se refiere al movimiento del carro desplazándose a lo largo del tornillo.

- La velocidad lineal es mucho menor que la velocidad rotacional.
  
- Esto se debe al paso reducido del tornillo (7.5 mm/rev), característico de sistemas con tornillo sin fin o de **rosca fina**, que requieren muchas vueltas para producir un desplazamiento significativo.






## Conclusiones

1. La relación de transmisión en sistemas polea-correa funciona igual que en engranajes: la velocidad angular y el torque se relacionan de forma inversa según los radios, pero ambas poleas giran en el mismo sentido (salvo que se indique lo contrario en simulación).

2. Simulaciones en Simscape permiten representar de manera precisa un sistema mecánico, incluyendo parámetros como fricción, inercia, elasticidad de la correa, y configuración del sentido de giro.

3. La correcta configuración de los bloques (polea, correa, acoplamiento) es esencial para obtener resultados realistas, como velocidad de salida y tensiones en la correa, lo cual es útil para validación y predicción de fallos.


## Referencias

[1] S. Niku, Introduction to Robotics: Analysis, Control, Applications, 4th ed., Wiley, 2023.

[2] R. Kelly, D. Santibáñez, and L. F. Reyes, Control of Robot Manipulators in Joint Space, 2nd ed., Springer, 2021.

[3] M. Spong, S. Hutchinson, and M. Vidyasagar, Robot Modeling and Control, 2nd ed., Wiley, 2020.

[4] J. E. Cote B., Perfiles de Movimiento, diapositivas de clase, 9° semestre, Universidad ECCI, 2025.
