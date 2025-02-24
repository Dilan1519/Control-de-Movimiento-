# ¿QUÉ ES EL CONTROL DE MOVIMIENTO?

El control de movimiento es una disciplina de la ingeniería que regula y coordina el desplazamiento de objetos mediante actuadores, sensores y algoritmos de control. Su aplicación es esencial en sectores como la manufactura, la robótica y la automatización de procesos. Es fundamental para garantizar precisión, eficiencia y optimización en sistemas industriales, mejorando la productividad y reduciendo errores. Su desarrollo ha permitido la evolución de máquinas inteligentes capaces de realizar operaciones con alta exactitud, impulsando la modernización y el avance tecnológico en diversas industrias.

## Índice
 [1. ¿En qué consiste?](#1-en-qué-consiste)
 
 [2. ¿En qué industria se usa?](#2-en-qué-industria-se-usa)
 
 [3. Ejes de Movimiento](#3-ejes-de-movimiento)

 [4. ¿Qué se controla?](#4-qué-se-controla)
 
 [5. ¿Cómo se hacia antes del control?](#5-cómo-se-hacia-antes-del-control)

 [6. ¿Componentes?](#6-componentes)

 [7. Control de cascada ](#7-control-de-cascada)

 [8. Ejercicio ](#8-Ejercicio)

 [9. Solución](#9-Solución)

 [10. Bibliografía](#10-Bibliografía)


## 1. ¿En qué consiste?

El control de movimiento, también llamado control de posicionamiento servo, consite en el proceso de mover una carga en un sistema mecánico.

💡**Ejemplo 1:** Un ejemplo antiguo de control de movimiento es el telar Jacquard (1801). Este telar automatizado, desarrollado por Joseph Marie Jacquard, utilizaba tarjetas perforadas para controlar el movimiento de los hilos en la fabricación de textiles con patrones complejos.

<div align="center">
  <img src="Imágenes/Clase%20%232/Telar Jacquard (1801).jpg" alt="Figura de prueba" width="400">
  <p><b>Figura 1.</b> Telar Jacquard (1801) </p>
</div>

## Movimientos del telar Jacquard

- **Movimiento de elevación de los hilos de urdimbre:**  
  - Se levantaban ciertos hilos según el patrón dictado por las tarjetas perforadas.
  - Este movimiento era clave para formar el diseño del tejido.

- **Movimiento del peine o batán:**  
  - Después de entrelazar los hilos, el peine golpeaba la trama para compactar el tejido.
  - Garantizaba que el tejido tuviera una estructura firme y uniforme.

- **Movimiento de avance de la tela:**  
  - A medida que se tejía, la tela se iba enrollando automáticamente.
  - Permitía la producción continua sin intervención manual.

- **Movimiento de las tarjetas perforadas:**  
  - Se desplazaban y giraban para indicar el siguiente patrón de tejido.
  - Funcionaban como un sistema de control programable mecánico.
  
## 2. ¿En qué industria se usa?

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
