# Control por Rechazo Activo de Perturbaciones (ADRC)

En esta sesión se aborda una técnica de control moderna conocida como control por rechazo activo de perturbaciones (ADRC, por sus siglas en inglés). Esta metodología se presenta como una alternativa a técnicas tradicionales como el control PID, con el objetivo de mejorar el desempeño del sistema ante incertidumbres y perturbaciones externas.

A diferencia de los enfoques clásicos, el ADRC se basa en el diseño de controladores en el espacio de estados, haciendo uso de observadores, pero con un enfoque que busca minimizar la dependencia del modelo del sistema. Esto permite que el controlador sea más robusto frente a imprecisiones en la modelación, y pueda gestionar de forma activa las perturbaciones y las incertidumbres del sistema.

El interés por esta técnica ha crecido en el ámbito de la investigación en control, ya que representa un paso hacia la creación de controladores que requieran la mínima información del modelo o incluso, en un futuro, lleguen a operar sin necesidad de conocer el modelo de la planta, adaptándose automáticamente a diferentes dinámicas.

## 1. ¿Qué es ADRC?

<div align="center">
  <img src="Imágenes_Corte_3/Clase%20%2312/Zhiqiang-Gao-png.png" alt="Figura de prueba" width="300">
  <p><b>Figura 1.</b>Zhiqiang Gao</p>
</div>

<div align="center">
  
| Concepto | Descripción breve |
|----------|-------------------|
| ADRC (Active Disturbance Rejection Control) | Técnica de control que rechaza activamente perturbaciones e incertidumbres del sistema. |
| ¿Por qué nace? | Para superar las limitaciones de los controladores PID, especialmente su fuerte dependencia del modelo. |
| Fundador | Propuesto por Zhiqiang Gao, investigador en tecnologías avanzadas de control en EE.UU. |

</div>

>**Nota:** Esta tabla resume los fundamentos y origen del ADRC como técnica moderna de control.


### ¿Cómo Funciona?

A diferencia del PID, ADRC incluye dentro del controlador un mecanismo para estimar y compensar todo aquello que no se conoce del modelo (perturbaciones, no linealidades, etc.).

En vez de luchar por tener el modelo perfecto del sistema, el ADRC asume que habrá errores, perturbaciones y no linealidades, y se adapta para corregirlos en tiempo real.

### Ventajas de ADRC

- Menor dependencia del modelo de la planta.  
- Rechazo no solo de perturbaciones, sino también de no linealidades complejas.  
- Controladores más robustos ante incertidumbre.  
- Ideal cuando no tenemos un modelo preciso o completo.

### Ejemplos en la Industria

<div align="center">
  
| Sector | Ejemplo de aplicación del ADRC |
|--------|-------------------------------|
| Robótica | Control de brazos robóticos con alta variabilidad de carga. |
| Automotriz | Estabilización de vehículos ante cambios de terreno o clima. |
| Procesos industriales | Control de temperatura en hornos con fluctuaciones térmicas. |
| Aeroespacial | Corrección de trayectorias en drones con viento impredecible. |

</div>

> **Nota:** Esta tabla muestra cómo ADRC se aplica a distintos sectores industriales con alta incertidumbre.

### Comparación Rápida: PID vs ADRC

<div align="center">
  
| Característica | PID | ADRC |
|----------------|-----|------|
| Dependencia del modelo | Alta | Baja |
| Rechazo de perturbaciones | Limitado | Activo y predictivo |
| No linealidades | No las maneja bien | Las rechaza automáticamente |
| Robustez | Media | Alta ante incertidumbre y variaciones |

</div>

> **Nota:** Esta tabla compara de forma concisa las diferencias clave entre controladores PID y ADRC.

### Componentes clave

El ADRC se basa en dos grandes pilares:

<div align="center">
  
| Componente | Descripción |
|------------|-------------|
| Ley de control no lineal | Calculada a partir del error del sistema mediante funciones no lineales. |
| ESO – Observador de Estados Extendido | Un observador que va más allá de los estados típicos… ¡y predice el caos! |

</div>

> **Nota:** Esta tabla resume los elementos esenciales que forman el núcleo del control ADRC.


### ¿Qué hace el ESO?

El ESO es como un espía dentro del sistema que:

- Estima los estados normales del sistema.
  
- Estima las perturbaciones que afectan al sistema.
  
- Detecta dinámicas desconocidas y no linealidades.

Esto significa que ya no es necesario modelar matemáticamente todas las complejidades del sistema, porque el observador se encarga de descubrirlas en tiempo real.

### ¿Qué lo hace tan poderoso?

- No necesitas un modelo exacto.  

- El controlador se adapta a sistemas complejos o mal conocidos.
  
- Puedes controlar plantas no lineales como si fueran lineales.

## 2. Características Clave del ADRC (Gao, 2014)

### 2.1. No necesitas un modelo exacto

Solo necesitamos:

- Orden del sistema
  
💡Ejemplo 1:  Segundo orden en un sistema masa-resorte-amortiguador.

<div align="center">
  <img src="Imágenes_Corte_3/Clase%20%2312/Masa-resorte-amortigador.jpg" alt="Figura de prueba" width="500">
  <p><b>Figura 2.</b>Masa resorte amortigador</p>
</div>

- Ganancia nominal

💡Ejemplo 2: Ganancia estática que ya se conoce.

<div align="center">
  <img src="Imágenes_Corte_3/Clase%20%2312/Ganancias estaticas.webp" alt="Figura de prueba" width="500">
  <p><b>Figura 3.</b>Ganancia estática</p>
</div>

- No importa si la ganancia varía o es no lineal.
  
- El ESO se encarga de absorberlo todo como parte de la perturbación.

#### Resumen visual:

<div align="center">
  
| ¿Qué tan bien conozco mi planta? | ¿Puedo usar ADRC? |
|----------------------------------|-------------------|
| Modelo incompleto             | Sí             |
| No linealidades raras         | Sí             |
| Dinámica desconocida          | Sí             |

</div>

> **Nota:**ADRC permite el control efectivo incluso cuando la información del sistema es limitada o inexacta.

### 2.2 Cancela perturbaciones + incertidumbre total

ADRC agrupa todo lo desconocido (no linealidades, variaciones, señales externas) en una sola variable: Perturbación total.

<div align="center">
  <img src="Imágenes_Corte_3/Clase%20%2312/Peturbacion.jpeg" alt="Figura de prueba" width="500">
  <p><b>Figura 4.</b>Perturbaciones</p>
</div>

Esto se traduce en:

- Menos modelado matemático.
   
- Un sistema controlable → puedemos hacer que todo "indeseado" tienda a cero.

#### ¿Qué logra esto?

El sistema rechaza cualquier cosa que lo aleje del comportamiento deseado: 

- Externo (perturbaciones del entorno)
  
- Interno (modelo inexacto)

#### Conceptos clave:

>🔑 *Perturbaciones externas:* Ruido, cambios del entorn.

>🔑 *Incertidumbre:* Parámetros desconocidos del modelo.


### 2.3 Hace que el sistema se comporte como tú quieres

- Objetivo del controlador: Forzar al sistema real a parecerse a uno ideal y más simple.

Esto implica:

- El error tiende a cero automáticamente

- No necesitas acción integral adicional
  
- Solo usas ganancias proporcionales, ¡mucho más fácil de ajustar!

## 3. LADRC: Control Lineal por Rechazo Activo de Perturbaciones

Una versión más simple y práctica del ADRC, propuesta por Gao en 2003.

### ¿Qué es LADRC?

>🔑 *LADRC:* Linear Active Disturbance Rejection Control.

Es una versión lineal del ADRC que:

Reemplaza la parte no lineal del controlador y el observador por herramientas linealesy más simples de implementar:

<div align="center">
  
| Componente | En ADRC | En LADRC |
|------------|---------|----------|
| Controlador | Función no lineal del error | Realimentación de estados |
| Observador | Observador extendido no lineal (ESO) | Observador tipo Luenberger |

</div>

> **Nota:** LADRC simplifica el diseño del ADRC usando solo herramientas lineales.

### ¿Pero puede controlar sistemas no lineales?

LADRC también funciona con sistemas no lineales, gracias a que:

- Estima y cancela perturbaciones.
  
- Rechaza no linealidades en tiempo real.

- No se limita como el PID, que solo trabaja bien en rangos casi lineales.

### Comparación 

<div align="center">
  
| Característica | PID | LADRC |
|----------------|-----|--------|
| Requiere modelo preciso | Sí |  No |
| Maneja no linealidades |  Difícil |  Sí, mediante estimación |
| Observador incluido |  No | Sí (Luenberger) |
| Fácil de implementar | Alta experiencia requerida |  Más accesible |
| Rechaza perturbaciones |  Parcialmente |  Activamente |

</div>

> **Nota:** Esta tabla destaca las ventajas prácticas de LADRC frente al PID tradicional.


### ¿Por qué usar LADRC?

- Reduce complejidad matemática del ADRC original.
  
- Usa herramientas de control clásico: realimentación + observador Luenberger.

- Ideal para aplicaciones reales con recursos limitados.

## 4 Estructura del Controlador LADRC

<div align="center">
  <img src="Imágenes_Corte_3/Clase%20%2312/Componentes ADRC.png" alt="Figura de prueba" width="500">
  <p><b>Figura 5.</b>Estructura del Controlador LADR</p>
</div>

### Componentes del esquema

<div align="center">
  
| Bloque                            | Función |
|----------------------------------|---------|
| Generador de trayectorias | Calcula los setpoints (posición, velocidad, aceleración, etc.) según la cinemática del sistema. En este curso, solo se usará la posición como referencia. |
| Controlador                 | Usa los valores del generador de trayectorias y las estimaciones del observador (estados z₁, z₂, ..., zₙ) para generar una acción de control **u₀**. |
| Observador de Estados Extendido (ESO) | Estima los estados del sistema y una perturbación total (**zₙ₊₁**) que incluye: - Perturbaciones, - No linealidades, - Errores de modelo. |
| Lazo interno de rechazo de perturbaciones | La señal **u₀** se corrige restando **zₙ₊₁**, y se divide entre la ganancia estática del sistema **b₀**. Esto genera la señal de entrada real **u** que actúa sobre la planta. |

</div>

> **Nota:** Cada bloque cumple una función precisa dentro de un esquema modular de control.

### Esquema tipo cascada (en espacio de estados)

Este diagrama es análogo a un esquema PID en cascada, pero:

- El controlador externo entrega la acción primaria (**u₀**).
  
- El lazo interno, basado en el ESO, rechaza perturbaciones.
  
- Todo se implementa en espacio de estados, no con bloques tipo PID.

- **zₙ₊₁** representa el **estado extendido** que agrupa todas las perturbaciones y errores dinámicos.
  
- **b₀** (ganancia estática o crítica) se usa para **compensar** el efecto de perturbaciones estimadas.

Este controlador se adapta muy bien a **sistemas rápidos** (con tiempos de respuesta cortos):

- Conversores de potencia (energías alternativas)
  
- Control de movimiento (servomotores, inversión rápida de giro)

### Ejemplos reales:

- Central eléctrica en China

<div align="center">
  <img src="Imágenes_Corte_3/Clase%20%2312/ThreeGorgesDam-China2009.jpg" alt="Figura de prueba" width="500">
  <p><b>Figura 6.</b>Central eléctrica en China</p>
</div>

- Controladores industriales de Allen Bradley (Rockwell Automation) usan LADRC internamente

<div align="center">
  <img src="Imágenes_Corte_3/Clase%20%2312/Controladores industriales de Allen Bradley (Rockwell Automation).jpeg" alt="Figura de prueba" width="500">
  <p><b>Figura 7.</b>Controladores industriales de Allen Bradley (Rockwell Automation)</p>
</div>

### ¿Por qué usar este esquema?

<div align="center">
  
| Ventaja                             | Detalle |
|-------------------------------------|---------|
|  Alta capacidad de rechazo de perturbaciones | Estimación y compensación activa |
| Respuesta muy rápida              | Ideal para sistemas con dinámica veloz |
| Generalizable                    | Se puede aplicar a muchos tipos de procesos |
| Modular                          | Cada componente cumple una función clara y reutilizable |

</div>

> **Nota:** LADRC logra un equilibrio entre simplicidad, robustez y velocidad de respuesta.

💡Ejemplo 3: Modelo No Lineal: Tanque con Forma Irregular

Transformar un modelo no lineal en una estructura que permita controlarlo como si fuera lineal, facilitando el diseño de controladores como LADRC.

<div align="center">
  <img src="Imágenes_Corte_3/Clase%20%2312/Supongamos.png" alt="Figura de prueba" width="500">
  <p><b>Figura 6.</b>Tanque con Forma Irregular</p>
</div>

### Sistema Físico

- Sistema: Tanque con forma irregular
  
- Entrada: `u` (flujo de entrada)
  
- Salida: `y = h` (altura del líquido)  

### Idea 

Un sistema no lineal puede separarse en dos partes:

- Parte lineal (ej. `K·u`)
  
- Parte no lineal (ej. `a·√(2gh) / A(h)`)

### Ecuaciones del Sistema

### Modelo dinámico (balance de masa):

$$
\frac{d}{dt} \left( \int_0^h A(h) \, dh \right) = u - a \sqrt{2gh}
$$

Aplicando el teorema fundamental del cálculo:

$$
A(h) \cdot \dot{h} = u - a \sqrt{2gh}
$$

Despejando $$\(\dot{h}\)$$:

$$
\dot{h} = \frac{1}{A(h)}u - \frac{a \sqrt{2gh}}{A(h)}
$$

### Interpretación de la Ecuación

<div align="center">
  
| Término | Significado |
|--------|-------------|
| $$\(\frac{1}{A(h)}u\)$$ | Parte que se puede considerar como ganancia variable del sistema |
| $$\(\frac{a \sqrt{2gh}}{A(h)}\)$$ | Perturbación no lineal que depende de la forma del tanque y la altura |

</div>

> **Nota:** La salida no responde linealmente ante entradas constantes debido a la forma del tanque.

### Aproximación Lineal

Si asumimos:

- $$\( A(h) = \text{constante} \)$$
  
- $$\( \sqrt{2gh} \approx \text{constante} \)$$

Entonces, el modelo se simplifica a:

$$
\dot{h} = K \cdot u + h
$$

### Gráfico (inferido del comportamiento)

- Línea azul: Entrada constante $$\(u\)$$.
    
- Línea negra: Comportamiento de $$\(h\)$$ (no lineal), que primero disminuye y luego aumenta → evidencia de que el sistema no responde linealmente.

### Conclusiones

- Es común separar modelos no lineales en partes que sí se pueden tratar como lineales.
  
- En este caso, la forma irregular del tanque hace que el área $$\(A(h)\)$$ sea variable, lo que complica el modelo.
  
- En modelos más complejos, esta no linealidad se absorbe en un estado adicional (como **zₙ₊₁** en LADRC), lo que permite ignorarla explícitamente al diseñar el controlador.

## 4. NADRC: Nonlinear Active Disturbance Rejection Control

Rechazar perturbaciones y no linealidades agrupándolas en una función desconocida $$\( f \)$$, que será estimada en tiempo real por un observador.

### Modelo Inicial del Sistema

Ecuación diferencial de segundo orden:

$$
\ddot{y} = -a_1 \dot{y} - a_0 y + b u
$$

Donde:

- $$\( y \)$$: salida del sistema
    
- $$\( u \)$$: entrada de control
   
- $$\( a_0, a_1 \)$$: parámetros del sistema
    
- $$\( b \)$$: ganancia del sistema


### Representación en Espacio de Estados

Definimos los estados:

$$
x_1 = y, \quad x_2 = \dot{y}
$$

Entonces, el sistema se reescribe como:

$$
\begin{cases}
\dot{x}_1 = x_2 \\
\dot{x}_2 = -a_0 x_1 - a_1 x_2 + b u + w \\
y = x_1
\end{cases}
$$

$$\( w \)$$: representa perturbaciones externas o incertidumbre del modelo

### Suposición Clave en NADRC

Agrupamos todas las incertidumbres y no linealidades en una sola función:

$$
f = -a_0 x_1 - a_1 x_2 + (b - b_0)u + w
$$

Donde:

- $$\( b_0 \)$$: estimación de la ganancia (puede diferir de $$\( b \))$$
  
- $$\( f \)$$: función que representa todo lo **desconocido** del sistema:
  
  - Modelo inexacto
    
  - Perturbaciones externas
    
  - Variaciones paramétricas
    
  - No linealidades

### Ventaja del Enfoque NADRC

En lugar de conocer exactamente el modelo dinámico, NADRC:

1. Estima la función $$\( f \)$$ en tiempo real mediante un observador extendido.
   
3. Compensa activamente dicha perturbación en el lazo de control.

Esto permite que el sistema se comporte como si se conociera perfectamente, incluso si el modelo real es complejo o incierto.

##  Modelo del Sistema: Base para NADRC

### Ecuación Diferencial del Sistema

Se parte de una ecuación de segundo orden:

$$
\ddot{y} = -a_1 \dot{y} - a_0 y + b u
$$

Donde:

- $$\( y \)$$: salida del sistema
  
- $$\( u \)$$: entrada (control)
  
- $$\( a_0, a_1 \)$$: parámetros conocidos del sistema
  
- $$\( b \)$$: ganancia del sistema

### Modelo en Espacio de Estados

Definimos los estados:

$$
x_1 = y, \quad x_2 = \dot{y}
$$

Entonces:

$$
\begin{cases}
\dot{x}_1 = x_2 \\
\dot{x}_2 = -a_0 x_1 - a_1 x_2 + b u + w \\
y = x_1
\end{cases}
$$

$$\( w \)$$: perturbación externa o incertidumbre del modelo

### Agrupación de Dinámicas Desconocidas

Se define:

$$
f = -a_0 x_1 - a_1 x_2 + (b - b_0)u + w
$$

Con esto, el modelo se reescribe como:

$$
\begin{cases}
\dot{x}_1 = x_2 \\
\dot{x}_2 = f + b_0 u \\
y = x_1
\end{cases}
$$

Donde:

- $$\( b_0 \)$$: estimación de la ganancia del sistema
  
- $$\( f \)$$: representa todas las incertidumbres y perturbaciones

### Modelo Extendido: Estado Adicional

Como $$\( f \)$$ es desconocida, se incluye como nuevo estado:

$$
x_3 = f
$$

Entonces, el modelo completo es:

$$
\begin{cases}
\dot{x}_1 = x_2 \\
\dot{x}_2 = x_3 + b_0 u \\
\dot{x}_3 = h \\
y = x_1
\end{cases}
$$

Este es el modelo extendido usado en NADRC. Se comporta como un sistema de orden 3.

## Observador de Estados Extendido (ESO)

Se diseña un observador para estimar los estados $$\( z_1, z_2, z_3 \)$$:

$$
\begin{cases}
\dot{z}_1 = z_2 - \beta_1 \gamma_1(e) \\
\dot{z}_2 = z_3 + b_0 u - \beta_2 \gamma_2(e) \\
\dot{z}_3 = - \beta_3 \gamma_3(e) \\
e = z_1 - y
\end{cases}
$$

Donde:

- $$\( \beta_i \)$$: ganancias del observador
  
- $$\( \gamma_i(e) \)$$: funciones no lineales del error $$\( e \)$$ (pueden ser lineales o de tipo sigmoidal, sat, etc.)
  
- $$\( e \)$$: error de estimación

### Ley de Control NADRC

La ley de control se define como:

$$
u = \frac{u_0 - z_3}{b_0}
$$

Esto compensa activamente la perturbación estimada $$\( z_3 \)$$.

### Resultado: Sistema Compensado

Sustituyendo en el modelo:

$$
\begin{cases}
\dot{x}_1 = x_2 \\
\dot{x}_2 = u_0 \\
y = x_1
\end{cases}
$$

Ahora el sistema se comporta como un doble integrador ideal, libre de perturbaciones

### Control No Lineal en NADRC: Función `fal()`

### Ley de Control No Lineal

Cuando se aplica NADRC no lineal, la señal de control auxiliar $$\( u_0 \)$$ no es una función lineal del error. En su lugar, se utiliza la función `fal()`:

$$
u_0 = k_1 \cdot \text{fal}(r_1 - z_1, \alpha_1, \delta) + k_2 \cdot \text{fal}(r_1 - z_2, \alpha_2, \delta)
$$

Donde:

- $$\( r_1 \)$$: referencia deseada.
  
- $$\( z_1, z_2 \)$$: estimaciones del estado (posición y velocidad).
  
- $$\( k_1, k_2 \)$$: ganancias del controlador.
  
- `fal`: función no lineal suavizada.
  
- $$\( \alpha_1, \alpha_2 \in (0,1) \)$$: determinan el grado de no linealidad.
  
- $$\( \delta \)$$: umbral de transición entre linealidad y no linealidad.

### Definición de la Función `fal`

La función `fal` se define por tramos como:

$$
\text{fal}(\tilde{e}, \alpha, \delta) =
\begin{cases}
\frac{\tilde{e}}{\delta^{1 - \alpha}}, & \text{si } |\tilde{e}| \leq \delta \\
|\tilde{e}|^{\alpha} \cdot \text{sign}(\tilde{e}), & \text{si } |\tilde{e}| > \delta
\end{cases}
$$

Donde:

- $$\( \tilde{e} \)$$: error (por ejemplo, $$\( r_1 - z_1 \) o \( r_1 - z_2 \))$$.
  
- $$\( \text{sign}(\cdot) \)$$: función signo.


### Ventajas de Usar `fal()`

- Respuesta Suavizada : Evita saltos bruscos o "chattering", típicos de funciones discontinuas como `sign()`.
  
- Robustez No Lineal: Mejora el comportamiento ante no linealidades estructurales y perturbaciones suaves.
  
- Control Fino en Errores Pequeños: El controlador actúa con mayor suavidad cuando el error es pequeño, evitando sobrecompensaciones.
  
- Ajuste Flexible: Los parámetros $$\( \alpha \)$$ y $$\( \delta \)$$ permiten personalizar el comportamiento del controlador.







