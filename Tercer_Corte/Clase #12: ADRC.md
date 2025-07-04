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

## 5. L-ADRC (Control Activo de Perturbaciones Lineal)

### Observador de Estados Extendido Lineal (ESO)

El ESO lineal* permite estimar los estados del sistema y la perturbación total $$\( h \)$$, con la siguiente dinámica:

$$
\begin{cases}
\dot{z}_1 = z_2 + L_1 e \\
\dot{z}_2 = z_3 + b_0 u + L_2 e \\
\dot{z}_3 = L_3 e \\
e = y - z_1
\end{cases}
\quad \text{donde} \quad y = x_1
$$

Estimaciones:

- $$\( z_1 \approx x_1 \)$$ (posición)
  
- $$\( z_2 \approx x_2 \)$$ (velocidad)
  
- $$\( z_3 \approx h \)$$ (perturbación total)

### Modelo del Sistema Extendido

Incluye la perturbación como una tercera variable de estado:

$$
\begin{cases}
\dot{x}_1 = x_2 \\
\dot{x}_2 = x_3 + b_0 u \\
\dot{x}_3 = h \\
y = x_1
\end{cases}
$$

Esto convierte el sistema en un modelo lineal de orden 3 con dinámica accesible a control.

### Ley de Control Lineal

La señal de control auxiliar $$\( u_0 \)$$ se calcula como:

$$
u_0 = k_1 (\tilde{r} - z_1) - k_2 z_2
$$

Donde:

- $$\( \tilde{r} \)$$: referencia deseada.
  
- $$\( z_1, z_2 \)$$: estimaciones de los estados reales.
  
- $$\( k_1, k_2 \)$$: ganancias de retroalimentación.

### Interpretación del Controlador

- $$\( \tilde{r} - z_1 \)$$: error de posición.
  
- $$\( z_2 \)$$ : velocidad estimada, que se usa para anticiparse a cambios.
  
- $$\( z_3 \)$$: perturbación total estimada, que se elimina con la ley:

$$
u = u_0 - \frac{z_3}{b_0}
$$

### Ventajas del L-ADRC

<div align="center">
  
| Característica                 | Ventaja                                     |
|-------------------------------|---------------------------------------------|
| Modelo reducido             | No necesita conocer todos los parámetros    |
| Rechazo activo de perturbaciones | Estima y cancela \( h \) en tiempo real      |
| Control lineal              | Simple de implementar y sintonizar          |
| Estabilidad robusta        | Frente a incertidumbre y ruido              |
| ESO de orden 3              | Permite mayor observabilidad y compensación |

</div>

L-ADRC ofrece una solución efectiva y linealmente implementable para sistemas con perturbaciones desconocidas y modelos incompletos.

## 6. Planteamiento General del L-ADRC

<div align="center">
  <img src="Imágenes_Corte_3/Clase%20%2312/Planteamiento ADRC.png" alt="Figura de prueba" width="500">
  <p><b>Figura 7.</b>Planteamiento pngr</p>
</div>

### Ecuación Base del Sistema

La dinámica del sistema se expresa de forma general como:

$$
y^{(n)}(t) = \kappa(x) u(t) + \xi(t)
$$

Donde:

<div align="center">
  
| Símbolo        | Significado                                                                 |
|----------------|------------------------------------------------------------------------------|
| $$\( y^{(n)}(t) \)$$ | Derivada de orden \( n \) de la salida \( y(t) \)                          |
| $$\( \kappa(x) \)$$  | Función de ganancia (en L-ADRC se aproxima por una constante \( b_0 \))    |
| $$\( u(t) \)$$       | Entrada de control                                                         |
| $$\( \xi(t) \)$$     | Perturbación total generalizada (dinámicas no modeladas, ruido, etc.)      |
</div>

### ¿Qué representa $$\( \xi(t) \)$$?

La perturbación $$\( \xi(t) \)$$ agrupa todo lo desconocido del sistema, incluyendo:

- No linealidades
  
- Incertidumbre del modelo
  
- Perturbaciones externas
  
- Dinámicas internas no modeladas

El objetivo de L-ADRC es estimar y compensar esta perturbación en tiempo real.

### Flujos clave en L-ADRC

El control L-ADRC puede visualizarse como un sistema de bloques con funciones especializadas:

<div align="center">
  
| Bloque     | Función                                                                 |
|------------|--------------------------------------------------------------------------|
|  Estimator  | Estima los estados reales y la perturbación total \( \xi(t) \)         |
| Rejector   | Cancela la perturbación estimada \( \xi(t) \) en la señal de control    |
| Controller | Aplica un controlador lineal (como PD o PID) sobre señales estimadas   |
| Process    | Representa al sistema físico real, sujeto a incertidumbre y perturbación |

</div>

Transformar un sistema con incertidumbre, no linealidades y perturbaciones en uno que se comporte como un integrador puro, lo que facilita su control mediante leyes lineales clásicas.

$$
\text{Sistema original (no lineal, perturbado)} \quad \longrightarrow \quad \text{Integrador controlable ideal}
$$

## ADRC - Observador de Estados

<div align="center">
  <img src="Imágenes_Corte_3/Clase%20%2312/bservador de estados.png" alt="Figura de prueba" width="500">
  <p><b>Figura 8.</b>Observador de Estados.png</p>
</div>

### ¿Qué es un Observador de Estados?

>🔑 *Un observador de estados:* es una herramienta matemática que permite estimar las variables internas de un sistema dinámico a partir de la salida medida y de un modelo del sistema.

### Ecuaciones Clave

<div align="center">

| Concepto         | Ecuación                                               | Descripción                                           |
|------------------|--------------------------------------------------------|-------------------------------------------------------|
| Estado real     |$$\( x_{k+1} = A x_k + B u_k \)$$                          | Evolución del sistema real                           |
| Estado estimado | $$\( \hat{x}_{k+1} = A \hat{x}_k + B u_k + L (y_k - \hat{y}_k) \)$$| Estimación basada en modelo + corrección del error   |

</div>

### Componentes clave de la estimación:

- 🔵 $$\( A \hat{x}_k + B u_k \)$$: Predicción del estado con el modelo del sistema.
  
- 🔴 $$\( L (y_k - \hat{y}_k) \)$$: Corrección del error entre salida real y estimada.


### Parámetros del Observador

<div align="center">

| Parámetro | Fórmula                      | Significado                                       |
|-----------|------------------------------|--------------------------------------------------|
| $$\( A_{ob} \)$$ | $$\( A - L C \)$$                  | Matriz de dinámica del observador                 |
| $$\( B_{ob} \)$$ | $$\( [B \quad L] \)$$              | Influencia de la entrada y corrección por error  |
| $$\( C_{ob} \)$$ | $$\( I_{n \times n} \)$$           | Salida igual al estado estimado (identidad)      |
| $$\( D_{ob} \)$$ | $$\( 0_{n \times m}, 0_{n \times p} \)$$ | No hay efecto directo de entrada o perturbación |

</div>

💡Ejemplo 4: Industria Automotriz

<div align="center">
  <img src="Imágenes_Corte_3/Clase%20%2312/vehículos autónomos.jpg" alt="Figura de prueba" width="500">
  <p><b>Figura 9.</b>vehículos autónomos</p>
</div>

En vehículos autónomos, algunas variables internas como la fuerza de fricción entre neumáticos y carretera no pueden medirse directamente.

Sin embargo, mediante un observador:

- Se mide la velocidad del vehículo.
  
- Se compara contra la respuesta esperada del modelo.
  
- Se estima la fuerza de fricción como una variable oculta (estado).

Así, el vehículo puede adaptarse al terreno sin necesidad de sensores adicionales, mejorando su capacidad de control en tiempo real.

## 7. ADRC: Estimación de Perturbaciones

### Modelo del sistema discreto con perturbación

Sistema original:

$$
\begin{cases}
x_{k+1} = A \cdot x_k + B \cdot u_k + F \cdot d_k \\
y_k = C \cdot x_k
\end{cases}
$$

Donde:

- $$\( x_k \)$$: estado del sistema
  
- $$\( u_k \)$$: entrada de control
  
- $$\( d_k \)$$: perturbación desconocida
  
- $$\( y_k \)$$: salida medida

Si la perturbación es constante:

$$
d_{k+1} = d_k
$$

Podemos redefinir el estado extendido como:

$$
x_a(k) = \begin{bmatrix} x(k) \\ d(k) \end{bmatrix}
$$

Y el sistema ampliado se convierte en:

$$
x_a(k+1) = A_a \cdot x_a(k) + B_a \cdot u(k)
$$

Donde:

$$
A_a = \begin{bmatrix} A & F \\ 0 & I \end{bmatrix}, \quad
B_a = \begin{bmatrix} B \\ 0 \end{bmatrix}
$$

La salida se define como:

$$
y(k) = \begin{bmatrix} C & 0 \end{bmatrix} \cdot x_a(k)
$$

## 8. ADRC – Observador Extendiendo al Estimador de Perturbaciones

<div align="center">
  <img src="Imágenes_Corte_3/Clase%20%2312/Estimacion de perturbaciones 1.png" alt="Figura de prueba" width="500">
  <p><b>Figura 10.</b>Estimacion de perturbaciones</p>
</div>

$$
\begin{cases}
x_{k+1} = A \cdot x_k + B \cdot u_k + F \cdot d_k \\
y_k = C \cdot x_k
\end{cases}
$$

Estimar no solo $$\( \hat{x}_k \)$$ (estado), sino también $$\( \hat{d}_k \)$$ (perturbación).

## Ampliando el sistema: agregamos la perturbación como estado

$$
x_a(k+1) = \begin{bmatrix} x(k+1) \\ d(k+1) \end{bmatrix} =
\begin{bmatrix}
A & F \\
0 & I
\end{bmatrix}
x_a(k) +
\begin{bmatrix}
B \\
0
\end{bmatrix}
u(k)
$$

$$
y(k) = \begin{bmatrix} C & 0 \end{bmatrix} x_a(k)
$$

## Observador extendido: Estimando estado + perturbación

El diseño es igual al clásico observador de estados, pero con una dimensión extra por la perturbación.

Estima el vector ampliado:

$$
\hat{x}_a(k) =
\begin{bmatrix}
\hat{x}_k \\
\hat{d}_k
\end{bmatrix}
$$

## 10. ADRC - Control Activo de Rechazo de Perturbaciones

La dinámica del sistema se expresa así:

$$
y^{(n)}(t) = u(t) + \xi(t)
$$

Llevado a forma de espacio de estados:

$$
\dot{x} = A x + B (u(t) + \xi(t)) \\
y = C x
$$

<div align="center">
  
| Matriz | Significado               | Forma                                           |
|--------|---------------------------|-------------------------------------------------|
| A      | Matriz del sistema        | Matriz de cambio de estados (tipo cadena)      |
| B      | Entrada + perturbación    | Última fila es 1                                |
| C      | Salida                    | Solo mide la primera variable                   |

</div>

### Observador de Luenberger Extendiendo ADRC

Se construye un observador para estimar el estado y la perturbación al mismo tiempo.

Error de estimación:

$$
\tilde{e}_y = y - \hat{y}
$$

Forma extendida del observador:

$$
\dot{\hat{x}}_\xi = A_\xi \hat{x}_\xi + B_\xi u + \lambda_\xi \tilde{e}_y
$$

<div align="center">
  
| Elemento   | ¿Qué es?              | ¿Qué hace?                                                |
|------------|------------------------|------------------------------------------------------------|
| $$\( A_\xi \)$$ | Matriz extendida       | Considera variables + perturbación                         |
| $$\( B_\xi \)$$ | Entrada extendida      | Acomoda el mismo \( u \) para más estados                 |
| $$\( \lambda_\xi \)$$ | Ganancias del observador | Ajustan la velocidad y precisión de la estimación |
</div>

Recoemdacione

- Con 2 estados es suficiente para motores.
  
- Lo importante es saber calcular los $$\( \lambda \) (o \( K_f \))$$.


### Dinámica del Error y Polinomio de Hurwitz

Restando las ecuaciones, se obtiene la dinámica del error:

$$
\tilde{e}_y^{(n+m)} + \lambda_{n+m-1} \tilde{e}_y^{(n+m-1)} + \cdots + \lambda_1 \dot{\tilde{e}}_y + \lambda_0 \tilde{e}_y = \xi^{(m)}(t)
$$

Este comportamiento se describe con el polinomio característico:

$$
p(s) = s^{n+m} + \lambda_{n+m-1} s^{n+m-1} + \cdots + \lambda_1 s + \lambda_0
$$


$$
\dot{\hat{x}}_{\xi} = A_{\xi} \hat{x}_{\xi} + B_{\xi} u + \lambda_{\xi} \tilde{e}_y
$$

💡Ejemplo 5: Masa-Resorte-Amortiguador

Controlar el desplazamiento de la masa.

<div align="center">
  <img src="Imágenes_Corte_3/Clase%20%2312/Ejemplo.png" alt="Figura de prueba" width="500">
  <p><b>Figura 11.</b>Ejemplo</p>
</div>

### Sistema físico:

- Una masa unida a un resorte y un amortiguador.
- 
- Aplicamos una fuerza externa $u(t)$ para mover la masa.

### Diagrama y leyes aplicadas

Aplicamos la Segunda Ley de Newton:

$$
\sum F = ma
$$

- Fuerzas que actúan:

<div align="center">
  
| Fuerza               | Expresión       | Descripción                        |
|----------------------|------------------|------------------------------------|
| Fuerza externa       | $u(t)$           | Actúa sobre la masa                |
| Fuerza del resorte   | $F_k = kx$       | Ley de Hooke                       |
| Fuerza del amortiguador | $F_b = B\dot{x}$ | Proporcional a la velocidad       |

</div>

### Ecuación diferencial

Usando la Segunda Ley de Newton:

$$
u(t) - F_k - F_b = M\ddot{x}(t)
$$

Sustituyendo las expresiones de fuerza:

$$
u(t) - kx(t) - B\dot{x}(t) = M\ddot{x}(t)
$$


$$
M\ddot{y}(t) + B\dot{y}(t) + Ky(t) = u(t)
$$

O también:

$$
u(t) = M\ddot{y}(t) + B\dot{y}(t) + Ky(t)
$$

Donde:

- $y(t)$: posición de la masa
  
- $M$: masa
  
- $B$: coeficiente de amortiguamiento
  
- $K$: constante del resorte

## Paso a paso hacia el modelo ADRC

Partimos de la ecuación diferencial ya obtenida:

$$
u(t) - Ky(t) - B\dot{y}(t) = M\ddot{y}(t)
$$

### Paso 1: Despejar la derivada de mayor orden

Queremos expresar la ecuación en función de la aceleración $\ddot{y}(t)$, porque ADRC requiere tener esa derivada máxima aislada:

$$
\ddot{y}(t) = \frac{1}{M} \left[ u(t) - Ky(t) - B\dot{y}(t) \right]
$$

### aso 2: Definir las variables de estado

Vamos a convertir este sistema de segundo orden en un sistema de primer orden (forma de espacio de estados), usando:

- $x_1 = y$  (la posición)  
- $x_2 = \dot{y}$  (la velocidad)

Entonces:

$$
\dot{x}_1 = \dot{y} = x_2
$$

$$
\dot{x}_2 = \ddot{y} = \frac{1}{M} \left( u(t) - Kx_1 - Bx_2 \right)
$$

### Resultado: Modelo en espacio de estados

El sistema queda expresado así:

$$
\begin{cases}
\dot{x}_1 = x_2 \\\\
\dot{x}_2 = \frac{1}{M} \left( u(t) - Kx_1 - Bx_2 \right)
\end{cases}
$$

## Modelo en Espacio de Estados

Ya definimos las variables de estado:

- $x_1 = y$ (posición)  
- $x_2 = \dot{y}$ (velocidad)

### Ecuaciones de estado

Las ecuaciones quedan:

$$
\begin{aligned}
\dot{x}_1 &= x_2 \\\\
\dot{x}_2 &= \frac{1}{M} u(t) - \frac{K}{M} x_1 - \frac{B}{M} x_2
\end{aligned}
$$

### Forma matricial

$$
\dot{X}(t) = A X(t) + B u(t)
$$

donde:

$$
X(t) = \begin{bmatrix} x_1 \\\\ x_2 \end{bmatrix}
$$

Las matrices del sistema son:

$$
A = \begin{bmatrix}
0 & 1 \\\\
-\frac{K}{M} & -\frac{B}{M}
\end{bmatrix},
\quad
B = \begin{bmatrix}
0 \\\\
\frac{1}{M}
\end{bmatrix}
$$

### Ecuación de salida

Dado que $y(t) = x_1$, tenemos:

$$
y(t) = C X(t) + D u(t)
$$

Con:

$$
C = \begin{bmatrix} 1 & 0 \end{bmatrix}, \quad D = \begin{bmatrix} 0 \end{bmatrix}
$$

### Sistema completo

$$
\begin{aligned}
\dot{X}(t) &= A X(t) + B u(t) \\\\
y(t) &= C X(t)
\end{aligned}
$$

### Forma estándar para ADRC

Partimos de:

$$
\ddot{y}(t) = \frac{1}{M} u(t) - \frac{K}{M} y(t) - \frac{B}{M} \dot{y}(t)
$$

La idea de ADRC es llevar esta ecuación a una forma genérica como:

$$
y^{(n)} = K u + \varepsilon(t)
$$

donde:

- $K = \frac{1}{M}$  
- $\varepsilon(t) = -\frac{K}{M} y(t) - \frac{B}{M} \dot{y}(t)$  
- $\varepsilon(t)$ es la **perturbación total generalizada** (todo lo que no es el control directo).


### Observador de Estado Extendido (ESO)

Para controlar este sistema, se diseña un observador que estima:

- El estado físico: $y$, $\dot{y}$
- La perturbación total: $\varepsilon(t)$

Este observador se llama **ESO (Extended State Observer)**.


### Modelo extendido (orden 3):

Variables extendidas:

- $x_1 = y$
- $x_2 = \dot{y}$
- $x_3 \approx \varepsilon(t)$

Ecuaciones del ESO:

$$
\begin{aligned}
\dot{x}_1 &= x_2 \\\\
\dot{x}_2 &= K u + x_3 \\\\
\dot{x}_3 &= 0
\end{aligned}
$$

También se puede extender a orden 4, si se quiere modelar el cambio de la perturbación:

$$
\dot{x}_3 = x_4 \quad \text{y} \quad \dot{x}_4 = 0
$$

Pero normalmente se asume que $\dot{\varepsilon}(t) \approx 0$, y se simplifica con $\dot{x}_3 = 0$.


### Uso del ESO en el control

Una vez que tienes la estimación $\hat{x}_3 \approx \varepsilon(t)$, puedes compensarla en el control con:

$$
u(t) = \frac{1}{K} \left( u_0(t) - \hat{x}_3 \right)
$$

donde:

- $u_0(t)$ es una señal de control convencional (PID, seguimiento de referencia, etc.).

<div align="center">
  
| Variable | Significado                         |
|----------|-------------------------------------|
| $x_1$    | Posición $y$                        |
| $x_2$    | Velocidad $\dot{y}$                 |
| $x_3$    | Perturbación generalizada $\varepsilon(t)$ |
| $x_4$    | Derivada de la perturbación (opcional)     |

</div>

### Modelo extendido del sistema (orden 4)

Definimos las variables de estado extendidas:

- $x_1 = y$ (posición)
- $x_2 = \dot{y}$ (velocidad)
- $x_3 \approx \varepsilon(t)$ (perturbación total)
- $x_4 = \dot{\varepsilon}(t)$ (derivada de la perturbación)

Ecuaciones del sistema extendido:

$$
\begin{aligned}
\dot{x}_1 &= x_2 \quad \text{(posición)} \\\\
\dot{x}_2 &= K u + x_3 \quad \text{(aceleración con perturbación)} \\\\
\dot{x}_3 &= x_4 \quad \text{(evolución de la perturbación)} \\\\
\dot{x}_4 &= \ddot{\varepsilon} \approx 0 \quad \text{(se suele asumir constante)}
\end{aligned}
$$

## Desde el punto de vista del observador (ESO)

Vamos a estimar:

$$
\begin{aligned}
\hat{x}_1 &\approx x_1 \quad \text{(posición)} \\\\
\hat{x}_2 &\approx x_2 \quad \text{(velocidad)} \\\\
\hat{x}_3 &\approx \varepsilon(t) \quad \text{(perturbación)} \\\\
\hat{x}_4 &\approx \dot{\varepsilon}(t) \quad \text{(derivada de la perturbación)}
\end{aligned}
$$

### Estructura del ESO con realimentación de error

Se define el error de estimación como:

$$
e_1 = y - \hat{x}_1
$$

Ecuaciones del observador extendido:

$$
\begin{aligned}
\dot{\hat{x}}_1 &= \hat{x}_2 + \lambda_3 e_1 \\\\
\dot{\hat{x}}_2 &= K u + \hat{x}_3 + \lambda_2 e_1 \\\\
\dot{\hat{x}}_3 &= \hat{x}_4 + \lambda_1 e_1 \\\\
\dot{\hat{x}}_4 &= 0 + \lambda_0 e_1
\end{aligned}
$$


### ¿Por qué funciona esto?

Este observador inyecta el error de salida $e_1$ multiplicado por las ganancias $\lambda_i$ para forzar que las estimaciones converjan rápidamente a los valores reales del sistema.

### Interpretación creativa

Imagina que el sistema es un auto y el observador es un copiloto que:

- Estima la velocidad ($\hat{x}_2$).
  
- Adivina la fuerza del viento ($\hat{x}_3$).
  
- Intuye si la pendiente está cambiando ($\hat{x}_4$).

Y lo hace **solo mirando la posición** ($x_1 = y$) y **corrigiendo sus predicciones con el error**.

### Estimación de la perturbación

La perturbación estimada también puede representarse con:

$$
\varepsilon \approx e^{(4)} + \lambda_3 e^{(3)} + \lambda_2 \ddot{e} + \lambda_1 \dot{e} + \lambda_0 e
$$


### ¿Y luego? Control con compensación de perturbación

Con el ESO estimando $\hat{x}_3 \approx \varepsilon(t)$, el control se define como:

$$
u = \frac{1}{K} \left(u_0 - \hat{x}_3 \right)
$$

donde:

- $u_0$ es el control deseado (por ejemplo, un controlador PD o de seguimiento).
  
- $\hat{x}_3$ es la perturbación estimada, que se compensa.

$$
\dot{x}_1 = x_2
$$

$$
\dot{x}_2 = \mathbb{K}u + \varepsilon
$$

$$
x_3 = \varepsilon
$$

$$
x_4 = \dot{\varepsilon}
$$

$$
\dot{x}_1 = x_2
$$

$$
\dot{x}_2 = \mathbb{K}u + x_3
$$

$$
\dot{x}_3 = x_4
$$

$$
\dot{x}_4 = \ddot{\varepsilon}
$$

Por lo cual  
Desde el punto de vista del observador  
se aplica la aproximación:

$$
e = x_1 - \hat{x}_1
$$

$$
\dot{\hat{x}}_1 = x_2 + \lambda_3 e
$$

$$
\dot{\hat{x}}_2 = \mathbb{K}u + x_3 + \lambda_2 e
$$

$$
\dot{\hat{x}}_3 = x_4 + \lambda_1 e
$$

$$
\dot{\hat{x}}_4 = 0 + \lambda_0 e
$$

$$
e^{(4)} + \lambda_3 \dddot{e} + \lambda_2 \ddot{e} + \lambda_1 \dot{e} + \lambda_0 e = \varepsilon
$$

Asumiendo: K=0,5, B=0,2, M=0,5

El observador implementado es:

<div align="center">
  <img src="Imágenes_Corte_3/Clase%20%2312/Asumiendo.png" alt="Figura de prueba" width="500">
  <p><b>Figura 12.</b>Asumiendo Polos</p>
</div>

El observador implementado es:

<div align="center">
  <img src="Imágenes_Corte_3/Clase%20%2312/Obsevador Implemenatdo.png" alt="Figura de prueba" width="500">
  <p><b>Figura 13.</b>Observador implementado</p>
</div>

Para poder cerrar el lazo se plantea la siguiente ley de control $$\( u \)$$:

$$
u = \frac{1}{k} \left( y^{(n)*} - k_1 (\dot{\hat{y}} - \dot{y}^*) - k_0 (\hat{y} - y^*) - \hat{\varepsilon} \right)
$$

El polinomio característico para el error de seguimiento $$\( e_y = y - y^* \)$$ es:

$$
P_{e_y}(s) = s^n + k_{n-1}s^{n-1} + \cdots + k_1 s + k_0
$$

Para este caso particular, con \( n = 2 \):

$$
P_{e_y}(s) = s^2 + k_1 s + k_0
$$

Para imponer la dinámica del error de seguimiento se ubican los polos en:

poly([-15 -15])

ans =

     1    30   225

Planta y el observador en lazo cerrado:

<div align="center">
  <img src="Imágenes_Corte_3/Clase%20%2312/Lazo Cerrado.png" alt="Figura de prueba" width="500">
  <p><b>Figura 14.</b>Lazo Cerrado</p>
</div>

Pruebas de desempeño PID:

<div align="center">
  <img src="Imágenes_Corte_3/Clase%20%2312/PID 1.png" alt="Figura de prueba" width="500">
  <p><b>Figura 15.</b>PID</p>
</div>

<div align="center">
  <img src="Imágenes_Corte_3/Clase%20%2312/PID 2.png" alt="Figura de prueba" width="500">
  <p><b>Figura 16.</b>PID</p>
</div>

<div align="center">
  <img src="Imágenes_Corte_3/Clase%20%2312/PID 3.png" alt="Figura de prueba" width="500">
  <p><b>Figura 17.</b>PID</p>
</div>

Pruebas de desempeño ADRC:

<div align="center">
  <img src="Imágenes_Corte_3/Clase%20%2312/ADRC 1.png" alt="Figura de prueba" width="500">
  <p><b>Figura 18.</b>ADRC</p>
</div>

<div align="center">
  <img src="Imágenes_Corte_3/Clase%20%2312/ADRC 2.png" alt="Figura de prueba" width="500">
  <p><b>Figura 19.</b>ADRC</p>
</div>

<div align="center">
  <img src="Imágenes_Corte_3/Clase%20%2312/ADRC 3.png" alt="Figura de prueba" width="500">
  <p><b>Figura 20.</b>ADRC</p>
</div>

A partir de las seis imágenes anteriores, se puede concluir que el control ADRC (Active Disturbance Rejection Control) ofrece un desempeño significativamente superior al de un controlador PID. En particular, su capacidad de respuesta ante perturbaciones es mucho más rápida y eficaz, lo que se traduce en una mayor robustez y estabilidad del sistema.

💡Ejemplo 6: 

- Modelo del Sistema

$$
\dot{x} = 
\begin{bmatrix}
x_2 \\
-0.25x_1 + 0.70x_2 + (4.75 - 4.50x_1)u
\end{bmatrix}
$$

$$
y = x_1
$$

$$
x = 
\begin{bmatrix}
x_1 & x_2
\end{bmatrix}^T
$$

<div align="center">
  <img src="Imágenes_Corte_3/Clase%20%2312/MODELO.png" alt="Figura de prueba" width="500">
  <p><b>Figura 21.</b>Modelo</p>
</div>

Respuesta en lazo abierto:

<div align="center">
  <img src="Imágenes_Corte_3/Clase%20%2312/MODELO 2.png" alt="Figura de prueba" width="500">
  <p><b>Figura 22.</b>Modelo</p>
</div>

- Planteamiento de cotrolador.

- Obtuvimos una función de segundo orden.

- La ganancia estatica es una función .

$$
\dot{y} = \dot{x}_1
$$

$$
\ddot{y} = \dot{x}_2 = \ddot{x}_1
$$

$$
\ddot{y} = (4.75 - 4.50y)u + 0.70\dot{y} - 0.25y
$$

- Como el sistema es de orden 2:

$$
y^{(2)} = \mathbb{K}u + \mathcal{E}(t)
$$

$$
\mathbb{K} = 4.75 - 4.50y
$$

$$
\mathcal{E} = 0.70\dot{y} - 0.25y
$$

Perturbaciones:

<div align="center">
  <img src="Imágenes_Corte_3/Clase%20%2312/PERTURBACIONES.png" alt="Figura de prueba" width="500">
  <p><b>Figura 23.</b>Perturbaciones</p>
</div>

Control robusto basado en técnicas ADRC de dos estados extendidos:

<div align="center">
  <img src="Imágenes_Corte_3/Clase%20%2312/CONTROL ROBUSTO.png" alt="Figura de prueba" width="500">
  <p><b>Figura 24.</b>Perturbaciones</p>
</div>

- Señal de entrada: adición de dos señales paso; Perturbación: tipo Rampa
  
<div align="center">
  <img src="Imágenes_Corte_3/Clase%20%2312/CONTROL ROBUSTO 2.png" alt="Figura de prueba" width="500">
  <p><b>Figura 25.</b>Perturbaciones</p>
</div>

- Señal de entrada: Rampa; Perturbación: tipo Paso
  
<div align="center">
  <img src="Imágenes_Corte_3/Clase%20%2312/CONTROL ROBUSTO 3.png" alt="Figura de prueba" width="500">
  <p><b>Figura 26.</b>Perturbaciones</p>
</div>

- Señal de entrada: Señal de orden 2; Perturbación: Sinusoidal
  
<div align="center">
  <img src="Imágenes_Corte_3/Clase%20%2312/CONTROL ROBUSTO 4.png" alt="Figura de prueba" width="500">
  <p><b>Figura 27.</b>Perturbaciones</p>
</div>

- Señal de entrada: Sinusoidal; Perturbación: Señal de orden 2
  
<div align="center">
  <img src="Imágenes_Corte_3/Clase%20%2312/CONTROL ROBUSTO 5.png" alt="Figura de prueba" width="500">
  <p><b>Figura 28.</b>Perturbaciones</p>
</div>

- Vareación de Párametros

<div align="center">
  <img src="Imágenes_Corte_3/Clase%20%2312/Variacion de parametros.png" alt="Figura de prueba" width="500">
  <p><b>Figura 29.</b>Vareación</p>
</div>

### Variación de parámetros

- Controlador robusto basado en técnicas ADRC de dos estados extendidos.
  
- Variación del parámetro que acompaña a 𝜀

<div align="center">
  
| Señal de entrada / Señal de Perturbación | ISE - Nominal        | ISE - Variación Paramétrica |
|------------------------------------------|----------------------|-----------------------------|
| Pasos / Rampa                            | 4.514 × 10⁻⁶         | 4.516 × 10⁻⁶                |
| Rampa / Paso                             | 1.058 × 10⁻⁷         | 1.058 × 10⁻⁷                |
| Orden 2 acotada / Sinusoidal             | 2.672 × 10⁻⁶         | 2.681 × 10⁻⁶                |
| Sinusoidal / Orden 2                     | 0.0001076            | 0.0001076                   |

</div>

### Variación de parámetros

- Controlador robusto basado en técnicas ADRC de dos estados extendidos.
  
- Variación del parámetro que acompaña al control

### ISE para distintas combinaciones de señales y valores de \( K \)

<div align="center">
  
| Señal de entrada / Señal de Perturbación | K = 0.5K           | K = 1K (Nominal)     | K = 4K            | K = 7K           |
|------------------------------------------|--------------------|----------------------|-------------------|------------------|
| Pasos / Rampa                            | 5.469 × 10⁻⁶       | 4.515 × 10⁻⁶         | 3.663 × 10⁻⁶      | 0.001678         |
| Rampa / Paso                             | 1.159 × 10⁻⁷       | 1.058 × 10⁻⁷         | 1.104 × 10⁻⁷      | 1.862 × 10⁻⁷     |
| Orden 2 acotada / Sinusoidal             | 2.717 × 10⁻⁶       | 2.68 × 10⁻⁶          | 2.277 × 10⁻⁶      | 1.558 × 10⁻⁵     |
| Sinusoidal / Orden 2                     | 0.0001111          | 0.0001076            | 9.959 × 10⁻⁵      | 0.00047          |

</div>

## Conclusiones

1. Mayor robustez ante perturbaciones:
   
El ADRC rechaza eficazmente perturbaciones internas y externas gracias a su observador de estados extendido, superando al PID en entornos inciertos o variables.

2. Mejor desempeño dinámico:
   
El ADRC presenta una respuesta más rápida y precisa ante cambios en la referencia o perturbaciones, logrando estabilización más veloz sin sacrificar estabilidad.

3. Diseño más flexible y adaptable:
   
A diferencia del PID, el ADRC permite separar el diseño del controlador y del observador, lo que facilita la sintonización y adaptación a distintos tipos de sistemas (lineales y no lineales).

## Referencias

[1] J. E. Cote B., ADRC, diapositivas de clase, 9° semestre, Universidad ECCI, 2025.
