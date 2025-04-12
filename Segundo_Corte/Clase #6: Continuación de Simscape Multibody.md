
# Articulaciones, Rigid transformation ,sensing y entradas

Ya que en la sesión anterior vimos como modelar sólidos y cambiar sus propiedades, en esta oportunidad veremos cómo es que estos se pueden conectar entre sí, esto con el objetivo de tener la capacidad de realizar simulaciones de mecanismos, para así tener la facilidad de realizar análisis ya sea de posición, velocidad o aceleración, además de ver las limitaciones de este tipo de simulación y como poder aprovecharlas al máximo.  

## Índice

[1. Articulaciones basicas en multibody](#1-Articulaciones-basicas-en-multibody)

[1.1 Articulación revoluta](#11-Articulación-revoluta)

[1.2 Articulación prismática](#12-Articulación-prismática)

[2 Propiedades generales de las articulaciones](#2-Tipos-de-Sistemas-y-su-Perfil-de-Movimiento)

[2.1 Actuadores en las articulaciones](#21-Actuadores-en-las-articulaciones)

[2.2 Sensores en las articulaciones](#22-Sensores-en-las-articulaciones)

[3 Transformaciones de rigid](#3-Transformaciones-de-rigid)

[3.1 Transformaciones de posición](#31-Transformaciones-de-posición)

[3.2 Transformcaiones de angulo](#32-Transformcaiones-de-angulo)

[4 Ejercicio](#4-ejercicio)

[5.Solución](#5-Solución)

[6 Conclusiones](#6-conclusiones)

[7 Referencias](#7-Referencias)


## 1. Articulaciones basicas en multibody

Como había mencionado antes, en multibody las articulaciones tienen la función de unir de cierta forma los sólidos, a continuación, explicare de que marea se unen estos sólidos y la forma en que la articulación los hace interactuar 

## 1.1 Articulación revoluta

La articulacion revoluta, como el nombre la sugiere, es una articulacion que hace girar un solido con respecto a otro en un eje determinado, esta articulacion solo puede generar rotaciones en el eje Z como se especifica en la descripcion de el bloque de esta articulacion, si se requiere una rotacion en un eje diferente, esto requerira del uso de un "Rigid Transform", este bloque sera explicado despues de la seccion de articulaciones.
<div align="center">
   <img src="Imágenes_Corte_2/Clase%20%236/articulacionr.png" alt="Figura de prueba" width="300">
  <p><b>Figura 1.</b>Articulacion revoluta multibody</p>
</div>

💡**Ejemplo 1:** Ejemplo aplicacion articulación revoluta.
- **Situación:** Se une un solido y el rigid original de la sumilación mediante una articulacion revoluta.

<div align="center">
   <img src="Imágenes_Corte_2/Clase%20%236/articulacionejem.png" alt="Figura de prueba" width="300">
  <p><b>Figura 2.</b>Diagrama ejemplo de articulación revoluta</p>
</div>
 
- **Resultado:** por accion de la gravedad que actua sobre el eje y, el solido comienza a girar sobre el eje z con un movimiento de tipo pendulo.

<div align="center">
   <img src="Imágenes_Corte_2/Clase%20%236/ejemplor.gif" alt="Figura de prueba" width="300">
  <p><b>Figura 3.</b>resultado ejemplo de articulación revoluta</p>
</div>

## 1.2 Articulación prismática

Esta articulación a diferencia de la revoluta, no genera un movimiento rotacional, en cambia esta genera un movimiento lineal entre dos sólidos, es decir que el sólido que esté conectado al follower de la articulación, se deslizara por el sólido conectado a la base de esta articulación. al igual que en la junta revoluta, este articulación solo funciona en un eje especifico, este se detalla en la descripción de la articulación y este eje es el eje Z, si se requiere una junta prismática en otro eje, este necesitara estar acompañado de un "Rigid Transform" para cambiar este eje. 

<div align="center">
   <img src="Imágenes_Corte_2/Clase%20%236/articulacionp.png" alt="Figura de prueba" width="300">
  <p><b>Figura 4.</b>Articulación prismatica multibody</p>
</div>

💡**Ejemplo 2:** Ejemplo aplicacion articulación prismatica.
- **Situación:** Se une un solido y el rigid original de la sumilación mediante una articulacion prismatica.

<div align="center">
   <img src="Imágenes_Corte_2/Clase%20%236/articulacionejemp.png" alt="Figura de prueba" width="300">
  <p><b>Figura 5.</b>Diagrama ejemplo de articulación prismatica</p>
</div>

- **Resultado:** por acción de la gravedad que actúa sobre el eje z, el sólido cae al vacío al deslizarse a través de la articulación prismática.

  <div align="center">
   <img src="Imágenes_Corte_2/Clase%20%236/ejemplop.gif" alt="Figura de prueba" width="300">
  <p><b>Figura 6.</b>Resultado ejemplo de articulación prismatica</p>
</div>

## 2 Propiedades generales de las articulaciones

Ya pudimos notar que diferentes articulaciones cuentan con diferentes propiedades, sin embargo, esto no quiere decir que las articulaciones sean absolutamente diferentes unas de otras, las articulaciones cuentan con funciones generales que se pueden usar en todas las articulaciones y se usan de las mismas maneras. a continuación, veremos las dos principales. 

## 2.1 Actuadores en las articulaciones

Tal cual como en una maquina real, esta simulación necesita de un actuador que realice la función de entrada de estos sistemas, pero en lugar de ser un motor o servo, las articulaciones permiten ingresar graficas o series de datos que le digan a multibody como va a moverse este mecanismo, en este caso la entrada se limita a dos tipos, de fuerza o torque para la articulación revoluta, y posición, ya sea metros para la prismática o radianes para la revoluta.

  <div align="center">
   <img src="Imágenes_Corte_2/Clase%20%236/actuador.png" alt="Figura de prueba" width="300">
  <p><b>Figura 7.</b>configuración de actuador para junta prismatica</p>
</div>

Cabe aclarar que si elegimos una entrada para la posición debemos poner la fuerza en auto calculada y viceversa, además de que si usamos el bloque "Simulink-PS
Convertir" necesitaremos configurarlo de una forma específica en cada caso.

💡**Ejemplo 3:** Ejemplo aplicacion articulación prismatica.
- **Situación:** Se une un solido y el rigid original de la sumilación mediante una articulacion prismatica, ademas de usar una entrada senoidal en el actuador de posición.
  <div align="center">
   <img src="Imágenes_Corte_2/Clase%20%236/dejemploa.png" alt="Figura de prueba" width="300">
  <p><b>Figura 8.</b>Diagrama ejemplo de actuador para junta prismatica</p>
</div>

  <div align="center">
   <img src="Imágenes_Corte_2/Clase%20%236/ejemploa.gif" alt="Figura de prueba" width="300">
  <p><b>Figura 9.</b>Ejemplo de actuador para junta prismatica</p>
</div>

- **Resultado:** El solido ya no cae por accion de la gravedad, si no que en cambio sigue el movimiento dictado por la onda seno que define su posición.

## 2.2 Sensores en las articulaciones

Así como pudimos ingresar datos en la simulación, también podemos sacarlos, todas las articulaciones cuentan con un sensor, que puede dar información sobre variables como: 

- Velocidad
- Aceleración
- posición

  <div align="center">
   <img src="Imágenes_Corte_2/Clase%20%236/sensor.png" alt="Figura de prueba" width="300">
  <p><b>Figura 10.</b>Configuración de sensor en articulaciones</p>
</div>

Para poder ver estas variables de forma visual, se debe usar un "PS-Simulink Converter", el cual permite a los osciloscopios de la simulación proyectas la variable, este conversor se debe conectar en el pin indicado con la primera letra de la variable a medir, por ejemplo "p" si es posición, o "v" si es velocidad.  

💡**Ejemplo 4:** Ejemplo sensor articulación prismatica.
- **Situación:** se pone una entrada de posición a la articulación, y por medio de el sensor de posición se obtiene de vuelta la misma información de posición.
  <div align="center">
   <img src="Imágenes_Corte_2/Clase%20%236/dejemplos.png" alt="Figura de prueba" width="300">
  <p><b>Figura 11.</b>Diagrama ejemplo de sensor para junta prismatica</p>
</div>

  <div align="center">
   <img src="Imágenes_Corte_2/Clase%20%236/ejemplos.png" alt="Figura de prueba" width="300">
  <p><b>Figura 12.</b>Ejemplo de sensor para junta prismatica</p>
</div>

- **Resultado:** El grafico obtenido a la salida del sensor y a la entrada del actuador son los mismos, por lo tanto el sensor funciona de manera adecuada. 

## 3 Transformaciones de rigid

El rigid es este simbolo de tres lineas que indica en que direccion estan apuntado los ejes X Y Z. este bloque permite modificar este rigis de dos formas, la primera en posicion, es decir cambniar la posicion del rigid, o en angulo, el cual permite cambiar la direccion en la que apuntan los ejes.

  <div align="center">
   <img src="Imágenes_Corte_2/Clase%20%236/rigid.png" alt="Figura de prueba" width="300">
  <p><b>Figura 13.</b>Rigid transformation</p>
</div>

## 3.1 Transformaciones de posición

En el momento de configurar la transformación de rigid podemos moverlo en base a dos tipos de coordenadas, (cartesiano y cilíndrico), la última opción permite mover los ejes individualmente.

  <div align="center">
   <img src="Imágenes_Corte_2/Clase%20%236/rigidt.png" alt="Figura de prueba" width="300">
  <p><b>Figura 14.</b>trasformacion de posicion de rigid</p>
</div>

## 3.2 Transformaciones de angulo

Este tipo de transformación hace que los ejes coordenados intercambien de lugar haciendo rotar el rigid tomando como base uno de los tres ejes, la transformación es realmente útil en el momento de usar las articulaciones, ya que estas se limitan a actuar sobre un solo eje, por lo tanto si en un sistema se necesita cierta articulación, pero esta no actúa sobre el eje deseado, ese eje puede ser reubicado gracias a la transformaciones de Angulo. 

💡**Ejemplo 5:** Ejemplo sensor articulación prismatica.
- **Situación:** se necesita una traslación de un bloque en el eje Y, pero la articulación prismática solo acuta sobre el eje z
  <div align="center">
   <img src="Imágenes_Corte_2/Clase%20%236/dejemplot.png" alt="Figura de prueba" width="300">
  <p><b>Figura 15.</b>Diagrama ejemplo de sensor para junta prismatica</p>
</div>

  <div align="center">
   <img src="Imágenes_Corte_2/Clase%20%236/ejemplot.gif" alt="Figura de prueba" width="300">
  <p><b>Figura 16.</b>Ejemplo de sensor para junta prismatica</p>
</div>

## 4 Ejercicio

Con lo aprendido anteriormente debe recrear un sistema biela corredera, en el cual un movimiento rotacional se transforma en un movimiento lineal, ademas use la funcion de sensor para ver la velocidad de la corredera

  <div align="center">
   <img src="Imágenes_Corte_2/Clase%20%236/ejer1.png" alt="Figura de prueba" width="300">
  <p><b>Figura 17.</b>Sistema biela corredera</p>
</div>

## 5 Solución
Recreando cada parte del mecanismo (Manivela, viela y corredera), conectandolos con las articulaciones correspondientes (3 revolutas y una prismatica), y haciendo las transformaciones de rigis adecuadas, (2 de angulo) para poner el eje de la prismatica en el lugar correcto, (1 de posición) para ubicar la corredera a tierra en el lugar adecuado, pudimos recrear el mecnismo y su cinematica.

  <div align="center">
   <img src="Imágenes_Corte_2/Clase%20%236/dejer1.png" alt="Figura de prueba" width="300">
  <p><b>Figura 17.</b>Diagrama sistema biela corredera</p>
</div>

  <div align="center">
   <img src="Imágenes_Corte_2/Clase%20%236/ejer1g.gif" alt="Figura de prueba" width="300">
  <p><b>Figura 17.</b>Animación sistema biela corredera</p>
</div>

## 6 Conclusiones

Al conocer todas las capacidades de simulynk multibody, tanto la forma de crear los mecanismos como la forma de obtener información de estos, este se vuelve una herramienta sumamente poderosa a la hora de analizar cualquier sistema mecánico o implementar perfiles de movimiento o sesiones sin necesidad de tener una planta física o modificarla. 


## 7 Referencias

