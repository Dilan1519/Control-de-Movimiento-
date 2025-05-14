# Conceptos de Transmisión Tornillo Guía

Durante las sesiones anteriores del curso, se abordaron los fundamentos del comportamiento del torque y la inercia en distintos tipos de mecanismos de transmisión. El objetivo principal ha sido entender cómo reflejar adecuadamente estas variables hacia el lado del motor, lo cual es esencial para un correcto dimensionamiento del mismo. Entre los mecanismos estudiados se encuentran los engranajes y las poleas con correas, destacando aspectos clave como la relación de transmisión, la eficiencia del sistema y la relación de inercia. Se discutió cómo estas variables afectan el rendimiento y la selección del motor, y se realizaron simulaciones en Simscape para visualizar su comportamiento.

Ahora, retomando la clase, se introducen nuevos mecanismos comúnmente utilizados en entornos industriales. Entre ellos se encuentra el tornillo guía, también conocido como tornillo sin fin, un componente ampliamente utilizado en diversos procesos mecánicos. Este mecanismo será analizado tanto desde su funcionamiento físico como desde su modelado y simulación, con el fin de ampliar el entendimiento sobre las diferentes formas de transmisión de movimiento y fuerza en sistemas industriales.

## Índice

 [10. Conclusiones](#10-Conclusiones)

 [11. Bibliografía](#11-Bibliografía)


## 1. Tornillo sin Fin

>🔑 *Tornillo sin fin:* Elemento mecánico que convierte movimiento rotacional en movimiento lineal, usado comúnmente en maquinaria para precisión y control de posición.

## 1.1 Principio de Funcionamiento

<div align="center">
  <img src="Imágenes_Corte_3/Clase%20%2311/Tornillo_Sin_Fin.gif" alt="Figura de prueba" width="300">
  <p><b>Figura 1.</b>Tornillo sin Fin</p>
</div>

- Al girar el tornillo, se genera un desplazamiento lineal en una tuerca o componente móvil acoplado a él.

- A esta parte móvil, que se desplaza a lo largo del tornillo, se le suele conectar una cama o bandeja que cumple funciones específicas en el sistema mecánico.
  
## 1.2 Rosca Cuadrada (Square Thread) vs Rosca Trapezoidal (Trapezoidal Thread)   

<div align="center">
  <img src="Imágenes_Corte_3/Clase%20%2311/Acme_Threads_Trapezoidal_Threads.png" alt="Figura de prueba" width="600">
  <p><b>Figura 2.</b>Square Thread y Trapezoidal Thread</p>
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


## 1.3 Rosca Directa (sin esferas) vs Tornillo con Recirculación de Bolas (Ball Screw)    

<div align="center">
  <img src="Imágenes_Corte_3/Clase%20%2311/Rosca Directa (sin esferas) y Tornillo con Recirculación de Bolas (Ball Screw).jpg" alt="Figura de prueba" width="600">
  <p><b>Figura 3.</b>Rosca Directa (sin esferas) vs Tornillo con Recirculación de Bolas (Ball Screw)  </p>
</div>

| Característica              | Rosca Directa (sin esferas)                                  | Tornillo con Recirculación de Bolas (Ball Screw)                      |
|----------------------------|---------------------------------------------------------------|------------------------------------------------------------------------|
| Mecanismo de movimiento    | Contacto directo entre rosca del tornillo y tuerca            | Movimiento asistido por esferas internas que actúan como rodamientos  |
| Fricción                   | Alta fricción                                                  | Muy baja fricción gracias a las esferas                               |
| Precisión del movimiento   | Menor precisión                                                | Alta precisión y suavidad                                             |
| Desgaste                   | Mayor desgaste debido al contacto directo                     | Menor desgaste por menor contacto directo                             |
| Capacidad de carga         | Limitada a cargas bajas o moderadas                          | Soporta cargas elevadas por mejor distribución del esfuerzo           |
| Costo                      | Más económico                                                 | Más costoso                                                           |
| Aplicaciones típicas       | Sistemas simples o de bajo costo donde la precisión no es crítica | Máquinas CNC, robótica, automatización de alta precisión          |

> **Nota:** Los tornillos con recirculación de bolas ofrecen ventajas significativas en eficiencia y precisión, siendo ideales para sistemas exigentes, aunque a un mayor costo.


## 1.4 Aplicaciones

<div align="center">

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




## Conclusiones

1. La relación de transmisión en sistemas polea-correa funciona igual que en engranajes: la velocidad angular y el torque se relacionan de forma inversa según los radios, pero ambas poleas giran en el mismo sentido (salvo que se indique lo contrario en simulación).

2. Simulaciones en Simscape permiten representar de manera precisa un sistema mecánico, incluyendo parámetros como fricción, inercia, elasticidad de la correa, y configuración del sentido de giro.

3. La correcta configuración de los bloques (polea, correa, acoplamiento) es esencial para obtener resultados realistas, como velocidad de salida y tensiones en la correa, lo cual es útil para validación y predicción de fallos.


## Referencias

[1] S. Niku, Introduction to Robotics: Analysis, Control, Applications, 4th ed., Wiley, 2023.

[2] R. Kelly, D. Santibáñez, and L. F. Reyes, Control of Robot Manipulators in Joint Space, 2nd ed., Springer, 2021.

[3] M. Spong, S. Hutchinson, and M. Vidyasagar, Robot Modeling and Control, 2nd ed., Wiley, 2020.

[4] J. E. Cote B., Perfiles de Movimiento, diapositivas de clase, 9° semestre, Universidad ECCI, 2025.
