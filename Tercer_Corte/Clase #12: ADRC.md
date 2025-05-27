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

>*Nota: Esta tabla resume los fundamentos y origen del ADRC como técnica moderna de control.*


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

> *Nota: Esta tabla muestra cómo ADRC se aplica a distintos sectores industriales con alta incertidumbre.*

### Comparación Rápida: PID vs ADRC

<div align="center">
  
| Característica | PID | ADRC |
|----------------|-----|------|
| Dependencia del modelo | Alta | Baja |
| Rechazo de perturbaciones | Limitado | Activo y predictivo |
| No linealidades | No las maneja bien | Las rechaza automáticamente |
| Robustez | Media | Alta ante incertidumbre y variaciones |

</div>

> *Nota: Esta tabla compara de forma concisa las diferencias clave entre controladores PID y ADRC.*

### Componentes clave

El ADRC se basa en dos grandes pilares:

<div align="center">
  
| Componente | Descripción |
|------------|-------------|
| Ley de control no lineal | Calculada a partir del error del sistema mediante funciones no lineales. |
| ESO – Observador de Estados Extendido | Un observador que va más allá de los estados típicos… ¡y predice el caos! |

</div>

> *Nota: Esta tabla resume los elementos esenciales que forman el núcleo del control ADRC.*


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


## 2. Definiciones
Utilice el símbolo '>' para crear bloques de texto. En la presente plantilla estas cajas están reservadas para resaltar las definiciones, las cuales deben ser breves, y la palabra o frase que se está definiendo debe estar en letra itálica. El inicio del bloque de texto debe realizarse con el emoji 🔑 .
>🔑 *Definición:* descripción precisa y clara del significado de una palabra, término, concepto o fenómeno. Es una explicación que establece los límites y el alcance de aquello que se está definiendo, aclarando su naturaleza, características esenciales y, en algunos casos, su relación con otros conceptos.

## 3. Subsecciones
Las subsecciones pueden utilizarse para sub dividir ciertos temas que se tienen en clases, por ejemplo si se está trabajandolos conversores D/A, puede ser necesario subdividir este en circuito de resistencias ponderadas y circuito de escalera R2R. 
### 3.1. Título de subsecciones
Para la creación de estas subsecciones debe utilizar un tamaño de letra más pequeño, por lo tanto utilice la etiqueta '###' 
### 3.2. Numeración de subsecciones
Siga la numeración de la sección seguida de un punto y luego el número de la subsección.

## 4. Ejemplos
Si en algún caso pretende dar un ejemplo explicativo ya sea a través de texto o através de ecuaciones matemáticos, utilizar la palabra 'Ejemplo' seguido de una numeración consecutiva dentro de la clase. Utilice el emoji 💡 antecediendo la palabra.

## 5. Ecuaciones
Para la edición de ecuaciones debe utilizar la etiqueta '$$' al comienzo y final de la ecuación para que la ecuación quede centrada ocupando una línea. Si se quiere que la ecuación quede integrada en el texto debe utilizar la etiqueta '$' al comienzo y final de la ecuación. Las ecuaciones pueden ser editadas utilizando el código LATEX, en el siguiente enlace encuentran un editor de ecuaciones que les genera el código. http://www.alciro.org/tools/matematicas/editor-ecuaciones.jsp . Sin embargo hay muchas otras herramientas que pueden utilizar para esto.

💡**Ejemplo 1:** si se va a representar la ecuación de la ley de Ohm se puede mostrar así $R=\frac{V}{I}$ o también,

$$R=\frac{V}{I}$$

$${
\begin{pmatrix*}[r]
63 & 71 & 2\\
6 & 829 & 12\\
599 & 9 & 361
\end{pmatrix*}
}={\begin{pmatrix*}[r]
63 & 71 & 2\\
6 & 829 & 12\\
599 & 9 & 361
\end{pmatrix*}}$$


## 6. Figuras
Todas las figuras que incluya deben ser generadas por ustedes, **no utilizar las figuras de las presentaciones**. Para incluir figuras puede seguir los siguientes pasos:
* Primero escribimos ![]().
* Después escribimos, dentro de los corchetes, el texto alternativo. Este es opcional y solo entra en acción cuando no se puede cargar la imagen correctamente.
* Después escribimos, dentro de los paréntesis, la ubicación del archivo (ya sea una url o una ubicación dentro de algun folder local). Se recomienda poner las imágenes en una carpeta que se llame imágenes dentro del repositorio github para que no tengan problemas al cargar las imágenes.

💡**Ejemplo 2:**

![Figura de prueba](images/plantilla/Captura2.PNG)

Figura 1. Figura de prueba

Incluya la respectiva etiqueta a modo de descripción de la figura y mantenga numeración consecutiva para todas las figuras de la clase.

## 7. Tablas
En caso de necesitar la inclusión de tablas para organizar información se recomienda el uso de la herramienta del siguiente enlace https://www.tablesgenerator.com/markdown_tables , la cual permite organizar la información dentro de la tabla y genera el código markdown automáticamente:

💡**Ejemplo 3:** 

| **Resultado** | **x = número de intentos hasta primer éxito** |
|---------------|-----------------------------------------------|
|       S       |                       1                       |
|       FS      |                       2                       |
|      FFS      |                       3                       |
|      ...      |                      ...                      |
|    FFFFFFS    |                       7                       |
|      ...      |                      ...                      |

Tabla 1. Tabla de ejemplo

Cada tabla debe llevar la etiqueta que describa su contenido y numeración consecutiva para todas las tablas

## 8. Código
Teniendo en cuenta que el curso requiere del desarrollo de código matlab, c, c++ u otro. Si requiere incluir pequeños segmentos de código en los apuntes hágalos de la siguiente manera:

💡**Ejemplo 4:**
```
var sumar2 = function(numero) {
  return numero + 2;
}
```

## 9. Ejercicios
Deben agregar 2 ejercicios con su respectiva solución, referentes a los temas tratados en cada una de las clases. Para agregar estos, utilice la etiqueta #, es decir como un nuevo título dentro de la clase con la palabra 'Ejercicios'. Cada uno de los ejercicios debe estar numerado y con su respectiva solución inmediatamente despues del enunciado. Antes del subtitulo de cada ejercicio incluya el emoji 📚

## Rúbrica
| 0-1                                                                                   | 1-2                                                                                  | 2-3                                                                                                                                                                               | 3-4                                                                                                                                                                       | 4-5                                                                                                                                                                               |
|---------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Presenta menos del 10% de los temas o no presenta por  el medio y formato  solicitado | Presenta menos del 40% de los temas solicitados, y  cumple parcialmente la plantilla | Presenta menos del 60% de los temas solicitados (con descripciones, gráficos tablas, etc), y cumple  parcialmente la plantilla. No presenta la totalidad  de ejercicios resueltos | Presenta menos del 80% de los temas solicitados (con descripciones, gráficos, tablas, etc) y cumple con  la plantilla. No presenta  la totalidad de ejercicios  resueltos | Presenta el 100% de los temas vistos en clase (con descripciones, gráficos, tablas, etc), siguiendo totalmente la plantilla. presenta la  totalidad de los ejercicios solicitados |

## 10. Conclusiones
Agregue unas breves conclusiones sobre los temas trabajados en cada clase, puede ser a modo de resumen de lo trabajado o a indicando lo aprendido en cada clase

## 11. Referencias
Agregue un subtítulo al final donde pueda poner todas las referencias consultadas incluyendo el origen o fuente de los ejercicios planteados. Tambien dentro del texto referencie los textos o artículos consultados y las figuras y tablas dentro de la explicación de las mismas.
