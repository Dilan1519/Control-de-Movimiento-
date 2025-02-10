# ¿QUÉ ES EL MOVIMIENTO DE CONTROL?

El control de movimiento es una disciplina de la ingeniería que regula y coordina el desplazamiento de objetos mediante actuadores, sensores y algoritmos de control. Su aplicación es esencial en sectores como la manufactura, la robótica y la automatización de procesos. Es fundamental para garantizar precisión, eficiencia y optimización en sistemas industriales, mejorando la productividad y reduciendo errores. Su desarrollo ha permitido la evolución de máquinas inteligentes capaces de realizar operaciones con alta exactitud, impulsando la modernización y el avance tecnológico en diversas industrias.

## Indice

## 1. ¿En qué consiste?

El control de movimiento, también llamado control de posicionamiento servo, consite en el proceso de mover una carga en un sistema mecánico.

💡**Ejemplo 1:** Un ejemplo antiguo de control de movimiento es el telar Jacquard (1801). Este telar automatizado, desarrollado por Joseph Marie Jacquard, utilizaba tarjetas perforadas para controlar el movimiento de los hilos en la fabricación de textiles con patrones complejos.

<div align="center">
  <img src="SI.png" alt="Figura de prueba" width="400">
  <p><b>Figura 1.</b> Figura de prueba</p>
</div>

## Movimientos del telar Jacquard:

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
  
## 2. ¿En qué industria se usa?:

A continuación, se muestra una tabla con las industrias donde se usa el control de movimiento, los tipos de máquinas que emplean esta tecnología, los países donde es más común y los beneficios clave en cada sector.

| **Industria**              | **Tipos de Máquinas**                                | **Países donde más se usan**      | **Beneficios clave**                                     |
|----------------------------|-----------------------------------------------------|---------------------------------|---------------------------------------------------------|
| **Empaque**                | Máquinas de envasado, cintas transportadoras, etiquetadoras | EE.UU., Alemania, China, México | Mayor velocidad, precisión en el empaquetado y reducción de desperdicios. |
| **Ensamblaje**             | Robots ensambladores, sistemas pick & place, CNC   | Japón, Alemania, Corea del Sur  | Ensamblaje preciso, reducción de costos y automatización avanzada. |
| **Impresión**              | Impresoras industriales, máquinas flexográficas     | EE.UU., China, Alemania, Brasil | Alta resolución, sincronización del material y rapidez de producción. |
| **Productos de madera**    | Sierras automáticas, cepilladoras CNC, routers CNC  | Canadá, EE.UU., Suecia, Brasil  | Corte preciso, optimización del material y reducción de errores. |
| **Maquinaria**             | Torno CNC, fresadoras, robots industriales         | Alemania, Japón, Italia, China  | Producción eficiente, mayor seguridad y reducción de tiempo de operación. |
| **Eléctrica/Semiconductores** | Máquinas de soldadura PCB, ensambladoras SMT       | Taiwán, Corea del Sur, China, EE.UU. | Ensamblaje de componentes de alta velocidad y precisión en micras. |

> **Nota:** Esta tabla presenta solo algunos ejemplos de aplicaciones y países donde el control de movimiento es clave en la industria.

## 3. Ejes de Movimiento:
Cada movimiento generado por un actuador en un sistema de control se denomina **eje de movimiento (axis)**. Un sistema puede tener múltiples ejes, y su sincronización es esencial para realizar tareas complejas con precisión y eficiencia.

## Tipos de Ejes de Movimiento

| Tipo de Eje         | Descripción | Ejemplo |
|--------------------|-------------|---------|
| 🏭 **Eje Lineal** | Movimiento en línea recta a lo largo de un solo eje (X, Y o Z). | Un torno CNC mueve el cortador en el eje X para dar forma a la pieza. |
| 🔧 **Eje Rotacional** | Movimiento giratorio alrededor de un eje fijo. | Un brazo robótico de ensamblaje rota en el eje Z para ajustar una pieza. |
| 📄 **Ejes Coordinados** | Múltiples ejes que trabajan en sincronización para realizar una tarea. | En una impresora, el cartucho de tinta se mueve en el eje X, mientras que el rodillo mueve el papel en el eje Y. |
| 🤖 **Ejes Interpolados** | Movimiento combinado de varios ejes para generar trayectorias complejas. | Un robot industrial realiza movimientos curvos en 3D con interpolación de sus ejes. |

## 4. ¿Qué se controla?:

El control de movimiento puede regular posición, velocidad, torque y aceleración. Dependiendo de la aplicación, se pueden controlar las cuatro variables, solo tres, dos o una.

>🔑 *Posición:* Determina la ubicación exacta de un objeto en el espacio. Se controla para asegurar que un mecanismo llegue a un punto específico con precisión.
>
>🔑 *Velocidad:* Regula la rapidez con la que un objeto se mueve de un punto a otro. Es crucial para evitar vibraciones y mejorar la eficiencia del proceso.
>
>🔑 *Torque:* Es la fuerza de giro aplicada a un eje o motor. Controlarlo permite garantizar que un sistema pueda mover cargas sin sobrecargas o fallos mecánicos.
>
>🔑 *Acerleración:* Es la variación de la velocidad en el tiempo. Se controla para evitar movimientos bruscos y reducir el desgaste de los componentes.

💡**Ejemplo 2:** Controlando las 4 variables (posición, velocidad, torque y aceleración)

<div align="center">
  <img src="FANUC Arc Mate 100iC.jpg" alt="Figura de prueba" width="400">
  <p><b>Figura 2.</b> Robot  FANUC Arc Mate 100iC </p>
</div>

- **Posición:** El brazo robótico debe moverse con precisión milimétrica para soldar en el punto exacto.

- **Velocidad:** Se ajusta para evitar sobrecalentamiento o defectos en la soldadura.

- **Torque:** Se controla para aplicar la presión adecuada en la unión de las piezas.

- **Aceleración:** Se regula para evitar movimientos bruscos que puedan afectar la calidad de la soldadura.

💡**Ejemplo 3:** Controlando 3 variables (posición, velocidad y torque)

<div align="center">
  <img src="CNC de fresado Haas VF-2.jpeg" alt="Figura de prueba" width="400">
  <p><b>Figura 3.</b> CNC de fresado Haas VF-2 </p>
</div>

- **Posición:** La herramienta debe ubicarse exactamente en la coordenada correcta para realizar cortes precisos.

- **Velocidad:** La velocidad de corte se ajusta según el material para evitar sobrecalentamiento o desgaste prematuro.

- **Torque:** Se regula para asegurar la fuerza suficiente en el mecanizado sin dañar la pieza.

- **Aceleración:** No se controla la aceleración directamente, ya que no es crítica para este proceso.

💡**Ejemplo 4:** Controlando 2 variables (posición y velocidad)

<div align="center">
  <img src="Cinta transportadora con parada automática ConveyLinx.avif" alt="Figura de prueba" width="400">
  <p><b>Figura 3.</b> Cinta transportadora con parada automática ConveyLinx </p>
</div>

- **Posición:** Se detiene exactamente en el punto donde debe descargarse un producto.

- **Velocidad:** Se ajusta para sincronizarse con otras máquinas de la línea de producción.

- **Torque:** No se controla el torque, porque la carga es liviana y no se requiere fuerza específica.

- **Aceleración:** No se controla la aceleración, ya que no es relevante en este tipo de movimiento

💡**Ejemplo 5:** Controlando solo 1 variable (torque)

<div align="center">
  <img src="Bosch GSR 18V-EC.jpg" alt="Figura de prueba" width="400">
  <p><b>Figura 3.</b> Cinta transportadora con parada automática ConveyLinx </p>
</div>

- **Posición:** No se controla la posición, porque no necesita ubicarse en coordenadas exactas.

- **Velocidad:** No se controla la velocidad, ya que funciona a una velocidad fija o ajustable manualmente.

- **Torque:** Se regula para apretar los tornillos con la fuerza exacta sin dañar la pieza.

- **Aceleración:** No se controla la aceleración, porque el usuario decide la rapidez del movimiento.

# ⏳ Historia del Control de Movimiento  

El control de movimiento no siempre fue electrónico. Antes de los motores y sensores modernos, los ingenieros usaban mecanismos mecánicos avanzados para lograr precisión y automatización.  

## 🏛️ 1. Primeros Métodos de Control Mecánico  

### 🔹 El Mundo Antiguo: Primeras Máquinas Autónomas  

#### ⚙️ Herón de Alejandría (Siglo I d.C.)  
- Inventó **puertas automáticas** en templos usando contrapesos.  
- Creó la **eolípila**, un dispositivo a vapor que anticipó las máquinas de vapor.  

#### 🔧 Los Autómatas Islámicos (Siglos IX - XIII)  
- **Al-Jazari** diseñó relojes automáticos y sistemas de bombeo de agua.  
- Creó mecanismos de engranajes y poleas para automatizar procesos.  

<details>
  <summary>📷 Ver Ejemplo</summary>
  <img src="https://upload.wikimedia.org/wikipedia/commons/9/95/Jacquard.loom.cards.jpg" width="400">
  <p>🔺 Telar Jacquard, un precursor del control automatizado.</p>
</details>

## ⚙️ 2. Revolución Industrial: La Era del Control Mecánico  

### 🌍 **Países Pioneros en la Automatización Mecánica**  
| País | Industria Destacada |
|------|--------------------|
| 🇬🇧 Reino Unido | Máquinas de vapor y telares |
| 🇫🇷 Francia | Industria textil y relojería |
| 🇩🇪 Alemania | Metalurgia y manufactura |

### 🏭 Ejemplo: **El Telar de Jacquard (1804)**  
- **Inventor:** Joseph Marie Jacquard (Francia).  
- **Innovación:** Tarjetas perforadas para controlar el patrón del tejido.  
- **Impacto:** Primera máquina en programarse sin intervención humana directa.  

### 🚂 Ejemplo: **Regulador de Watt (1788)**  
- **Inventor:** James Watt (Inglaterra).  
- **Innovación:** Regulador centrífugo para mantener estable la velocidad de las máquinas de vapor.  
- **Impacto:** Primer sistema de **retroalimentación mecánica**.  

## 🔩 3. ¿Cómo Funcionaban Sin Control Electrónico?  

| Mecanismo | Función | Ejemplo |
|-----------|---------|---------|
| **Engranajes y ruedas de levas** | Generar movimientos repetitivos | Telares mecánicos |
| **Cajas de cambio y árboles de transmisión** | Transmitir energía a varias máquinas | Fundiciones de acero |
| **Mecanismos de frenado y relojes de control** | Regular procesos en intervalos de tiempo | Molinos de viento |
| **Sistemas de tarjetas perforadas** | Programar secuencias automáticas | Máquinas textiles |

## ⚠️ 4. Desventajas de los Métodos Antiguos  

❌ **Poca flexibilidad**: Modificar una máquina requería reconstruir todo el sistema.  
❌ **Errores por desgaste**: Engranajes y levas perdían precisión con el tiempo.  
❌ **Altos costos de mantenimiento**: Reemplazar piezas dañadas era caro.  
❌ **Dependencia del operador**: Se necesitaban trabajadores para supervisar.  


