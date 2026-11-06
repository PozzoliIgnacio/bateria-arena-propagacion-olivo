---
Titulo esp.:
Año: 2026
Padre: "[[CUDAR - Desarrollo de Pila de Arena]]"
Importancia:
  - B
URL:
---
## 1. Idea central
El paper evalúa, mediante simulación en COMSOL Multiphysics y un análisis comparativo con baterías de ion-litio, si una **batería de arena de sílice** puede almacenar excedentes de energía fotovoltaica en forma de calor y devolverla a un **motor Stirling** tipo Beta que genera electricidad para una vivienda. 
El modelo de referencia carga 240,2 kg de arena con seis resistencias de 600 W durante 5 horas hasta unos 350 °C. 
La conclusión principal es que el sistema es **técnicamente viable y ambientalmente favorable**, con vida útil superior a 30 años y un costo inicial menor que el de litio (US$ 5 997 frente a US$ 11 050). 
Sus limitaciones son la **baja densidad energética**, la **baja eficiencia de conversión a electricidad** (20–35 %) y una ventana de temperatura útil corta (~42 min). Por eso el autor propone usarlo como **complemento o respaldo**, no como reemplazo de la red.
### Glosario

| Abreviatura | Significado |
|---|---|
| **CA / AC** | Corriente alterna |
| **CC / DC** | Corriente continua |
| **MPPT** | *Maximum Power Point Tracking*: seguimiento del punto de máxima potencia del panel |
| **AVR** | Regulador automático de voltaje del generador |
| **PV / FV** | Fotovoltaico |
| **COMSOL** | Software de simulación multifísica (térmica, eléctrica, etc.) |
| **CAPEX** | Gasto de capital (inversión inicial) |
| **GEI** | Gases de efecto invernadero |
| **PFAS** | Sustancias perfluoroalquiladas ("químicos eternos") |
| **bis-FASI** | Bis-perfluoroalquil sulfonimidas, tipo de PFAS presente en baterías de litio |
| **NREL** | Laboratorio Nacional de Energías Renovables (EE. UU.) |
| **ENDURING** | Proyecto NREL de almacenamiento térmico de larga duración |
| **INAMHI** | Instituto Nacional de Meteorología e Hidrología (Ecuador) |
| **k** (en el texto, "conductividad térmica") | Capacidad del material para conducir calor, en W/m·K |
| **c_p** | Calor específico: energía por unidad de masa para elevar 1 K |
| **ΔT** | Variación de temperatura |

## 2. Resumen por secciones
### 2.0 Resumen y Abstract
Presentan el objetivo, la metodología (cuantitativa, analítica y comparativa) y las palabras clave: batería de arena, almacenamiento térmico, autoabastecimiento, fotovoltaica y motor Stirling. No aportan cifras nuevas, pero sirven como mapa de todo el trabajo.
### 2.1 Introducción
- Plantea el contexto de la transición energética y la necesidad de almacenar energía de forma barata y limpia.
- Presenta la **arena de sílice** como medio de almacenamiento de bajo costo. Puede acumular calor y convertirlo en electricidad mediante un ciclo termodinámico.
- Compara la tecnología con las **baterías de ion-litio**, que son la referencia establecida.
- Anticipa dos temas: viabilidad técnica y financiera, y obstáculos para una aplicación a gran escala (infraestructura, aceptación social y regulación).
### 2.2 Metodología
Usan tres enfoques complementarios:
1. **Analítico:** descomponer el sistema en elementos (transferencia de calor, distribución térmica, eficiencia del Stirling, potencia eléctrica).
2. **Comparativo:** evaluar arena vs. litio según eficiencia, durabilidad, capacidad, impacto ambiental, facilidad de implementación y costo.
3. **Simulación:** modelado tridimensional en COMSOL de conductividad térmica de la arena, temperatura de las resistencias y eficiencia del intercambiador.
### 2.3 Arquitectura del sistema (cadena de conversión)
La energía sigue este recorrido:
1. **Captación:** paneles fotovoltaicos con eficiencia promedio del 21 %, producen CC.
2. **Regulación:** controlador MPPT que ajusta continuamente el punto de operación para extraer la máxima potencia.
3. **Conversión:** inversor CC → CA para alimentar las resistencias.
4. **Almacenamiento:** las resistencias calientan la arena (efecto Joule).
5. **Transferencia:** un intercambiador de calor extrae el calor de la arena y lo lleva al fluido de trabajo del Stirling.
6. **Conversión final:** el Stirling convierte calor en movimiento mecánico, y un generador síncrono lo transforma en electricidad.

Idea clave: hay **dos conversiones de energía** (eléctrica → calor, y calor → eléctrica). Cada una tiene pérdidas, y por eso la eficiencia global es baja.
### 2.4 Dimensionamiento fotovoltaico
- **Consumo mensual de referencia:** 346 kWh, a partir del promedio de distribuidoras.
- **Irradiancia:** 4,5 kWh/m²·día, valor representativo de Ecuador. Se usa para estimar la producción diaria de los paneles.
- **Arreglo:** 9 paneles Trina Solar TSM-400-DE 09 de 400 W (3,6 kW), en 3 cadenas de 3 paneles en serie.
- **Regulador:** Victron SmartSolar MPPT 150/85.
- **Inversor:** Victron MultiPlus-II 48/5000/70-50, con entrega continua de hasta 4 kW a 230 V y picos de hasta 9 kW.
### 2.5 Diseño térmico de la batería de arena
**Contenedor:** caja de acero inoxidable 304 con dimensiones externas de 0,6 × 0,6 × 0,835 m. Tiene 5 cm de aislante, por lo que el espacio útil es de 0,5 × 0,5 × 0,735 m, es decir, **0,184 m³**.
**Resistencias:** seis resistencias tubulares de 400 mm de largo, Ø 10 mm y 600 W a 230 V, distribuidas de forma equidistante (separación efectiva de 0,27 m) para evitar zonas frías.
![[Viabilidad tecnica y economica del uso de baterias de arena para el almacenamiento termico en el autoabastecimiento energetico residencial-1793780357631.webp]]*Vista superior con las seis resistencias en hexágono y el intercambiador en el centro. Muestra cómo se logra una distribución térmica homogénea.*

**Aislante:** fibra cerámica, elegida por su buena aislación a alta temperatura, bajo espesor y disponibilidad comercial.
![[Viabilidad tecnica y economica del uso de baterias de arena para el almacenamiento termico en el autoabastecimiento energetico residencial-1793780341086.webp]]
*Figura 3 — Diseño del contenedor con aislante, arena, resistencias e intercambiador. Muestra la caja completa con la tapa, la puerta lateral y los tubos de salida del intercambiador.*

**Masa de arena:** se calcula con el balance de calor sensible. Ver la sección 3 del análisis para la ecuación.
### 2.6 Intercambiador de calor
- Elegido: **carcasa y tubos**, que se integra de forma inmersa en la arena. Ventajas: resiste temperaturas altas (>600 °C según la literatura citada), es fácil de mantener, separa el fluido portador del foco térmico y permite configuraciones modulares.
- Alternativas descartadas: placas soldadas (limitaciones con temperaturas y presiones extremas), espirales (útiles con fluidos con partículas) e intercambiadores aire-aire (menor eficiencia).
### 2.7 Motor Stirling y generador
- **Tipo elegido: Beta.** Tiene un solo cilindro con desplazador y pistón. Es más simple que el Alfa (que requiere dos pistones sincronizados y mayor temperatura de arranque) y opera desde unos **300 °C**, temperatura que la batería sí puede alcanzar.
- **Potencia media requerida:** aproximadamente 194 W.
- **Generador:** síncrono monofásico de CA, 220 V y 60 Hz, con AVR para mantener el voltaje estable aunque varíe la velocidad del motor.
### 2.8 Resultados de la simulación en COMSOL
**Parámetros del modelo:** las Figuras 4 y 5 muestran las propiedades asignadas a las resistencias y a la arena (calor específico, densidad, conductividad térmica).

**Temperatura en el tiempo (Tabla 1):** 

| Tiempo (s) | Tiempo (h) | Temperatura (K) | Temperatura (°C) |
|---|---|---|---|
| 0 | 0 | 293,15 | 20 |
| 600 | 0,17 | 304,15 | 31 |
| 1 800 | 0,5 | 326,15 | 53 |
| 3 600 | 1 | 360,15 | 87 |
| 10 800 | 3 | 493,15 | 220 |
| 14 400 | 4 | 560,15 | 287 |
| 18 000 | 5 | 626,15 | 353 |
![[Viabilidad tecnica y economica del uso de baterias de arena para el almacenamiento termico en el autoabastecimiento energetico residencial-1793780711305.webp]]
Puntos destacados:
- El **pico de 626 K (353 °C)** supera el umbral de diseño de 623,15 K (350 °C). El autor lo atribuye a la inercia térmica y al aislamiento.
- La curva es **casi lineal** (~66 K/h), lo que se justifica porque la potencia de entrada es constante.
- La simulación confirma que la energía coincide con el balance de calor. Ver sección 3.
### 2.9 Comparación con ion-litio (Tablas 2 y 3)
- **Técnica (Tabla 2):** la arena tiene vida útil >30 años frente a 10–15 años del litio, y opera entre 200 y 600 °C. Pero tiene menor densidad energética (10–15 kWh/m³ frente a 200–250 kWh/m³) y menor eficiencia de conversión total (20–35 % frente a 90–95 %).
- **Ambiental (Tabla 3):** el litio tiene alto consumo de agua, 56–494 kg CO₂/kWh en producción, uso de materiales tóxicos y reciclabilidad limitada. La arena tiene consumo de agua bajo, emisiones mínimas y no usa materiales tóxicos.
- **Económica:** US$ 5 997 para el sistema con arena frente a US$ 11 050 para el de litio. El paper no aclara la moneda, pero el símbolo "$" sugiere dólares.
### 2.10 Discusión y conclusiones
- La batería de arena **no reemplaza** la red, sino que la **complementa** y reduce el consumo en horas pico o en zonas rurales con acceso intermitente.
- Los autores proponen que el **siguiente paso** es validar experimentalmente un prototipo a escala para confirmar la eficiencia térmica (89,91 %) y la conversión térmica-eléctrica (~35 %). Estas cifras son las estimaciones del paper.
- Líneas de trabajo futuro: mejorar la densidad energética y la eficiencia de conversión.
## 3. Parámetros técnicos clave

| Parámetro | Valor en el paper | Observación |
|---|---|---|
| **Volumen / masa de arena** | Masa: **240,2 kg** de arena de sílice seca de grano fino. Volumen útil: **0,184 m³** (0,5 × 0,5 × 0,735 m, calculado). | El volumen de arena no aparece explícitamente. La densidad aparente que se deduce es ~1 305 kg/m³. |
| **Potencia de carga** | **3,6 kW** (6 × 600 W) | Dato explícito. |
| **Energía de carga** | **64 800 kJ** (18 kWh) en **5 h** | Dato explícito. |
| **Energía útil almacenada** | **5,83 MJ ≈ 1,62 kWh** (Tabla 2) | Ver inconsistencias en la sección 4. |
| **Capacidad / densidad energética** | 10–15 kWh/m³ (estimada, Tabla 2) | No se explica el cálculo. |
| **Potencia de entrega** | Motor Stirling: **~194 W** medios (generador nominal ~200 W) | "0,994 kW en una hora" no es una unidad clara. |
| **ΔT de trabajo** | Inicio: 20 °C (293,15 K). Pico: 353 °C (626 K). Umbral de diseño: 350 °C. Umbral del motor: 300 °C. | **Temperatura mínima útil antes de recarga: no especificada explícitamente.** Solo aparece "~42 min" por encima de 300 °C. |
| **Tipo de intercambiador (carga)** | Seis resistencias tubulares inmersas en la arena (400 mm, Ø10 mm, 600 W) | Distribución hexagonal, separación de 0,27 m. |
| **Tipo de intercambiador (descarga)** | Carcasa y tubos inmerso en la arena, con fluido portador hacia el Stirling | **El fluido portador no está especificado.** |
| **Material aislante** | Fibra cerámica, espesor de 5 cm. Carcasa de acero inoxidable 304. | Espesor de la fibra explícito, pero conductividad no indicada. |
| **Eficiencia reportada** | Térmica del sistema: **89,91 %**. Conversión térmica → eléctrica: **~35 %** (conclusiones) o **20–35 %** (discusión y Tabla 2). | El 89,91 % **no tiene método de cálculo explícito**. |
| **Temperatura de operación del Stirling** | Arranque eficiente: ~300–350 °C | Dato explícito, con dos valores. |

## 4. Hallazgos críticos
### Soluciones técnicas del paper
- **Uniformidad térmica:** seis resistencias equidistantes evitan zonas frías en la arena. Es una solución geométrica simple.
- **Diseño del contenedor:** caja de acero inoxidable con aislante de fibra cerámica. Para evitar pérdidas, el espacio útil se reduce porque el aislante ocupa 5 cm.
- **Conductividad térmica:** el paper reconoce que la arena tiene baja conductividad y que esto limita la velocidad de carga. Propone mejorarla con control de humedad, compactación y aditivos conductores (citando a Tetteh et al., 2024). **No implementa estas mejoras**, solo las sugiere.
- **Granulometría:** la arena fina mejora la transferencia de calor y reduce los tiempos de carga y descarga (Niksiar et al., 2024).
- **Inercia térmica:** el sistema mantiene el calor almacenado durante mucho tiempo porque la arena tiene gran capacidad de retención.
- **Estabilidad del material:** la arena puede calentarse y enfriarse miles de veces sin degradarse, y eso justifica la vida útil de 30 años.
### Limitaciones reconocidas por el autor
- Baja densidad energética: requiere mucho volumen de arena.
- Baja eficiencia de conversión a electricidad (Stirling).
- Temperatura útil corta, de unos 42 minutos.
- No hay validación experimental; todos los resultados son simulaciones.

### Cómo me sirve para mi trabajo (pila de arena)
**1. Validar mi balance de calor.** El paper usa $Q = m \cdot c_p \cdot \Delta T$ para dimensionar la arena. Es el mismo método que tengo planteado en la Fase 2 de mi documento. Puedo usar sus datos como caso de prueba: con $c_p \approx 0{,}82$ kJ/kg·K y $\Delta T = 330$ K, la masa resulta ~240 kg. Eso confirma que el balance cierra.

**3. Revisar mi temperatura de diseño.** Mi documento habla de llegar a 500 °C, que es el valor de la planta finlandesa. Pero mi requisito real es que el **sustrato** quede entre 20 y 30 °C. El paper apunta a 350 °C porque su destino es el Stirling, no el sustrato. Un cálculo rápido muestra el efecto:

Supongo que el sustrato necesita 174 W por metro cuadrado (20 W/m × 8,7 m) durante 12 h de noche. Eso son ~2,1 kWh ≈ 7,5 MJ por cada metro cuadrado de cama. Con $c_p = 0{,}82$ kJ/kg·K, la masa necesaria es:

| ΔT de la arena (K) | Masa de arena (kg) |
|---|---|
| 30 | ~306 |
| 50 | ~183 |
| 100 | ~92 |
| 200 | ~46 |
| 300 | ~31 |


**4. No aplicar el 35 % de conversión a mi caso.** El paper calcula eficiencia para generar electricidad con un Stirling. Mi destino es **calor directo** al sustrato, así que la eficiencia relevante es la de transferencia térmica (de la arena al sustrato). Esa eficiencia debería ser mucho mayor, pero hay que medirla o simularla.

**5. Intercambiador de descarga.** El diseño de carcasa y tubos inmerso en la arena es una buena plantilla para el ítem 3 de mi ingeniería de detalle ("diseño del sistema de intercambio de calor con el sustrato"). A diferencia del paper, yo sí tengo que definir el fluido portador (agua o aire) y cómo llega al sustrato.

**6. Corregir el aislante de mi documento.** En la Fase 3 propongo "lana de vidrio o espuma de poliuretano que soporten 500 °C". La espuma de poliuretano **no soporta 500 °C** y se degrada a temperaturas mucho menores. La lana de vidrio tampoco es adecuada para esa temperatura. El paper elige **fibra cerámica** para 350 °C, que es una referencia más sólida si mantengo temperaturas altas.

**7. Material de la arena.** Mi documento habla de una mezcla de arena y arcilla, mientras que el paper usa arena de sílice seca. La arcilla cambia el calor específico, la conductividad y la humedad. El paper además señala que la humedad afecta la conductividad efectiva. Si uso mezcla, tengo que caracterizar el material.
