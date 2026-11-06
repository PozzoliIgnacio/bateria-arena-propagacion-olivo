---
Tipo:
  - Articulo
Año: 2024
URL: https://www.sciencedirect.com/science/article/pii/S2352152X24009356
Titulo esp.: Mejora de la conductividad térmica de la arena en sist de almacenamiento térmico
Padre: "[[CUDAR - Desarrollo de Pila de Arena]]"
Importancia:
  - A
---
# 1. Idea Central

**Objetivo principal:** Este estudio investiga la mejora de la conductividad térmica de lechos de arena para sistemas de almacenamiento de energía térmica (TES) mediante la adición de virutas metálicas de desecho (aluminio, latón y acero) provenientes de talleres mecánicos, con el fin de habilitar su uso en sistemas de baterías Carnot (ETES) de manera sostenible y económica.

**Conclusión fundamental:** La incorporación de virutas metálicas de desecho (especialmente un 20% en volumen de aluminio mezclado uniformemente) logra aumentar la tasa de calentamiento hasta **1.7 veces** respecto a la arena pura, mejorando significativamente la conductividad térmica efectiva. El modelo numérico ZBS (Zehner-Bauer-Schlünder) con término de radiación es el que mejor predice el comportamiento experimental, con un error inferior a 8°C. Esta solución de economía circular ofrece un enfoque rentable para superar las limitaciones térmicas de la arena sin recurrir a materiales costosos o procesos de recubrimiento complejos.

---

### Glosario de Abreviaciones

|Abreviatura|Significado en Inglés|Significado en Español|
|---|---|---|
|**TES**|Thermal Energy Storage|Almacenamiento de Energía Térmica|
|**ETES**|Electro-Thermal Energy Storage|Almacenamiento Electro-Térmico de Energía (Batería Carnot)|
|**CSP**|Concentrated Solar Power|Energía Solar Concentrada|
|**PCM**|Phase Change Material|Material de Cambio de Fase|
|**HTF**|Heat Transfer Fluid|Fluido de Transferencia de Calor|
|**ZBS**|Zehner-Bauer-Schlünder|Modelo de conductividad térmica efectiva (nombres de autores)|
|**RMSE**|Root Mean Square Error|Error Cuadrático Medio (métrica de precisión del modelo)|
|**MRF**|Mesh Refinement Factor|Factor de Refinamiento de Malla (en simulación COMSOL)|
|**EDM**|Electrical Discharge Machining|Mecanizado por Descarga Eléctrica (para virutas de latón)|
|**SEM**|Scanning Electron Microscopy|Microscopía Electrónica de Barrido (técnica de caracterización)|
|**FTIR**|Fourier Transform Infrared Spectroscopy|Espectroscopía Infrarroja por Transformada de Fourier|

# 2. Resumen por Secciones

## 2.1. Introducción

**Contexto:** Las energías renovables requieren sistemas de almacenamiento para equilibrar la oferta y demanda. Las baterías de iones de litio son costosas y tienen limitaciones de materiales críticos. Los sistemas de almacenamiento térmico (TES) emergen como alternativa, especialmente las baterías Carnot (ETES), que convierten electricidad en calor, lo almacenan y luego lo reconvierten en electricidad.

**Problema:** La arena es un material TES ideal por su bajo costo, abundancia y alta tolerancia térmica (~1700°C), pero su baja conductividad térmica (0.2-0.7 W/m·K) limita la transferencia de calor y la eficiencia del sistema. Los materiales de cambio de fase (sales fundidas) tienen mejor conductividad pero son corrosivos y costosos.

**Innovación:** Este estudio propone mejorar la conductividad de la arena añadiendo virutas metálicas de desecho (aluminio, latón y acero) desde una perspectiva de economía circular, evitando procesos de recubrimiento complejos y costosos no escalables a gran escala.

## 2.2. Métodos (Sección 2)

### 2.2.1. Experimental (Sección 2.1)

**Configuración experimental:**

- **Contenedor:** Rectangular de aluminio (380 mm alto × 230 mm largo × 380 mm ancho) — ver **Figura 1** (callout abajo).
- **Fuentes de calor:** Dos resistencias tubulares (2 kW cada una, control On/Off) de 298 mm × 309 mm × 50 mm, separadas 95 mm, con control hasta 1000°C.
- **Termopares:** Dos termopares tipo K: T3 entre los calentadores (45 ± 0.7 mm de cada uno) y T4 a 30 mm del calentador (ver **Figura 1**).
- **Aislamiento:** Superficie superior expuesta al aire ambiente (<26°C) sin aislamiento, para simular condiciones reales de pérdidas.

**Materiales utilizados:**

|Material|Tamaño|Conductividad (W/m·K)|Densidad (kg/m³)|Calor Específico (J/kg·K)|Punto de Fusión (°C)|
|---|---|---|---|---|---|
|**Arena Silica (marrón)**|0.06-0.2 mm|0.2-0.7|1800|703|1713|
|**Virutas Aluminio**|15-20 mm × 1.5 mm × 0.5 mm|205|2712|897|660|
|**Virutas Latón**|0.25 mm diámetro × 4.5 mm|~113|8430-8730|~380|900-940|
|**Virutas Metálicas Mixtas** (90% acero + 10% Al)|10-15 mm × 1.5 mm × 0.5 mm|50-70|~7850|~490|1370-1540|

**Como se obtienen?:**

- virutas de aluminio se obtuvieron a partir de procesos de mecanizado de tornos. Miden entre 15 y 20 mm de largo, 0.5mm de espesor y 1.5mm de ancho
- las virutas de laton surgen como subproducto del mecanizado por electroerosion con alambre

**Métodos de mezcla:** Dos configuraciones (ver **Tabla 1** y **Figura 1C**):

1. **Método por Capas:** 8 capas de arena (base 60 mm + 7 capas de 30 mm) separadas por capas de virutas metálicas de 10 mm, representando 20% del volumen total.
2. **Método Uniforme:** Mezcla homogénea de arena y virutas (20% volumen de virutas).

![[Improved effective thermal conductivity of sand bed in thermal energy storage systems-1790645518732.webp]]

> **Figura 1.** Vista en sección transversal del lado izquierdo indicando el caso de mezcla por capas. Se ve el contenedor rectangular con los calentadores, termopares y las capas alternas de arena y virutas metálicas. Incluye las cotas: 380 mm (alto), 230 mm (largo), 380 mm (ancho), separación de calentadores 95 mm, posiciones de termopares T3 y T4.

> [!NOTE] Termopar
> - es un sensor de Temperatura muy común en la industria.
> - Funcionamiento (efecto seebeck): cuándos dos metales distintos están unidos, un extremo (el caliente) y el otro extremo (la punta fría o conexión al medidor) están a una T diferente. Se genera un pequeño voltaje que es directamente proporcional a la diferencia de T
> - En la sección 2.1 del articulo especifican que se usan termopar del tipo K
> - En el articulo los autores ponen 4 puntos de medición:
> 	- T1 y T2 en la superficie de los calentadores. Actúan como el termostato de control, el sistema de control On/Off lee estos termopares y si la T baja de 500° enciende los 2000W, si supera los 500° entonces los apaga
> 	- T3 atrapado entre los dos calentadores: mide la acumulación de calor en la zona central. Como esta rodeado de calor por ambos lados y la arena conduce mal entonces este punto tarda mucho en enfriarse.  
> 	  Esta zona central es la _**trampa de calor**_ que describe el paper
> 	- T4 es el termopar exterior: mide como se escapa el calor hacia los laterales y las perdidas térmicas hacia el ambiente. Como la arena conduce mal, T4 siempre tiene una T mas baja que en la zona central T3. Sirve para cuantificar el gradiente térmico
> - Sirven para la **validaci**ó**n del modelo computacional** en COMBOL.  
![[Improved effective thermal conductivity of sand bed in thermal energy storage systems-1790645846227.webp]]
### 2.2.2. Modelado Numérico (Sección 2.2) - COMSOL Multiphysics
Para simular el lecho se utilizo el modulo _Heat Transfer in Solids_. Dado el alto costo computacional de simular millones de granos individuales, la arena se representó como un sólido homogéneo continuo mediante la **técnica de medio efectivo.**
**L**os calentadores están modelados como fuente de calor uniforme (fuentes de calor volumétricas) condicionales: las fuentes de calor se aplican segun una declaración _if_ para representar los controladores de encendido/apagado. La T se mide en el T3 y si es menor a 500° entonces el dominio del calentador se convierte en una fuente de calor constante de 2000W

**Control de calentadores:** Condicionales ON/OFF (si T < 500°C → 2000 W; si no → 0 W).

**Ecuación de transferencia de calor** en el dominio tridimensional es**:**

$$  
\rho C_p \frac{\partial T}{\partial t} + \nabla \cdot \mathbf{q} = Q \tag{1}  
$$

Donde la ley de conducción térmica de Fourier define el vector de flujo de calor $q$ en función del gradiente espacial de temperaturas:

$$  
\mathbf{q} = -k \nabla T  
$$

**Variables:**

- $\rho$ = densidad del medio continuo efectivo (kg/m³)
- $C_p$ = capacidad calorífica a presión constante del medio(J/kg·K)
- $T$ = temperatura (K)
- $t$ = tiempo (s)
- $\mathbf{q}$ = vector de flujo de calor (W/m²)
- $Q$ = fuente de calor volumétrica interna generada por las resistencias térmicas (W/m³)
- $k$ = conductividad térmica efectiva del lecho (W/m·K)

La conductividad térmica de la arena depende de la T y es compleja de calcular debido a la numero vía de transferencias de calor entre los granos de arena y los espacios vacíos. Hay numerosos correlaciones para calcular la conductividad efectiva

**Correlaciones de conductividad efectiva probadas:** Yagi-Kunii, Kunii-Smith, Zehner-Schlünder, Zehner-Bauer-Schlünder (ZBS), Batchelor, Hadley y Gonzo. Se evaluaron con y sin término de radiación.

> [!NOTE] **Que significa esto?**
> - el lecho de arena no es un solido, es una mezcla de tres cosas:
> 	- granos de sílice (solido)
> 	- aire atrapado entre los granos (gas)
> 	- Pequeños puntos de contacto entre granos (por donde viaja el calor por conducción solida)
> - por ende el modelo matemático y físico no puede considerar la conductividad térmica del cuarzo puro ya que seria erróneo por que el aire aísla y los contactos puntuales dificultan el paso del calor. La conductividad pura del cuarzo es de 1,5 W/mK mientras que la real de la arena seca va de 0,2 a 0,7
> - Para resolver esto los ingenieros usan **correlaciones matemáticas** que son formulas que, introduciendo datos como la porosidad, tamaño de grano, la temperatura, conductividad del aire y del solido, te devuelven un único numero: **la conductividad efectiva** de modo que el programa trata la arena como un solido homogéneo con esa conductividad calculada
> - Los autores probaron 7 modelos distintos para ver cual se ajustaba mejor a sus experimentos:
> 	- **modelos clásicos (**enfoque en el contacto solido**):**
> 		- **Yagi-Kuni** y **Kuni-Smith**: se centran en la resistencia térmica en los puntos de contacto entre granos. Asume que el calor pasa de grano a grano a través de pequeñas áreas circulares. Son muy buenos prediciendo la conductividad a temperaturas bajas o de ambiente
> 	- **Modelos modernos** (enfoque en la geometría del poro)
> 		- **Zehner-Schlünder (ZS)**: modelo muy usado en ingeniería química. Idealiza los poros (huecos entre granos) como capas cilíndricas concéntricas de solido y gas. Es mas preciso que los anteriores
> 		- **Zehner-Bauer-Schlünder (ZBS)**: Es el anterior pero mejor. Bauer añade un termino extra que considera la resistencia de contacto real entre partículas
> 	- **Otros modelos alternativos** (para comparar)
> 		- **Batchelor, Hadley y Gonzo**: Son modelos más matemáticos. En lugar de fijarse en la forma del grano, usan promedios ponderados (mezclan la conductividad del sólido y del gas en serie y en paralelo) para estimar un valor medio. Suelen dar valores de conductividad más altos que los modelos de contacto.
> - EL modelo en el que se basa el paper es el ZBS ya que es el que mejor predice como se comporta la arena a altas T  

> [!NOTE] **Que significa evaluarlos con y sin termino de radiación?**
> - Sin radiación: las formulas solo consideran que el calor solo se mueve por conduccion
> - Con radiación: añade un termino matemático extra a la formula. Esto se hace ya que cuando la arena supera los 300°-350°C los huecos de aire entre los granos se comportan como pequeños hornos haciendo que el calor ya no solo viaje por conducción sino que los granos calienten emiten radiación infrarroja (fotones) que viajan a través del hueco de aire e impacta en el grano de al lado, calentandolo
> - **Conclusión:** en el articulo se muestra que el modelo ZBS + Radiación es el único que replicaba con un error menor a 8°C la T real que marcaban los termopares T3 y T4. Sin la radiación el modelo predice T mucho mas bajas ya que subestima cuanto calor viaja entre granos a 500°  

Para modelar las pérdidas térmicas en las superficies del contenedor expuestas al ambiente, se aplicaron dos **condiciones de frontera**:

1. **Flujo radiactivo hacia el ambiente (ley de Stefan-Boltzmann):** Radiación superficie-ambiente
    
    $$  
    -\mathbf{\hat{n}} \cdot \mathbf{\hat{q}} = \psi \sigma (T_{amb}^{4} - T^{4})  
    $$
    
2. **Flujo por convección natural con el aire exterior:**
    
    $$  
    -\mathbf{\hat{n}} \cdot \mathbf{\hat{q}} = h (T_{amb} - T)  
    $$
    

**Variables:**

- $\mathbf{n}$ = vector normal a la superficie exterior.
- $\psi$ = emisividad superficial (arena: 0.9, aluminio: 0.1)
- $\sigma$ = constante de Stefan-Boltzmann (5.67×10⁻⁸ W/m²·K⁴)
- $T_{amb}$ = temperatura ambiente (285.15 K)
- $h$ = coeficiente de transferencia de calor por convección natural (5 W/m²·K)

**Malla:** Malla tetraédrica libre, factor de refinamiento MRF=2 (base) con estudio de sensibilidad MRF=1,2,3.
![[Improved effective thermal conductivity of sand bed in thermal energy storage systems-1790646163178.webp]]
> **Figura 3.** Geometría del TES utilizada en el modelado. Modelo CAD con dimensiones en metros (m): altura 0.6 m, ancho 0.4 m, profundidad 0.3 m aproximadamente. Incluye la ubicación de los calentadores y los puntos de termopares.
![[Improved effective thermal conductivity of sand bed in thermal energy storage systems-1790646179901.webp]]
![[Improved effective thermal conductivity of sand bed in thermal energy storage systems-1790646189362.webp]]
### 2.2.3. Cálculo de Tasa de Calentamiento (Sección 2.3)

**Fórmula:**

$$  
HR = \frac{\Delta T}{\Delta t} \tag{4}  
$$

Donde:

- $HR$ = Tasa de Calentamiento en cada paso de evaluación (°C/min)
- $\Delta T$ = cambio de temperatura entre mediciones consecutivas (°C)
- $\Delta t$ = cambio de tiempo para el mismo intervalo (min)

**Procedimiento:** Se registró el tiempo para alcanzar cada intervalo de 50°C desde 50°C hasta 500°C. Se identificó la tasa máxima para cada composición y se comparó con la arena pura.

## 2.3. Resultados y Discusión (Sección 3)

### 2.3.1. Validación del Modelo Térmico (Sección 3 - Figuras 5, 6, 7, 8)
![[Improved effective thermal conductivity of sand bed in thermal energy storage systems-1790646314723.webp]]
> **Figura 5.** Perfiles de temperatura de los termopares del lecho de arena: T1 y T2 (superficie de calentadores), T3 (termopar entre calentadores), T4 (termopar a 30 mm del calentador). Gráfica de temperatura (°C) vs tiempo (horas), mostrando las curvas de calentamiento.

- Los calentadores alcanzan 500°C en 30 min.
- T4 (30 mm del calentador) se calienta más rápido inicialmente que T3 (entre calentadores).
- Después de 80 min, T3 supera a T4, alcanzando la temperatura del calentador después de 7 horas.
- T3 actúa como "trampa de calor" (heat trap) debido a los calentadores en ambos lados.
- T4 se estabiliza en ~350°C después de 3 horas por pérdidas al ambiente.

**Figura 6A y 6B** — Correlaciones de conductividad térmica:

> **Figura 6.** Correlaciones de conductividad térmica efectiva para materiales granulares desde temperatura ambiente hasta 500°C: (A) expresiones sin radiación, (B) expresiones con radiación. Gráficas de conductividad (W/m·K) vs temperatura (°C).

![[Improved effective thermal conductivity of sand bed in thermal energy storage systems-1790646339593.webp]]
- Las correlaciones que incluyen radiación tienen curvatura positiva.
- El modelo ZBS con radiación predice conductividades ligeramente superiores a Zehner-Schlünder.
- El término de radiación es pequeño a bajas temperaturas pero crece con la temperatura.

**Figura 7A y 7B** — Comparación modelo-experimento:
![[Improved effective thermal conductivity of sand bed in thermal energy storage systems-1790646365753.webp]]

> **Figura 7.** (A) Comparación de modelos de correlación con datos medidos en T3. (B) Gráfico de error RMSE promedio para cada correlación en los cuatro puntos de temperatura.

- Las correlaciones con mayor conductividad predicen temperaturas más altas en T3.
- El modelo ZBS + Radiación mostró el **menor error RMSE (< 8°C)**.
- Las correlaciones Hadley, Gonzo y Zehner representan mejor la conductividad en todo el rango de temperatura, mientras que Yagi-Kunii y Kunii-Smith son mejores solo a baja temperatura.

**Figura 8** — Validación final:

> **Figura 8.** Comparación del modelo Zehner-Bauer con radiación y datos medidos en el lecho de arena para T1, T2, T3, T4.

![[Improved effective thermal conductivity of sand bed in thermal energy storage systems-1790646383853.webp]]
- Excelente concordancia modelo-experimento para T1, T2 y T4.
- Desviación leve en T3 por encima de 350°C, atribuida a simplificaciones en el modelo de calentadores y pérdidas térmicas no uniformes.

### 2.3.2. Sensibilidad de Malla y Pérdidas Térmicas

- **MRF=2** (simulación ~2 horas) es adecuado; MRF=3 tomó 3.5 horas con resultados casi idénticos.
- Aumento de pérdidas (emisividad arena: 0.9→0.97, emisividad aluminio: 0.1→0.3, h: 5→20 W/m²·K) provocó solo:
    - 1% de disminución en T3 (temperatura media). Esto es así ya que esta rodeado de arena y de dos fuentes de calor, aunque la superficie exterior se enfrié mucho el calor atrapado en el medio tarda muchísimo en escapar. La arena actúa como un aislante natural para su propio núcleo
    - 6% de disminución en T4. T4 esta cerca de la pared exterior del contenedor, al aumentar las perdidas en la superficie el frio del exterior penetra mas rápido hacia la zona periférica
    - El modelo es **relativamente insensible** a las pérdidas térmicas. Significa que los autores pueden confiar en la simulación por mas que hayan estimado mal al emisividad real de la arena o el viento real de la habitación. Incluso equivocándose mucho, la T en la zona de interés (T3, donde iría el motor Stirling) apenas varia.
        - Esto tiene gran implicación practica ya que significa que para construir sistemas de este tipo **no hace falta gastar dinero en aislantes perfectos o carcasas selladas al vacío** ya que aunque la superficie exterior pierda calor, el centro del lecho de arena retiene el calor de forma estable
> [!NOTE] Definición  **Que significa aumento de perdidas? Que significa que el ‘modelo es relativamente insensible a las perdidas térmicas’?**
> - en el modelo numérico los autores tuvieron que inventar o estimar ciertos valores para las condiciones de contorno (paredes del contenedor). Como no estaban seguros de esos valores en la vida real, forzaron al modelo al peor escenario posible, es decir que multiplicaron artificialmente la cantidad de calor que se escapa al ambiente. Para ello cambiaron tres parámetros:
> 	- Emisividad de la arena (0,9 → 0,97): la emisividad mide la capacidad de un material para irradiar calor, al subirlo a 0.97 (casi un cuerpo negro perfecto) obligan a la superficie de arena a radiar mucho mas calor hacia el aire exterior
> 	- Emisividad del aluminio (0.1 → 0.3): el aluminio del contenedor es brillante y refleja el calor (emisividad baja). Al subirlo a 0.3 se obliga a la caja metálica a desprender mas calor por radiación
> 	- Coeficiente de convección _h_ (5 → 20 W/m²·K): este coeficiente mide la eficiencia con la que el aire que roza la superficie se lleva el calor. Al multiplicarlo por 4 estamos simulando que hay una corriente de aire muy fuerte enfriando el contenedor  
### 2.3.3. Mejora de Conductividad con Virutas Metálicas (Figura 9 y Tabla 3)
**Resultados clave (T3 - zona entre calentadores):**

|Composición|Tasa Máxima (°C/min)|Rendimiento (vs arena pura)|
|---|---|---|
|Arena Pura|5.0|1.00×|
|**Latón + Arena (capas)**|**8.8**|**1.79×** (mejor)|
|Metales Mixtos + Arena (capas)|8.7|1.76×|
|Aluminio + Arena (capas)|8.5|1.71×|
|Aluminio + Arena (uniforme)|8.4|1.70×|
|Latón + Arena (uniforme)|8.2|1.65×|
|Metales Mixtos + Arena (uniforme)|7.3|1.48×|

**Análisis de resultados:**

- **Latón en capas** es el mejor (1.79×) debido a:
    - Mayor densidad (3× aluminio)
    - Forma de alambre recto que crea "aletas" conductoras y reduce espacios porosos
    - Mayor cantidad de material en la capa por su geometría compacta
- **Aluminio uniforme** es el más equilibrado (1.70×) y económicamente viable (precio 4× más barato que latón).
- Los metales mixtos (90% acero) tienen menor rendimiento por su baja conductividad.

**Figura 9:** Impacto del medio de almacenamiento en el flujo de calor hacia los termopares T3 (A) y T4 (B). Gráficas de temperatura (°C) vs tiempo (horas) comparando arena pura con mezclas de virutas metálicas (aluminio, latón y metales mixtos) en ambos métodos (capas y uniforme). Son dos gráficas: una para T3 y otra para T4.

![[Improved effective thermal conductivity of sand bed in thermal energy storage systems-1790646739799.webp]]

### 2.3.4. Efecto de la Concentración de Aluminio (Figura 10 y Tabla 5)

|% Aluminio (volumen)|Tasa Máxima (°C/min)|Rendimiento (vs arena pura)|
|---|---|---|
|0% (arena pura)|5.0|1.00×|
|5%|5.9|1.18×|
|10%|6.7|1.36×|
|**20%**|**8.4**|**1.70×**|

**Interpretación:** El aumento no es lineal; se requiere un contenido mínimo (cerca del umbral de percolación) para conectar las virutas y crear caminos conductivos efectivos. Con 5-10% las virutas están aisladas; con 20% se forman redes conductoras.

![[Improved effective thermal conductivity of sand bed in thermal energy storage systems-1790646755380.webp]]

> **Figura 10.** Comparación de diferentes composiciones de contenido de aluminio: 5%, 10% y 20% mezclados uniformemente con arena. Gráficas de temperatura (°C) vs tiempo (horas) para T3 (A) y T4 (B), mostrando cómo aumenta la conductividad con mayor porcentaje de aluminio.

### 2.3.5. Comparación con Otros Estudios (Tabla 6)

|Referencia|Método|Rango de Temp.|Aplicación|
|---|---|---|---|
|Chung et al. [26]|Recubrimiento de arena con nanopartículas|20-700°C|CSP|
|García-Plaza et al. [27]|Recubrimiento con grafito/carbono|20-210°C|CSP (lecho fluidizado)|
|Yi et al. [28]|Adición de polvo de granito|Baja T|Bomba de calor geotérmica|
|Barbi et al. [29]|PCM + arena|12-35°C|Bomba de calor geotérmica|
|Liu et al. [30]|Caucho reciclado + arena|No espec.|Bomba de calor geotérmica|
|**Este estudio**|**Virutas metálicas de desecho**|**20-500°C**|**Baterías Carnot, TES en lecho empacado**|

**Ventaja de este estudio:** Amplio rango de temperatura, enfoque en baterías Carnot, solución escalable y de bajo costo (economía circular), sin necesidad de procesos de recubrimiento complejos.

## 2.4. Conclusiones (Sección 4)

- La arena es un material TES prometedor por su bajo costo, pero su baja conductividad térmica limita su uso en sistemas que requieren altas tasas de transferencia de calor (ej. motores Stirling).
- El modelo ZBS con radiación predice adecuadamente la conductividad efectiva (error < 8°C), aunque hay un 5% de desajuste a altas temperaturas (>350°C).
- La adición de virutas metálicas de desecho (especialmente 20% de aluminio en mezcla uniforme) multiplica por 1.7 la tasa de calentamiento, mejorando significativamente la transferencia de calor.
- La configuración de **latón en capas** ofrece la mejora máxima (1.79×), pero la mezcla **aluminio-uniforme** es más económica y práctica.
- Esta solución de economía circular reduce costos, evita el reciclaje energéticamente costoso de virutas metálicas y mejora la eficiencia de baterías Carnot y otros sistemas TES.

---

# 3. Parámetros Técnicos Claves

|Parámetro|Valor / Descripción|¿Especificado?|
|---|---|---|
|**Volumen / Masa de arena**|Volumen del lecho: 0.38 × 0.23 × 0.38 = **0.0332 m³** <br> Densidad: 1800 kg/m³ (arena) o 1425 kg/m³ (medida de muestra) <br> Masa aprox.: ~47-60 kg de arena|✅ Sí (especificado)|
|**Potencia y Capacidad**|**Potencia de calentamiento:** 2 × 2 kW = **4 kW** (dos resistencias) <br> **Capacidad de almacenamiento:** No se calcula directamente en el estudio; es un experimento de mejora de conductividad, no de capacidad energética. <br> Temperatura máxima alcanzada: 500°C (control)|⚠️ Potencia sí; capacidad no especificada|
|**ΔT de trabajo**|**Rango experimental:** 20°C (inicial) → 500°C (máximo) <br> **ΔT ≈ 480°C** <br> **Temperatura útil mínima:** ~350°C (estabilización en T4) antes de requerir recarga; aunque no se define explícitamente. En la práctica, el sistema puede operar entre 20°C y 500°C.|✅ Sí (rango 20-500°C)|
|**Tipo de intercambiador**|**Inyección de calor:** Dos resistencias eléctricas tubulares (tubular-type resistance heaters) **enterradas directamente en el lecho de arena**. No hay fluido térmico. **Extracción de calor:** No implementada en este estudio; se menciona como trabajo futuro el acoplamiento con motor Stirling. El método propuesto sería conducción directa desde el lecho al motor Stirling insertado en el material TES.|✅ Sí (resistencias enterradas)|
|**Material aislante**|**Sin aislamiento en la superficie superior** (expuesta al aire ambiente).||
|**Contenedor de aluminio** (actúa como pared conductora, no aislante).|||
|Las pérdidas térmicas se modelan por radiación y convección natural al ambiente. No se usa aislante externo; esto representa un escenario de pérdidas realista.|✅ Sí (sin aislamiento)||
|**Eficiencia reportada**|**No se reporta eficiencia eléctrica → calor → eléctrica** (no se implementó la recuperación de electricidad). Se reporta mejora en **tasa de calentamiento** (heat rate) en lugar de eficiencia: <br> - Latón en capas: 1.79× mejor que arena pura <br> - Aluminio 20% uniforme: 1.70× mejor <br> - El modelo numérico tiene precisión de **< 8°C de error** (RMSE). <br> No se proporciona eficiencia en términos de energía recuperada/energía almacenada.|❌ No especificado|

---

# 4. Hallazgos Críticos

1. **Solución de economía circular innovadora:** Utiliza virutas metálicas de desecho (normalmente sin valor secundario) para mejorar la conductividad térmica de la arena, evitando procesos de reciclaje energéticamente costosos y reduciendo el costo total del sistema TES.
2. **Mejora significativa de la conductividad:** La adición de solo 20% en volumen de virutas de aluminio (mezcla uniforme) multiplica por **1.7** la tasa de calentamiento, pasando de 5.0 a 8.4°C/min. Esto es suficiente para habilitar el uso de arena en baterías Carnot con motores Stirling.
3. **Latón en capas como mejor configuración:** A pesar de que el aluminio tiene mayor conductividad que el latón, las virutas de latón (residuos de EDM, forma de alambre) crean capas densas y compactas que actúan como **aletas conductoras**, logrando la mayor mejora (1.79×). La forma y geometría del residuo son tan importantes como su conductividad intrínseca.
4. **Modelo ZBS con radiación como predictor preciso:** El modelo Zehner-Bauer-Schlünder que incluye radiación predice la temperatura del lecho con un error **inferior a 8°C**, demostrando que los efectos radiativos no son despreciables por encima de 350°C y deben incluirse en simulaciones de TES de alta temperatura.
5. **Efecto umbral de percolación:** El contenido de virutas debe superar el **umbral de percolación** (~10-20% en volumen) para crear una red conductora continua. Con 5-10% de aluminio, las virutas están aisladas y la mejora es modesta (1.18-1.36×); con 20% se logra una red conectada y la mejora es sustancial (1.70×).
6. **Diseño simplificado y bajo costo:** A diferencia de otros estudios que requieren recubrimientos complejos, mezclas con PCM costosos o polvos de granito, esta solución solo requiere **mezclar virutas con arena** y compactar, lo que la hace escalable industrialmente.
7. **Sistema de calentamiento sin partes móviles:** Los calentadores eléctricos enterrados eliminan la necesidad de fluidos térmicos o bombas, reduciendo costos de mantenimiento y fallos mecánicos.
8. **Baja sensibilidad a pérdidas térmicas:** El modelo muestra que incluso aumentando significativamente las pérdidas por radiación y convección, la temperatura en el centro del lecho (T3) solo disminuye un 1%, lo que indica un diseño robusto frente a variaciones en condiciones ambientales.
9. **Potencial para eliminar bombas de calor en TES subterráneos:** La mejora de conductividad permite que el sistema opere a altas temperaturas (500°C) sin necesidad de bombas de calor, reduciendo costos y complejidad en comparación con sistemas geotérmicos de baja temperatura.
10. **Validación experimental-numérica robusta:** El estudio combina experimentos detallados con simulación COMSOL, validando el modelo con datos reales y demostrando que la simulación puede usarse para diseñar sistemas TES a gran escala sin necesidad de construir prototipos costosos.

# Material complementario: ecuaciones y tablas para el modelado térmico.

[1-s2.0-S2352152X24009356-mmc1.docx](attachment:2eda521a-f6be-4252-9657-38d91b64adf0:1-s2.0-S2352152X24009356-mmc1.docx)

## TABLA S1: Correlaciones para la conductividad térmica efectiva de materiales granulares

|Correlación|Expresión Matemática|
|---|---|
|**Batchelor** [1], [2]|$k_{e}^{B} = k_{f}\left( 4 \cdot \ln(\kappa) - 11 \right)$|
|**Hadley** [2], [3]|$k_{e}^{H} = k_{f}\left( \left( 1 - \alpha_{0} \right)\left( \frac{\epsilon f_{0} + \kappa\left( 1 - \epsilon f_{0} \right)}{1 - \epsilon\left( 1 - f_{0} \right) + \kappa\epsilon\left( 1 - f_{0} \right)} \right) + \frac{2\alpha_{0}(\kappa)^{2}(1 - \epsilon) + (1 + 2\epsilon)\kappa}{(2 + \epsilon)\kappa + 1 - \epsilon} \right)$|
|**Gonzo** [2], [4]|$k_{e}^{G} = k_{f}\left( \frac{1 + 2C(1 - \epsilon) + \left( 2C^{3} - 0.1C \right)(1 - \epsilon)^{2} + (1 - \epsilon)^{3} \cdot 0.05 \cdot e^{4.5 \cdot C}}{1 - C(1 - \epsilon)} \right)$|
|**Kunii-Smith** [2], [5]|$k_{e}^{KS} = k_{f}\left( \epsilon + \frac{\beta(1 - \epsilon)}{\phi + \gamma\left( \frac{k_{f}}{k_{s}} \right)} \right)$|
|**Yagi-Kunii** [2], [6]|$k_{e}^{YK} = k_{f}\left( \frac{\beta(1 - \epsilon)}{\phi + \gamma\left( \frac{k_{f}}{k_{s}} \right)} \right)$|
|**Zehner-Schlünder (ZS)** [7]|$k_{e}^{ZS} = k_{f}\left( \left( 1 - \sqrt{1 - \epsilon} \right) + \sqrt{1 - \epsilon} \cdot \Gamma \right)$|
||$\Gamma = \frac{2}{1 - \frac{B}{\kappa}}\left( \frac{\kappa - 1}{\left( 1 - \frac{B}{\kappa} \right)^{2}}\frac{B}{\kappa} \cdot \ln\left( \frac{\kappa}{B} \right) - \frac{B - 1}{1 - \frac{B}{\kappa}} - \frac{1}{2}(B + 1) \right)$|
|**Zehner-Bauer-Schlünder (ZBS)** [7]|$k_{e}^{ZBS} = k_{f}\left( \left( 1 - \sqrt{1 - \epsilon} \right) + \sqrt{1 - \epsilon} \cdot \left( \omega\kappa + (1 - \omega)\Gamma \right) \right)$|
|**Yagi-Kunii con radiación** [6]|$k_{e}^{YK,r} = k_{f}\left( \epsilon\frac{\beta \cdot d_{p} \cdot h_{rv}}{k_{f}} + \frac{\beta(1 - \epsilon)}{\gamma\left( \frac{k_{f}}{k_{s}} \right) + \frac{1}{\frac{1}{\phi} + \frac{d_{p} \cdot h_{rs}}{k_{f}}}} \right)$|
||$h_{rv} = 0.1952\left( 1 + \frac{\epsilon(1 - \psi)}{2\psi(1 - \epsilon)} \right)^{- 1} \cdot \left( \frac{T}{100} \right)^{3}$|
||$h_{rs} = \frac{0.1952\psi}{2 - \psi} \cdot \left( \frac{T}{100} \right)^{3}$|
|**Kunii-Smith con radiación** [5]|$k_{e}^{KS,r} = k_{f}\left( \epsilon\left( 1 + \frac{\beta \cdot h_{rv} \cdot d_{p}}{k_{f}} \right) + \frac{\beta(1 - \epsilon)}{\gamma\left( \frac{k_{f}}{k_{s}} \right) + \frac{1}{\frac{1}{\phi} + \frac{d_{p} \cdot h_{rs}}{k_{f}}}} \right)$|
||$h_{rv} = 0.227\left( 1 + \frac{\epsilon(1 - \psi)}{2\psi(1 - \epsilon)} \right)^{- 1} \cdot \left( \frac{T}{100} \right)^{3}$|
||$h_{rs} = \frac{0.227\psi}{2 - \psi} \cdot \left( \frac{T}{100} \right)^{3}$|
|**Zehner-Schlünder con radiación** [7]|$k_{e}^{ZS,r} = k_{e}^{ZS} + k_{e}^{r}$|
||$k_{e}^{r} = 4F_{B}\sigma d_{p}T^{3}$|
||$F_{B} = \left( 1 - \sqrt{1 - \epsilon} \right)\epsilon + \frac{\sqrt{1 - \epsilon}}{2\text{/}\psi - 1} \cdot \frac{B + 1}{B} \cdot \frac{1}{1 + \frac{1}{\left( 2\text{/}\psi - 1 \right)\Lambda}}$|
|**ZBS con radiación** [7]|$k_{e}^{ZBS,r} = k_{e}^{ZBS} + k_{e}^{r}$|

---

## TABLA S2: Funciones y variables de las correlaciones de conductividad térmica efectiva (ETC)

|Variable|Definición|Descripción|Fuente|
|---|---|---|---|
|$\kappa$|$\frac{k_{s}}{k_{f}}$|Relación de conductividades sólido/fluido|—|
|$\alpha_{0}$|$\log\left( \alpha_{0} \right) = - 1.084 - 6.778(\epsilon - 0.298)$|Parámetro de consolidación (Hadley)|[2]|
|$\Lambda$|$\frac{k_{s}}{4\sigma d_{p}T^{3}}$|Término simplificador|[7]|
|$\phi$|$\phi = \phi_{2} + \left( \phi_{1} + \phi_{2} \right)\frac{\epsilon - 0.26}{0.216}\$ para $0.26 \leq \epsilon \leq 0.476$|Parámetro de ajuste que describe el espesor de la película de fluido que rodea los granos (Kunii-Smith)|[5]|
||$\phi = \phi_{1}\$ para $\epsilon \geq 0.476$|||
||$\phi = \phi_{2}$ para $\epsilon \leq 0.26$|||
||$\phi_{1or2} = \frac{0.5\left( (\kappa - 1)\text{/}\kappa \right)^{2} \cdot sin^{2}\left( \theta_{0} \right)}{\ln\left( \kappa - (\kappa - 1)\cos\left( \theta_{0} \right) \right) - \left( (\kappa - 1)\text{/}\kappa \right)\left( 1 - cos\left( \theta_{0} \right) \right)} - \frac{2}{3\kappa}$|||
||$sin^{2}\left( \theta_{0} \right) = 2\text{/}3$ para $\ \epsilon \geq 0.476$|||
||$sin^{2}\left( \theta_{0} \right) = 1\text{/}\left( 4\sqrt{3} \right)$ para $\epsilon \leq 0.26$|||
|$\epsilon$|$\epsilon = 1 - \frac{\rho_{bulk}}{\rho_{grain}}$|Porosidad del medio de arena|—|
|$B$|$1.25\left( \frac{1 - \epsilon}{\epsilon} \right)^{10\text{/}9}$|Parámetro de deformación (modelos Zehner)|[7]|
|$C$|$\frac{k_{s} - k_{f}}{k_{s} + 2k_{f}}$|Polarizabilidad térmica reducida (Gonzo)|[2], [4]|
|$f_{0}$|$f_{0} = 0.8 + 0.1\epsilon$|Parámetro de cierre (Hadley)|[2]|
|$\rho_{bulk}$|1425 kg/m³|Densidad aparente de la arena (medida)|Medido|
|$\rho_{grain}$|2650 kg/m³|Densidad de un grano de arena|—|
|$k_{s}$|$0.95 + 1.21 \cdot 10^{- 3} \cdot T + 7.19 \cdot 10^{- 7} \cdot T^{2}$|Conductividad térmica del grano TES [W/(m·K)]|[8]|
|$\psi$|0.7|Emisividad de un grano de arena|[7]|
|$d_{p}$|0.5 mm|Tamaño medio de grano|—|
|$k_{f}$|$6 \cdot 10^{- 5} \cdot T + 0.0081$|Conductividad térmica del aire en el TES [W/(m·K)]|[9]|
|$\beta$|0.9|Parámetro de deformación (Yagi-Kunii; Kunii-Smith)|[5], [7]|
|$\gamma$|2/3|Parámetro de ajuste (Yagi-Kunii; Kunii-Smith)|[5], [7]|
|$\omega$|0.0010|Parámetro de área de contacto (modelos Zehner)|[10]|
|$\sigma$|$5.67 \cdot 10^{- 8}\ W\text{/}\left( m^{2} \cdot K^{4} \right)$|Constante de Stefan-Boltzmann|—|

## Referencias completas (material suplementario)