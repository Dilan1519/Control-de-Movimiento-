# Gemelos Digitales de Quancer

En esta unidad se aborda el control de movimiento utilizando herramientas modernas como Quanser y Simulink, con énfasis en el sistema Qube-Servo 2. Este dispositivo es una planta didáctica que permite experimentar con principios de control real y diseño de sistemas dinámicos.

A lo largo de la práctica, se trabajará tanto con la planta física como con sus gemelos digitales, lo que permite simular, analizar y validar algoritmos de control antes de aplicarlos al sistema real.

Además, se estudiará la configuración básica del sistema, incluyendo:

- El uso de bloques de conexión en Simulink.

- Lectura de variables físicas como la posición angular a través del encoder.

- Monitoreo de señales como la corriente suministrada al motor.

- Comprensión de cómo interactúan estos elementos dentro del entorno de simulación y control.

Este enfoque integral busca desarrollar una visión clara del funcionamiento del sistema de control desde su modelado hasta su implementación.

# 1. Configuración inicial: Instalación y conexión

Para trabajar con el Qube-Servo 2 desde Simulink, es necesario configurar correctamente el entorno de trabajo. Esto incluye instalar los complementos (_add-ons_) necesarios para conectar tanto con la planta física como con los gemelos digitales.

## Complementos necesarios

<div align="center">
  
| Complemento                  | Función                                       | Licencia      | Disponible en casa | Disponible en laboratorio |
|-----------------------------|-----------------------------------------------|---------------|--------------------|---------------------------|
| Quanser QLabs/QSim Add-On   | Permite la conexión con los gemelos digitales | Gratuito      | Si              | Si                        |
| Quanser Hardware Add-On     | Permite la conexión con la planta física      | Licencia paga | No                  | Si (instalado)            |

</div>

> **Nota**: Las pruebas con la planta física solo se pueden realizar en los computadores del laboratorio, ya que requieren licencias especiales.

## 2. Paso a paso: Configuración inicial

### Instalar el complemento para gemelos digitales

1. Abrir MATLAB.
   
<div align="center">
  <img src="Imágenes_Corte_3/Clase%20%2310/Paso 0.png" alt="Figura de prueba" width="400">
  <p><b>Figura 1.</b> Abrir Matlab </p>
</div>

3. Ir a la pestaña **“Add-Ons”** y seleccionar **“Get Add-Ons”**.



5. Buscar **"Quanser QLabs"** o **"Quanser Virtual Qube-Servo 2"**.
6. Instalar el complemento correspondiente.

  


<div align="center">
  <img src="Imágenes_Corte_3/Clase%20%2310/Paso_1_Quanser.jpg" alt="Figura de prueba" width="400">
  <p><b>Figura 1.</b> Abrir Smnew </p>
</div>

<div align="center">
  <img src="Imágenes_Corte_3/Clase%20%2310/Paso_2_Quanser.jpg" alt="Figura de prueba" width="400">
  <p><b>Figura 1.</b> Abrir Smnew </p>
</div>

<div align="center">
  <img src="Imágenes_Corte_3/Clase%20%2310/Paso_3_Quanser.jpg" alt="Figura de prueba" width="400">
  <p><b>Figura 1.</b> Abrir Smnew </p>
</div>

<div align="center">
  <img src="Imágenes_Corte_3/Clase%20%2310/Paso_4_Quanser.jpg" alt="Figura de prueba" width="400">
  <p><b>Figura 1.</b> Abrir Smnew </p>
</div>

<div align="center">
  <img src="Imágenes_Corte_3/Clase%20%2310/Paso_5_Quanser.jpg" alt="Figura de prueba" width="400">
  <p><b>Figura 1.</b> Abrir Smnew </p>
</div>

<div align="center">
  <img src="Imágenes_Corte_3/Clase%20%2310/Paso_6_Quanser.jpg" alt="Figura de prueba" width="400">
  <p><b>Figura 1.</b> Abrir Smnew </p>
</div>

<div align="center">
  <img src="Imágenes_Corte_3/Clase%20%2310/Paso_7_Quanser.jpg" alt="Figura de prueba" width="400">
  <p><b>Figura 1.</b> Abrir Smnew </p>
</div>

<div align="center">
  <img src="Imágenes_Corte_3/Clase%20%2310/Paso_8_Quanser.jpg" alt="Figura de prueba" width="400">
  <p><b>Figura 1.</b> Abrir Smnew </p>
</div>

<div align="center">
  <img src="Imágenes_Corte_3/Clase%20%2310/Paso_9_Quanser.jpg" alt="Figura de prueba" width="400">
  <p><b>Figura 1.</b> Abrir Smnew </p>
</div>

<div align="center">
  <img src="Imágenes_Corte_3/Clase%20%2310/Paso_10_Quanser.jpg" alt="Figura de prueba" width="400">
  <p><b>Figura 1.</b> Abrir Smnew </p>
</div>

<div align="center">
  <img src="Imágenes_Corte_3/Clase%20%2310/Paso_11_Quanser.jpg" alt="Figura de prueba" width="400">
  <p><b>Figura 1.</b> Abrir Smnew </p>
</div>

<div align="center">
  <img src="Imágenes_Corte_3/Clase%20%2310/Paso_12_Quanser.jpg" alt="Figura de prueba" width="400">
  <p><b>Figura 1.</b> Abrir Smnew </p>
</div>

<div align="center">
  <img src="Imágenes_Corte_3/Clase%20%2310/Paso_13_Quanser.jpg" alt="Figura de prueba" width="400">
  <p><b>Figura 1.</b> Abrir Smnew </p>
</div>

<div align="center">
  <img src="Imágenes_Corte_3/Clase%20%2310/Paso_14_Quanser.jpg" alt="Figura de prueba" width="400">
  <p><b>Figura 1.</b> Abrir Smnew </p>
</div>

<div align="center">
  <img src="Imágenes_Corte_3/Clase%20%2310/Paso_15_Quanser.jpg" alt="Figura de prueba" width="400">
  <p><b>Figura 1.</b> Abrir Smnew </p>
</div>

<div align="center">
  <img src="Imágenes_Corte_3/Clase%20%2310/Paso_16_Quanser.jpg" alt="Figura de prueba" width="400">
  <p><b>Figura 1.</b> Abrir Smnew </p>
</div>

<div align="center">
  <img src="Imágenes_Corte_3/Clase%20%2310/Paso_17_Quanser.jpg" alt="Figura de prueba" width="400">
  <p><b>Figura 1.</b> Abrir Smnew </p>
</div>

<div align="center">
  <img src="Imágenes_Corte_3/Clase%20%2310/Paso_18_Quanser.jpg" alt="Figura de prueba" width="400">
  <p><b>Figura 1.</b> Abrir Smnew </p>
</div>

<div align="center">
  <img src="Imágenes_Corte_3/Clase%20%2310/Paso_19_Quanser.jpg" alt="Figura de prueba" width="400">
  <p><b>Figura 1.</b> Abrir Smnew </p>
</div>

<div align="center">
  <img src="Imágenes_Corte_3/Clase%20%2310/Motor_Movimiento.gif" alt="Figura de prueba" width="400">
  <p><b>Figura 1.</b> Abrir Smnew </p>
</div>



## 5. Conclusiones


## 6. Bibliografía

[1] MathWorks, "Simscape Multibody," [En línea]. Disponible: https://la.mathworks.com/products/simscape.html. [Accedido: 06-Mar-2025].
