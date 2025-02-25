# ¿QUÉ ES EL CONTROL CASCADA?

El control cascada en una técnica de control la cual se usa comúnmente en el control de movimiento, esto ya que al necesitar controlar más de una variable a la vez y una dependiente de otra, se hace uso de un sistema compuesto por dos controladores, donde la salida del primer controlador sirve de setpoint para el segundo. 

## Índice
 [1. ¿En qué consiste?](#1-en-qué-consiste)
 
 [2. ¿Qué condiciones necesita?](#2-Qué-condiciones-necesita)
 
 [3. Ejes de Movimiento](#3-ejes-de-movimiento)

 [4. ¿Qué se controla?](#4-qué-se-controla)
 
 [5. ¿Cómo se hacia antes del control?](#5-cómo-se-hacia-antes-del-control)

 [6. ¿Componentes?](#6-componentes)

 [7. Control de cascada ](#7-control-de-cascada)

 [8. Ejercicio ](#8-Ejercicio)

 [9. Solución](#9-Solución)

 [10. Bibliografía](#10-Bibliografía)

💡**Ejemplo 1:** Control en Cascada de Nivel y Caudal en un Tanque

**Descripción del Sistema**

Imaginemos un tanque de almacenamiento de agua en una planta industrial.

- Entrada: El agua entra desde una tubería controlada por una válvula de entrada.
- Salida: El agua sale por otra tubería, donde la demanda de flujo varía debido a diferentes condiciones del proceso.
- Objetivo: Mantener el nivel del tanque constante a pesar de las variaciones en la salida.
- El desafío aquí es que si solo controlamos el nivel, la respuesta será lenta y el sistema puede volverse inestable.

**Problema con un Control de Lazo Único**

Si solo utilizamos un controlador de nivel (LC – Level Controller), este actuaría directamente sobre la válvula de entrada basándose únicamente en la medición del nivel del tanque. Sin embargo, esto tiene tres problemas principales:

Retardos en la respuesta 🚨

Si el nivel empieza a bajar, el controlador intentará corregirlo abriendo más la válvula de entrada.
Sin embargo, el nivel del tanque cambia lentamente porque depende de la acumulación o pérdida de líquido, lo que puede hacer que la respuesta sea demasiado tardía.
Oscilaciones en el nivel 🌊

Como el nivel responde lentamente, el controlador podría sobrecompensar abriendo demasiado la válvula.
Esto puede llevar a una sobrecarga en la entrada, causando oscilaciones no deseadas en el nivel.
Falta de estabilidad ante perturbaciones ⚠️

Si la demanda de salida varía abruptamente, el control de nivel tardará en detectarlo y reaccionar, lo que puede llevar a desbordamientos o vaciados imprevistos del tanque.


## 1. ¿En qué consiste?

Como su nombre lo sugiere, esta técnica consiste en poner en serie dos o más algoritmos de control, donde las variables controladas por estos algoritmos, son dependientes una de la otra de manera sucesiva, pero esta técnica no puede ser usada al azar, ya que requiere de ciertas condiciones y reglas para ser implementada de la manera correcta.

  
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
