# Conceptos de Transmisión Tornillo Guía

Durante las sesiones anteriores del curso, se abordaron los fundamentos del comportamiento del torque y la inercia en distintos tipos de mecanismos de transmisión. El objetivo principal ha sido entender cómo reflejar adecuadamente estas variables hacia el lado del motor, lo cual es esencial para un correcto dimensionamiento del mismo. Entre los mecanismos estudiados se encuentran los engranajes y las poleas con correas, destacando aspectos clave como la relación de transmisión, la eficiencia del sistema y la relación de inercia. Se discutió cómo estas variables afectan el rendimiento y la selección del motor, y se realizaron simulaciones en Simscape para visualizar su comportamiento.

Ahora, retomando la clase, se introducen nuevos mecanismos comúnmente utilizados en entornos industriales. Entre ellos se encuentra el tornillo guía, también conocido como tornillo sin fin, un componente ampliamente utilizado en diversos procesos mecánicos. Este mecanismo será analizado tanto desde su funcionamiento físico como desde su modelado y simulación, con el fin de ampliar el entendimiento sobre las diferentes formas de transmisión de movimiento y fuerza en sistemas industriales.

## Índice

 [10. Conclusiones](#10-Conclusiones)

 [11. Bibliografía](#11-Bibliografía)


## 1. Tornillo sin Fin

>🔑 *Tornillo sin fin:* Elemento mecánico que convierte movimiento rotacional en movimiento lineal, usado comúnmente en maquinaria para precisión y control de posición.

## 1.1 Principio de Funcionamiento

- Al girar el tornillo, se genera un desplazamiento lineal en una tuerca o componente móvil acoplado a él.

- A esta parte móvil, que se desplaza a lo largo del tornillo, se le suele conectar una cama o bandeja que cumple funciones específicas en el sistema mecánico.
  
<div align="center">
  <img src="Imágenes_Corte_3/Clase%20%2311/Tornillo_Sin_Fin.gif" alt="Figura de prueba" width="300">
  <p><b>Figura 1.</b>Tornillo sin Fin</p>
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
<div align="center">

<div align="center">
  <img src="Imágenes_Corte_3/Clase%20%2311/Acme_Threads_Trapezoidal_Threads.png" alt="Figura de prueba" width="300">
  <p><b>Figura 1.</b>Tornillo sin Fin</p>
</div>

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





💡**Ejemplo 2:** 


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
| Radio $$r$$    | 0.02 m         | 0.01 m             |
| Largo            | 0.01 m         | 0.01 m             |
| Densidad $$\rho\$$| 7800 kg/m³  | 7800 kg/m³         |

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

## 9. Resultado de la Simulación del Sistema de Engranajes

 <div align="center">
  <img src="Imágenes_Corte_2/Clase%20%239/Simulacion_Engranajes.gif" alt="Figura de prueba" width="600">
  <p><b>Figura 9.</b>Gif Engranajes</p>
</div>

Durante la simulación, se observó que la rueda seguidora (de menor radio) gira al doble de velocidad que la rueda base. Esto valida correctamente la relación de transmisión definida en la configuración del bloque *Common Gear Constraint*, donde:

- Gear Ratio $$Nf/Nb$$ = 0.5

## 10. Inercia Reflejada a través de Engranajes

 <div align="center">
  <img src="Imágenes_Corte_2/Clase%20%239/Inercia_Reflejada.png" alt="Figura de prueba" width="300">
  <p><b>Figura 9.</b>Gif Engranajes</p>
</div>

- Concepto General

Cuando una carga con inercia $$J_{\text{load}}$$ está conectada al eje de un motor mediante un sistema de engranajes, el motor no percibe directamente dicha inercia. En su lugar, experimenta una inercia reflejada $$J_{\text{ref}}$$, la cual depende de la relación de transmisión del sistema mecánico.

- Casos de Acople

 <div align="center">
   
| Tipo de Acople     | Modelo             | Expresión de Torque                            |
|--------------------|--------------------|------------------------------------------------|
| Directo            | Eje rígido         | $$T_m = J_{\text{load}} \, \ddot{\theta}_m$$ |
| Con engranajes     | Transmisión mecánica | $$T_m = J_{\text{load}} \left( \frac{r_m}{r_l} \right)^2 \ddot{\theta}_m$$ |

</div>

- Descripción de Variables

- $$T_m$$: Torque aplicado por el motor
  
- $$T_l$$: Torque sobre la carga
  
- $$\ddot{\theta}_m$$: Aceleración angular del motor
  
- $$\ddot{\theta}_l$$: Aceleración angular de la carga
  
- $$\(r_m \), \( r_l \)$$: Radios de la rueda motriz y de la carga, respectivamente
  
- $$\( N_{GB} = \frac{r_l}{r_m} \)$$: Relación de transmisión del engranaje

- Derivación de la Inercia Reflejada

Partimos de la condición de desplazamiento tangencial:

$$r_l \theta_l = r_m \theta_m \Rightarrow \omega_m = \frac{r_l}{r_m} \omega_l$$

- Derivación de la Inercia Reflejada

Partimos de la condición de desplazamiento tangencial:

$$
r_l \theta_l = r_m \theta_m \quad \Rightarrow \quad \omega_m = \frac{r_l}{r_m} \omega_l
$$

Usando dinámica rotacional en la carga:

$$
T_l = J_{\text{load}} \, \ddot{\theta}_l
$$

Como los torques se reflejan por la relación de radios:

$$
\frac{r_l}{r_m} T_m = J_{\text{load}} \, \ddot{\theta}_l
$$

Ahora, usamos la relación de aceleraciones angulares:

$$
\ddot{\theta}_l = \frac{r_m}{r_l} \ddot{\theta}_m
$$

Sustituyendo en la expresión de torque:

$$
T_m = J_{\text{load}} \left( \frac{r_m}{r_l} \right)^2 \ddot{\theta}_m
$$

Finalmente, definimos la **inercia reflejada** como:

$$
J_{\text{ref}} = J_{\text{load}} \cdot \left( \frac{r_m}{r_l} \right)^2
$$


Por lo tanto, definimos la inercia reflejada:

$$J_{\text{ref}} = J_{\text{load}} \cdot N_{GB}^2$$

Cuando hay una reducción (es decir, el engranaje del motor es más pequeño que el de la carga), el motor siente una inercia menor.

## 11. Eficiencia en Sistemas de Movimiento

- Definición General

La eficiencia $$\eta$$ se define como la relación entre la potencia de salida y la potencia de entrada:

$$
\eta = \frac{P_{\text{out}}}{P_{\text{in}}}
$$

Donde la potencia mecánica es:

$$
P = T \cdot \omega
$$

- $$T$$: Torque (Nm)
  
- $$\omega$$: Velocidad angular (rad/s)

- Aplicación al Torque y a la Inercia Reflejada

Relación entre potencias en carga y motor considerando eficiencia:

$$
T_l \cdot \omega_l = \eta \cdot T_m \cdot \omega_m
$$

Despejando el torque del motor:

$$
T_m = \frac{T_l}{\eta \cdot N_{GB}}
$$

Donde:

- $$N_{GB} = \frac{\omega_l}{\omega_m}$$: Relación de engranaje
  
- $$eta \in (0, 1]$$: Eficiencia del sistema

- Inercia Reflejada con Eficiencia

Cuando hay engranajes con pérdidas:

$$
J_{\text{ref}} = \frac{J_{\text{load}}}{\eta} \cdot N_{GB}^2
$$

- Interpretación:
 
Una menor eficiencia implica mayor inercia aparente en el eje del motor → se requiere más esfuerzo para mover la misma carga.

- Valores Típicos de Eficiencia

 <div align="center">
   
| Calidad del Sistema | Rango de Eficiencia \( \eta \) | Comentario                         |
|---------------------|-------------------------------|------------------------------------|
| Baja calidad        | 0.60 – 0.75                   | Alto rozamiento                    |
| Media calidad       | 0.80 – 0.90                   | Común en la industria              |
| Alta calidad        | 0.95 – 0.98                   | Sistemas bien diseñados/lubricados|
| Ideal (teórico)     | 1.00                          | Sin pérdidas (imposible)           |

</div>

## 12. Inercia Total en Sistemas Mecánicos

- ¿Qué es la inercia total?

La inercia total $$J_{\text{total}}$$ es la suma de todas las inercias relevantes reflejadas al eje del motor. Representa el esfuerzo total que el motor debe vencer para generar movimiento.

$$
J_{\text{total}} = J_m + J_{\text{on motor shaft}} + J_{\text{ref}}
$$

- ¿Por qué es importante considerar todos estos elementos?

- **Diseño de controladores**
  
  Es clave conocer cuánta inercia debe acelerarse para diseñar una respuesta dinámica precisa (por ejemplo, PI, PID, control óptimo...).

- **Selección del motor**
  
  Subestimar la inercia puede causar sobrecalentamiento, inestabilidad o bajo rendimiento.

- **Análisis de arranque/parada**
  
  Una inercia total alta implica mayor torque necesario en transitorios.

- **Aplicaciones de alta masa o velocidad**
  
  Elementos como ruedas motrices o acoplamientos suelen tener gran inercia, impactando significativamente el diseño del sistema.

💡**Ejemplo 4:** Cálculo de la Inercia Total Vista por el Motor

Determinar la inercia total reflejada al eje del motor considerando todos los elementos del sistema de transmisión mostrado.

 <div align="center">
  <img src="Imágenes_Corte_2/Clase%20%239/Ejemplo_Coupling.png" alt="Figura de prueba" width="300">
  <p><b>Figura 10.</b>Gif Ejempl0 4</p>
</div>

- Sistema Analizado

El sistema está compuesto por:

- Motor con inercia $$J_m$$
    
- Acople (coupling) con inercia $$J_{\text{coupling}}$$
  
- Rueda motriz del engranaje (unida directamente al motor) con inercia $$J_{\text{mg}}$$ç
  
- Rueda seguidora del engranaje con inercia $$J_{\text{lg}}$$
    
- Carga conectada al engranaje con inercia $$J_{\text{load}}$$  

Se conectan mediante:

- Relación de engranaje: $$N_{GB} = \frac{r_l}{r_m}$$
  
- Eficiencia mecánica del sistema: $$\eta \in (0, 1]$$

- Fórmulas Utilizadas

- Inercia reflejada al eje del motor
  
Se considera que la rueda seguidora y la carga* están después del engranaje, por lo tanto:

$$
J_{\text{ref}} = \frac{1}{\eta} \cdot N_{GB}^2 \cdot \left( J_{\text{lg}} + J_{\text{load}} \right)
$$

- Inercia directa en el eje del motor

$$
J_{\text{on motor shaft}} = J_{\text{coupling}} + J_{\text{mg}}
$$

- Inercia total vista por el motor

Combinando todos los elementos:

$$
J_{\text{total}} = J_m + J_{\text{coupling}} + J_{\text{mg}} + \frac{1}{\eta} \cdot N_{GB}^2 \cdot \left( J_{\text{lg}} + J_{\text{load}} \right)
$$

## 13. Relación de Inercia $$J_R$$

Definición

La relación de inercia compara la inercia total que el motor debe mover (reflejada al eje del motor) con la inercia del rotor del motor:

$$
J_R = \frac{J_{\text{on motor shaft}} + J_{\text{ref}}}{J_m}
$$

Donde:

- $$J_R$$: Relación de inercia (adimensional)  
- $$J_{\text{on motor shaft}}$$: Inercia directa en el eje del motor (acople, rueda motriz, etc.)  
- $$J_{\text{ref}}$$: Inercia reflejada al eje del motor (de la carga y engranajes)  
- $$J_m$$: Inercia del rotor del motor  

- Interpretación Física

<div align="center">
  
| Valor de $$J_R$$ | Interpretación |
|-------------------|----------------|
| $$J_R \approx 1$$ | El motor mueve una inercia similar a la suya propia |
| $$J_R > 3$$       | El sistema está fuertemente cargado (el motor debe mover mucha masa) |
| $$J_R < 1$$       | El sistema es muy ligero en comparación con el motor |

</div>

También puede interpretarse como un porcentaje relativo.

Por ejemplo, si $$J_R = 4$$, significa que el motor está moviendo 4 veces su propia inercia.

- Expresión Extendida

Considerando que la inercia reflejada incluye distintos componentes (como engranajes y carga):

$$
J_R = \frac{J_{\text{on motor shaft}} + J_{\text{load} \to M} + J_{\text{GB} \to M}}{J_m}
$$

Donde:

- $$J_{\text{load} \to M}$$: Carga reflejada al eje del motor
  
- $$J_{\text{GB} \to M}$$: Caja de engranajes reflejada al eje del motor  


💡**Ejemplo 5:**

Un motor tiene una inercia de:

$$
J_m = 0.02 \, \text{kg} \cdot \text{m}^2
$$

La inercia total reflejada al eje del motor es:

$$
J_{\text{on motor shaft}} + J_{\text{ref}} = 0.06 \, \text{kg} \cdot \text{m}^2
$$

Entonces:

$$
J_R = \frac{0.06}{0.02} = 3
$$

Esto indica que la carga representa 300% de la inercia del motor, lo cual puede ser aceptable o no, dependiendo del fabricante y del tipo de control requerido.

💡**Ejemplo 6:**

 <div align="center">
  <img src="Imágenes_Corte_2/Clase%20%239/Ejemplo_6_load.png" alt="Figura de prueba" width="300">
  <p><b>Figura 11.</b>Gif Ejempl0 6</p>
</div>

- Convertir Unidades

La inercia del engranaje está dada en $$\text{kg} \cdot \text{cm}^2$$. Se convierte a $$\text{kg} \cdot \text{m}^2$$:

$$
J_{GB} = 0.15\, \text{kg} \cdot \text{cm}^2 = 0.15 \times 10^{-4} = 1.5 \times 10^{-5} \, \text{kg} \cdot \text{m}^2
$$

- Reflejar la Inercia de la Carga al Eje del Motor

La fórmula para reflejar una inercia a través de un engranaje con relación \( N \) (reducción salida/entrada):

$$
J_{\text{load} \to M} = \frac{J_{\text{load}}}{N^2} = \frac{10 \times 10^{-4}}{5^2} = \frac{10 \times 10^{-4}}{25} = 4 \times 10^{-5} \, \text{kg} \cdot \text{m}^2
$$

- Reflejar la Inercia del Engranaje al Eje del Motor

Ya está dada como reflejada a la entrada (es decir, al eje del motor):

$$
J_{GB \to M} = 1.5 \times 10^{-5} \, \text{kg} \cdot \text{m}^2
$$

- Calcular la Relación de Inercia \( J_R \)

Usamos la fórmula completa:

$$
J_R = \frac{J_{\text{load} \to M} + J_{GB \to M}}{J_m}
$$

Sustituyendo valores:

$$
J_R = \frac{4 \times 10^{-5} + 1.5 \times 10^{-5}}{1.5 \times 10^{-5}} = \frac{5.5 \times 10^{-5}}{1.5 \times 10^{-5}} = 3.67
$$


💡**Actividad 1:**

<div align="center">
  <img src="Imágenes_Corte_2/Clase%20%239/Actividad_Clase_9.png" alt="Figura de prueba" width="300">
  <p><b>Figura 12.</b>Actividad</p>
</div>

- Datos del sistema

- Engranaje 651: $$N_{651} = \frac{60}{30} = 2$$

- Engranaje 652: $$N_{652} = \frac{90}{30} = 3$$
  
- Inercia de la carga: $$J_{\text{load}} = 5 \times 10^{-4} \, \text{kg} \cdot \text{m}^2$$

- Inercia del motor: $$J_m = 3 \times 10^{-6} \, \text{kg} \cdot \text{m}^2$$

- Calcular la Relación de Transmisión Total

$$
N_{\text{total}} = N_{651} \times N_{652} = 2 \times 3 = 6
$$

- Reflejar la Inercia de la Carga al Eje del Motor

$$
J_{\text{ref}} = \frac{J_{\text{load}}}{N_{\text{total}}^2} = \frac{5 \times 10^{-4}}{(2 \times 3)^2} = \frac{5 \times 10^{-4}}{36} \approx 1.38 \times 10^{-5} \, \text{kg} \cdot \text{m}^2
$$

- Calcular la Relación de Inercia \( J_R \)

$$
J_R = \frac{J_{\text{ref}}}{J_m} = \frac{1.38 \times 10^{-5}}{3 \times 10^{-6}} \approx 4.6
$$

## 14. Mecanismo Polea-Correa

<div align="center">
  <img src="Imágenes_Corte_2/Clase%20%239/Poleas.png" alt="Figura de prueba" width="300">
  <p><b>Figura 13.</b>Poleas</p>
</div>

Un sistema polea-correa es un mecanismo que transmite movimiento rotacional entre dos ejes, utilizando:

- Dos poleas de diferentes radios.

- Una correa (lisa o dentada) que conecta ambas poleas.

La relación de radios determina la transformación de velocidad angular y torque entre los ejes conectados.

- Comportamiento Mecánico

- A diferencia de los engranajes, ambas poleas giran en el mismo sentido.

- La velocidad angular se transforma según la relación inversa de radios:

$$
\frac{\omega_2}{\omega_1} = \frac{r_1}{r_2}
\quad \Rightarrow \quad \text{Si una polea es más pequeña, gira más rápido.}
$$

- El torque se transforma de forma inversa a la velocidad angular:

$$
\frac{T_2}{T_1} = \frac{r_2}{r_1}
$$

## 15. Simulación en Simscape: Sistema Polea-Correa con Motor DC

<div align="center">
  <img src="Imágenes_Corte_2/Clase%20%239/Simulación_simscape_Poleas.png" alt="Figura de prueba" width="700">
  <p><b>Figura 14.</b>imulación en Simscape: Sistema Polea-Correa con Motor DC</p>
</div>

- Componentes del Sistema

- Motor DC Moog C23L33W10: Motor alimentado con 24 V DC, genera una velocidad de salida de 11,500 rpm.

- Sistema Polea-Correa:

  - Compuesto por dos bloques de polea configurables.

  - Correa modelada como bloque adicional, para simular comportamiento realista (elasticidad, deslizamiento, etc.).
- Medidores de velocidad:

  - $$\omega_{\text{motor}} = 11{,}500 \, \text{rpm}$$

  - $$\omega_{\text{salida}} = -24{,}642.86 \, \text{rpm}$$

- Relación de Transmisión

La relación de velocidades observada es:

$$
\frac{\omega_{\text{salida}}}{\omega_{\text{motor}}} = \frac{-24{,}642.86}{11{,}500} \approx -2.14
$$

Esto implica:

- La salida gira en sentido opuesto al motor.

- La relación de transmisión efectiva es de aproximadamente 2.14:1 (inversa), lo que sugiere una diferencia de radios entre poleas.


- Configuraciones Avanzadas en Simscape

Los bloques de Belt Pulley permiten ajustar:

- Tamaño de poleas: Define directamente la relación de transmisión.

- Forma de las poleas: Lisos, acanalados, dentados, etc.

- Tipo de correa: Elástica, rígida, con o sin deslizamiento.

- Deslizamiento relativo: Para simular pérdida de adherencia bajo carga.

- Punto de ruptura / fatiga: Útil para análisis de durabilidad y fallas.

## 16. Configuración del Bloque: Acoplamiento (Belt Pulley)

<div align="center">
  <img src="Imágenes_Corte_2/Clase%20%239/Poleas_Ya_casi.png" alt="Figura de prueba" width="700">
  <p><b>Figura 15.</b>Configuración del Bloque: Acoplamiento (Belt Pulley)</p>
</div>

<div align="center">
  
| Parámetro              | Opciones disponibles           | Descripción                                                                 |
|------------------------|-------------------------------|-----------------------------------------------------------------------------|
| **Tipo de correa**     | Ideal (No slip), Realista     | Define si hay o no deslizamiento entre la correa y las poleas.             |
| **Dirección**          | Same direction, Opposite direction | Sentido de rotación entre poleas. Afecta el signo de la salida.       |
| **Tensión máxima**     | Valor numérico (N)            | Límite de tracción antes del fallo del material.                           |
| **Advertencia de tensión** | Activada / Desactivada     | Informa si se supera la tensión máxima configurada en la simulación.       |

</div>

- Configuración del Bloque: Polea

<div align="center">
  
| Parámetro            | Unidad / Opciones               | Descripción                                                                 |
|----------------------|----------------------------------|-----------------------------------------------------------------------------|
| **Radio de la polea** | m, cm, etc.                     | Determina la relación de transmisión entre poleas.                         |
| **Fricción viscosa** | N·m/(rad/s)                      | Modela pérdida de energía por fricción en cojinetes o ejes.                |
| **Inercia**          | Activada / Desactivada (No inertia) | Considera el momento de inercia de la polea en el sistema. Afecta torque. |

</div>

- Configuración del Bloque: Correa

<div align="center">
  
| Parámetro           | Opciones / Valores               | Descripción                                                                |
|---------------------|----------------------------------|----------------------------------------------------------------------------|
| **Tipo de correa**   | Ideal, trapezoidal, dentada      | Influye en el contacto con la polea y en el comportamiento dinámico.      |
| **Masa de la correa**| kg                               | Contribuye al momento de inercia reflejado en el sistema.                 |
| **Elasticidad**      | N/m                              | Modela el comportamiento elástico de la correa bajo carga.                |
| **Amortiguamiento**  | N·s/m                            | Simula disipación de energía por vibraciones.                             |
| **Tensión máxima**   | N                                | Valor umbral en el que la correa "falla" o se rompe en simulación.        |

</div>

- Tabla de Relación de Giro entre Poleas

<div align="center">
  
| Configuración       | Polea motriz (entrada) | Polea seguidora (salida) | Sentido resultante  |
|---------------------|------------------------|---------------------------|----------------------|
| **Same direction**   | $$+\omega\$$            | $$+\omega\$$               | Mismo sentido        |
| **Opposite direction** | $$+\omega\$$         | $$-\omega\$$             | Sentido contrario     |

</div>

<div align="center">
  <img src="Imágenes_Corte_2/Clase%20%239/Simulacion_Poleas.png" alt="Figura de prueba" width="700">
  <p><b>Figura 17.</b>Simulación</p>
</div>

<div align="center">
  <img src="Imágenes_Corte_2/Clase%20%239/Simulacion_xd.gif" alt="Figura de prueba" width="700">
  <p><b>Figura 16.</b>Simulación</p>
</div>

## Conclusiones

1. La relación de transmisión en sistemas polea-correa funciona igual que en engranajes: la velocidad angular y el torque se relacionan de forma inversa según los radios, pero ambas poleas giran en el mismo sentido (salvo que se indique lo contrario en simulación).

2. Simulaciones en Simscape permiten representar de manera precisa un sistema mecánico, incluyendo parámetros como fricción, inercia, elasticidad de la correa, y configuración del sentido de giro.

3. La correcta configuración de los bloques (polea, correa, acoplamiento) es esencial para obtener resultados realistas, como velocidad de salida y tensiones en la correa, lo cual es útil para validación y predicción de fallos.


## Referencias

[1] S. Niku, Introduction to Robotics: Analysis, Control, Applications, 4th ed., Wiley, 2023.

[2] R. Kelly, D. Santibáñez, and L. F. Reyes, Control of Robot Manipulators in Joint Space, 2nd ed., Springer, 2021.

[3] M. Spong, S. Hutchinson, and M. Vidyasagar, Robot Modeling and Control, 2nd ed., Wiley, 2020.

[4] J. E. Cote B., Perfiles de Movimiento, diapositivas de clase, 9° semestre, Universidad ECCI, 2025.
