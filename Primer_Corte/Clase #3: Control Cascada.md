# ¿QUÉ ES EL CONTROL CASCADA?

El control cascada en una técnica de control la cual se usa comúnmente en el control de movimiento, esto ya que al necesitar controlar más de una variable a la vez y una dependiente de otra, se hace uso de un sistema compuesto por dos controladores, donde la salida del primer controlador sirve de setpoint para el segundo. 

## Índice

 [8. Ejercicio ](#8-Ejercicio)

 [9. Solución](#9-Solución)

 [10. Bibliografía](#10-Bibliografía)

💡**Ejemplo 1:** Control en Cascada de Nivel y Caudal en un Tanque

**Descripción del Sistema**

Imaginemos un tanque de almacenamiento de agua en una planta industrial.

- **Entrada:** El agua entra desde una tubería controlada por una válvula de entrada.
- **Salida:** El agua sale por otra tubería, donde la demanda de flujo varía debido a diferentes condiciones del proceso.
- **Objetivo:** Mantener el nivel del tanque constante a pesar de las variaciones en la salida.

El desafío aquí es que si solo controlamos el nivel, la respuesta será lenta y el sistema puede volverse inestable.

**Problema con un Control de Lazo Único**

Si solo utilizamos un controlador de nivel, este actuaría directamente sobre la válvula de entrada basándose únicamente en la medición del nivel del tanque. Sin embargo, esto tiene tres problemas principales:

**Retardos en la respuesta** 

- Si el nivel empieza a bajar, el controlador intentará corregirlo abriendo más la válvula de entrada.
- Sin embargo, el nivel del tanque cambia lentamente porque depende de la acumulación o pérdida de líquido, lo que puede hacer que la respuesta sea demasiado tardía.

**Oscilaciones en el nivel**

- Como el nivel responde lentamente, el controlador podría sobrecompensar abriendo demasiado la válvula.
- Esto puede llevar a una sobrecarga en la entrada, causando oscilaciones no deseadas en el nivel.

**Falta de estabilidad ante perturbaciones**

- Si la demanda de salida varía abruptamente, el control de nivel tardará en detectarlo y reaccionar, lo que puede llevar a desbordamientos o vaciados imprevistos del tanque.

**¿Qué se busca en el control en cascada en este caso?**

- **Mejor respuesta a perturbaciones:** El lazo de caudal responde rápidamente a cambios en la demanda sin esperar a que el nivel fluctúe demasiado.
- **Mayor estabilidad:** Se minimizan oscilaciones en el nivel, evitando desbordamientos o caídas abruptas.
- **Precisión en la regulación:** Se asegura que el flujo de entrada siempre sea el adecuado para mantener el nivel deseado.
  
## 1. Control de Lazo Único y Control en Cascada

>🔑 *Control de Lazo Único:* El control de lazo único es el esquema de control más básico en sistemas de automatización y regulación de procesos. Se caracteriza porque un solo controlador recibe la señal de una variable medida, la compara con un valor deseado (setpoint) y genera una señal de control para actuar sobre un elemento final con el objetivo de minimizar el error.

<div align="center">
  <img src="Imágenes/Clase%20%233/Control con un solo lazo.png" alt="Figura de prueba" width="400">
  <p><b>Figura 1.</b> Control con un solo lazo </p>
</div>

>🔑 *Control en Cascada:* El control en cascada es una estrategia avanzada de control donde se utilizan dos o más lazos de control anidados, con el objetivo de mejorar la respuesta del sistema ante perturbaciones y reducir retardos en la acción de control.

<div align="center">
  <img src="Imágenes/Clase%20%233/Diagrama Control Cascada.png" alt="Figura de prueba" width="400">
  <p><b>Figura 2.</b> Diagrama Control Cascada </p>
</div>

## 1.1 ¿Cómo funciona el control de lazo único?

- **Sensor:** Mide la variable de proceso (Ejemplo: temperatura, nivel, presión, velocidad).
- **Controlador:** Compara el valor medido con el setpoint y calcula la acción correctiva.
- **Elemento final de control:** Recibe la señal del controlador y ajusta el sistema (Ejemplo: una válvula, un variador de frecuencia, un motor).
- **Sistema controlado:** El proceso responde a la acción de control y la variable vuelve al setpoint.

💡**Ejemplo 2:** Control de temperatura de un horno:

<div align="center">
  <img src="Imágenes/Clase%20%233/Control de Temperatura de un horno.jpeg" alt="Figura de prueba" width="300">
  <p><b>Figura 1.</b> Control de temperatura de un horno </p>
</div>

- Se mide la temperatura con un sensor (termopar).
- Un controlador PID compara la temperatura con el setpoint.
- Si la temperatura es baja, el controlador aumenta el flujo de gas en la válvula de combustión para calentar más.
- Si la temperatura es alta, reduce el flujo de gas para evitar sobrecalentamiento.

## 1.2 Ventajas y Desventajas de Control de Lazo único

<div align="center">
 
| Ventajas      | Desventajas  |
|------------------------------------------|----------------------------------------|
| Fácil de diseñar e implementar. | Si hay retardos en el sistema, puede generar inestabilidad. |
| Requiere menos sensores y hardware. | Solo corrige el error cuando la variable ya ha sido afectada. |
| Adecuado cuando los efectos de perturbaciones son mínimos. |En sistemas con múltiples variables interconectadas, puede ser insuficiente. |

</div>

> **Nota:** El control de lazo único es simple y económico, pero reactivo y menos eficiente en sistemas con perturbaciones o retardos.

## 1.3 ¿Cómo funciona el control de lazo de cascada?

En este esquema se tienen dos controladores trabajando en conjunto:

- **Lazo Primario:** Controla la variable principal del proceso y genera el setpoint para el lazo secundario.
- **Lazo Secundario:** Controla una variable intermedia que responde más rápido a perturbaciones y ayuda a estabilizar el proceso.

**Flujo de operación:**

- El sensor del lazo primario mide la variable principal (Ejemplo: temperatura del reactor).
- El controlador primario calcula la corrección y envía el setpoint al controlador secundario.
- El lazo secundario mide una variable más rápida (Ejemplo: temperatura del vapor en la tubería) y ajusta el sistema antes de que afecte a la variable principal.
- El elemento final de control (Ejemplo: válvula de combustible) actúa para mantener la estabilidad del sistema.

## 1.4 Ventajas y Desventajas de Control de Cascada

<div align="center">
 
| Ventajas         | Desventajas    |
|------------------------------------------|----------------------------------------|
| El lazo secundario reacciona antes de que la variable principal se vea afectada. | Se necesitan sensores y controladores adicionales. |
| Se minimizan los efectos de perturbaciones externas. |  Es necesario sintonizar correctamente ambos controladores para evitar inestabilidad. |

</div>

> **Nota:** El control en cascada mejora la estabilidad y el rechazo de perturbaciones, pero requiere mayor complejidad y ajuste preciso.

## 1.5 Criterio para elegir qué variable va en el lazo primario y cuál en el secundario

El criterio principal para seleccionar qué variable se coloca en cada lazo se basa en qué variable genera más perturbaciones y cuál responde más rápido.

- **Lazo primario:** Se encarga de la variable más lenta y crítica del sistema.
- **Lazo secundario:** Se encarga de la variable más rápida y responde a perturbaciones inmediatas.

## 1.6 Criterios de selección de controladores:

<div align="center">

| Criterio                        | Controlador del Lazo Secundario  | Controlador del Lazo Primario  |
|----------------------------------|--------------------------------------|--------------------------------------|
| Velocidad de respuesta          | Rápida                               | Más lenta que C2                    |
| Función principal               | Rechazar perturbaciones antes de afectar el lazo primario | Alcanzar el setpoint eliminando errores en estado estacionario |
| Controladores recomendados      | P o PI                              | PI o PID                            |

</div>

> **Nota:** El control en cascada mejora la estabilidad y el rechazo de perturbaciones, pero requiere mayor complejidad y ajuste preciso.

💡**Ejemplo 3:** Ejemplo de selección de controladores

**Control de temperatura en un reactor químico**

- Lazo secundario controla la temperatura del vapor en la tubería → Controlador PI para respuesta rápida.
- Lazo primario controla la temperatura del reactor → Controlador PID para minimizar oscilaciones y eliminar error estacionario.

**Control de posición en un motor eléctrico**

- Lazo secundario controla la velocidad del motor → Controlador PI para ajustar rápido la velocidad.
- Lazo primario controla la posición del motor → Controlador PID para precisión y suavidad en la salida.

## 1.7 Aplicación al ejemplo 1 del tanque

**Nivel del tanque (variable más lenta) → Lazo primario**

- El nivel del tanque cambia lentamente porque depende de la acumulación o pérdida de líquido.
- Es la variable que queremos mantener estable en todo momento.
- Si solo controláramos el nivel, la respuesta del sistema sería muy lenta y con retardos.

**Caudal de entrada (variable más rápida) → Lazo secundario** 

- El caudal cambia rápidamente con la apertura de la válvula.
- Es una variable que se puede modificar instantáneamente para compensar perturbaciones.
- Controlando el caudal antes que el nivel, podemos actuar de inmediato sin esperar a que el nivel fluctúe demasiado.

## 1.8 ¿Cómo aplicar este criterio en otros sistemas?

Siempre debemos preguntarnos:

¿Cuál es la variable final que quiero mantener estable? → Esa va en el lazo primario.

¿Cuál es la variable que puede responder más rápido y ayudar a estabilizar la variable principal? → Esa va en el lazo secundario.

## 2. Métodos de sintonización 

>🔑 *Control en Cascada:* El control en cascada es una estrategia avanzada de control donde se utilizan dos o más lazos de control anidados, con el objetivo de mejorar la respuesta del sistema ante perturbaciones y reducir retardos en la acción de control.
