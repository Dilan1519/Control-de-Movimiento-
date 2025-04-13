# ¿QUÉ SON PERFILES DE MOVIMIENTO?

Durante la clase pasada, se introdujeron los perfiles de movimiento, comenzando por los perfiles lineales, los cuales permiten construir perfiles más complejos como el perfil trapezoidal de velocidad. Este tipo de perfil es útil para definir los distintos setpoints que un controlador debe seguir en cada instante de tiempo, asegurando un movimiento más controlado y eficiente.

En esta clase, se continúa con el estudio de los perfiles, enfocándonos en el perfil de velocidad con curva en S. A diferencia del perfil trapezoidal donde la aceleración cambia bruscamente, la curva en S busca suavizar la transición entre los distintos estados del movimiento, reduciendo vibraciones y esfuerzos mecánicos.

## Índice

[1. ¿En qué Consiste?](#1-en-qué-Consiste)

💡**Ejemplo 1:** Perfil de velocidad simétrico.

Dado el perfil de velocidad simétrico de la figura, calcule la velocidad máxima y la aceleración máxima.

- **Solución:**

<div align="center">
  <img src="Imágenes_Corte_2/Clase%20%238/Ejemplo_1_Continuación.png" alt="Figura de prueba" width="200">
  <p><b>Figura 1.</b>Ejemplo 1 Perfil de Velocidad</p>
</div>

Se tiene un perfil triangular simétrico. La distancia total recorrida desde $$s_0$$ hasta $$s_B$$ se obtiene como suma de dos áreas de triángulos:

$$ s_B = \frac{1}{2} v_{\text{max}} \cdot \frac{t}{2} + \frac{1}{2} v_{\text{max}} \cdot \frac{t}{2} $$

Simplificando:

$$ s_B = \frac{1}{2} v_{\text{max}} \cdot t $$

- **Cálculo de la velocidad máxima:**

Despejando $$\( v_{\text{max}} \)$$:

$$v_{\text{max}} = \frac{2 s_B}{t}$$

- **Cálculo de la aceleración máxima:**

La aceleración es el cambio de velocidad en el tiempo de subida:

$$a = \frac{v_{\text{max}}}{\frac{t}{2}} = \frac{2v_{\text{max}}}{t}$$

## 1. Comparativa entre Perfil Trapezoidal y Perfil Curva en S

<div align="center">
  <img src="Imágenes_Corte_2/Clase%20%238/Comparación.png" alt="Figura de prueba" width="600">
  <p><b>Figura 2.</b>Comparación entre Perfil Trapezoidal y Perfil Curva en S</p>
</div>

<div align="center">
 
| **Aspecto**                     | **Perfil Trapezoidal**                                                                 | **Perfil Curva en S**                                                                                  |
|-------------------------------|----------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------|
| **Velocidad (v)**              | Línea recta con pendiente constante (acelera, mantiene, desacelera)                    | Transiciones suaves, forma curva al inicio y final del perfil                                          |
| **Aceleración (a)**            | Escalonada, cambia bruscamente entre 0, +a y -a                                        | Curva continua, suaviza las transiciones; aproximación por polinomios de segundo orden                |
| **Jerk (j)**                   | Impulsos instantáneos (teóricamente infinitos), cambios repentinos en la aceleración  | Escalones finitos, cambios graduales; el jerk se vuelve controlado y continuo                         |
| **Suavidad del movimiento**    | Baja, puede generar vibraciones o sobresfuerzos                                       | Alta, transición progresiva sin golpes                                                                |
| **Representación matemática**  | Líneas rectas por tramos                                                              | Polinomios de 2º orden para aceleración; su integral (posición) es de 3º orden                        |
| **Efecto sobre el sistema**    | Mayor desgaste mecánico por los cambios abruptos                                       | Menor desgaste, mayor protección a actuadores y mecanismos                                            |
| **Tiempo de cálculo**          | Bajo, más simple de implementar                                                        | Requiere mayor esfuerzo computacional                                                                 |
| **Simetría**                   | Puede ser simétrico o asimétrico                                                      | Igual: permite tanto perfiles simétricos como asimétricos                                             |
| **Aplicaciones típicas**       | Sistemas donde el tiempo es prioritario y el impacto mecánico es tolerable            | Sistemas que requieren mucha suavidad: robótica, manipulación de objetos frágiles, CNC, etc.         |
| **Perfil de posición (x)**     | Lineal en cada etapa, con quiebres en las transiciones                                | Crecimiento suave (de orden 3), curva continua con pendiente variable al inicio y final               |

</div>

> **Nota:** La elección entre un perfil trapezoidal y uno en **curva en S** depende del compromiso entre tiempo de movimiento y suavidad requerida.

## 1.1 Comparativa entre Perfil en S (Mixto) y Perfil de Curva en S Pura

<div align="center">
  <img src="Imágenes_Corte_2/Clase%20%238/Comparación_2.png" alt="Figura de prueba" width="600">
  <p><b>Figura 3.</b>Comparativa entre Perfil en S (Mixto) y Perfil de Curva en S Pura</p>
</div>

<div align="center">
 
| **Aspecto**                 | **Perfil en S (Mixto)**                                                                 | **Perfil de Curva en S Pura**                                                                                 |
|----------------------------|-----------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------|
| **Estructura**             | Dos tramos de 2º orden (parabólicos) conectados con un tramo de 1º orden (recta de velocidad constante) | Solo dos tramos de 2º orden conectados directamente, sin sección intermedia lineal                          |
| **Transición en velocidad**| Tiene un tramo de velocidad constante (pendiente cero en a(t))                         | No tiene velocidad constante: la velocidad cambia continuamente                                               |
| **Aceleración (a)**        | Tiene tramos con aceleración constante (forma tipo meseta)                            | Transición continua; la aceleración tiene forma triangular                                                    |
| **Jerk (j)**               | Forma escalonada, con periodos planos (cero) entre valores positivos y negativos       | Jerk cambia de positivo a negativo sin tramos planos, lo que reduce el Jerk promedio                         |
| **Suavidad**               | Alta suavidad, pero menos que el perfil S puro                                        | Máxima suavidad: sin saltos ni planos; ideal para movimientos extremadamente delicados                       |
| **Continuidad de funciones** | Discontinua en la segunda derivada (jerk), pero continua en posición, velocidad y aceleración | Continua hasta en jerk (aunque cambia bruscamente), lo que suaviza aún más la transición                   |
| **Complejidad matemática** | Moderada (requiere resolver dos polinomios y una línea recta)                         | Más compleja: solo funciones de segundo orden; se debe calcular su conexión sin segmentos constantes          |
| **Aplicaciones típicas**   | Sistemas donde se busca suavidad, pero se permite velocidad constante (CNC, pick & place) | Sistemas ultra precisos o delicados: óptica, impresión 3D de alta precisión, medicina robótica, etc.      |

</div>

> **Nota:** El perfil en S mixto ofrece un buen balance entre suavidad y simplicidad. El perfil en S puro, al evitar completamente los tramos constantes y mantener la continuidad incluso en el jerk.

## 2. Modelo Matemático de la Curva en S

Cada segmento del perfil de velocidad en forma de curva en S se modela utilizando un polinomio de segundo orden, cuya expresión general es:

$$v(t) = C_1 t^2 + C_2 t + C_3$$

Este polinomio describe la velocidad como una función del tiempo durante las fases de aceleración y desaceleración suaves.

- No se trata de un único polinomio para todo el movimiento, sino de varios segmentos, cada uno con sus propios coeficientes.
  
- En total, puede haber hasta 4 o más segmentos si se consideran aceleración, velocidad constante y desaceleración, o si se trata de una curva S pura.
  
## 2.1 ¿Por qué Usar un Polinomio de Segundo Orden?

Porque permite una transición continua y suave en la aceleración.

- Su derivada (la aceleración):

$$a(t) = \frac{dv}{dt} = 2C_1 t + C_2$$

es una función lineal, lo que genera un perfil de aceleración en forma de triángulo.

- La derivada de la aceleración (el jerk):

$$j(t) = \frac{da}{dt} = 2C_1$$

es constante, lo que implica un jerk limitado y controlado.

## 2.2 Determinación de los coeficientes

Los coeficientes $$C_1$$, $$C_2$$ y $$C_3$$ se calculan usando condiciones de frontera, es decir, los valores conocidos de velocidad y tiempo al inicio y final de cada segmento.

Por ejemplo, si queremos construir una función de velocidad que vaya desde una velocidad inicial $$v_0$$ hasta una velocidad final $$v_f$$ en un tiempo $$t_f$$, usando también la aceleración inicial $$a_0$$, podemos plantear un sistema de ecuaciones:

$$
\begin{cases}
v(0) = v_0 \\
v(t_f) = v_f \\
a(0) = \left. \frac{dv}{dt} \right| = a_0
\end{cases}
$$

Recordando que:

$$\frac{dv}{dt} = 2C_1 t + C_2 \Rightarrow a(t)$$

Con estas condiciones, se puede resolver el sistema para obtener los valores de los coeficientes $$C_1$$, $$C_2$$ y $$C_3$$ que hacen que el perfil encaje exactamente con los requerimientos del movimiento.

## Desarrollo del modelo matemático para la curva A

Encontrar los coeficientes del polinomio de segundo orden que modela la velocidad $$v(t)$$ en el intervalo $$0 < t < \frac{t_a}{2}$$, correspondiente al primer tramo del perfil de curva en S.

$$v(t) = C_1 t^2 + C_2 t + C_3$$

### Condiciones de frontera

Para este intervalo, se conocen los siguientes valores:

<div align="center">
  
| Tiempo $$t$$            | Velocidad $$v(t)$$         | Aceleración $$a(t)$$       |
|---------------------------|-------------------------------|-------------------------------|
| $$t = 0$$              | $$v(0) = 0$$                | $$a(0) = 0$$                |
| $$t = \frac{t_a}{2}$$   | $$v\left(\frac{t_a}{2}\right) = \frac{v_m}{2}$$ | $$a\left(\frac{t_a}{2}\right) = a$$|

</div>

Paso 1: Derivar la función para obtener la aceleración

$$ a(t) = \frac{dv(t)}{dt} = 2C_1 t + C_2 $$

Paso 2: Aplicar condiciones de frontera

Evaluando $$v(0) = 0$$:

$$v(0) = C_1(0)^2 + C_2(0) + C_3 = 0 \Rightarrow C_3 = 0$$

Evaluando $$a(0) = 0$$:

$$a(0) = 2C_1(0) + C_2 = 0 \Rightarrow C_2 = 0$$

Evaluando \( v\left(\frac{t_a}{2}\right) = \frac{v_m}{2} \):

$$v\left(\frac{t_a}{2}\right) = C_1 \left(\frac{t_a}{2}\right)^2 = \frac{v_m}{2} \Rightarrow
C_1 = \frac{2v_m}{t_a^2}$$

La función de velocidad para el primer tramo (curva A) es:

$$v(t) = \frac{2v_m}{t_a^2} t^2$$

Y su derivada, que representa la aceleración:

$$a(t) = \frac{4v_m}{t_a^2} t$$

Este modelo permite una aceleración suave y progresiva, con jerk constante, ideal para movimientos que requieran control fino sin impactos o vibraciones abruptas.

💡**Ejemplo 2:** Determinar la posición del eje en 100 ms

**Datos del problema**

- Velocidad máxima: $$v_m = 32 \, \text{cm/s}$$
  
- Tiempo total de aceleración: $$t_a = 30 \, \text{ms}$$
  
- Tiempo objetivo: $$t = 100 \, \text{ms}$$

**División del perfil**

El perfil está compuesto por tres zonas:

- **Curva A**: aceleración creciente $$(0 \, \text{ms} \leq t < 15 \, \text{ms})$$
  
- **Curva B**: aceleración decreciente $$(15 \, \text{ms} \leq t < 30 \, \text{ms})$$
  
- **Sección constante**: velocidad constante $$(30 \, \text{ms} \leq t \leq 100 \, \text{ms})$$

## Expresiones de velocidad

## Para la curva A:

$$v_A(t) = \frac{2 v_m}{t_a^2} t^2 = \frac{2 \cdot 32}{30^2} t^2 = \frac{64}{900} t^2$$

## Para la curva B (con $$t \in [15, 30]$$):

$$v_B(t) = v_m - \frac{2 v_m}{t_a^2} (t_a - t)^2 = 32 - \frac{64}{900}(30 - t)^2$$

Expandimos:

$$(30 - t)^2 = t^2 - 60t + 900$$

Entonces:

$$v_B(t) = 32 - \left( \frac{64}{900} t^2 - \frac{64}{15} t + 64 \right) = -\frac{64}{900} t^2 + \frac{64}{15} t - 32$$

### 📏 Cálculo de posición total

La posición es el área bajo la curva de velocidad:

$$s(t) = \int_0^{15} v_A(t) \, dt + \int_{15}^{30} v_B(t) \, dt + \int_{30}^{100} v_m \, dt$$

#### ① Integrar curva A:

$$\int_0^{15} \frac{64}{900} t^2 \, dt = \frac{64}{900} \cdot \left[ \frac{t^3}{3} \right]_0^{15} = \frac{64}{900} \cdot \frac{3375}{3} = \frac{64 \cdot 1125}{900} = \boxed{80 \, \text{cm}}$$

### Integrar curva B:

$$\int_{15}^{30} \left( -\frac{64}{900} t^2 + \frac{64}{15} t - 32 \right) dt$$

Integrando término a término:

$$= \left[ -\frac{64}{900} \cdot \frac{t^3}{3} + \frac{64}{15} \cdot \frac{t^2}{2} - 32t \right]_{15}^{30}$$

Después de calcular:

$$= \boxed{80 \, \text{cm}}$$

### Sección de velocidad constante:

$$\int_{30}^{100} 32 \, dt = 32 \cdot (100 - 30) = \boxed{2240 \, \text{cm}}$$

###  Resultado final:

$$s(100) = 80 + 80 + 2240 = \boxed{2400 \, \text{cm}}$$

## Modelo usado con fórmulas de posición

## Sección A (0 a 15 ms):

$$s_A(t) = 0.023 \cdot t^3$$

Evaluado en $$t = 15$$:

$$s_A = 0.023 \cdot 3375 = \boxed{77.62 \, \text{cts}}$$

## Sección B (15 a 30 ms):

Modelo cúbico:

$$s_B(t) = 32t + 0.071 \left( 900t - \frac{60}{2} t^2 + \frac{t^3}{3} \right)$$

Evaluado entre 15 y 30:

$$s_B = 480 - 64.12 = \boxed{415.88 \, \text{cts}}$$

## Sección C (30 a 100 ms):

$$s_C = 32 \cdot (100 - 30) = \boxed{2240 \, \text{cts}}$$

## Resultado total en cts:

$$s_{0C}(100) = 77.62 + 415.88 + 2240 = \boxed{2733.49 \, \text{cts}}$$

## Ejercicio:

```matlab
% Parámetros
v_max = 10;       % Velocidad máxima (in/s)
t_acc = 4;        % Tiempo de aceleración (s)
t = linspace(0, t_acc, 1000);  % Vector de tiempo

% Perfil de velocidad con curva S pura (sigmoide suavizada)
v = v_max ./ (1 + exp(-12*(t/t_acc - 0.5)));

% Derivada numérica para obtener aceleración
a = [0 diff(v)./diff(t)];  % Aceleración aproximada (in/s^2)

% Gráfica
figure;
subplot(2,1,1);
plot(t, v, 'b', 'LineWidth', 2);
xlabel('Tiempo (s)');
ylabel('Velocidad (in/s)');
title('Perfil de Velocidad (Curva S Pura)');
grid on;

subplot(2,1,2);
plot(t, a, 'r', 'LineWidth', 2);
xlabel('Tiempo (s)');
ylabel('Aceleración (in/s^2)');
title('Perfil de Aceleración');
grid on;
```
<div align="center">
  <img src="Imágenes_Corte_2/Clase%20%238/Ejercicio_matlab_Clase_8.png" alt="Figura de prueba" width="600">
  <p><b>Figura 4.</b>Ejercicio Matlab</p>
</div>

## Movimiento Multi-Eje

El movimiento multi-eje implica la coordinación simultánea de dos o más ejes para ejecutar trayectorias complejas o perfiles de movimiento deseados. Es común en sistemas como máquinas CNC, robots y entornos automatizados.


### Formas de Coordinación

<div align="center">
  
| Tipo de Movimiento     | Descripción                                                  | Características Clave                          |
|------------------------|--------------------------------------------------------------|------------------------------------------------|
| **Movimiento secuencial** | Se mueve un eje a la vez, de forma alternada.                  | Simple, pero no eficiente para trayectorias suaves. |
| **Slew Motion**         | Ambos ejes se mueven al mismo tiempo, sin sincronización precisa. | Más rápido, pero puede causar trayectorias irregulares. |
| **Interpolated Motion** | Ambos ejes inician y terminan exactamente al mismo tiempo.      | Trayectorias suaves, ideal para curvas y diagonales. |

</div>

###  Definiciones Clave

- **Interpolación**: Técnica que ajusta la velocidad y aceleración de cada eje para seguir una trayectoria específica (por ejemplo, una línea recta).
- **Coordinación de ejes**: Control de la relación temporal y espacial entre múltiples ejes.
- **Perfil de movimiento**: Representación del desplazamiento, velocidad o aceleración de un eje a lo largo del tiempo.


### Ejemplo Ilustrativo

Supongamos que se desea mover un cabezal de una posición $$(X_0, Y_0) a (X_f, Y_f)$$:

- **Movimiento secuencial**: Primero se mueve X, luego Y (o viceversa).

- **Slew Motion**: X e Y se mueven simultáneamente, pero pueden llegar en tiempos diferentes.

- **Interpolación**: Se calcula una trayectoria (por ejemplo, línea recta) para que ambos ejes lleguen al punto final al mismo tiempo.

💡**Ejemplo 2:** (slew motion).

<div align="center">
  <img src="Imágenes_Corte_2/Clase%20%238/Ejemplo (slew motion).png" alt="Figura de prueba" width="400">
  <p><b>Figura 4.</b>Ejemplo (slew motion)</p>
</div>

Considere la máquina de la figura. Si ambos ejes se mueven a una velocidad de 4 cm/s usando un perfil de velocidad trapezoidal con $$t_a = 0.2\,s$$, ¿cuánto tiempo le tomará a cada eje completar el movimiento?

Resueltado – Slew Motion

Se tienen los siguientes datos para el movimiento de los ejes:

- $$t_a = 0.2\,s$$

- $$L_x = 16\,cm , v_x = 4\,cm/s$$

- $$L_y = 12\,cm ,  v_y = 4\,cm/s$$

#### Cálculos

Para el eje **X**:
$$
t_m^x = \frac{L_x}{v_m} - t_a = \frac{16\,cm}{4\,cm/s} - 0.2 = 3.8\,s
$$

$$
t_{\text{total}}^x = 3.8 + 2t_a = 4.2\,s
$$

Para el eje **Y**:
$$
t_m^y = \frac{L_y}{v_m} - t_a = \frac{12\,cm}{4\,cm/s} - 0.2 = 2.8\,s
$$

$$
t_{\text{total}}^y = 2.8 + 2t_a = 3.2\,s
$$


### Ejemplo Resuelto – Interpolated Motion

Para lograr que ambos ejes terminen al mismo tiempo, se toma como referencia el perfil de velocidad del eje que **toma más tiempo** (en este caso, el eje X) y se interpola el perfil de velocidad para el eje Y.

#### Datos conocidos:

- $$v_x = 4\,cm/s$$
- $$t_a = 0.2\,s$$
- $$L_y = 12\,cm$$

- Se conoce que el tiempo total del eje X fue:  
  
  $$
  t_m^x + 2t_a = 3.8 + 0.4 = 4.2\,s
  $$
  
  Entonces:
    
  $$
  t_m = 3.8\,s
  $$

#### Ecuación:

$$
t_m = \frac{L_y}{v_y} - t_a
\Rightarrow
v_y = \frac{L_y}{t_m + t_a} = \frac{12\,cm}{3.8 + 0.2} = 3\,cm/s
$$

## Conclusiones 

1. Ajustar la velocidad de uno de los ejes para que ambos terminen simultáneamente garantiza que la trayectoria entre dos puntos (por ejemplo, de A a B) sea continua y precisa, lo cual es esencial en aplicaciones como corte láser, CNC o robótica.

2. En movimientos interpolados, se toma como referencia el eje que requiere más tiempo para recorrer su distancia, y los otros ejes ajustan su perfil de velocidad en consecuencia.

3. Al realizar interpolación, no solo se ajusta la velocidad final del eje más rápido, sino que también debe garantizarse que el perfil (en este caso trapezoidal) mantenga su forma, respetando tiempos de aceleración y desaceleración para evitar sobreesfuerzos o movimientos no deseados.

## Referencias

[1] J. J. Craig, Introduction to Robotics: Mechanics and Control, 3rd ed., Pearson Prentice Hall, 2005.

[2] L. Sciavicco y B. Siciliano, Modeling and Control of Robot Manipulators, 2nd ed., Springer, 2012.

[3] M. P. Groover, Automation, Production Systems, and Computer-Integrated Manufacturing, 4th ed., Pearson, 2015.

[4] Bosch Rexroth AG, Mechatronics and Motion Control – Application Manual, 2002.

[5] J. E. Cote B., Perfiles de Movimiento, diapositivas de clase, 9° semestre, Universidad ECCI, 2025.
