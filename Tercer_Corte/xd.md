# 🔧 Análisis Cinemático de un Mecanismo de Cuatro Barras con Deslizador

## ✅ Paso 1: Definición del Mecanismo y sus Parámetros

Estamos analizando un sistema de cuatro barras donde una barra es un deslizador horizontal.

### Elementos del mecanismo:
- **A**: Longitud de la barra de entrada → ``
- **B**: Longitud de la barra intermedia → ``
- **C**: Longitud de la barra deslizante → `variable`
- **D**: Altura fija del deslizador → ``
- **ΘA**: Ángulo de la barra A con respecto al eje X
- **ΘB**: Ángulo de la barra B con respecto al eje X

### 🎯 Objetivo:
Determinar las posiciones de los puntos **P** y **Q**, y la longitud del deslizador **C** en función del ángulo **ΘA**.

---

## ✅ Paso 2: Identificación del Triángulo y Aplicación del Teorema del Coseno

Se forma un triángulo con los puntos:
- Origen `(0, 0)`
- Punto **P** (unión entre barras A y B)
- Punto **Q** (extremo del deslizador)

### Lados del triángulo:
- Lado **A**: Desde el origen hasta **P**
- Lado **B**: Entre **P** y **Q**
- Lado **C**: Desde el origen hasta **Q**

### Teorema del Coseno:
$$
B^2 = (Q_x - P_x)^2 + (Q_y - P_y)^2
$$

---

## ✅ Paso 3: Descomposición de Vectores en Coordenadas

### Punto **P** (final de la barra A):
$$
P_x = A \cdot \cos(\Theta_A) \\
P_y = A \cdot \sin(\Theta_A)
$$

### Punto **Q** (extremo del deslizador):
$$
Q_x = C \\
Q_y = D
$$

---

## ✅ Paso 4: Derivación de las Ecuaciones

Sustituyendo las coordenadas en la fórmula del teorema de Pitágoras:

$$
B^2 = (C - A\cos(\Theta_A))^2 + (D - A\sin(\Theta_A))^2
$$

### Expansión:

$$
B^2 = C^2 - 2AC\cos(\Theta_A) + A^2\cos^2(\Theta_A) + D^2 - 2AD\sin(\Theta_A) + A^2\sin^2(\Theta_A)
$$

### Agrupando:

$$
B^2 = C^2 + D^2 + A^2(\cos^2(\Theta_A) + \sin^2(\Theta_A)) - 2AC\cos(\Theta_A) - 2AD\sin(\Theta_A)
$$

Usando la identidad trigonométrica:

$$
\cos^2(\Theta_A) + \sin^2(\Theta_A) = 1
4$

$$
B^2 = C^2 + D^2 + A^2 - 2AC\cos(\Theta_A) - 2AD\sin(\Theta_A)
$$

### Despejando **C**:

$$
C^2 - 2AC\cos(\Theta_A) = B^2 - D^2 - A^2 + 2AD\sin(\Theta_A)
$$

Aplicando la fórmula cuadrática para **C**:

$$
C = \frac{2A\cos(\Theta_A) \pm \sqrt{(2A\cos(\Theta_A))^2 - 4(B^2 - D^2 - A^2 + 2AD\sin(\Theta_A))}}{2}
$$

---

## ✅ Paso 5: Cálculo de la Distancia **H**

La distancia **H** es la distancia desde el origen hasta el deslizador:

$$
H = \sqrt{C^2 + D^2}
$$

O sustituyendo **C** con su valor:

$$
H = \sqrt{\left(A\cos(\Theta_A) + \sqrt{B^2 - (D - A\sin(\Theta_A))^2}\right)^2 + D^2}
$$

---

✅ **Resultado**: Esta serie de pasos permite determinar la posición del deslizador **C** y la distancia **H** en función del ángulo de entrada **ΘA**, utilizando geometría y trigonometría básicas.

# 🧮 Cálculo Numérico del Mecanismo con Deslizador

## ✅ Parámetros Seleccionados

- Longitud de la barra de entrada (**A**) = 10 mm  
- Longitud de la barra intermedia (**B**) = 30 mm  
- Altura del deslizador (**D**) = 30 mm  
- Ángulo de entrada (**ΘA**) = 10°  

---

## ✅ 1. Conversión del Ángulo a Radianes

$$
\Theta_A = 10^\circ = \frac{10 \cdot \pi}{180} \approx 0.1745 \, \text{rad}
$$

---

## ✅ 2. Coordenadas del Punto **P**

Usamos trigonometría para obtener las coordenadas:

$$
P_x = A \cdot \cos(\Theta_A) = 10 \cdot \cos(0.1745) \approx 9.85 \, \text{mm}
$$

$$
P_y = A \cdot \sin(\Theta_A) = 10 \cdot \sin(0.1745) \approx 1.74 \, \text{mm}
$$

---

## ✅ 3. Cálculo del Deslizador **C**

Aplicando la fórmula cuadrática deducida anteriormente, se obtienen dos soluciones para **C**:

$$
C_1 = 19.48 \, \text{mm} \quad \text{(Solución principal esperada)}
$$


$$
C_2 = 0.22 \, \text{mm} \quad \text{(Solución secundaria, cercana al origen)}
$$

Ambas soluciones son matemáticamente válidas, representando dos posibles configuraciones del mecanismo.

---

## ✅ 4. Cálculo de las Distancias **H**

La distancia desde el origen al deslizador **Q** para cada valor de **C** es:

$$
H_1 = \sqrt{C_1^2 + D^2} = \sqrt{19.48^2 + 30^2} \approx 35.77 \, \text{mm}
$$

$$
H_2 = \sqrt{C_2^2 + D^2} = \sqrt{0.22^2 + 30^2} \approx 30.00 \, \text{mm}
$$

---

## 📌 Conclusión

- La configuración **C₁ = 19.48 mm** representa una posición física coherente del deslizador.
- La distancia **H₁ = 35.77 mm** indica la extensión real del sistema desde el origen al extremo del deslizador en esta configuración.
- La solución **C₂ = 0.22 mm**, aunque válida, probablemente corresponde a una posición muy plegada o cercana al pivote, menos utilizada en operación práctica.




