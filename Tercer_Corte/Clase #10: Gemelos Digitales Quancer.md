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

- Abrir el Library Browser

Haz clic en el ícono de librerías en la parte superior izquierda o usa el atajo Ctrl + Shift + L.

<div align="center">
  <img src="Imágenes_Corte_3/Clase%20%2310/Paso_8_Quanser.jpg" alt="Figura de prueba" width="800">
  <p><b>Figura 11.</b> Library Browser </p>
</div>

- Verificar instalación de QUARC

Si el complemento está instalado correctamente, deberías ver una sección llamada:

QUARC Targets

<div align="center">
  <img src="Imágenes_Corte_3/Clase%20%2310/Paso_9_Quanser.jpg" alt="Figura de prueba" width="300">
  <p><b>Figura 12.</b> QUARC Targets </p>
</div>

- Navegar por las bibliotecas

Ir a:

QUARC Targets → Data Acquisition → Generic → Configuration

<div align="center">
  <img src="Imágenes_Corte_3/Clase%20%2310/Paso_10_Quanser.jpg" alt="Figura de prueba" width="300">
  <p><b>Figura 13.</b> QUARC Targets </p>
</div>

- Agregar el bloque HIL Initialize

Arrastra el bloque HIL Initialize al lienzo del modelo.

<div align="center">
  <img src="Imágenes_Corte_3/Clase%20%2310/Paso_11_Quanser.jpg" alt="Figura de prueba" width="300">
  <p><b>Figura 14.</b> bloque HIL Initialize </p>
</div>

## Configuración del bloque HIL Initialize

Una vez agregado el bloque HIL Initialize, es necesario configurarlo correctamente para establecer la comunicación con el Qube-Servo 2 virtual. Sigue estos pasos:

- Haz doble clic sobre el bloque HIL Initialize para abrir su configuración.

<div align="center">
  <img src="Imágenes_Corte_3/Clase%20%2310/Paso_12_Quanser.jpg" alt="Figura de prueba" width="400">
  <p><b>Figura 15.</b> Configuración Bloque HIL Initialize </p>
</div>

- En la pestaña Main, configura lo siguiente:

   - Board type:

     ```plaintext
     qube_servo2_usb
     ```

  - Haz clic en el botón Defaults para cargar los parámetros por defecto del sistema.

   - Board identifier:

     ```plaintext
     0@tcpip://localhost:18920
     ```

- Este identificador establece la conexión con el disco del Qube-Servo 2 virtual.

   - Marca la casilla:

     ```
     Active during normal simulation
     ```

- Haz clic en OK para cerrar la ventana y aplicar la configuración.

- Verificación y ejecución

- Asegúrate de que el disco del Qube-Servo 2 esté abierto en Quanser Interactive Labs (desde la ventana que aparece al ejecutar `QLabs.launch`).

- Luego, en Simulink, haz clic en el botónn Run (pestaña *Simulation*) para ejecutar el modelo usando QUARC.

<div align="center">
  <img src="Imágenes_Corte_3/Clase%20%2310/Paso_13_Quanser.jpg" alt="Figura de prueba" width="400">
  <p><b>Figura 16.</b> Run </p>
</div>

Si todo está configurado correctamente, la tira LED del Qube-Servo 2 se pondrá verde, indicando que hay una conexión activa entre el modelo de Simulink y el gemelo digital.

<div align="center">
  <img src="Imágenes_Corte_3/Clase%20%2310/Paso_14_Quanser.jpg" alt="Figura de prueba" width="400">
  <p><b>Figura 17.</b> Conexión activa </p>
</div>

## Agregar el bloque HIL Read Encoder Timebase

QUARC Targets → Data Acquisition → Generic → Timebases

- Arrastra el bloque HIL Read Encoder Timebase al modelo.
  
<div align="center">
  <img src="Imágenes_Corte_3/Clase%20%2310/Paso_15_Quanser.jpg" alt="Figura de prueba" width="400">
  <p><b>Figura 18.</b> Bloque HIL Read Encoder Timebase</p>
</div>

- Haz doble clic sobre el bloque y configura:

En la pestaña Main:

Marca la opción Active during normal simulation

<div align="center">
  <img src="Imágenes_Corte_3/Clase%20%2310/Paso_16_Quanser.jpg" alt="Figura de prueba" width="400">
  <p><b>Figura 19.</b> Active during </p>
</div>

- Conecta un bloque Constant al bloque HIL Write Analog, para enviar un valor de voltaje fijo al motor (puedes comenzar con un valor bajo, por ejemplo, 1 o 0.5).

<div align="center">
  <img src="Imágenes_Corte_3/Clase%20%2310/Write Analog.png" alt="Figura de prueba" width="500">
  <p><b>Figura 20.</b> Conexiones </p>
</div>

- Observación del comportamiento

Al ejecutar el modelo con esta configuración:

- El motor comienza a girar de forma continua en una dirección.

- No presenta problemas de arranque ni vibraciones anormales.

- La respuesta es estable y proporcional al valor enviado.

<div align="center">
  <img src="Imágenes_Corte_3/Clase%20%2310/Motor_Movimiento.gif" alt="Figura de prueba" width="400">
  <p><b>Figura 21.</b> Preuba </p>
</div>

## Configuración en el bloque HIL Read Encoder Timebase (Lectura de corriente)

Aunque el bloque originalmente se usa para leer encoders, también permite configurar la lectura de otras entradas, como señales analógicas.

- Haz doble clic en el bloque HIL Read Encoder Timebase.

- En la pestaña Main, localiza la opción Analog channels.

<div align="center">
  <img src="Imágenes_Corte_3/Clase%20%2310/Corriente_1.png" alt="Figura de prueba" width="400">
  <p><b>Figura 22.</b>  Analog channel </p>
</div>

- Haz clic en los tres puntos (...) a la derecha de esa opción para abrir el editor de canales.

- En la ventana emergente:

Busca en la sección Available channels el canal llamado:

Motor current sense A

- Selecciónalo y haz clic en la flecha hacia la derecha (→) para moverlo a la sección Selected channels.

<div align="center">
  <img src="Imágenes_Corte_3/Clase%20%2310/Corriente_2.png" alt="Figura de prueba" width="400">
  <p><b>Figura 23.</b>  Analog channel </p>
</div>

- Haz clic en OK para cerrar el editor de canales y aplicar la selección.

- Esquema para visualizar la señal de corriente
  
Una vez configurado el bloque HIL Read Encoder Timebase para incluir la lectura de la corriente, podemos visualizar esa señal en tiempo real usando los bloques estándar de Simulink.

- Identifica la salida del bloque HIL Read Encoder Timebase correspondiente a la corriente (usualmente la segunda salida si el encoder es la primera).

Añade al modelo los siguientes bloques desde la librería de Simulink:

Simulink → Sinks → Scope

Simulink → Sinks → Display

<div align="center">
  <img src="Imágenes_Corte_3/Clase%20%2310/Corriente_4.png" alt="Figura de prueba" width="400">
  <p><b>Figura 24.</b>  Bloques </p>
</div>

Conecta la salida de corriente a ambos bloques:

<div align="center">
  <img src="Imágenes_Corte_3/Clase%20%2310/Corriente_3.png" alt="Figura de prueba" width="600">
  <p><b>Figura 25.</b>  Señal de Corriente en Amperios </p>
</div>

 
## Configuración del bloque HIL Read Encoder Timebase (Encoder- Posición)

Ya tenemos este bloque en el modelo, y ahora debemos asegurarnos de que lea también la posición.

- Haz doble clic sobre el bloque HIL Read Encoder Timebase.

- En la pestaña Main, localiza la opción Encoder channels.

<div align="center">
  <img src="Imágenes_Corte_3/Clase%20%2310/Encoder_1.png" alt="Figura de prueba" width="400">
  <p><b>Figura 26.</b>  Encoder </p>
</div>

- Haz clic en los tres puntos (...) a la derecha para abrir el editor de canales.

En la ventana emergente:

- Busca en Available channels el canal:

<div align="center">
  <img src="Imágenes_Corte_3/Clase%20%2310/Encoder_2.png" alt="Figura de prueba" width="400">
  <p><b>Figura 27.</b>  Encoder </p>
</div>

- Pásalo a Selected channels usando la flecha (→).

- Haz clic en OK para guardar los cambios.

## Conversión de cuentas a grados

El encoder del Qube-Servo 2 mide la posición en cuentas. Para interpretar esta medición de forma más comprensible, debemos convertirla a grados.

<div align="center">
  <img src="Imágenes_Corte_3/Clase%20%2310/Encoder_4.png" alt="Figura de prueba" width="400">
  <p><b>Figura 28.</b>  Encoder </p>
</div>

- Relación de conversión

```plaintext
1 vuelta = 2048 cuentas = 360°
```

Grados = Cuentas × (360 / 2048)
       ≈ Cuentas × 0.1758

Ganancia ≈ 0.17578

- Añade al modelo los siguientes bloques desde la librería de Simulink:

Simulink → Sinks → Scope

Simulink → Sinks → Display

<div align="center">
    <img src="Imágenes_Corte_3/Clase%20%2310/Enocoder_3.png" alt="Figura de prueba" width="400">
  <p><b>Figura 29.</b>  Bloques </p>
</div>

Conecta la salida de Posición a ambos bloques:

<div align="center">
  <img src="Imágenes_Corte_3/Clase%20%2310/Encoder_5.png" alt="Figura de prueba" width="600">
  <p><b>Figura 30.</b>  Señal de Posición en Amperios </p>
</div>

## Lectura de la velocidad angular del motor

La velocidad angular indica qué tan rápido cambia la posición del motor, generalmente medida en grados por segundo (°/s) o radianes por segundo (rad/s).

Aunque no todos los sistemas entregan esta variable directamente, el Qube-Servo 2 sí lo permite a través del encoder, si está correctamente configurado.

- Configuración del bloque HIL Read Encoder Timebase para velocidad

- Haz doble clic en el bloque `HIL Read Encoder Timebase`.

- En la pestaña Main, busca la sección Other Channels.

<div align="center">
  <img src="Imágenes_Corte_3/Clase%20%2310/Tacometro_2.png" alt="Figura de prueba" width="600">
  <p><b>Figura 31.</b> Tacometro </p>
</div>

- Haz clic en los tres puntos `(...)` a la derecha para abrir el selector de canales.

 En la lista de Available channels, selecciona:

```plaintext
Tachometer 0
```

Pásalo a Selected channels usando la flecha (→) y haz clic en OK.

Como el tacometro esta de Cuentas/S , lo pasamos con la misma ganancia anterior:

Velocidad (°/s) = Cuentas/segundo × (360 / 2048)
                ≈ Cuentas/segundo × 0.17578

- Conecta la salida del canal de velocidad al bloque Gain.

<div align="center">
  <img src="Imágenes_Corte_3/Clase%20%2310/Tacometro_3.png" alt="Figura de prueba" width="600">
  <p><b>Figura 31.</b> Tacometro </p>
</div>

- Añade los siguientes bloques de visualización:

- Scope: Para ver cómo varía la velocidad angular en el tiempo.

- Display: Para visualizar el valor numérico en tiempo real.

<div align="center">
  <img src="Imágenes_Corte_3/Clase%20%2310/Tacometro_4.png" alt="Figura de prueba" width="600">
  <p><b>Figura 31.</b> Señal Velcodiad Angular </p>
</div>

## Conclusiones

- La conexión entre Simulink y Quanser requiere una configuración inicial específica, incluyendo la instalación del complemento de Quanser y la ejecución de comandos como QLabs.setup y QLabs.launch. Esto permite trabajar con gemelos digitales sin necesidad de tener la planta física siempre disponible.

- El bloque HIL Initialize es esencial para establecer la comunicación con la planta (física o virtual). Su correcta configuración garantiza que los demás bloques de adquisición y control funcionen adecuadamente durante la simulación.

- Es posible adquirir variables clave del sistema, como corriente, posición y velocidad angular, mediante los bloques de lectura (HIL Read Encoder Timebase). Estas señales deben procesarse con conversiones apropiadas (por ejemplo, cuentas a grados) para obtener valores interpretables.

- La visualización de las señales en tiempo real a través de Scope y Display es fundamental para el análisis del comportamiento del sistema. Esto permite verificar de forma intuitiva si el sistema está operando dentro de parámetros normales.

- Este entorno ofrece una plataforma sólida para implementar y probar estrategias de control como PID, y observar su impacto en variables del sistema como posición y velocidad, todo dentro de un entorno seguro y flexible que replica el comportamiento de la planta real.


## 6. Bibliografía

[1] J. E. Cote B., Control de movimiento con Quanser y Simulink, explicación oral, 9° semestre, Universidad ECCI, 2025.

[2] Quanser, QUBE-Servo 2 Virtual Plant Manual, disponible en: https://www.quanser.com/resource-type/virtual-resources/?_products=1590

[3] Quanser, Quanser QUBE-Servo 2 Documentation & Files, disponible en: https://quanserinc.app.box.com/s/5x59eq0l1ygebs6uyexnmcshwxxqish6

[4] Quanser, QUBE-Servo 2 User Manual (PDF), disponible en: https://wwwlehre.dhbw-stuttgart.de/~flaemig/MATLAB/Quanser_CubeServo/QUBE-Servo%20User%20Manual.pdf
