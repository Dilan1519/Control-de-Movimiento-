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
  
## 1 Control de Lazo Único y Control en Cascada

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
| Requiere menos sensores y hardware. | NSolo corrige el error cuando la variable ya ha sido afectada. |
| Adecuado cuando los efectos de perturbaciones son mínimos. |En sistemas con múltiples variables interconectadas, puede ser insuficiente. |

</div>

> **Nota:** El control de lazo único es simple y económico, pero reactivo y menos eficiente en sistemas con perturbaciones o retardos.

## 1.3 ¿Cómo funciona el control de lazo de cascada?

En este esquema se tienen dos controladores trabajando en conjunto:

- Lazo Primario: Controla la variable principal del proceso y genera el setpoint para el lazo secundario.
- Lazo Secundario: Controla una variable intermedia que responde más rápido a perturbaciones y ayuda a estabilizar el proceso.

**Flujo de operación:**

- El sensor del lazo primario mide la variable principal (Ejemplo: temperatura del reactor).
- El controlador primario calcula la corrección y envía el setpoint al controlador secundario.
- El lazo secundario mide una variable más rápida (Ejemplo: temperatura del vapor en la tubería) y ajusta el sistema antes de que afecte a la variable principal.
- El elemento final de control (Ejemplo: válvula de combustible) actúa para mantener la estabilidad del sistema.

<div align="center">

| Ventajas del Control en Cascada          | Desventajas del Control en Cascada     |
|------------------------------------------|----------------------------------------|
| El lazo secundario reacciona antes de que la variable principal se vea afectada. | Se necesitan sensores y controladores adicionales. |
| Se minimizan los efectos de perturbaciones externas. |  Es necesario sintonizar correctamente ambos controladores para evitar inestabilidad. |

</div>

Criterio para elegir qué variable va en el lazo primario y cuál en el secundario

El criterio principal para seleccionar qué variable se coloca en cada lazo se basa en qué variable genera más perturbaciones y cuál responde más rápido.

🔹 Lazo primario (externo): Se encarga de la variable más lenta y crítica del sistema.
🔹 Lazo secundario (interno): Se encarga de la variable más rápida y responde a perturbaciones inmediatas.

  
## 2. ¿Qué condiciones necesita?

A continuación, se muestra una tabla con las industrias donde se usa el control de movimiento, los tipos de máquinas que emplean esta tecnología, los países donde es más común y los beneficios clave en cada sector.

<div align="center">

| **Industria**              | **Tipos de Máquinas**                                | **Países donde más se usan**      | **Beneficios clave**                                     |
|----------------------------|-----------------------------------------------------|---------------------------------|---------------------------------------------------------|
| **Empaque**                | Máquinas de envasado, cintas transportadoras, etiquetadoras | EE.UU., Alemania, China, México | Mayor velocidad, precisión en el empaquetado y reducción de desperdicios. |
| **Ensamblaje**             | Robots ensambladores, sistemas pick & place, CNC   | Japón, Alemania, Corea del Sur  | Ensamblaje preciso, reducción de costos y automatización avanzada. |
| **Impresión**              | Impresoras industriales, máquinas flexográficas     | EE.UU., China, Alemania, Brasil | Alta resolución, sincronización del material y rapidez de producción. |
| **Productos de madera**    | Sierras automáticas, cepilladoras CNC, routers CNC  | Canadá, EE.UU., Suecia, Brasil  | Corte preciso, optimización del material y reducción de errores. |
| **Maquinaria**             | Torno CNC, fresadoras, robots industriales         | Alemania, Japón, Italia, China  | Producción eficiente, mayor seguridad y reducción de tiempo de operación. |
| **Eléctrica/Semiconductores** | Máquinas de soldadura PCB, ensambladoras SMT       | Taiwán, Corea del Sur, China, EE.UU. | Ensamblaje de componentes de alta velocidad y precisión en micras. |

</div>

> **Nota:** Esta tabla presenta solo algunos ejemplos de aplicaciones y países donde el control de movimiento es clave en la industria.

## 3. Ejes de Movimiento

Cada movimiento generado por un actuador en un sistema de control se denomina **eje de movimiento (axis)**. Un sistema puede tener múltiples ejes, y su sincronización es esencial para realizar tareas complejas con precisión y eficiencia.

## Tipos de Ejes de Movimiento
<div align="center">
 
| Tipo de Eje         | Descripción | Ejemplo |
|--------------------|-------------|---------|
| **Eje Lineal** | Movimiento en línea recta a lo largo de un solo eje (X, Y o Z). | Un torno CNC mueve el cortador en el eje X para dar forma a la pieza. |
| **Eje Rotacional** | Movimiento giratorio alrededor de un eje fijo. | Un brazo robótico de ensamblaje rota en el eje Z para ajustar una pieza. |
| **Ejes Coordinados** | Múltiples ejes que trabajan en sincronización para realizar una tarea. | En una impresora, el cartucho de tinta se mueve en el eje X, mientras que el rodillo mueve el papel en el eje Y. |
| **Ejes Interpolados** | Movimiento combinado de varios ejes para generar trayectorias complejas. | Un robot industrial realiza movimientos curvos en 3D con interpolación de sus ejes. |
 
</div>

> **Nota:** Esta tabla da una pequeña explicación de los tipos de ejes de movimiento.

## 4. ¿Qué se controla?

El control de movimiento puede regular posición, velocidad, torque y aceleración. Dependiendo de la aplicación, se pueden controlar las cuatro variables, solo tres, dos o una.

>🔑 *Posición:* Determina la ubicación exacta de un objeto en el espacio. Se controla para asegurar que un mecanismo llegue a un punto específico con precisión.
>
>🔑 *Velocidad:* Regula la rapidez con la que un objeto se mueve de un punto a otro. Es crucial para evitar vibraciones y mejorar la eficiencia del proceso.
>
>🔑 *Torque:* Es la fuerza de giro aplicada a un eje o motor. Controlarlo permite garantizar que un sistema pueda mover cargas sin sobrecargas o fallos mecánicos.
>
>🔑 *Acerleración:* Es la variación de la velocidad en el tiempo. Se controla para evitar movimientos bruscos y reducir el desgaste de los componentes.

💡**Ejemplo 2:** Controlando las 4 variables (posición, velocidad, torque y aceleración)


  
## 2. ¿Qué condiciones necesita?

A continuación, se muestra una lista con las condiciones mas importantes a tener en cuenta al momento de diseñar un sistema de control cascada.

- **velocidad de los controladores:**  
  - Al diseñar un controlador cascada, se deben tener en cuenta las velocidades de respuesta de los controladores, ya que el orden de la cascada dependerá de esta velocidad, los sistemas más rápidos serán los que se encuentren en la parte más interna de la cascada, y de esta forma se ordenan los controladores hasta llegar al controlador más lento el cual será el más externo de la cascada.

## 3. Ejes de Movimiento

Cada movimiento generado por un actuador en un sistema de control se denomina **eje de movimiento (axis)**. Un sistema puede tener múltiples ejes, y su sincronización es esencial para realizar tareas complejas con precisión y eficiencia.

## Tipos de Ejes de Movimiento
<div align="center">
 
| Tipo de Eje         | Descripción | Ejemplo |
|--------------------|-------------|---------|
| **Eje Lineal** | Movimiento en línea recta a lo largo de un solo eje (X, Y o Z). | Un torno CNC mueve el cortador en el eje X para dar forma a la pieza. |
| **Eje Rotacional** | Movimiento giratorio alrededor de un eje fijo. | Un brazo robótico de ensamblaje rota en el eje Z para ajustar una pieza. |
| **Ejes Coordinados** | Múltiples ejes que trabajan en sincronización para realizar una tarea. | En una impresora, el cartucho de tinta se mueve en el eje X, mientras que el rodillo mueve el papel en el eje Y. |
| **Ejes Interpolados** | Movimiento combinado de varios ejes para generar trayectorias complejas. | Un robot industrial realiza movimientos curvos en 3D con interpolación de sus ejes. |
 
</div>

> **Nota:** Esta tabla da una pequeña explicación de los tipos de ejes de movimiento.

## 4. ¿Qué se controla?

El control de movimiento puede regular posición, velocidad, torque y aceleración. Dependiendo de la aplicación, se pueden controlar las cuatro variables, solo tres, dos o una.

>🔑 *Posición:* Determina la ubicación exacta de un objeto en el espacio. Se controla para asegurar que un mecanismo llegue a un punto específico con precisión.
>
>🔑 *Velocidad:* Regula la rapidez con la que un objeto se mueve de un punto a otro. Es crucial para evitar vibraciones y mejorar la eficiencia del proceso.
>
>🔑 *Torque:* Es la fuerza de giro aplicada a un eje o motor. Controlarlo permite garantizar que un sistema pueda mover cargas sin sobrecargas o fallos mecánicos.
>
>🔑 *Acerleración:* Es la variación de la velocidad en el tiempo. Se controla para evitar movimientos bruscos y reducir el desgaste de los componentes.

💡**Ejemplo 2:** Controlando las 4 variables (posición, velocidad, torque y aceleración)
