---
Titulo esp.: "Batería Carnot con motor Stirling y arena como medio de almacenamiento: prototipo de 1 kWe"
Año: 2026
Padre: "[[CUDAR - Desarrollo de Pila de Arena]]"
Importancia:
  - A
URL: https://www.sciencedirect.com/science/article/pii/S2352152X26020906#article
---
# 1. Idea Central
El estudio construye y ensaya el **primer prototipo integrado** de una _batería de Carnot_ que usa **arena de sílice** como medio de almacenamiento térmico: un tanque aislado lleno de arena se **carga con resistencias eléctricas** (hasta ~700 °C en las resistencias) y el calor se **extrae por conducción** (placas y bloque de cobre) hacia un **motor Stirling de pistón libre de 1 kWe** que vuelve a generar electricidad. Se complementa con un modelo 3D en COMSOL para extrapolar a 400 y 500 °C.

**Conclusión fundamental:** la arena es un medio viable y barato, y el ciclo funciona de punta a punta, pero la **eficiencia electricidad→electricidad experimental es muy baja (4,4 % a 8,3 %)** frente a lo que predice la simulación idealizada (19,1 % a 31,6 %). La brecha se debe sobre todo a **pérdidas de calor al ambiente/estructura (64 % de la energía)**, a la **baja conductividad térmica de la arena** y a la refrigeración del motor, no al motor en sí. Son problemas de ingeniería (aislamiento, puentes térmicos, intercambio de calor) y no límites del concepto.
![[Stirling engine-based Carnot battery with sand as heat storage medium - 1 kWe prototype-1793754307311.webp|507]]
## Glosario de abreviaciones

|Abrev.|Significado|Nota|
|---|---|---|
|**SECB**|Stirling Engine-based Carnot Battery|Batería de Carnot basada en motor Stirling (el sistema del paper)|
|**ETES**|Electro-Thermal Energy Storage|Almacenamiento electro-térmico: electricidad → calor → electricidad|
|**TES**|Thermal Energy Storage|Almacenamiento de energía térmica (aquí, la arena)|
|**Carnot battery**|—|Almacena electricidad como calor y la reconvierte a electricidad|
|**RCCB**|Rankine Cycle Carnot Battery|Variante con ciclo Rankine|
|**BCCB**|Brayton Cycle Carnot Battery|Variante con ciclo Brayton|
|**HP–ORC**|Heat Pump – Organic Rankine Cycle|Bomba de calor + ciclo Rankine orgánico|
|**ORC**|Organic Rankine Cycle|Ciclo Rankine con fluido orgánico|
|**PCM**|Phase Change Material|Material de cambio de fase (calor latente); aquí Al–Si (aluminio-silicio)|
|**LIB**|Lithium-Ion Battery|Batería de ion-litio|
|**PV**|Photovoltaic|Fotovoltaica|
|**CSP**|Concentrated Solar Power|Energía solar concentrada|
|**PID**|Proportional–Integral–Derivative|Controlador usado para regular la potencia de las resistencias|
|**LCOS**|Levelised Cost of Storage|Costo nivelado de almacenamiento (USD/kWh entregado)|
|**RTE**|Round-Trip Efficiency|Eficiencia de ida y vuelta (energía eléctrica recuperada / energía eléctrica de carga)|
|**CAPEX**|Capital expenditure|Costo de inversión inicial ($C_{cap}$)|
|**O&M**|Operation & Maintenance|Costos de operación y mantenimiento|
|**IEA**|International Energy Agency|Agencia Internacional de la Energía|
|**CAD**|Computer-Aided Design|Diseño asistido por computadora (SolidWorks 2023)|
|**COMSOL**|COMSOL Multiphysics 6.3|Software de simulación por elementos finitos|
|**kWe / kWth**|kW eléctricos / térmicos|Potencia eléctrica vs. potencia térmica|
# 2. Resumen por Secciones
## 2.1 Introducción y contexto (Sección 1)
**TES (almacenamiento térmico):** permite almacenar a largo plazo (incluso estacional) usando calor o electricidad.

**Batería de Carnot:** convierte electricidad → calor (almacenado) → electricidad. Ventajas frente a otras opciones: puede entregar **calor directo** además de electricidad, se puede instalar como retrofit, y usa materiales baratos y de larga vida. Desventaja: eficiencia menor que bombeo hidráulico o baterías electroquímicas.  ![[Stirling engine-based Carnot battery with sand as heat storage medium - 1 kWe prototype-1793754454628.webp]] **Fig. 1**: Clasificación de las baterías de Carnot según la conversión _potencia → calor_, el _almacenamiento_ (sensible / latente / termoquímico) y la conversión _calor → potencia_ (Rankine, Brayton, Stirling, otras). 

**Estado del arte (1.1) en resumen:**
- **Teóricos/tecno-económicos:** Alsagri (sal fundida solar, hasta 82,6 % considerando electricidad + calor de proceso); Zhao et al. (regeneradores en HP–ORC bajan el LCOS ~12 %); Jacob & Liu (PCM + CO₂ supercrítico, LCOS = 476 USD/kWh).
- **Simulación:** Scharrer et al. (HP–ORC en comunidades; importa el dimensionamiento y la economía de escala).
- **Experimentales (escasos):** Weitzer (HP–ORC, 41,8 % sin pérdidas de almacenamiento). Para Stirling, casi todo es con **PCM metálico Al–Si**: Rea (18,5 %, 1 kWe), Lindquist (13 kWe), Alemam (TES.POD®, 600 kWh, 13 kWe, **23 % RTE**). Problemas: costo, materiales y manejo complejo.
- **Arena:** Tetteh et al. [20] mostraron que **inclusiones metálicas aumentan la conductividad efectiva** de la arena, pero sin prototipo con motor.

**Brecha de investigación:** nadie había demostrado experimentalmente una batería de Carnot **completa** con **arena** + motor Stirling. Esa es la contribución.

**Trade-off clave de la arena:** muy barata, abundante, estable a alta temperatura, **pero con baja conductividad térmica**, lo que limita el flujo de calor hacia el motor. Se mitiga con diseño de interfaz, aletas, placas, inclusiones metálicas o lechos compuestos.
## 2.2 Materiales y métodos (Sección 2)
### 2.2.1 Montaje experimental
![[Stirling engine-based Carnot battery with sand as heat storage medium - 1 kWe prototype-1793754541566.webp]] ***Fig. 2**: Esquema 3D del ETES (A), foto antes de instalar resistencias (B), equipo operativo (C) y detalle de termocuplas (D). Es la imagen más útil del paper para entender la **geometría del contenedor y del intercambiador**.*

- **Tanque:** rectangular con extensión en embudo abajo, **0,2 m³** de volumen total.
- **Carga:** **10 resistencias de sauna** (Harvia) de 3 kW / 230 V cada una (30 kW nominales), metidas dentro de la arena.
- **Extracción:** dos **placas de cobre** (0,65 × 0,65 × 0,01 m) separadas 0,14 m y fijadas a un **bloque de cobre** (0,14 × 0,225 × 0,225 m) llamado _engine head_, soldado por láser al cilindro caliente del motor. El calor viaja **por conducción**: arena → placas de cobre → bloque → motor.
- **Motor:** Microgen de pistón libre, hermético, 1 kWe nominal (50 Hz, 230 V), 26 % de eficiencia eléctrica, vida de diseño 50.000 h, 49 kg. **Arranca solo cuando la cabeza alcanza 180 °C** y requiere refrigerante (4–7 L/min, entrada 6–70 °C). Refrigeración por tubo de agua en el cilindro frío; tubos de aire comprimido en la cabeza para emergencias.
- **Control:** caja con controladores **PID** + medidores de pulsos; **9 termocuplas tipo K**.
- **Aislación:** 2 capas de manta **Insulfrax LTX** (50 mm c/u, 96 kg/m³) ≈ **100 mm** en total.
- **Medio de almacenamiento:** arena de sílice marrón (0,6–2 mm), cp = 703 J/(kg·K), punto de fusión 1713 °C, k = 0,2–0,7 W/(m·K), densidad aparente 1800 kg/m³.
### 2.2.2 Procedimiento experimental
- Dos casos: **cabeza del motor a 300 °C** y **a 350 °C**. Cada caso se corrió **2 días seguidos** para simular uso solar (el día 2 arranca con calor residual del día 1).
- Las resistencias se mantienen por PID a ~700 °C hasta que la cabeza llega al set-point; luego se apaga la carga y el almacenamiento se descarga hasta enfriarse.
- **Por qué 300 y 350 °C:** por encima del umbral de 180 °C, dentro de los límites de seguridad del prototipo, separados 50 °C para medir sensibilidad, y para validar el modelo antes de extrapolar a 400–500 °C.
- **Adquisición:** muestreo cada $\Delta t = 1$ s. Incertidumbre expandida (k = 2) de la RTE: ±1,3 % (300 °C) y ±1,5 % (350 °C).
### 2.2.3 Modelo numérico (COMSOL 6.3)
- Interfaz _Heat Transfer in Solids_, transitorio. Geometría importada de SolidWorks 2023: **66 dominios sólidos** (aislante, arena, carcasas, placas, bloque, resistencias). Malla de **~10 millones** de elementos tetraédricos (Lagrange cuadrático).
- Propiedades relevantes: arena ρ = 1425 kg/m³ con conductividad efectiva dependiente de T (correlación Zehner-Bauer-Schlünder), cobre k = 400 W/(m·K), acero k = 45 W/(m·K), aislante k = 0,29 W/(m·K).
- Condiciones de borde: convección h = 5 W/(m²·K), ambiente 14,5 °C; la resistencia es una **fuente volumétrica de calor** con curva empírica limitada a su potencia nominal (3000 W según el paper).
- **Importante:** el PID real que limitaba la resistencia a ~700 °C **no está modelado**, y el motor es un "módulo virtual" (ecuaciones 2 y 3).
- El modelo se discretizo usando una configuracion de malla controlada por la fisica, la cual utiliza elementos tetraedrivos con funciones forma cuadratica de Langrage para resolver campos de T con presicion. 
- Las simulaciones se ejecutaron usando un solver que depende del tiempo con paso de tiempo automatico basado en el metodo de formula de diferenciación hacia atrás, Las tolerancias del solucionador se austan para manejar las no linealidades de las propiiedades del material dependintes de la T y el comportamiento de la fuente de calor emitida 
![[Stirling engine-based Carnot battery with sand as heat storage medium - 1 kWe prototype-1793754829803.webp]]
***Fig. 3**: Mallado del ETES sin aislación (a) y con aislación (b). Solo si querés documentar el nivel de refinamiento de malla.*
### 2.2.4 Ecuaciones del modelo y del análisis
**Ec. (1) — Conducción de calor transitoria** (gobierna toda la simulación):
$$\nabla \cdot (k \nabla T) + \dot{Q}_v = \rho, c_p \frac{\partial T}{\partial t}$$
- $k$: conductividad térmica del material [W/(m·K)].
- $T$: temperatura [K o °C].
- $\dot{Q}_v$: generación interna de calor por unidad de volumen [W/m³] (las resistencias).
- $\rho$: densidad [kg/m³].
- $c_p$: calor específico a presión constante [J/(kg·K)].
- $\partial T/\partial t$: variación de la temperatura en el tiempo.

**Ec. (2) — Potencia del motor Stirling** (polinomio empírico del fabricante):
$$P_{engine}(T) = -0{,}0032,T^2 + 6{,}6065,T - 2282{,}4$$
- $P_{engine}$: potencia eléctrica del motor [W].
- $T$: temperatura de la cabeza del motor, **en kelvin** (comprobé que da ≈ 450 W a 300 °C y ≈ 590 W a 350 °C, consistente con lo que se reporta en la simulación).
- Válida solo entre **180 °C (453,15 K) y 520 °C (793,15 K)**; fuera de ese rango el motor se considera apagado.

**Ec. (3) — Eficiencia térmica real del motor** (fracción de la de Carnot):
$$\eta_{eng} = \phi \left(1 - \frac{T_c}{T_h}\right)$$
- $\eta_{eng}$: eficiencia térmica del motor.
- $\phi = 0{,}58$: factor empírico que representa que el motor real rinde ~58 % de uno ideal.
- $T_h$: temperatura del lado caliente (cabeza del motor) [K].
- $T_c$: temperatura del lado frío (agua de refrigeración a la entrada) [K].

**Ec. (4) — Potencia de refrigeración** (calor retirado por el agua):
$$\dot{q} = \frac{\dot{V}}{60,(1000)},\rho, c_p,(T_{out}-T_{in})$$
- $\dot{V}$: caudal de refrigerante [L/min] (el $/60$ pasa a segundos y $/1000$ a m³).
- $\rho$: densidad del agua (1000 kg/m³).
- $c_p$: calor específico del agua (4186 J/(kg·°C)).
- $T_{out}, T_{in}$: temperatura de salida y entrada del refrigerante [°C]. Aumentos típicos de 4–7 °C a 7 L/min.

**Ec. (5) — Energía total de refrigeración:**
$$E_{cool} = \sum \dot{q}\cdot\Delta t$$
- $\Delta t$: paso de tiempo de medición (1 s). Se suma en todo el ciclo y se pasa de J a kWh.

**Ec. (6) — Eficiencia de ida y vuelta (RTE):**
$$\eta_{RTE} = \frac{E_{discharge}}{E_{charge}} \times 100\%$$
- $E_{charge}$: energía eléctrica consumida al cargar, medida en la caja de control [kWh].
- $E_{discharge}$: energía eléctrica neta entregada por el generador del Stirling [kWh].

**Ec. (7) — Eficiencia de Carnot** (techo teórico del motor):
$$\eta_{Carnot} = 1 - \frac{T_c}{T_h}$$
- $T_h$ y $T_c$ en kelvin (cabeza del motor y agua de entrada). De los valores de la Tabla 2 se deduce $T_c \approx 20,°C$ (deducción mía).

**Ec. (8) — LCOS (costo nivelado de almacenamiento), forma general:**
$$LCOS = \frac{C_{cap} + \sum_{y=1}^{Y}\dfrac{C_{O\&M,y}}{(1+r)^y}}{\sum_{y=1}^{Y}\dfrac{E_{discharge,y}}{(1+r)^y}}$$

- $C_{cap}$: costo de capital (CAPEX) del prototipo.
- $C_{O\&M,y}$: costo de operación y mantenimiento del año $y$.
- $r$: tasa de descuento.
- $Y$: vida calendario [años].
- $E_{discharge,y}$: energía eléctrica entregada en el año $y$.

**Ec. (9)–(11) — Versión simplificada para un prototipo** (sin descuento, O&M constante):
$$LCOS \approx \frac{C_{cap} + Y, C_{O\&M}}{N_{cycles}, E_{discharge,cycle}} \quad E_{discharge,cycle} = \eta_{RTE}, E_{charge,cycle} \quad N_{cycle} = \frac{L_h}{t_{discharge}}$$

- $N_{cycles}$: cantidad de ciclos en la vida útil.
- $L_h$: vida del motor en horas de operación (50.000 h).
- $t_{discharge}$: duración de la descarga por ciclo (9–14 h).
- $E_{charge,cycle}$, $E_{discharge,cycle}$: energía de carga y de descarga de un ciclo.
## 2.3 Resultados (Sección 3)
### 3.1 Resultados experimentales
![[Stirling engine-based Carnot battery with sand as heat storage medium - 1 kWe prototype-1793757187815.webp]] ***Fig. 4**: Ciclo de 2 días: temperaturas de resistencia y de la cabeza del motor (a, b) y potencia generada (c, d), para 300 °C y 350 °C. Muestra las **oscilaciones on/off del motor** y el solapamiento carga/descarga.*

- Las resistencias llegan a ~700 °C en 1,5 h y se mantienen ahí con PID hasta que la cabeza alcanza el set-point.
- **Tiempos de carga:** 300 °C → ~3 h (día 1) y ~2,5 h (día 2); 350 °C → ~5,2 h y ~5 h. El día 2 es más corto por el calor residual: la operación continua conviene.
- **Fenómeno de arranque:** al arrancar el motor, la temperatura de la cabeza baja un poco y la potencia cae brevemente porque **la arena no repone calor lo bastante rápido** (baja conductividad). Si la carga se interrumpe, el motor se **apaga y reinicia repetidamente** (oscilaciones), lo que reduce la potencia media y estresa el motor.
- **Potencia y duración:**
    - 300 °C: pico ≈ 500 W, ~9 h de descarga, ≈ 4,3 kWh por ciclo.
    - 350 °C: pico 660 W (día 1, 13 h) y 690 W (día 2, 14 h); el día 2 entregó 13,6 % más energía que el día 1, lo que muestra sensibilidad a las condiciones iniciales.
![[Stirling engine-based Carnot battery with sand as heat storage medium - 1 kWe prototype-1793757274831.webp|334]]
### 3.2 Simulación vs. experimento
![[Stirling engine-based Carnot battery with sand as heat storage medium - 1 kWe prototype-1793757327421.webp|422]] ***Fig. 6**: Comparación experimental (línea continua) vs. simulada (línea discontinua) de temperaturas y potencia para 300 y 350 °C. Es la imagen clave para ver **cuánto se parece el modelo a la realidad**.*

|Caso|Pico de potencia (sim.)|Duración descarga (sim.)|Experimento|
|---|---|---|---|
|300 °C|460 W (a las 3,9 h)|> 18 h|500 W (3,2 h), ~9–10 h|
|350 °C|594 W (a las 4,2 h)|> 20 h|~700 W (≈ 6 h), 13,2 h|
|400 °C|732 W|28,6 h|No ensayado|
|500 °C|923 W|33,6 h|No ensayado|

- Las resistencias simuladas llegan a 753 °C (300 °C), ~800 °C (350 °C), 820 °C (400 °C) y 858 °C (500 °C); el modelo no limita la temperatura de la resistencia como lo hacía el PID real.
- **Por qué el modelo da más duración y menos pérdidas:** asume contacto térmico ideal, conductividad uniforme de la arena y pérdidas despreciables; en la realidad hay heterogeneidad del empaquetado, resistencias de contacto y pérdidas estructurales. Los autores lo ven como **cota superior** realista.
![[Stirling engine-based Carnot battery with sand as heat storage medium - 1 kWe prototype-1793757399033.webp|479x640]]***Fig. 8**: Mapas 3D de temperatura en t = 0, 2, 5 y 10 h para 300, 400 y 500 °C. Es la mejor imagen para ver los **gradientes y puntos calientes** en la arena (útil para tu propia simulación térmica).*

- **Lectura de los mapas (Fig. 8):** en carga hay **puntos calientes junto a las resistencias** (≈ 700 a 850 °C) mientras partes de la arena van rezagadas (mínimos ≈ 350 a 400 °C). A 400–500 °C hay más estratificación e inercia térmica (el motor funciona más tiempo); a 500 °C queda un punto caliente en el centro del lecho a las 10 h. La capa externa del aislante se mantiene a temperatura ambiente, por lo que el espesor del aislante simulado es suficiente.
### 3.3 Eficiencia
**Tabla 2 (página 5) — RTE vs. eficiencia de Carnot del motor**

|Caso|RTE (%)|Carnot del motor (%)|
|---|---|---|
|300 °C Día 1 (exp.)|4,4|48,9|
|300 °C Día 2 (exp.)|5,9|48,9|
|350 °C Día 1 (exp.)|6,8|53|
|350 °C Día 2 (exp.)|8,3|53|
|300 °C (sim.)|19,1|48,9|
|350 °C (sim.)|23,2|53|
|400 °C (sim.)|26,9|56,5|
|500 °C (sim.)|31,6|62,1|
![[Stirling engine-based Carnot battery with sand as heat storage medium - 1 kWe prototype-1793757541192.webp]] **Fig. 9**: _Sankey del balance de energía_ Para el ciclo representativo de 300 °C: de 53 kWh eléctricos de entrada, 18,87 kWh llegan al motor, 2,33 kWh salen como electricidad, 16,54 kWh se van al refrigerante y 34,13 kWh se pierden al ambiente/estructura. 

**Balance de energía del ciclo (Ec. 12):**
$$E_{charge} = E_{discharge} + Q_{cool} + Q_{env} + E_{aux} + \Delta E_{res}$$
- $E_{charge}$: electricidad de entrada en la carga.
- $E_{discharge}$: electricidad generada por el motor.
- $Q_{cool}$: calor rechazado al refrigerante.
- $Q_{env}$: pérdida neta de calor al ambiente (incluye puentes térmicos).
- $E_{aux}$: consumo eléctrico auxiliar (control, refrigeración).
- $\Delta E_{res}$: energía residual almacenada al terminar el ensayo.

**Reparto medido (300 °C):** 2,33 kWh útiles (**4,4 %**), 16,54 kWh a refrigerante (**31,2 %**) y 34,13 kWh a pérdidas ambientales/estructurales (**64,4 %**).

**Origen de las pérdidas ($Q_{env}$):** (i) puentes térmicos y penetraciones (soportes, marcos de acero soldados al tanque, conexiones) que el modelo no representa; (ii) aislación no optimizada para ciclado repetido a alta temperatura; (iii) los sistemas de refrigeración/emergencia del motor que aumentan el rechazo de calor.
### 3.4 Discusión (limitaciones)
1. Pérdidas térmicas no capturadas (soportes soldados al tanque).
2. Propiedades de la arena simplificadas (conductividad uniforme; en la realidad hay huecos y resistencia de contacto).
3. Interfaces resistencia–arena e inercia térmica de la resistencia simplificadas.
4. Dinámica del motor y control (picos de arranque, interacción con refrigerante) no representada.
5. Incertidumbre de instrumentos y deriva de condiciones de borde.
6. Ensayos limitados a 300–350 °C por tolerancias de componentes; extrapolar a 400–500 °C requiere mejores materiales y aislación.
7. Sin regeneradores ni intercambiadores avanzados, lo que sesga la RTE experimental a la baja.

**Comparación con otros SECB (Tabla 3):** Rea 2019 (100 kg Al–Si, 1 kWe, 18,5 %); Lindquist 2019 (Al–Si, motor de 13 kWe); Alemam 2023 (600 kWhth Al–Si, 10,5 kW durante 13 h, 23 % RTE, motor 25 %, respuesta < 5 s); Tetteh 2024 (arena con inclusiones metálicas, mejora de conductividad); **este trabajo** (arena, 1 kWe, 4,4–8,3 % exp.; hasta 31,6 % simulado).
### 3.5 Estimación preliminar de LCOS
- CAPEX del prototipo: **€41.402** (≈ 48.500 USD con 1 € = 1,1719 USD; conversión mía). O&M supuesto: 1 % del CAPEX por año, vida de 10 años; ciclos estimados $N_{cycle}$ ≈ 3571–5556 (50.000 h / 14 h y 50.000 h / 9 h).

**Tabla 4 (página 13) — LCOS**

|Caso|Th (°C)|RTE (%)|LCOS (USD/kWh)|
|---|---|---|---|
|Prototipo medido|300|4,4|4,12–6,41|
|Prototipo medido|350|8,3|2,18–3,40|
|Simulado|300|19,1|0,95–1,48|
|Simulado|350|23,2|0,78–1,22|
|Simulado|400|26,9|0,67–1,05|
|Simulado|500|31,6|0,57–0,89|
|Concepto PCM de alta T [35]|n/d|n/d|476|

Los valores son indicadores de **demostrador de laboratorio**, no de escala comercial. Dominan el costo (i) la baja RTE y (ii) el CAPEX de prototipo único.
## 2.4 Conclusiones (Sección 4)
- El ciclo electricidad → calor en arena → electricidad **se demostró experimentalmente**.
- De 300 a 350 °C: el pico de potencia sube de ~500 a ~690 W y la descarga de ~9 a ~14 h, pero la RTE sigue baja (4,4–5,9 % y 6,8–8,3 %).
- Las pérdidas fuera de la etapa de conversión dominan; son principalmente un problema de **cómo se aisló una estructura compleja**, y por eso son corregibles.
- La simulación (19,1–31,6 %) debe leerse como **objetivos de diseño**, no como desempeño real, especialmente por encima de 400 °C (no validado).
- Para ser competitivo se requiere: (i) menos pérdidas (aislación, sellado, puentes térmicos); (ii) mejor entrega de calor al motor (intercambiador y mayor conductividad del lecho); (iii) conversión mejor adaptada a la temperatura; (iv) menores pérdidas parásitas y de control.
- Es un prototipo temprano; en futuros ensayos separarán carga y descarga para evitar el sesgo de la RTE.
# 3. Parámetros técnicos clave

|Parámetro|Dato del paper|
|---|---|
|**Volumen / masa de arena**|Volumen total del tanque: **0,2 m³** (rectangular + embudo). Arena de sílice marrón 0,6–2 mm, densidad aparente 1800 kg/m³ (en el modelo se usa 1425 kg/m³), cp = 703 J/(kg·K), k = 0,2–0,7 W/(m·K). **Masa de arena: No especificada en el paper** (estimación mía: como máximo ~360 kg si todo el volumen fuera arena, pero parte del volumen lo ocupan placas, bloque y resistencias, así que sería menos).|
|**Potencia y capacidad**|**Entrada:** 10 resistencias × 3 kW = 30 kW nominales. **Salida:** motor de 1 kWe nominal; picos medidos de ~500 W (300 °C) y 660–690 W (350 °C). **Energía por ciclo (300 °C):** 53 kWh de carga → 18,87 kWh llegan al motor → 2,33 kWh eléctricos (en el texto se cita ≈ 4,3 kWh por ciclo en la sección 3.1, y 2,33 kWh en el balance de la Fig. 9; el paper no aclara esa diferencia). **Capacidad térmica nominal de la arena: No especificada en el paper.**|
|**ΔT de trabajo**|**Carga:** resistencias a ~700 °C (límite del PID). **Cabeza del motor:** 300 y 350 °C (experimento), 400 y 500 °C (simulación). **Mínimo útil:** **180 °C** (el motor se apaga cuando la cabeza baja de ahí). Rango operativo del motor: 180–520 °C. Agua de refrigeración: entrada 6–70 °C. Ambiente en la simulación: 14,5 °C.|
|**Tipo de intercambiador**|**Inyección:** 10 resistencias eléctricas tubulares (vaina Incoloy 800 con MgO) **enterradas directamente en la arena**. **Extracción:** **conducción pura** por 2 placas de cobre (0,65 × 0,65 × 0,01 m) + bloque de cobre (engine head) soldado por láser al cilindro caliente del Stirling; **no hay fluido caloportador ni aire forzado** en el lado caliente. **Lado frío:** tubo de agua de refrigeración; tubos de aire comprimido en la cabeza solo para emergencias.|
|**Material aislante**|**Insulfrax LTX Blanket** (fibra de silicato alcalinotérreo biosoluble, Unifrax/Lektar Oy), **2 capas de 50 mm (≈ 100 mm)**, densidad 96 kg/m³; k = 0,29 W/(m·K) en el modelo. Carcasa/estructura de acero.|
|**Eficiencia reportada**|**RTE electricidad → electricidad (experimental):** 4,4 % y 5,9 % a 300 °C; 6,8 % y 8,3 % a 350 °C. **Simulada:** 19,1 % (300 °C), 23,2 % (350 °C), 26,9 % (400 °C), 31,6 % (500 °C). Eficiencia nominal del motor: 26 %. **Ojo con tu aplicación:** el paper no reporta una "eficiencia térmica de recuperación de calor útil". Solo se puede inferir del balance: de 53 kWh de entrada, 18,87 kWh llegaron al motor (≈ 35,6 %, cálculo mío), y de ahí 16,54 kWh salieron como calor al refrigerante.|

# 4. Hallazgos Críticos
- **Primera demostración experimental** de una batería de Carnot completa con arena + Stirling de pistón libre (1 kWe). La arena funciona como TES barato y estable, pero con una RTE experimental de solo **4,4–8,3 %**.
- **Más temperatura = mejor:** de 300 a 350 °C, la potencia pico sube de ~500 a ~690 W y la duración de descarga de ~9 a ~14 h. En simulación, de 400 a 500 °C la potencia pico pasa de 732 a 923 W y la duración de 28,6 a 33,6 h.
- **Conductividad térmica de la arena (0,2–0,7 W/m·K) es el cuello de botella** del flujo de calor hacia el motor: causa caídas de potencia en el arranque, oscilaciones on/off y deja zonas de arena "rezagadas" lejos de las resistencias.
	- **Cómo la enfrentaron:** (1) **placas de cobre** (0,65 × 0,65 × 0,01 m) que extienden la superficie de intercambio dentro del lecho y (2) bloque de cobre soldado al motor. Como mejoras futuras proponen **inclusiones metálicas** (virutas) en la arena [ref. 20 del paper], aletas/placas, lechos compuestos y mejor diseño de la interfaz.
- **Las pérdidas dominan, no el motor:** en el ciclo de 300 °C, **64,4 % de la energía se perdió** al ambiente/estructura, 31,2 % se rechazó por refrigeración y solo 4,4 % volvió como electricidad. El problema principal es **aislación y puentes térmicos**.
	- **Puentes térmicos como culpable principal:** los soportes y marcos de acero soldados al tanque, penetraciones y conexiones no estaban en el modelo y enfriaban la arena más rápido. La conclusión dice que el fallo fue _"el método de aislar una estructura compleja"_, lo que se puede corregir con ingeniería.
- **Geometría del contenedor y mapa térmico:** la simulación muestra **puntos calientes junto a las resistencias** (700–850 °C) con gradientes fuertes hacia el resto del lecho. A 500 °C, un punto caliente persiste en el centro después de 10 h; a 300 °C el perfil es más uniforme pero con menos calor disponible.
- **Operación continua ayuda:** el día 2 necesita menos tiempo de carga (aprovecha calor residual) y rinde más, y la RTE es mayor que el día 1 (5,9 vs 4,4 %; 8,3 vs 6,8 %).
- **Modelo útil como cota superior:** simula bien tendencias, pero sobreestima porque supone contacto perfecto, conductividad uniforme y sin pérdidas parásitas. Sirve para diseñar, no para predecir el valor real.
- **Economía:** CAPEX del prototipo ≈ €41.400; LCOS medido de 2,2 a 6,4 USD/kWh; el simulado a 500 °C baja a 0,57–0,89 USD/kWh. Todo indicativo, de laboratorio. 
- **Calor útil ≠ pérdida:** los autores aclaran que el calor al refrigerante (31 %) se puede valorizar (calefacción), lo que hace más atractivo el sistema cuando el objetivo es **calor** y no electricidad.
# Para nuestro TP
- Es mejor enviar calor directo antes que convertir el calor a electricidad: en este paper se ve que hay una baja eficiencia en intentar convertir el calor acumulado en energia eletrica a traves de un motor Stirling.
	- Nuestro objetivo es **entregar calor al sustrato**, no electricidad: te interesa la parte del balance que el paper llama $Q_{cool}$, no la RTE eléctrica. Quitar el Stirling elimina el cuello de botella de conversión y deja solo **carga → almacenamiento → extracción térmica**.
- Al igual que este articulo, hay que tener cuidado con el calculo del aislamiento exterior para evitar perdidas nocturnas y diseñar un sistema de extraccion que supere la baja conductividad termica de la arena
- Lecciones transferibles de diseño: 
	- **aislación y puentes térmicos** (evitar estructuras metálicas soldadas que conecten el interior con el exterior) 
	- **conducción lenta de la arena** (aletas, placas metálicas o inclusiones para repartir el calor) 
	- **puntos calientes junto a la resistencia** (distribuir resistencias o limitar su temperatura de vaina).