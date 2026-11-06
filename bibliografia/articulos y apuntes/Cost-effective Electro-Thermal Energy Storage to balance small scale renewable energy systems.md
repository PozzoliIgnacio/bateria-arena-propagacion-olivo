---
Titulo esp.: Almacenamiento de energía electrotérmica rentable para sistemas de energía renovable a pequeña escala
Tipo:
  - Articulo
URL: https://www.sciencedirect.com/science/article/pii/S2352152X21005557?via%3Dihub
Año: 2021
Padre: "[[CUDAR - Desarrollo de Pila de Arena]]"
Importancia:
  - B
---
# 1. Idea Central

El estudio presenta y evalúa un novedoso sistema de almacenamiento electro-térmico (ETES) diseñado para ser modular, escalable y de bajo costo. Utiliza materiales térmicos comunes (arena, sales fundidas o aceite térmico) para almacenar calor, y motores Stirling de pistón libre (FPSE) para convertir ese calor de nuevo en electricidad. La conclusión principal es que el sistema ETES, especialmente cuando utiliza arena como medio de almacenamiento, alcanza una eficiencia de ida y vuelta del **47,4%** y un costo por kWh hasta **seis veces menor** que el de las baterías de ion-litio, ofreciendo una alternativa prometedora para sistemas renovables aislados de pequeña escala, evitando el uso de materiales críticos y reduciendo la huella ambiental.

La investigación concluye que la arena de sílice seca es el medio de almacenamiento mas eficiente, seguro y de menor costo.

### Glosario de Abreviaciones

|Abreviatura|Significado en inglés|Traducción al español|
|---|---|---|
|**CAES**|_Compressed Air Energy Storage_|Almacenamiento de energía por aire comprimido|
|**CAPEX**|_Capital Expenditure_|Gasto de capital / Inversión en activos fijos|
|**CHP**|_Combined Heat and Power_|Cogeneración de calor y electricidad|
|**CSP**|_Concentrated Solar Power_|Energía solar concentrada (mencionada en referencias)|
|**EDP**|_Engineering Design Process_|Proceso de diseño ingenieril|
|**EES**|_Electrical Energy Storage_|Almacenamiento de energía eléctrica (directa)|
|**ESS**|_Energy Storage Systems_|Sistemas de almacenamiento de energía|
|**ETES**|_Electro-thermal Energy Storage_|Almacenamiento electro-térmico (el sistema propuesto)|
|**FES**|_Flywheel Energy Storage_|Almacenamiento de energía por volante de inercia|
|**FPSE**|_Free-piston Stirling Engine_|Motor Stirling de pistón libre|
|**HESS**|_Hydrogen Energy Storage System_|Sistema de almacenamiento de energía con hidrógeno|
|**LIB**|_Lithium-ion Battery_|Batería de iones de litio|
|**LFP**|_Lithium Iron Phosphate_|Fosfato de hierro y litio (química de cátodo para baterías)|
|**NMC**|_Nickel Manganese Cobalt_|Níquel manganeso cobalto (química de cátodo para baterías)|
|**PHS**|_Pumped Hydro Storage_|Almacenamiento por bombeo hidroeléctrico|
|**PV**|_Photovoltaic_|Fotovoltaico (energía solar)|
|**SC**|_Super Capacitor_|Supercondensador|
|**SMES**|_Superconducting Magnetic Energy Storage_|Almacenamiento de energía magnética por superconductividad|
|**TES**|_Thermal Energy Storage_|Almacenamiento de energía térmica|
|**VRFB**|_Vanadium Redox Flow Battery_|Batería de flujo redox de vanadio|

# 2. Resumen por Secciones

## **1. Introducción y Contexto**

El artículo comienza justificando la necesidad de almacenamiento de energía para integrar fuentes renovables intermitentes (solar, eólica) en la red eléctrica, especialmente en sistemas aislados (off-grid). Destaca que, aunque existen diversas tecnologías de almacenamiento (mecánicas, eléctricas directas, químicas y térmicas), muchas no son adecuadas para aplicaciones de pequeña escala debido a sus requisitos geográficos o su falta de modularidad.

Se señala que las baterías de ion-litio (LIB) son actualmente la opción dominante, pero su creciente demanda para el sector del transporte y su dependencia de materiales críticos (litio, cobalto) podrían generar escasez y aumentos de precio en el futuro. Por ello, se propone un nuevo sistema de almacenamiento electro-térmico indirecto (ETES) que convierte electricidad en calor, lo almacena en materiales de bajo costo y luego lo convierte de nuevo en electricidad mediante motores Stirling.
![[Cost-effective Electro-Thermal Energy Storage to balance small scale renewable energy systems-1790466682225.webp]]
> **Figura 1 – Clasificación de sistemas de almacenamiento:** diagrama de clasificación de los sistemas de almacenamiento de energía, destacando la necesidad de un paso de conversión. El ETES se clasifica dentro de los "Sistemas de almacenamiento de energía térmica indirecta".

## **2. Materiales y Métodos**

- **Criterios de diseño del ETES:** Se establecieron cuatro criterios principales: 1) bajo costo, 2) ausencia de materiales críticos, 3) alta eficiencia y 4) baja huella ambiental. Se siguió un proceso de diseño ingenieril (Engineering Design Process, EDP).
- **Materiales de almacenamiento térmico (TES):** Se seleccionaron tres materiales por su disponibilidad y bajo costo:
    - **Aceite térmico (Therminol VP-1):** Rango de temperatura 180 °C – 400 °C (orgánico, volátil por encima de 400 °C).
    - **Sal fundida (Dynalene MS-2):** Rango 200 °C – 500 °C (cristaliza por debajo de 200 °C, es corrosiva).
    - **Arena:** Rango 180 °C – 950 °C (sólida, no requiere fluido de transferencia de calor, estable a altas temperaturas y muy abundante).
- **Metodología de evaluación:**
    - Se asumió una eficiencia de carga del 100% (toda la electricidad se convierte en calor).
    - Se seleccionó un motor Stirling de tipo gamma de baja temperatura (especificaciones en Tabla 1) con una potencia de salida de 2.525 kW y una eficiencia térmico-eléctrica del 21% a 180 °C de lado caliente y 30 °C de lado frío (equivalente al 63% de la eficiencia de Carnot).
    - Se consideraron pérdidas de calor a través del aislamiento, basándose en estudios experimentales previos (tasas de enfriamiento de ~4 °C/h a 550 °C y <1.5 °C/h por debajo de 300 °C).
    - **Fórmulas clave:**
        - Potencia de carga: $P_{in} = \dfrac{m C_p \Delta T}{t}$
            - Donde m es la masa del material de almacenamiento termico, Cp es la capacidad calorifica especifica promedio del material de almacenamiento termico en el rango de T objetivo, $\Delta T$ es la diferencia de T durante la carga y t es el tiempo transcurrido. ‘P’ es la cantidad de electricidad necesaria para cargar el almacenamiento de energía, según la ecuación es energía térmica a lo largo del tiempo
        - **Modelo Matemático de Descarga:** La eficiencia de conversión de calor a electricidad se modela corrigiendo la eficiencia de Carnot variable ($\eta_{th}$) de acuerdo con un factor experimental de operación del motor Stirling del 63%:$$  
            \eta_{\text{thermal-to-electric}} = \left(1 - \frac{T_l}{T_h}\right) \cdot 0.63  
            $$
            Donde $T_l$ es la temperatura fría constante ($30^\circ\text{C}$) y $T_h$ es la temperatura variable de la arena en contacto con el motor
        - Eficiencia térmico-eléctrica variable para el motor stirling: $\eta = 0.63 \times \left(1 - \dfrac{T_c}{T_h}\right)$
        - Potencia de descarga: $P_{out} = \dfrac{m C_p \Delta T}{t} \times 0.63 \times \left(1 - \dfrac{T_c}{T_h}\right)$
![[Cost-effective Electro-Thermal Energy Storage to balance small scale renewable energy systems-1790466722356.webp]]
> **Tabla 1 – Especificaciones del motor Stirling:** Potencia de salida 2.525 kW, Eficiencia térmica a eléctrica 21%, Fracción de la eficiencia de Carnot 65%, Temperatura del cilindro caliente 180 °C y Temperatura del cilindro frío 30 °C.

![[Cost-effective Electro-Thermal Energy Storage to balance small scale renewable energy systems-1790466754638.webp]]
**Diseño del sistema ETES (**_Electro-thermal Energy Storage,_ Almacenamiento electro-térmico**):
- tanque de almacenamiento térmico fabricado con **acero ferrítico y material aislante de alta T**
![[Cost-effective Electro-Thermal Energy Storage to balance small scale renewable energy systems-1790466773653.webp]]
- El calentador o conductor térmico debe diseñarse para que el calor se distribuya de forma eficiente y uniforme, mejorando así la conductividad térmica de ciertos materiales de almacenamiento térmico como la arena.
- Forma económica de diseñar el tanque de almacenamiento térmico es usar acero ferrítico de grado 4724 o 2713, con temperaturas de resistencia entre 550 y 858 °C.
- Se puede usar un material aislante de alta T para cubrir la superficie interna del tanque siempre que el material de almacenamiento térmico sea un solido. Un ejemplo típico de material aislante de alta T es la manta ‘RS Pro Superwool 607 HT’, con una T de tolerancia de 1300 °C
- Si se opera en T extremadamente altas (hasta 950°C aguanta el arena), puede llegar a fallar el acero del tanque. Por ello es que al colocar el aislamiento por dentro se logra un gradiente térmico donde el interior del aislante esta a 950° pero la pared del tanque de acero se mantiene a una T mucho mas baja.
- Como se integran los motores Stirling en el tanque de almacenamiento?
    - Los sistemas TES existentes que usan motores stirling necesitan un medio de transferencia de calor, como aceites térmicos, para hacer circular el calor alrededor del intercambiador de calor. Esto requiere accesorios adicionales con aislamiento y un mecanismo de bombeo para el funcionamiento a alta T lo que conlleva mayores perdidas de E y mayores costos
    - Los sistemas ETES eliminan todos esos problemas soldando las cabezas calientes de los motores directamente a barras conductoras que actúan como intercambiadores de calor internos sumergidos en la arena, lo cual simplifica mecánicamente el sistema y elimina bombas o tuberías externas

# **3. Resultados y Discusión**

## **Comportamiento de descarga:**

El objetivo de este apartado es evaluar cómo cambia la potencia eléctrica de salida y la eficiencia del sistema a medida que el acumulador se va enfriando.

Para entender esta sección, los autores proponen un caso de estudio con los siguientes parámetros de partida:

- Un tanque de 1**.5 m^3** completamente cargado a **400 °**.
- Se descarga utilizando un aceite térmico (Therminol VP-1) como medio acumulador, enfriándose hasta los 1**80°** (límite inferior útil para el motor Stirling).
- Un motor Stirling de baja temperatura acoplado a un generador.

### Potencia Mecánica Ideal vs. Potencia Eléctrica Regulada (Figura 4)
![[Cost-effective Electro-Thermal Energy Storage to balance small scale renewable energy systems-1790466796665.webp]]
En la **Figura 4**, se comparan dos curvas de potencia durante la descarga:
- **La Curva Azul (Potencia Mecánica del Motor Stirling):** La eficiencia termodinámica del motor Stirling está directamente acoplada a la eficiencia de Carnot, la cual depende de la temperatura instantánea del medio caliente (T_h):$$  
    \eta_{th} = 1 - \frac{T_l}{T_h}  
    $$
    Al inicio de la descarga, con el acumulador a 400°, la diferencia de temperatura con el foco frío 30° es máxima, por lo que la eficiencia y la potencia mecánica potencial del motor son muy elevadas. A medida que el acumulador se enfría, la potencia mecánica disponible cae exponencialmente (curva azul hacia abajo).
- **La Línea Roja (Potencia Eléctrica de Salida):** En la práctica, el motor Stirling impulsa un generador eléctrico que tiene una **potencia nominal limitada** (en este ensayo, fijada en aproximadamente **2.7 kW**. Por lo tanto, aunque al inicio el motor tenga la capacidad mecánica de producir más energía, el generador eléctrico recorta la salida a su límite de diseño.
- **El Área Amarilla (Exceso de Potencia):** Representa la energía térmica que el motor Stirling _podría_ haber transformado en trabajo pero que el generador eléctrico no puede absorber. Es una pérdida por sobredimensionamiento térmico inicial.
### Tiempo de Descarga Ideal vs. Tiempo de Descarga Real (Figura 5)
![[Cost-effective Electro-Thermal Energy Storage to balance small scale renewable energy systems-1790466826942.webp]]
La comparación entre las dos figuras nos muestra el cuello de botella físico más importante para _nuestro diseño mecánico de pila de arena_:
- **El Escenario Ideal (Figura 4 → ~15.5 horas):**  
    Si asumiéramos que la transferencia de calor dentro del acumulador es instantánea y perfecta (conductividad térmica infinita), el calor se distribuiría de forma homogénea hacia el motor y la descarga a potencia constante de2.7kW se prolongaría durante unas **15.5 horas** antes de que el lecho caiga de los 180°.
- **El Escenario Real (Figura 5 → ~2.5 horas):**  
    En la simulación física real, la energía eléctrica constante se agota en solo **2.5 horas**.
    - ¿Por qué? Debido a la **resistencia a la transferencia de calor (conductividad térmica finita)** del medio acumulador.  
        Para entregar 2.7kW eléctricos, el motor Stirling demanda un flujo de calor constante extremadamente alto de la arena/aceite. Como el medio tiene una velocidad de conducción térmica limitada, el calor no llega lo suficientemente rápido desde las zonas alejadas del tanque hacia la cabeza del motor. El medio en contacto directo con el intercambiador se enfría rápidamente, provocando que la temperatura efectiva de entrada del motor T_h caiga por debajo de 180° mucho antes de lo ideal, deteniendo la generación útil.
### _Implicancia Directa para el Diseño Mecánico de la Pila de Arena_
Este análisis de la sección 3.1 es una advertencia de diseño para ti: **no basta con calcular cuánta energía cabe teóricamente en la masa de arena ($(m \cdot C_p \cdot \Delta T)$)**
Si diseñas un contenedor de arena estático sin un intercambiador de calor altamente eficiente, la batería se "descargará" localmente en la zona de contacto en muy pocas horas (debido a la bajísima conductividad térmica de la arena de sílice), dejando la mayor parte del calor atrapado e inutilizable en el resto del tanque. Debes diseñar una geometría de intercambiador interno (por ejemplo, aletas de alta conductividad o varillas metálicas distribuidas) que maximice la tasa de transferencia de calor desde todo el volumen de arena hacia tu fluido de trabajo.
## **Selección del material TES:**

Se compararon los tres materiales en un tanque de 1.5 m³ con 1 a 4 motores Stirling. Los resultados (Tabla 2) muestran que la arena ofrece la mejor eficiencia (**47.4%**) gracias a su amplio rango de temperatura (180 °C – 950 °C) y su alta capacidad calorífica. El aceite térmico alcanza un 35% y la sal fundida un 38.3%. La arena también es la más barata y abundante.
![[Cost-effective Electro-Thermal Energy Storage to balance small scale renewable energy systems-1790466859285.webp]]
![[Cost-effective Electro-Thermal Energy Storage to balance small scale renewable energy systems-1790466868346.webp]]
## **Caso de estudio en Ghana:**
Se simuló el ETES como almacenamiento principal de una granja solar fotovoltaica de 61 kW en Accra, Ghana, utilizando datos reales de irradiancia del PVWatts Calculator. El primer día se necesitan **400 kWh** para cargar el sistema desde temperatura ambiente hasta 400 °C (usando aceite térmico en este ejemplo). En días posteriores, solo se requieren **149 kWh** para recargar desde 180 °C hasta 400 °C. La energía descargada durante la noche fue de unos **70 kWh**.

## **Análisis de costos:**

Se realizó una comparación de costos con otras tecnologías de almacenamiento para sistemas de 1 MW y 100 MW (Tabla 3). Para el ETES con arena (1.5 m³, 88 kWh de capacidad), el costo total del sistema (tanque de acero, aislamiento, motor Stirling y generador) se estima en **24.142** $, mas el costo de la arena (2446 kg x 0,25$/kg=611,5$. Sumando el costo total de diseño nos daría un costo por kWh de **69 $/kWh**, que es:

- 6 veces más barato que las baterías de ion-litio en 2020.
- 4 veces más barato que la proyección de costo de las baterías de ion-litio para 2030.
- 7 veces más barato que las baterías de flujo redox de vanadio (VRFB).
![[Cost-effective Electro-Thermal Energy Storage to balance small scale renewable energy systems-1790467243612.webp]]

## **4. Conclusión**

El sistema ETES, especialmente con arena como material de almacenamiento, ofrece una solución modular, de bajo costo, sin materiales críticos y con una eficiencia aceptable (47.4%). Su vida útil se estima entre 25 y 50 años, muy superior a la de las baterías (10-20 años). Es especialmente adecuado para sistemas renovables aislados en zonas rurales, donde el costo y la disponibilidad de materiales son factores clave.

---

# 3. Parámetros Técnicos Clave

- **Volumen / Masa de arena:** Tanque de **1,5 m³** que contiene **2446 kg** de arena (el material seleccionado como óptimo). La arena es de tipo "garnet" o similar, con un precio de mercado de 0,25 $/kg.
- **Potencia y Capacidad:**
    - **Capacidad de almacenamiento térmico útil:** $198.4\text{ kWh}$ (_corregido de la cifra errónea de 359 kWh del paper original de 2021_).
    - **Potencia de descarga nominal:** **2,525 kW** por motor Stirling. El sistema base utiliza un solo motor, pero pueden añadirse más para aumentar la potencia.
    - **Duración de descarga:** Aproximadamente **35 horas** (88 kWh / 2,5 kW) en condiciones ideales; en la práctica, la duración de descarga a potencia constante es de unas **2,5 horas** debido a la tasa de transferencia de calor.
- **ΔT de trabajo:**
    - **Temperatura máxima de calentamiento:** **950 °C** (para arena). En el análisis principal se usa este valor.
    - **Temperatura mínima útil (antes de recarga):** **180 °C** (para arena y aceite térmico). Esta T es la mínima útil para mantener la eficiencia del motor Stirling
    - **Rango térmico efectivo:** ΔT = 950 °C – 180 °C = **770 °C**.
- **Tipo de intercambiador:**
    - No se emplean fluidos de transferencia de calor intermedios.
    - El calor se genera mediante **resistencias eléctricas** que están **enterradas** en el material de almacenamiento (arena). Estas resistencias también actúan como **barras conductoras de calor** (metálicas) que distribuyen el calor de manera uniforme.
    - Los cilindros calientes de los motores Stirling están **soldados o integrados** directamente en el tanque y en contacto con estas barras, permitiendo la conducción sólido-sólido sin bombas ni pérdidas asociadas.
    - Consiste en una varilla central metálica de alta conductividad que funciona simultáneamente como soporte físico para las resistencias eléctricas calefactoras (carga) y como puente térmico acoplado directamente (por soldadura) a la cabeza del motor Stirling (descarga)
- **Material aislante:** Se utiliza una manta aislante (de fibra cerámica) de alta temperatura **RS Pro Superwool 607 HT** (tolerancia de 1300 °C) colocada en el interior del tanque (cuando se usa arena) para proteger el acero. El tanque es de **acero ferrítico grado 4724 o 4713**, con resistencia a temperaturas entre 550 °C y 858 °C.
- **Eficiencia reportada:** **47,4%** (eficiencia de ida y vuelta, calculada como energía eléctrica descargada / energía eléctrica cargada × 100). Esta es la eficiencia para el sistema con arena, la más alta de las tres opciones estudiadas.
    - esto quiere decir que se perderá mas de la mitad de la energía (52.6%) en el proceso de almacenamiento y transferencia

---

# 4. Hallazgos Críticos

- **Innovación clave:** La integración directa de los motores Stirling en el tanque de almacenamiento, sin necesidad de fluidos de transferencia de calor intermedios, lo que reduce costos, complejidad y pérdidas energéticas.
- **Solución al problema de conductividad de la arena:** Para superar la baja conductividad térmica de la arena, se diseñan **barras metálicas (heater/heat conductor)** que actúan como resistencias eléctricas y como conductores de calor, distribuyendo el calor de manera eficiente y uniforme en todo el volumen del tanque.
    - diseño de una **estructura metálica interna solidaria (varilla calefactora/conductora)** que actúa como un puente térmico de alta conductividad. Esta estructura distribuye uniformemente el flujo de calor durante el calentamiento eléctrico y actúa como un colector de flujo térmico concentrado hacia las cabezas de los motores Stirling durante la fase de descarga, eliminando la necesidad de costosos sistemas de fluidos caloportadores de alta presión, bombas o aletas metálicas complejas
- **Diseño del contenedor:** El tanque es de acero ferrítico con aislamiento interior de alta temperatura (Superwool 607 HT) para soportar temperaturas de hasta 950 °C. Para materiales líquidos, el aislamiento se coloca en el exterior.
- **Pérdidas de calor:** Se basan en estudios experimentales de tanques de sales fundidas. Se consideran pérdidas menores, con tasas de enfriamiento de 4 °C/h a 550 °C y <1.5 °C/h por debajo de 300 °C, que pueden minimizarse con un aislamiento adecuado.
- **Modularidad y escalabilidad:** El sistema es altamente modular: se pueden añadir más motores Stirling para aumentar la potencia de descarga, y tanques de mayor volumen para aumentar la capacidad. Esto lo hace adecuado tanto para aplicaciones de pequeña escala (1 MW) como para grandes plantas (100 MW).
- **Limitación principal:** La eficiencia del 47.4% es inferior a la de las baterías (80-90%), pero el costo mucho menor y la larga vida útil pueden compensar esta desventaja en aplicaciones donde el costo y la disponibilidad de materiales son más importantes que la eficiencia máxima.