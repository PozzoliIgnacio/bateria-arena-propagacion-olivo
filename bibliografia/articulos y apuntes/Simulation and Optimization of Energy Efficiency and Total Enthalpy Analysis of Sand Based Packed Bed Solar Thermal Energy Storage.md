---
Titulo esp.: Simulación y optimización de la eficiencia energética y análisis de la entalpía total del almacenamiento de energía solar térmica en lechos empaquetados a base de arena
Año: 2024
Padre: "[[CUDAR - Desarrollo de Pila de Arena]]"
Importancia:
  - B
URL: https://www.sciencedirect.com/org/science/article/pii/S2151862924001282#fig-6
---
## 1. Idea Central
El estudio **simula y optimiza con COMSOL Multiphysics un almacenamiento térmico sensible de lecho empacado de arena**, con **agua caliente como fluido de transferencia (HTF) y también como medio de almacenamiento**. 
Se diseñó para hornear _injera_ con energía solar en zonas rurales de Etiopía. 
Se varían cuatro parámetros (altura, diámetro, caudal de agua y tamaño de partícula) para **minimizar el tiempo de carga**, y el resultado se valida con el método Taguchi y un ANOVA.

**Conclusión fundamental:** la geometría óptima es **H = 1,4 m, D = 0,4 m, caudal = 0,02 kg/s, partícula = 12 mm**. El diámetro es el parámetro más influyente. El tanque optimizado se carga hasta ~520 K en **~2000 s**, contra más de 3500 s del diseño nominal. Su eficiencia de carga promedio es **13,7 % mayor** que la nominal y **13,1 % mayor** que la de un almacenamiento de concreto de la literatura.
### Glosario de abreviaciones

|Sigla / símbolo|Significado|
|---|---|
|**STES** (el paper lo escribe también "STEM" en la nomenclatura)|_Sensible Thermal Energy Storage_: almacenamiento por calor sensible (sube la temperatura del material)|
|**LTES / PCM**|Almacenamiento por calor latente / Material de cambio de fase|
|**HTF**|_Heat Transfer Fluid_: fluido caloportador (aquí, agua)|
|**COMSOL**|Software de elementos finitos multifísica|
|**EES**|_Engineering Equation Solver_ (software de resolución de ecuaciones)|
|**Taguchi / L 9**|Método estadístico de diseño de experimentos; L 9 = arreglo ortogonal de 9 ensayos|
|**S/N (SNRA 4)**|_Signal-to-Noise ratio_: métrica de Taguchi, aquí "mayor es mejor"|
|**ANOVA**|Análisis de varianza (p < 0,05 = factor significativo)|
| $Q_s$ |Energía térmica almacenada|
| $m$, $\dot m$ |Masa / caudal másico|
| $C_p$, $C_{p,s}$, $C_{p,f}$ |Calor específico (general / arena / fluido)|
| $\rho$ |Densidad|
| $V$ |Volumen|
| $\varepsilon$ |Porosidad (fracción de huecos del lecho)|
| $A_s$ |Área superficial del tanque|
| $D$, $H$ |Diámetro y altura del tanque|
| $T_H$, $T_C$ |Temperatura caliente y fría|
| $T_{s,ini}$, $T_{f,ini}$ |Temperatura inicial de la arena y del fluido|
| $\Delta t$ |Intervalo de tiempo|
| $v$ |Volumen específico|
## 2. Resumen por Secciones
### 2.0 Introducción (Sección 1)
- La energía solar es intermitente, así que hace falta almacenarla. El calor se puede guardar como **latente** (cambio de fase, casi isotérmico) o como **sensible** (subiendo la temperatura del material).
- En un **lecho empacado**, el fluido atraviesa un relleno sólido (esferas, grava, arena) dentro de un recipiente de acero con aislante.
- La arena es barata y local. Se citan trabajos que usan arena a baja y alta temperatura, pero **no hay trabajos de arena para temperatura media**. Ese es el hueco que el paper declara cubrir.
- Dato de la literatura: usar agua en vez de aire acorta unas **5 veces** el tiempo de carga, porque el agua tiene mucha mayor capacidad calorífica.
- Un tanque más esbelto y partículas más chicas mejoran la transferencia convectiva fluido-sólido, pero **aumentan la caída de presión**. Hay un compromiso.
### 2.1 Descripción del sistema (Sec. 2.1)
Componentes: colector parabólico, absorbedor, tubería caliente, válvulas, tanque de almacenamiento, tubo de acero inoxidable, sartén de horneado y tanque de agua.
- **Carga:** el agua caliente fluye a traves del tubo de acero inoxidable (tubo caliente) y transfiere la energia termica a la arena y al fluido dentro del tanque de almacenamiento. Entra por **arriba**, cede calor a la arena y sale por **abajo**.
- **Descarga:** el calor almacenado se transfiere a traves del tubo de acero inoxidable desde el material de almacenamiento al mode para hornear. El flujo se **invierte** y el agua entra por abajo, se calienta y sale por arriba.
- Esto mantiene la **estratificación térmica** (termoclina): zona caliente arriba, fría abajo, aprovechando la flotación.
- 
![[Simulation and Optimization of Energy Efficiency and Total Enthalpy Analysis of Sand Based Packed Bed Solar Thermal Energy Storage-1793739366325.webp]] *Figura 1: esquema del sistema completo.*  
- *El agua fria se almacena en el tanque de almacenamiento, luego fluye a traves de la tuberia fria y llega al absorvedor. 
- *Se mantiene en el punto focal del colector parabolico de forma que se calienta debido a la concentracion de radiacion solar en el foco del colector.*
- *Luego se hace fluir el agua caliente a traves del tubo de acero inoxidable (tubo caliente) y se transfiere la energia termica a la arena y al fluido dentro del tanque de almacenamiento.*
![[Simulation and Optimization of Energy Efficiency and Total Enthalpy Analysis of Sand Based Packed Bed Solar Thermal Energy Storage-1793739423698.webp]] *Figura 2 a y 2 b: vista 3D y 2D del lecho con las flechas de carga/descarga
	- Durante al carga, el agua caliente o el vapor ingresan al almacenamiento por la parte superior, transfieren energia termica o calor a la arena y salen por la parte inferior
	- En la descarga el agua pasa por el fondo, se calienta con la arena y sale por la parte superior.*
### 2.2 Ecuaciones de almacenamiento (Sec. 2.1)
**Energía sensible almacenada (Ec. 1):** Capacidad de energia sencible almacenada 
$$Q_s = mC_p\Delta T = (\rho v)C_p\Delta T$$
- $Q_s$: energía almacenada [J]
- $m$: masa de arena [kg]
- $C_p$: calor específico de la arena (835-850 J/kg·K)
- $\rho$: densidad de la arena (1600 kg/m³)
- $v$: volumen de arena [m³]
- $\Delta T$: diferencia entre temperatura máxima y mínima del rango de trabajo

**Capacidad volumétrica de la arena:** $\rho C_p = 835 \times 1600 = 1{,}336{,}000\ \text{J/m}^3\text{K}$. Cuanto mayor es este producto, mejor es el material.

**Potencia entregada por un almacenamiento de fluido (Ec. 2):** define el balance de energia en transferencia, donde $\dot Q_t$ es la potencia termica entregada. 
$$\dot Q_t = \dot m, C_f,(T_h - T_c)$$
- $\dot Q_t$: potencia térmica [W]
- $\dot m$: caudal másico del fluido
- $C_f$: calor específico del fluido
- $T_h - T_c$: salto de temperatura del fluido

**Energía total y volumen ideal (Ecs. 3-4).** 
$$E = \dot Q_t,\Delta t \qquad V_{ideal} = \frac{\dot m,\Delta t}{\rho_f}$$
$V_{ideal}$ es el volumen de agua pura que entregaría esa energía durante $\Delta t$.
### 2.3 Diseño conceptual del tamaño (Sec. 2.2)
**Relación de aspecto (Ecs. 5-7).** Se busca minimizar la relación superficie/volumen, o sea las pérdidas:
$$A_s = 2\cdot\frac{\pi}{4}D^2 + \pi D H \qquad V = \frac{\pi}{4}D^2 H \qquad F=\frac{A_s}{V}\to \min$$
- $A_s$: área total del cilindro (2 tapas + pared lateral)
- $V$: volumen del cilindro
- $F$: relación superficie/volumen a minimizar

El óptimo geométrico (resuelto en EES (software de resolucion de ecuaciones de ecuaciones)) da **D/H = 1**. 
	- *El diametro del almacenamiento D y la altura H se fijan en funcion de la relacion de aspecto, (D/H) la cual esta limitada por la viabildiad estructural*
Pero por requisitos de transferencia de calor y de espacio, **eligieron D/H = 0,4** (un tanque más alto y esbelto). Es un compromiso entre pérdidas y transferencia/estratificación.
	- *A medida que aumenta el tamaño del material de almacenamiento, aumentara l superficie por volumen de la misma masa.*

**Partículas y porosidad.** Se adoptaron **ε = 0,2** y **12 mm**, basándose en trabajos previos (lechos de ~1 cm; sílice de 1,5 cm con ε = 0,22).

**Caudal de diseño (Ecs. 8-11).** Se parte de la energía para hornear injera: **37,841 MJ en 2,5 h**.
$$\dot Q_T = \frac{37.841\times10^6\ \text{J}}{2{,}5\cdot 3600\ \text{s}} \approx 4{,}2\ \text{kW} \qquad \dot m = \frac{\dot Q_T}{C_f,(T_h-T_c)} \approx 0{,}0167\ \text{kg/s}$$

**Volumen real (Ecs. 12-13).** Como la arena almacena menos calor por volumen que el agua, el tanque real debe ser mayor que el ideal. 
$$ V_{real}=[(\rho_{f} \cdot C_{f})+(1-\varepsilon)\rho_{s} \cdot C_{S}]>V_{ideal} (\rho_{f}\cdot C_{f}) $$
Donde $\rho_s C_s$ es el producto densidad × calor específico de la arena y $\rho_f C_f$ el del agua. 
Resultados:
- $V_{ideal}$ = 0,088 m³
- $V_{real}$ = 0,173 m³ (H = 1,125 m, D = 0,45 m)
- Relación 4:1 arena:agua → arena 0,1384 m³ y agua 0,0346 m³
- Masa total = 221,44 kg (arena) + 34 kg (agua) = **255,44 kg**
### 2.4 Modelo matemático (Sec. 3)
**Supuestos:**
1. No hay pérdida de calor al ambiente (recipiente perfectamente aislado).
2. Partículas dispuestas uniformemente.
3. Flujo axial, solo de arriba hacia abajo.

**Condiciones de borde:**
- En $t=0$ no hay flujo y todo está a $T_{s,ini}=T_{f,ini}=100,°C$.
- Para $t>0$ la entrada se fija en $T_H = 250,°C$ con velocidad constante.
- Todas las paredes son adiabáticas salvo entrada y salida.

**Propiedades (Tabla 1):**

|Material|Conductividad (W/mK)|Calor específico|Densidad (kg/m³)|
|---|---|---|---|
|Arena|2,4|850 J/kgK (la tabla dice "kJ", es un error de unidades)|1600|
|Agua|–|4128 J/kgK|1000|

**Parámetros de COMSOL (Tabla 2):** H = 1,125 m, D = 0,45 m, partícula 12 mm (la tabla dice "m", es un error de unidades), caudal 0,0167 kg/s, velocidad de entrada 4,45×10⁻⁴ m/s, T inicial 100 °C, T entrada 250 °C, presión del sistema 45 bar.

**Eficiencia de carga (Ecs. 17-19):** mide la eficiencia energetica de carga comparando la T real alcanzada en el tiempo $t$ contra el maximo diferencial de T teoricamente disponible
$$\eta_{charge} = \frac{m_{stored},C_{p,stored},(T_{avg}-T_{cold})}{\dot m_f,C_{p,f},(T_H-T_{cold})} \qquad m_{stored}C_{p,stored}=m_fC_{p,f}+m_{sand}C_{p,sand}$$
$$\eta_{ch}(t)=\frac{T_{charge}(t)-T_{cold}}{T_H-T_{cold}}$$
- $T_{avg}$: temperatura promedio del almacenamiento en ese instante
- $T_{cold}$: temperatura inicial (100 °C)
- $T_H$: temperatura de entrada (250 °C)
- La Ec. 19 es la versión simplificada: una **temperatura adimensional**. Vale 0 al inicio y 1 cuando todo el lecho alcanzó $T_H$.

**Diseño de experimentos (Sec. 3.4):**
- Se simula y optimiza la altura de almacenamiento, el diametro de almacenamiento, el caudal masico y el tamaño de las paticulas de arena. Para encontrar la combinacion optima, se dan valores diferentes para cada factor. 
- Hay 4 parametros y tres niveles: valor adivinado, valor minimo y un valor maximo. 4 factores × 3 niveles = 81 combinaciones, demasiado costoso para simular.
	- Por ende es necesario optimizar estos parametros en dos fases 
- **Fase 1:** H ∈ {0,85; 1,4; 1,8} m, caudal ∈ {0,01; 0,015; 0,02} kg/s, D ∈ {0,40; 0,46; 0,52} m → 27 ensayos (el barrido tardó ~4 días de cómputo).
- **Fase 2:** tamaño de partícula ∈ {9; 11; 14} mm, fijando el óptimo de la fase 1.
- Criterio: **"mayor es mejor"** para temperatura promedio y entalpía a los 3600 s.
- El metodo Taguchi se usa para validar la optimizacion simulada en COMSOL, este metodo es una tecnica de analisis estadistico para aplicar en actividades robustas de diseño y planificacion de calidad mediante el uso de funciones de perdida y amtrices ortogonales 
### 2.5 Resultados (Sec. 4)
**Malla (4.1.1).** Malla gruesa de 131.088 elementos de dominio y 12.945 de borde, considerada aceptable. ![[Simulation and Optimization of Energy Efficiency and Total Enthalpy Analysis of Sand Based Packed Bed Solar Thermal Energy Storage-1793743202751.webp]]*Figura 3: malla del tanque (a) completa y (b) ampliada.*

**Simulación nominal (4.1.2).**
- A 900 s, ~520 K solo cerca de la entrada. A 3600 s, todo el lecho ronda 523 K.
- Tiempos para llegar a 520 K en el diseño nominal:

|Posición|Agua|Arena|
|---|---|---|
|Arriba (entrada)|~100 s|~300 s|
|Centro|~2000 s|~2300 s|
|Abajo (salida)|~3500 s|~3800 s|

- La **arena siempre va retrasada respecto al agua**: el calor viaja rápido por el fluido y luego pasa a la arena (no están en equilibrio térmico instantáneo).
![[Simulation and Optimization of Energy Efficiency and Total Enthalpy Analysis of Sand Based Packed Bed Solar Thermal Energy Storage-1793743292794.webp]]*Figura 4: mapas de temperatura a 0, 20, 180, 900, 1800 y 3600 s.*  
![[Simulation and Optimization of Energy Efficiency and Total Enthalpy Analysis of Sand Based Packed Bed Solar Thermal Energy Storage-1793743327197.webp]]*Figura 5 (p. 1056), curvas T vs. tiempo (arriba/centro/abajo, agua y arena).*

**Optimización fase 1 (4.2).**
- El **ensayo 25** (H = 1,4 m, 0,02 kg/s, D = 0,4 m) gana: llega a **523,14 K** y 949,4 kJ/kg a 3600 s, y carga el punto inferior de la arena en ~2500 s. El segundo es el ensayo 22 (H = 1,4; 0,015 kg/s; D = 0,4).
- Con D = 0,46 o 0,52 m, la arena del fondo casi no se calienta en el tiempo simulado.
- **Tendencia clara:** diámetro chico y caudal alto cargan más rápido.
![[Simulation and Optimization of Energy Efficiency and Total Enthalpy Analysis of Sand Based Packed Bed Solar Thermal Energy Storage-1793743431228.webp]]
*Figura 6 a, 6 b y 6 c: temperatura de la arena en el punto inferior para D = 0,4 / 0,46 / 0,52 m.

**Validación Taguchi + ANOVA (4.3).**
- Se usa un L 9, que **no incluye** el ensayo 25. Aun así, los gráficos de efectos principales de S/N apuntan a H = 1,4, caudal = 0,02 y D = 0,4, que coincide con COMSOL.
- ANOVA (p < 0,05 = significativo):

|Factor|p|¿Significativo?|
|---|---|---|
|Diámetro D|0,025|Sí (el más influyente)|
|Caudal|0,044|Sí|
|Altura H|0,110|No|

**Fase 2: tamaño de partícula (4.4).** Probando 9, 11 y 14 mm **no hay cambio apreciable**, así que se mantienen los 12 mm.


**Caída de presión (4.5).** Es **despreciable**: 0,70 Pa a 20 s, 0,50 Pa a 1800 s y 0,45 Pa a 3600 s. Decrece con el tiempo porque el agua caliente es menos viscosa.

**Optimizado vs. nominal (4.6).**

|Métrica|Nominal|Optimizado|
|---|---|---|
|Arena del fondo llega a 520 K|~3800 s|~2000 s|
|Centro (agua / arena) llega a 520 K|~1900 / ~2000 s|~900 / ~1000 s|
|Temperatura promedio de 523,15 K|~3500 s|~2000 s|
|Entalpía promedio ≈ 0,49 MJ/kg|~4000 s|~1400 s|
|Entalpía promedio ≈ 0,53 MJ/kg|–|~2000 s|
|Eficiencia de carga a 2000 s|~87 %|~100 %|

- Contra el **concreto** de la literatura (Prasad et al.), a 2000 s la eficiencia es ~80 %.
- El concreto es mejor hasta ~600 s (frente al optimizado) y ~1600 s (frente al nominal). Después, la arena lo supera.
- Promedio entre 0 y 2700 s: el optimizado supera al nominal en **13,7 %** y al concreto en **13,1 %**.
![[Simulation and Optimization of Energy Efficiency and Total Enthalpy Analysis of Sand Based Packed Bed Solar Thermal Energy Storage-1793743613219.webp]] ![[Simulation and Optimization of Energy Efficiency and Total Enthalpy Analysis of Sand Based Packed Bed Solar Thermal Energy Storage-1793743628235.webp]] ***Figura 10**: mapas nominal vs. optimizado a 20, 900, 1800 y 4000 s.*  

**Energía total (4.7).**
$$H(T)=C_{pm}(T-T _0)+H(T_ 0)$$

- Entalpía inicial: 0,186 MJ/kg. Entalpía cargada: 0,525 MJ/kg. Δ = **0,339 MJ/kg**.
- Energía total = 0,339 MJ/kg × 255,44 kg ≈ **86,72 MJ**.
- Se **supone un 30 % de pérdidas**, así que queda una energía neta de **60,7 MJ**.
- Eso supera con holgura los **37,841 MJ** que necesita la injera.
### 2.6 Conclusiones (Sec. 5)
Se confirma el óptimo (H = 1,4 m; D = 0,4 m; 0,02 kg/s). **El diámetro es el factor dominante, seguido por el caudal**, y la altura no es significativa. El tamaño de partícula no influye. Las mejoras frente al nominal son grandes en tiempo de carga y entalpía promedio.
## 3. Parámetros técnicos clave

|Parámetro|Dato del paper|
|---|---|
|**Volumen / masa de arena**|Diseño nominal: 0,173 m³ totales, de los cuales **0,1384 m³ de arena (221,44 kg)** y 0,0346 m³ de agua (~34 kg). Total 255,44 kg. Densidad de la arena 1600 kg/m³, ε = 0,2, partícula 12 mm. **Tipo exacto de arena: no especificado en el paper.** El volumen del tanque optimizado (1,4 × Ø0,4 m) no se informa; por cálculo propio ≈ 0,176 m³.|
|**Potencia y capacidad**|Demanda de diseño: **4,2 kW durante 2,5 h** (37,841 MJ ≈ 10,5 kWh). Capacidad bruta: **86,72 MJ (≈ 24,1 kWh)**. Neta con 30 % de pérdidas supuestas: **60,7 MJ (≈ 16,9 kWh)**.|
|**ΔT de trabajo**|Entrada **250 °C (523 K)**, temperatura inicial/mínima **100 °C (373 K)** → **ΔT = 150 K**. Presión del sistema 45 bar (supongo que para mantener el agua líquida a 250 °C). No hay temperatura "mínima útil de recarga" definida más allá de los 100 °C del ciclo estable.|
|**Tipo de intercambiador**|**Contacto directo:** el agua caliente fluye entre las partículas del lecho (arriba → abajo al cargar, abajo → arriba al descargar). En la descripción general del sistema, el calor llega por un **tubo de acero inoxidable** en termosifón. **No hay resistencias eléctricas ni aletas**; la fuente es un colector solar parabólico con absorbedor.|
|**Material aislante**|**No especificado en el paper.** Se asume pared adiabática en el modelo y una pérdida global del 30 % en el balance final.|
|**Eficiencia reportada**|**Eficiencia de carga** (no eléctrico → calor útil): ~100 % a 2000 s en el optimizado, ~87 % en el nominal y ~80 % en el concreto. Promedio 0-2700 s: +13,7 % y +13,1 %. **No se reporta eficiencia global** (carga + almacenamiento + descarga) ni eficiencia eléctrica → térmica.|

## 4. Hallazgos críticos
- **La geometría óptima no es la de mínima superficie/volumen.** El óptimo geométrico es D/H = 1, pero el mejor resultado térmico salió con D/H ≈ 0,29 (0,4 / 1,4 m): **un tanque esbelto**. La estratificación y la transferencia pesan más que la superficie de pérdidas.
- **El diámetro es la variable de diseño más sensible** (p = 0,025). Pasar de 0,40 a 0,52 m deja la arena del fondo prácticamente sin cargar en 3600 s. El caudal es la segunda variable (p = 0,044) y la altura es la menos relevante (p = 0,11).
- **La baja conductividad de la arena (k = 2,4 W/mK) se esquiva, no se resuelve.** El calor no viaja por conducción a través de la arena, sino que lo lleva el agua que circula entre las partículas. La arena va siempre ~300 s detrás del agua.
- **La estratificación (termoclina) es la base del diseño.** Se logra con flujo vertical de arriba hacia abajo al cargar y flujo invertido al descargar.
- **Tamaño de partícula (9, 11 o 14 mm): sin efecto notable** en este modelo. La caída de presión es despreciable (< 1 Pa).
- **Contenedor.** Solo hay un análisis geométrico (relación de aspecto) y la fracción volumétrica 4:1 arena:agua. **No hay cálculo estructural, dilatación térmica ni selección de materiales de pared.**
- **Pérdidas de calor.** El modelo es adiabático y el 30 % de pérdida es un supuesto, no un resultado. **No se estudia ningún aislante.** Es la mayor limitación de cara a una aplicación real.
- **Comparación con concreto:** la arena es peor al principio (primeros ~600-1600 s) y mejor después, con cargas más rápidas del tanque completo.
- **Limitaciones metodológicas a tener presentes:**
    - Rango de 250 °C (agua a 45 bar), lejos de los 500 °C de una batería de arena tipo Polar Night.
    - Solo se evalúa la **carga**. La descarga se describe pero no se simula ni optimiza.
    - El ANOVA se apoya en solo 9 ensayos (2 grados de libertad), con poco poder estadístico.
    - Hay inconsistencias menores: la Ec. 11, errores de unidades en las Tablas 1-2, y referencias cruzadas de ensayos mal numeradas (por ejemplo, "trial 23" con 0,02 kg/s cuando la Tabla 3 dice 0,015).