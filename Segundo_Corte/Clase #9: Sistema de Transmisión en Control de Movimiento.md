# Sistema de Transmisión en Control de Movimiento

En sesiones anteriores se revisaron los principales componentes de un sistema de control de movimiento, incluyendo los controladores, el esquema de control en cascada y los perfiles de movimiento. Estos últimos funcionan como señales de referencia (set points) para los controladores, definiendo cómo debe evolucionar la posición, velocidad o aceleración del sistema a lo largo del tiempo.

A partir de esta clase se inicia el estudio de la parte mecánica del sistema, enfocándose específicamente en el sistema de transmisión. Este sistema es el encargado de acoplar el actuador, usualmente un motor, con la carga, es decir, el elemento físico que se debe mover para cumplir con una tarea específica dentro del proceso.

El análisis del sistema de transmisión es crucial, ya que determina cómo se transfiere el movimiento del motor hacia la carga. En el contexto del curso, este estudio se orientará hacia el dimensionamiento del motor, es decir, la selección adecuada de su capacidad en función de los requerimientos de la carga. Un dimensionamiento correcto garantiza que el sistema pueda ejecutar su tarea sin sobrecargas ni fallos.

## Índice

[1. ¿En qué Consiste?](#1-en-qué-Consiste)

## 1. Diseño de Transmisión en Control de Movimiento

Garantizar que el perfil de movimiento definido se transmita correctamente desde el motor hasta la carga mediante un sistema de transmisión bien dimensionado.

<div align="center">
  <img src="Imágenes_Corte_2/Clase%20%239/1_Diapositiva_Diseño_de_Transmición.png" alt="Figura de prueba" width="300">
  <p><b>Figura 1.</b>Diseño de Transmición</p>
</div>

- Importancia de una buena selección de motor y transmisión

<div align="center">
  
| Caso               | Consecuencia                                                             |
|--------------------|---------------------------------------------------------------------------|
| Subdimensionamiento | El motor no puede cumplir con la tarea → Fallo y reemplazo costoso.      |
| Sobredimensionamiento | Capacidad desaprovechada → Mayor costo y menor eficiencia.              |

</div>
  
> **Nota:** La selección debe considerar variaciones futuras en el proceso, como aumento de carga o cambios en el mecanismo.

- Tipos de acoplamiento

<div align="center">
  
| Tipo de transmisión | Descripción                                                             |
|---------------------|-------------------------------------------------------------------------|
| Directo             | La carga se acopla directamente al eje del motor.                       |
| Engranajes          | Modifican torque y velocidad mediante relación de transmisión.          |
| Polea-correa        | Permite ajustar velocidad/torque, absorbe vibraciones.                  |
| Tornillo sin fin    | Alta reducción, ideal para movimientos lentos y de alta fuerza.         |
| Transportadoras     | Transmiten movimiento lineal para desplazar objetos.                    |

</div>

> **Nota:** La elección del tipo de acoplamiento impacta directamente en el rendimiento, la eficiencia y el mantenimiento del sistema. Debe seleccionarse según la aplicación y las condiciones de operación.

💡**Ejemplo 1:**

Supóongamos que necesitas mover una caja de 10 kg mediante una banda transportadora. Si más adelante se aumenta la carga a 20 kg, un motor mal dimensionado podría falla

<div align="center">
  <img src="Imágenes_Corte_2/Clase%20%239/Ejemplo_1_Clase_9.jpeg" alt="Figura de prueba" width="300">
  <p><b>Figura 2.</b>Ejemplo 1</p>
</div>

- Solución:

  - Dimensionar el motor considerando una margen de carga adicional.

  - Analizar el tipo de transmisión para optimizar torque/velocidad según el requerimiento.

- ¿Por qué no basta con mirar el torque de la carga?
  
Cuando usamos transmisiones no directas (como engranajes), el torque y la inercia de la carga no se transfieren tal cual al motor.

- Se debe hacer una reflexión de parámetros:

  - Convertir inercia y torque de la carga a valores equivalentes en el eje del motor.

  - Considerar también la inercia del mecanismo (engranajes, poleas, etc.), no solo de la carga final.

## 2. Requerimientos de Diseño en Control de Movimiento

También es crucial balancear la inercia motor-carga para garantizar estabilidad y desempeño. Además, deben considerarse factores como costo, precisión, frecuencia de operación y restricciones del entorno.

 <div align="center">
  <img src="Imágenes_Corte_2/Clase%20%239/2_Diapositiva_Clase_9.gif" alt="Figura de prueba" width="300">
  <p><b>Figura 3.</b>Inercia Motor</p>
</div>

🔑 Margen de seguridad: Factor multiplicativo aplicado al requerimiento mínimo de torque para garantizar que el motor funcione correctamente incluso en condiciones imprevistas. Generalmente se recomienda un margen entre 1.2 y 2.0, dependiendo del nivel de incertidumbre del sistema.

- Factores comunes en la selección del motor

<div align="center">
   
| Requisito                | ¿Por qué es importante?                                 | Consecuencia de ignorarlo                          |
|--------------------------|---------------------------------------------------------|----------------------------------------------------|
| Torque mínimo requerido  | Mover la carga sin que el motor se sobrecargue         | Subdimensionamiento, falla del sistema             |
| Relación de inercias     | Estabilidad del sistema de control                     | Respuesta lenta o inestable                        |
| Costos                   | Ajustarse al presupuesto del proyecto                  | Inviabilidad del diseño                            |
| Precisión y ciclos       | Garantizar repetibilidad y rendimiento en tiempo esperado | Fallos de calidad o productividad              |

</div>

> **Nota:** La correcta evaluación de estos factores asegura una selección de motor equilibrada entre rendimiento, eficiencia y viabilidad económica.

💡**Ejemplo 2:** 

**Pregunta:**  

Supongamos que nuestro sistema requiere 2.5 Nm de torque para funcionar correctamente. Si decides usar un margen de seguridad del 1.5, ¿cuál debería ser el torque mínimo nominal del motor?

**Solución:**  

$$T_{\text{motor}} = 2.5\, \text{Nm} \times 1.5 = 3.75\, \text{Nm}$$

Deberiamos elegir un motor con un torque nominal de al menos **3.75 Nm**.

## 3. Posibles Problemas de Diseño en Sistemas de Movimiento

🔑 Transmisión mecánica: Sistema que adapta la velocidad y el torque entre un actuador (como un motor) y la carga. Puede incluir engranajes, bandas, poleas, tornillos sin fin, etc.

En el diseño de sistemas mecatrónicos, es común enfrentarse a distintos escenarios dependiendo de los elementos que ya estén disponibles o definidos. Estos escenarios afectan directamente el enfoque del proceso de diseño.

- Tipos de problemas de diseño:

<div align="center">
  
| Tipo | Datos conocidos                            | A determinar                      | Contexto típico                                                      |
|------|--------------------------------------------|-----------------------------------|----------------------------------------------------------------------|
| 1    | Movimiento deseado de la carga             | Transmisión y motor               | Proyectos que inician desde cero                                     |
| 2    | Motor y transmisión existentes             | Movimiento resultante de la carga | Análisis de reutilización o diagnóstico                              |
| 3    | Motor existente + movimiento deseado       | Transmisión                       | Muy común en entornos industriales con recursos limitados            |
| 4    | Movimiento deseado + transmisión existente | Motor                             | Frecuente en modernización de maquinaria                             |

</div>

> **Nota:** Identificar correctamente el tipo de problema permite enfocar el diseño o análisis hacia soluciones más eficientes y viables dentro del contexto del proyecto.

- Comparativa internacional del tipo de problemas más comunes

<div align="center">
  
| País        | Escenario más común  | Razón principal                                                        |
|-------------|----------------------|------------------------------------------------------------------------|
| 🇨🇴 Colombia   | Tipos 3 y 4           | Reutilización de equipos por limitaciones de presupuesto              |
| 🇩🇪 Alemania   | Tipo 1               | Alto nivel de planeación y diseño desde cero                          |
| 🇺🇸 Estados Unidos | Tipo 1 y 4        | Innovación frecuente + modernización de líneas antiguas               |
| 🇯🇵 Japón      | Tipo 1 y 2           | Fuerte enfoque en eficiencia y análisis de ciclo de vida              |

</div>

> **Nota:** Las decisiones de diseño están fuertemente influenciadas por el contexto económico, cultural y tecnológico de cada país, lo que define prioridades distintas en cada escenario.

## 4. Inercia y Torque Reflejado

- Conceptos Clave

<div align="center">
  
| Término                   | Definición                                                                 |
|---------------------------|----------------------------------------------------------------------------|
| Inercia (J)               | Propiedad física que representa la resistencia de un cuerpo a cambiar su velocidad angular. |
| Torque (τ)                | Fuerza que produce un giro sobre un eje. Se relaciona con la inercia por leyes de Newton.   |
| Aceleración angular (α)   | Cambio de velocidad angular por unidad de tiempo.                          |

</div>

> **Nota:** Estos conceptos son fundamentales para entender el comportamiento dinámico de sistemas rotacionales y seleccionar adecuadamente un motor o sistema de transmisión.

- Ley de Newton para rotaciones

 <div align="center">
  <img src="Imágenes_Corte_2/Clase%20%239/Ley_de_NEWTON_para_Rotaciones.png" alt="Figura de prueba" width="300">
  <p><b>Figura 4.</b>Inercia Motor</p>
</div>

$$\sum \tau = J \cdot \alpha$$

Esta ecuación es el equivalente rotacional de la famosa:

$$F = m \cdot a$$

**En este contexto:**

- $$\sum \tau$$: Torque total aplicado sobre el sistema.

- $$J$$: Momento de inercia del sistema.
  
- $$\alpha$$: Aceleración angular.

- Inercia reflejada

Cuando hay una cadena de transmisión (acoples, engranajes, bandas, etc.), el motor no ve directamente la inercia de la carga, sino una inercia reflejada, que depende del sistema de transmisión.

Esto es crucial para:

- Dimensionar correctamente el motor.

- Prever el torque que deberá ejercer el motor.

- ¿Inercia rotacional o lineal?

Aunque la inercia $$J$$ es formalmente un concepto rotacional, en ingeniería de control de movimiento se usa también para sistemas en traslación porque ambos representan resistencia al cambio de velocidad.

 <div align="center">
   
| Movimiento          | Variable análoga a la masa/inercia     |
|---------------------|-----------------------------------------|
| Rotacional          | $$J$$ inercia rotacional            |
| Lineal/traslación   | $$m$$ masa                          |

</div>

> **Nota:** Reconocer la equivalencia conceptual entre masa e inercia permite aplicar principios similares tanto en sistemas lineales como rotacionales, facilitando el modelado y análisis dinámico.

## Ejercicio 1
 
Un motor debe acelerar una carga con una inercia reflejada de  $$ J = 0.05\, \text{kg}\text{m}^2$$ a una velocidad de $$100\, \text{rad/s}$$ en $$2\, \text{s}$$. 

¿Qué torque promedio debe aplicar el motor?

**Solución:**

1. **Aceleración angular:**

$$\alpha = \frac{\Delta \omega}{\Delta t} = \frac{100}{2} = 50\, \text{rad/s}^2$$

2. **Aplicando la ley de Newton rotacional:**

$$\tau = J \cdot \alpha = 0.05 \cdot 50 = 2.5\, \text{N} \cdot \text{m}$$

**Resultado:** El torque promedio requerido es **2.5 N·m**.

## 5. Relación de Engranajes y su Efecto en el Sistema

 <div align="center">
  <img src="Imágenes_Corte_2/Clase%20%239/7_Diapositiva_Engranajes.png" alt="Figura de prueba" width="300">
  <p><b>Figura 5.</b>Engranajes</p>
</div>

- Concepto general

La relación de engranajes $$N_{GB}$$ describe cómo se transforman la velocidad angular y el torque entre el motor y la carga mediante un sistema de engranajes:

$$N_{GB} = \frac{\omega_m}{\omega_l} = \frac{r_l}{r_m} = \frac{n_l}{n_m} = \frac{T_l}{T_m}$$

**Donde:**

- $$\omega_m, \omega_l$$: Velocidad angular del motor y la carga
    
- $$r_m, r_l$$: Radios de los engranajes
  
- $$n_m, n_l$$: Número de dientes de cada engranaje
  
- $$T_m, T_l$$: Torque del motor y de la carga  


- Relación desde la velocidad tangencial:

Como los engranajes están en contacto en un punto común:

$$V_{\text{tangencial}} = \omega_m r_m = \omega_l r_l$$

Entonces:

$$\frac{\omega_m}{\omega_l} = \frac{r_l}{r_m}$$

- Relación desde la cantidad de dientes

También se puede deducir la relación de transmisión a partir del número de dientes:

$$\frac{n_l}{n_m} = \frac{r_l}{r_m} \Rightarrow N_{GB} = \frac{n_l}{n_m}$$

- Relación desde la potencia

Como la potencia mecánica se conserva:

$$P = T_m \omega_m = T_l \omega_l$$

Entonces:

$$\frac{\omega_m}{\omega_l} = \frac{T_l}{T_m}$$

## 6. Simulación de Engranajes en Simscape

 <div align="center">
  <img src="Imágenes_Corte_2/Clase%20%239/8_Diapositiva_Simulación_simscape.png" alt="Figura de prueba" width="700">
  <p><b>Figura 6.</b>Simulación de Engranajes en Simscape</p>
</div>

- Descripción del sistema

El sistema utiliza un motor DC Moog C23L33W10 alimentado a 24 V, conectado a un sistema de engranajes modelado con bloques de Simscape (no Multibody). Esto permite simular únicamente variables dinámicas del sistema: torque, velocidad y aceleración.

- Modelado del engranaje

El bloque de engranaje en Simscape representa dos ruedas:

  -  Rueda motriz (lado izquierdo del bloque): conectada al eje del motor.
    
  -  Rueda conducida (lado derecho): entrega el movimiento transformado.

Este bloque simula automáticamente la relación de transformación, considerando:

- Relación de radios o número de dientes.
  
- Variables opcionales: fricción, eficiencia, juego entre dientes, etc.

- Análisis de velocidades

Según el sistema simulado:

<div align="center">
  
| Variable               | Valor            |
|------------------------|------------------|
| Velocidad del motor    | $$\omega_m = 11500 \ \text{rpm}$$ |
| Velocidad de salida    | $$\omega_l = 2300 \ \text{rpm}$$  |

</div>

Relación de engranajes:

$$N_{GB} = \frac{\omega_l}{\omega_m} = \frac{2300}{11500} = 0.2$$

Esto implica:

- Reducción de velocidad a la salida.
  
- Aumento del torque** en la carga (idealmente, por conservación de potencia).

- Relación y reflexión

La relación también afecta otras variables importantes:

- Inercia reflejada al motor:

$$J_{\text{reflejada}} = J_{\text{carga}} \cdot N_{GB}^2$$

- Torque requerido por el motor:

$$T_m = \frac{T_l}{N_{GB}}$$

## 7. Modelo de Engranajes en Simscape Multibody (Aproximado con Discos)

 <div align="center">
  <img src="Imágenes_Corte_2/Clase%20%239/9_Diapositiva_Engranajes_con_Discos.png" alt="Figura de prueba" width="700">
  <p><b>Figura 7.</b>Engranajes con Discos</p>
</div>

Simular el comportamiento cinemático de un sistema de engranajes usando ruedas lisas (sin dientes) en Simscape Multibody. Aunque no hay contacto real, se utiliza una restricción de movimiento para simular el acoplamiento.

- Componentes del Modelo
  
<div align="center">
  
| Elemento                | Descripción técnica |
|-------------------------|---------------------|
| Base-gear y Follower-gear | Discos sólidos con radios distintos, simulando engranajes cilíndricos. |
| Solid Blocks            | Definen masa, geometría y densidad (ej. acero). |
| Revolute Joints         | Permiten rotación individual de cada engranaje. |
| Rigid Transforms        | Ajustan posición para evitar superposición. |
| Gear Constraint         | Impone relación angular entre ruedas. |
| Simulink-PS Converter   | Conecta señales de Simulink al entorno físico. |

</div>

- Parámetros Usados

<div align="center">
  
| Parámetro      | Base Gear  | Follower Gear |
|----------------|------------|---------------|
| Radio          | 0.02 m     | 0.01 m        |
| Largo          | 0.01 m     | 0.01 m        |
| Densidad       | 7800 kg/m³ | 7800 kg/m³    |

</div>

- Relación de Movimiento

La restricción impuesta por el bloque Gear Constraint determina:

$$\frac{\omega_{\text{follower}}}{\omega_{\text{base}}} = \frac{r_{\text{base}}}{r_{\text{follower}}} = \frac{0.02}{0.01} = 2$$

- El engranaje seguidor gira el doble de rápido que el base, en sentido opuesto.

- Observaciones clave

- No se modelan fuerzas de contacto ni fricción entre dientes.
  
- Ideal para análisis cinemático y visualización del movimiento.
  
- Para un modelado más realista: usar modelos CAD exportados desde herramientas como SolidWorks.

💡**Ejemplo 3:** Engranajes con masa y momento de inercia reflejado

- Fundamento teórico

Para acoplamiento ideal (sin pérdidas), el momento de inercia reflejado desde el seguidor hacia el base es:

$$J_{\text{reflejado}} = J_{\text{seguidor}} \cdot \left( \frac{r_{\text{base}}}{r_{\text{seguidor}}} \right)^2$$

- Configuración de parámetros

<div align="center">

| Propiedad       | Engranaje Base | Engranaje Seguidor |
|------------------|----------------|--------------------|
| Radio (\(r\))    | 0.02 m         | 0.01 m             |
| Largo            | 0.01 m         | 0.01 m             |
| Densidad (\(\rho\)) | 7800 kg/m³  | 7800 kg/m³         |

</div>

- Cálculo del momento de inercia

Para cilindros sólidos:

$$J = \frac{1}{2} m r^2$$

Volumen del seguidor:

$$V = \pi r^2 h = \pi (0.01)^2 (0.01) = 3.14 \times 10^{-6} \, \text{m}^3$$

- Masa del seguidor:

$$m = \rho V = 7800 \cdot 3.14 \times 10^{-6} \approx 0.0245 \, \text{kg}$$

Momento de inercia del seguidor:

$$J_{\text{seguidor}} = \frac{1}{2} \cdot 0.0245 \cdot (0.01)^2 = 1.225 \times 10^{-6} \, \text{kg} \cdot \text{m}^2$$

Momento reflejado en el engranaje base:

$$J_{\text{reflejado}} = 1.225 \times 10^{-6} \cdot \left( \frac{0.02}{0.01} \right)^2 = 4.9 \times 10^{-6} \, \text{kg} \cdot \text{m}^2$$

## 8. Configuración del bloque *Common Gear Constraint*

 <div align="center">
  <img src="Imágenes_Corte_2/Clase%20%239/10_Diapositiva_Engranaje_Comun.png" alt="Figura de prueba" width="700">
  <p><b>Figura 8.</b>Engranaje Común</p>
</div>

El bloque Common Gear Constraint permite modelar la interacción cinemática entre dos engranajes externos (sin fricción ni contacto real) imponiendo una restricción de movimiento rotacional.

- Opción 1: *Center Distance and Ratio*

 <div align="center">
   
| Parámetro               | Valor   | Descripción                                              |
|-------------------------|---------|----------------------------------------------------------|
| Type                    | External| Define el tipo de engranajes (externos o internos).      |
| Specification Method    | Center Distance and Ratio | Método basado en la distancia entre centros y relación de transmisión. |
| Center Distance         | 3 cm    | Distancia entre los ejes de los dos engranajes.          |
| Gear Ratio (Nf/Nb)      | 0.5     | Relación de transmisión: dientes del **seguidor/base**.  |

</div>

- Opción 2: Pitch Circle Radii

 <div align="center">
   
| Parámetro               | Valor   | Descripción                                              |
|-------------------------|---------|----------------------------------------------------------|
| Type                    | External| Tipo de engranaje (externo).                             |
| Specification Method    | Pitch Circle Radii | Método basado en los radios de los círculos de paso.         |
| Base Gear Radius        | 2 cm    | Radio del engranaje base.                               |
| Follower Gear Radius    | 1 cm    | Radio del engranaje seguidor.                           |

</div>

- ¿Qué hace el bloque internamente?

El bloque impone una relación entre las velocidades angulares de los dos ejes:

$$\omega_b \cdot r_b = - \omega_f \cdot r_f$$

Donde:

- $$\omega_b$$: velocidad angular del engranaje base
  
- $$\omega_f$$: velocidad angular del engranaje seguidor
  
- $$r_b$$: radio del engranaje base
  
- $$r_f$$: radio del engranaje seguidor  

El signo negativo indica que los engranajes giran en sentidos opuestos al estar acoplados de forma externa.






















































CONCLUSONES 1. El perfil de velocidad trapezoidal es una herramienta fundamental en el diseño de trayectorias para sistemas de movimiento, como robots o ejes lineales. Su principal ventaja es que permite planificar el desplazamiento de manera suave y controlada, dividiéndolo en tres fases: aceleración, velocidad constante y desaceleración. Esta estructura facilita un movimiento más eficiente y menos agresivo para los componentes mecánicos, al evitar cambios bruscos de velocidad.

2. A través del uso de fórmulas geométricas y analíticas, se pueden calcular con precisión todos los parámetros clave del movimiento: tiempos de aceleración y desaceleración, duración del movimiento uniforme y el desplazamiento total. Estas relaciones permiten adaptar el perfil a las restricciones físicas del sistema, como la aceleración máxima o la distancia que se debe recorrer. Además, la posibilidad de calcular la posición en cada instante del tiempo es esencial para aplicaciones que requieren alta precisión.

3. Tanto el enfoque geométrico como el analítico resultan válidos y complementarios. El primero ofrece una solución rápida e intuitiva mediante áreas bajo la curva de velocidad, mientras que el segundo brinda mayor exactitud y permite analizar el comportamiento del sistema en todo momento. La correcta aplicación de estos métodos garantiza trayectorias optimizadas, seguras y eficientes, fundamentales en sistemas automatizados modernos



Referencias

[1] J. J. Craig, Introduction to Robotics: Mechanics and Control, 3rd ed., Pearson Prentice Hall, 2005.

[2] L. Sciavicco y B. Siciliano, Modeling and Control of Robot Manipulators, 2nd ed., Springer, 2012.

[3] M. P. Groover, Automation, Production Systems, and Computer-Integrated Manufacturing, 4th ed., Pearson, 2015.

[4] Bosch Rexroth AG, Mechatronics and Motion Control – Application Manual, 2002.

[5] J. E. Cote B., Perfiles de Movimiento, diapositivas de clase, 9° semestre, Universidad ECCI, 2025.
