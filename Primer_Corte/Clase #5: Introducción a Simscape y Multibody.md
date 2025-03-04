# Introducción a Simscape y Multibody

Los software de modelado estructural permiten simular esfuerzos, materiales y comportamiento ante fuerzas, pero no analizan la dinámica del sistema. Aunque generan animaciones basadas en la cinemática, no ofrecen curvas de posición, velocidad o aceleración en función del tiempo. Para ello, se requieren herramientas específicas de simulación dinámica.

## Índice

 [8. Ejercicio ](#8-Ejercicio)

 [9. Solución](#9-Solución)

 [10. Bibliografía](#10-Bibliografía)
  
## 1. Características

<div align="center">
 
| Característica              | Descripción |
|-----------------------------|-------------|
| **Tipo de modelado**        | Basado en cuerpos rígidos y articulaciones con restricciones. |
| **Generación de ecuaciones** | Calcula automáticamente ecuaciones diferenciales y cinemáticas. |
| **Análisis en el tiempo**   | Muestra la respuesta temporal de variables dinámicas. |
| **Animación 3D**            | Visualiza el movimiento del sistema en tiempo real. |
| **Integración con otros sistemas** | Permite combinar con modelos hidráulicos, térmicos, electromecánicos y eléctricos. |
| **Uso de motores**          | Se pueden agregar modelos de motores para simular accionamientos. |

</div>

> **Nota:** Este modelo permite realizar simulaciones dinámicas avanzadas con integración de múltiples disciplinas, facilitando el análisis y diseño de sistemas complejos.

## 1.1 Simscape y sus aplicaciones en distintas industrias:

<div align="center">

| Industria         | Aplicaciones con Simscape |
|------------------|-------------------------|
| **Automotriz**    | Modelado de sistemas de suspensión, frenos, transmisión y motores eléctricos. |
| **Aeroespacial**  | Simulación de actuadores hidráulicos, controles de vuelo y trenes de aterrizaje. |
| **Robótica**      | Diseño de manipuladores, simulación de control de motores y análisis de dinámica. |
| **Manufactura**   | Modelado de líneas de producción, control de maquinaria y sistemas neumáticos. |
| **Energía**       | Simulación de turbinas eólicas, paneles solares y sistemas de almacenamiento de energía. |
| **Dispositivos médicos** | Análisis de prótesis, exoesqueletos y sistemas biomédicos electromecánicos. |

</div>

> **Nota:** Simscape es una herramienta poderosa para la simulación multidominio, permitiendo modelar y analizar sistemas físicos en diversas industrias con alta precisión y realismo.

<div align="center">
  <img src="Imágenes/Clase%20%235/Ejemplo_Pendulo_1.jpg" alt="Figura de prueba" width="400">
  <p><b>Figura 2.</b> Diagrama Control Cascada </p>
</div>

<div align="center">
  <img src="Imágenes/Clase%20%235/Ejemplo_Pendulo_2.jpg" alt="Figura de prueba" width="400">
  <p><b>Figura 2.</b> Diagrama Control Cascada </p>
</div>

<div align="center">
  <img src="Imágenes/Clase%20%235/Ejemplo_Pendulo_3.jpg" alt="Figura de prueba" width="400">
  <p><b>Figura 2.</b> Diagrama Control Cascada </p>
</div>

<div align="center">
  <img src="Imágenes/Clase%20%235/Ejemplo_Pendulo_4.jpg" alt="Figura de prueba" width="400">
  <p><b>Figura 2.</b> Diagrama Control Cascada </p>
</div>

<div align="center">
  <img src="Imágenes/Clase%20%235/Ejemplo_Pendulo_5.jpg" alt="Figura de prueba" width="400">
  <p><b>Figura 2.</b> Diagrama Control Cascada </p>
</div>

<div align="center">
  <img src="Imágenes/Clase%20%235/Ejemplo_Pendulo_6.jpg" alt="Figura de prueba" width="400">
  <p><b>Figura 2.</b> Diagrama Control Cascada </p>
</div>

<div align="center">
  <img src="Imágenes/Clase%20%235/Ejemplo_Pendulo_7.jpg" alt="Figura de prueba" width="400">
  <p><b>Figura 2.</b> Diagrama Control Cascada </p>
</div>

<div align="center">
  <img src="Imágenes/Clase%20%235/Ejemplo_Pendulo_8.jpg" alt="Figura de prueba" width="400">
  <p><b>Figura 2.</b> Diagrama Control Cascada </p>
</div>

<div align="center">
  <img src="Imágenes/Clase%20%235/Ejemplo_Pendulo_9.jpg" alt="Figura de prueba" width="400">
  <p><b>Figura 2.</b> Diagrama Control Cascada </p>
</div>

<div align="center">
  <img src="Imágenes/Clase%20%235/Ejemplo_Pendulo_10.jpg" alt="Figura de prueba" width="400">
  <p><b>Figura 2.</b> Diagrama Control Cascada </p>
</div>

<div align="center">
  <img src="Imágenes/Clase%20%235/Pendulo_Simple.gif" alt="Figura de prueba" width="400">
  <p><b>Figura 2.</b> Diagrama Control Cascada </p>
</div>

<div align="center">
  <img src="Imágenes/Clase%20%235/Ejemplo_pendulo_11.jpg" alt="Figura de prueba" width="400">
  <p><b>Figura 2.</b> Diagrama Control Cascada </p>
</div>

<div align="center">
  <img src="Imágenes/Clase%20%235/Ejemplo_pendulo_12.jpg" alt="Figura de prueba" width="400">
  <p><b>Figura 2.</b> Diagrama Control Cascada </p>
</div>

<div align="center">
  <img src="Imágenes/Clase%20%235/Ejemplo_pendulo_13.jpg" alt="Figura de prueba" width="400">
  <p><b>Figura 2.</b> Diagrama Control Cascada </p>
</div>

<div align="center">
  <img src="Imágenes/Clase%20%235/Pendulo_Simple_1.gif" alt="Figura de prueba" width="400">
  <p><b>Figura 2.</b> Diagrama Control Cascada </p>
</div>

<div align="center">
  <img src="Imágenes/Clase%20%235/Ejemplo_Pendulo_14.png" alt="Figura de prueba" width="400">
  <p><b>Figura 2.</b> Diagrama Control Cascada </p>
</div>

<div align="center">
  <img src="Imágenes/Clase%20%235/Ejemplo_Pendulo_15.png" alt="Figura de prueba" width="400">
  <p><b>Figura 2.</b> Diagrama Control Cascada </p>
</div>

<div align="center">
  <img src="Imágenes/Clase%20%235/Pendulo_Simple_2.gif" alt="Figura de prueba" width="400">
  <p><b>Figura 2.</b> Diagrama Control Cascada </p>
</div>

<div align="center">
  <img src="Imágenes/Clase%20%235/Ejemplo_Pendulo_16.png" alt="Figura de prueba" width="400">
  <p><b>Figura 2.</b> Diagrama Control Cascada </p>
</div>

>🔑 *Control de Lazo Único:* El control de lazo único es el esquema de control más básico en sistemas de automatización y regulación de procesos. Se caracteriza porque un solo controlador recibe la señal de una variable medida, la compara con un valor deseado (setpoint) y genera una señal de control para actuar sobre un elemento final con el objetivo de minimizar el error.



💡**Ejemplo 4:** Control en Cascada en un Sistema de Tanque y Flujo

Definición de la Planta

La respuesta obtenida se aproxima a un sistema de primer orden con retardo:

$$ G(s) = \frac{K e^{-t_d s}}{\tau s + 1} $$

El sistema consta de:

**Relación entre la válvula y el flujo de entrada.**

$$ G_2(s) = \frac{5e^{3-s}}{8s+1} $$

**flujo de entrada y el nivel del tanque.**

$$ G_1(s) = \frac{e^{13-s}} {27s+1}$$

Para identificar el lazo interno y el lazo externo en un sistema de control en cascada, generalmente se sigue el criterio del tiempo de respuesta (𝜏), en este caso sería:

### Lazo Interno (Rápido): Relación entre la válvula y el flujo de entrada

Se modela con la función de transferencia:

$$ G_2(s) = \frac{5e^{3-s}}{8s+1} $$

Aquí, una apertura de la válvula tarda 8 segundos en afectar el flujo y tiene un pequeño retardo de 1 segundo.

### Lazo Externo (Lento): Relación entre el flujo de entrada y el nivel del tanque

Se modela con la función de transferencia:

$$ G_1(s) = \frac{K e^{-10s}}{15s+1} $$

El nivel del tanque cambia con una constante de tiempo de 15 segundos y un retardo de 10 segundos debido a la inercia del sistema.

**Sintonización Lazo secundario por método de Ziegler & Nichol**

$$ \frac{0.9}{k_{2}}\left( \frac{t_{2}}{t_{m}}\right)= \frac{0.9}{5}\left( \frac{8}{3} \right) = 0.48 $$

$$ t_{i2} = 3.33 \cdot t_{m} = 3.33 \cdot 3 = 9.99 $$

**Sintonización Lazo Primario**

$$
K_{\text{Total}} = K_1 \cdot 1 = K_1 = 1
$$

$$
t_{m\text{Total}} = t_{m1} + t_{m2} = 13 + 3 = 16
$$

$$
\tau_{\text{Total}} \approx \tau_1 \approx 15
$$

$$
K_{c1} = \left( \frac{1.2}{K_{\text{Total}}} \right) \cdot \left( \frac{\tau_{\text{Total}}}{t_{m\text{Total}}} \right) = \left( \frac{1.2}{1} \right) \cdot \left( \frac{15}{16} \right) = 1.2 \times \frac{15}{16} = 1.125
$$

$$
T_{i1} = 2 t_{m\text{Total}} = 2 \times 16 = 32
$$

$$
T_{d1} = 0.5 t_{m\text{Total}} = 0.5 \times 16 = 8
$$

## 3. MÉTODOS DE SINTONIZACIÓN

## 3.1 Metodologías empíricas de lazo abierto Austin

Austin fue una ingeniera y discípula de Astro, reconocida por desarrollar el método del relé. En su tesis doctoral, presentada en 1986, propuso una metodología de sintonización para esquemas de control en cascada, utilizando controladores PI y PID.

El objetivo central de su trabajo fue abordar el problema de la separación de modelos en estos sistemas. Para ello, planteó un método basado en curvas de reacción, donde todas las curvas se obtienen desde una misma entrada: la entrada del sistema.

Para utilizar la tabla, primero es importante recordar que el lazo secundario se diseña de manera independiente, aplicando cualquier metodología conocida. Se asume que este ya ha sido definido antes de usar la tabla.

- Si en el lazo secundario se elige un controlador proporcional (P), se deben usar las fórmulas de la fila correspondiente.
  
- Si se selecciona un controlador PI en el secundario, se deben emplear las fórmulas de la fila siguiente.

En la parte superior de la tabla, se encuentran las opciones para el lazo primario:

- Si se elige un controlador PI en el primario, se usan las fórmulas de la primera columna.
  
- Si se selecciona un PID, se emplean las de la segunda columna.
  
- Para determinar las fórmulas adecuadas, se busca la intersección entre la fila del controlador secundario y la columna del controlador primario.

Por ejemplo:

-Si en el secundario se usa un controlador proporcional (P) y en el primario un PID, se debe seleccionar la fórmula ubicada en la intersección correspondiente.

-Si se utilizan controladores PI en ambos lazos, la ganancia proporcional del primario se calcula con la fórmula correspondiente en la tabla.

<div align="center">
  <img src="Imágenes/Clase%20%233/Austin.jpg" alt="Figura de prueba" width="500">
  <p><b>Figura 1.</b> Tabla de Austin </p>
</div>

<div align="center">
  <img src="Imágenes/Clase%20%233/Austin_2.jpg" alt="Figura de prueba" width="500">
  <p><b>Figura 1.</b> Tabla </p>
</div>

