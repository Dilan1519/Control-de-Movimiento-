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

- Abrir MATLAB.
   
<div align="center">
  <img src="Imágenes_Corte_3/Clase%20%2310/Paso 0.png" alt="Figura de prueba" width="400">
  <p><b>Figura 1.</b> Abrir Matlab </p>
</div>

- Ir a la pestaña Add-Ons y seleccionar Get Add-Ons.

<div align="center">
  <img src="Imágenes_Corte_3/Clase%20%2310/Paso_03.png" alt="Figura de prueba" width="800">
  <p><b>Figura 2.</b> Add-Ons & Add-Ons </p>
</div>

- Buscar Quanser QLabs.

<div align="center">
  <img src="Imágenes_Corte_3/Clase%20%2310/Paso_2_Quanser.jpg" alt="Figura de prueba" width="800">
  <p><b>Figura 3.</b> Quanser QLabs </p>
</div>

- Instalar el complemento correspondiente.

<div align="center">
  <img src="Imágenes_Corte_3/Clase%20%2310/Paso_1_Quanser.jpg" alt="Figura de prueba" width="400">
  <p><b>Figura 4.</b>Instalar el complemento</p>
</div>

## Registro en la plataforma QLabs

Antes de usar la plataforma, debes registrarte en el sguiente enlace:  https://portal.quanser.com/Accounts/Login?returnUrl=/.

Usa exclusivamente tu correo institucional, ya que es el que será habilitado para acceder a la plataforma.

<div align="center">
  <img src="Imágenes_Corte_3/Clase%20%2310/Paso_4_Quanser.jpg" alt="Figura de prueba" width="400">
  <p><b>Figura 5.</b> Inico de Sesión </p>
</div>

## Configuración del entorno para el gemelo digital

Después de instalar el complemento para QLabs, es necesario ejecutar algunos comandos desde la ventana de comandos de MATLAB (_Command Window_) para habilitar la conexión con el entorno virtual.

- Ejecutar el siguiente comando en la ventana de comandos:

   ```matlab
   QLabs.setup

Este comando configura automáticamente los recursos necesarios para usar el gemelo digital. Internamente ejecuta procesos como sl_customization y otros necesarios para que todo quede listo.

- Luego, ejecutar el segundo comando:

   ```matlab
   QLabs.launch

<div align="center">
  <img src="Imágenes_Corte_3/Clase%20%2310/Paso_3_Quanser.jpg" alt="Figura de prueba" width="800">
  <p><b>Figura 6.</b>Comandos QLabs.setup & QLabs.launch</p>
</div>

Esto abrirá una ventana emergente con la opción de seleccionar una de las 3 plantas disponibles (entre ellas, el Qube-Servo 2).

<div align="center">
  <img src="Imágenes_Corte_3/Clase%20%2310/Paso_5_Quanser.jpg" alt="Figura de prueba" width="600">
  <p><b>Figura 7.</b> Ventana Emergente de las 3 plantas </p>
</div>

<div align="center">
  
| Producto         | Sensores principales                                                                 | Actuadores        | Características clave                                                                                   | Tipo de sistema               |
|------------------|----------------------------------------------------------------------------------------|-------------------|-----------------------------------------------------------------------------------------------------------|-------------------------------|
| **Qube-Servo 2** (DC Motor) | - Encoder rotativo  <br> - Sensor de corriente                                 | Motor DC          | - Sistema de control de posición y velocidad <br> - Ideal para control PID, LQR y observadores           | Rotacional simple             |
| **Aero**         | - Encoders rotativos (ejes de *pitch* y *yaw*) <br> - Sensor de corriente              | Motores *brushless* | - Sistema aéreo con 2 grados de libertad <br> - Simula el control de una aeronave                        | Rotacional 2D (aeronáutico)   |
| **Ball and Beam**| - Potenciómetro (ángulo del brazo) <br> - Sensor óptico (posición de la bola)         | Motor DC          | - Sistema no lineal y sub-actuado <br> - Ideal para control avanzado (estado, realimentación)           | Traslacional con oscilación   |

</div>

- Recursos clave para el Qube-Servo 2

<div align="center">
  <img src="Imágenes_Corte_3/Clase%20%2310/Manuales.png" alt="Figura de prueba" width="600">
  <p><b>Figura 8.</b> Recursos </p>
</div>

A continuación, se presentan enlaces clave para profundizar en el estudio y uso del Qube-Servo 2, tanto en su versión física como virtual. Estos materiales incluyen documentación técnica, guías prácticas y simulaciones listas para usar en Simulink.

<div align="center">
  
| Recurso                                                                                                      | Descripción                                                                                                                                         |
|-------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------|
| 🔗 [Repositorio de recursos virtuales de Quanser](https://www.quanser.com/resource-type/virtual-resources/?_products=1590) | Página oficial con materiales interactivos, simulaciones y manuales orientados a la enseñanza y uso del gemelo digital del Qube-Servo 2.           |
| 🔗 [Carpeta Box con laboratorios y archivos de simulación](https://quanserinc.app.box.com/s/5x59eq0l1ygebs6uyexnmcshwxxqish6) | Contiene modelos en Simulink, ejercicios prácticos, controladores PID y experimentos de control más avanzados. Ideal para estudiantes.             |
| 🔗 [Manual de usuario del Qube-Servo 2 (PDF)](https://wwwlehre.dhbw-stuttgart.de/~flaemig/MATLAB/Quanser_CubeServo/QUBE-Servo%20User%20Manual.pdf) | Documento técnico detallado con especificaciones, conexiones, sensores, actuadores y recomendaciones para el uso correcto de la planta física.     |

</div>

> **Nota**: En los siguientes enlaces se pueden encontrar manuales importantes del Qube-Servo 2, incluyendo simulaciones listas para usar como controladores **PID**, entre otras herramientas clave para el aprendizaje práctico:

## Creación del esquema básico en Simulink para el Qube-Servo 2

Para comenzar a trabajar con la planta virtual o física del Qube-Servo 2, es necesario construir un modelo en Simulink que permita la comunicación con el hardware (real o virtual). A continuación, se detalla el procedimiento paso a paso:

- Abrir Simulink

En la ventana de comandos de MATLAB, escribe:

   ```matlab
   Simulink
   ```
Presiona Enter.

- En la ventana de Simulink, selecciona Blank Model para iniciar con un archivo vacío.

<div align="center">
  <img src="Imágenes_Corte_3/Clase%20%2310/Blank Model.png" alt="Figura de prueba" width="600">
  <p><b>Figura 10.</b> Blank Model </p>
</div>

- Crear un nuevo archivo
  
En la ventana de Simulink, selecciona "Blank Model" para iniciar con un archivo vacío.

<div align="center">
  <img src="Imágenes_Corte_3/Clase%20%2310/Paso_8_Quanser.jpg" alt="Figura de prueba" width="400">
  <p><b>Figura 1.</b> Abrir Smnew </p>
</div>

- Abrir el Library Browser

Haz clic en el ícono de librerías en la parte superior izquierda o usa el atajo Ctrl + Shift + L.

<div align="center">
  <img src="Imágenes_Corte_3/Clase%20%2310/Paso_6_Quanser.jpg" alt="Figura de prueba" width="400">
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
