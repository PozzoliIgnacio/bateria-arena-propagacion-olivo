---
Titulo esp.: Revisión integral de modelos de simulación dinámica de sistemas de lecho empaquetado para aplicaciones de almacenamiento de energía térmica en la producción de energía renovable
Año: 2025
Padre: "[[CUDAR - Desarrollo de Pila de Arena]]"
Importancia:
  - A
URL: https://pmc.ncbi.nlm.nih.gov/articles/PMC11891709/#se0330
---
## 1. Idea Central
**Objetivo y Conclusión Fundamental:**
El estudio presenta una revisión exhaustiva y una guía práctica sobre los modelos físicos y los esquemas numéricos utilizados para simular la dinámica de sistemas de almacenamiento de energía térmica (TES) basados en lechos empacados (Packed-Bed, PB). Los autores comparan desde modelos simplificados (monofásicos) hasta modelos avanzados (bifásicos con gradiente térmico en partículas), aplicados a tecnologías como CSP, PTES, CAES y LAES. 
La conclusión fundamental es que el **modelo bifásico 1D de fase sólida continua, resuelto mediante el método de Euler implícito, ofrece el mejor equilibrio entre precisión, versatilidad y tiempo de cómputo**. Además, se demuestra que el tiempo de almacenamiento y la velocidad del fluido afectan significativamente la eficiencia de descarga, y se establecen parámetros óptimos de discretización espacial y temporal.

**Glosario de Abreviaciones:**
*   **TES:** Thermal Energy Storage (Almacenamiento de Energía Térmica).
*   **PB:** Packed-Bed (Lecho Empacado).
*   **HTF:** Heat Transfer Fluid (Fluido de Transferencia de Calor).
*   **CSP:** Concentrated Solar Power (Energía Solar Concentrada).
*   **PTES:** Pumped Thermal Energy Storage (Almacenamiento de Energía Térmica Bombeada).
*   **CAES:** Compressed Air Energy Storage (Almacenamiento de Energía por Aire Comprimido).
*   **LAES:** Liquid Air Energy Storage (Almacenamiento de Energía por Aire Líquido).
*   **PCM:** Phase Change Material (Material de Cambio de Fase).
*   **TRL:** Technology Readiness Level (Nivel de Madurez Tecnológica).
*   **LCOE:** Levelized Cost of Electricity (Costo Nivelado de Electricidad).
*   **VRE:** Variable Renewable Energy (Energía Renovable Variable).
*   **Bi:** Número de Biot.
## 2. Resumen por Secciones
### 1. Introducción
Contextualiza la necesidad de almacenamiento a gran escala debido a la intermitencia de las renovables. Destaca que el TES es independiente de la geografía, tiene alta densidad energética y es económico. El lecho empacado (PB) utiliza un tanque único (a diferencia del sistema de dos tanques de sales fundidas), donde un fluido (gas o líquido) intercambia calor con un sólido (rocas, arena, etc.), creando una zona de gradiente térmico llamada **termoclina**.
La zona de transición entre la región caliente y fría dentro del tanque se denomina **termoclina.** 
![[Comprehensive review of dynamical simulation models of packed-bed systems for thermal energy storage applications in renewable power production-1793393134719.webp|509]]
	*Fig. 1 del paper (Pág. 4). Es el esquema básico de un sistema PB, mostrando el tanque, el sólido, la entrada/salida del fluido y la termoclina.*

**Aplicaciones principales:**
*   **CSP:** El PB se integra en ciclos Brayton o Rankine.
*   **PTES:** Usa ciclos de bomba de calor reversibles.
*   **CAES / LAES:** Almacenamiento por aire comprimido o licuado, donde el PB recupera el calor de la compresión.
### 2. Propiedades Dinámicas del Sistema
Define los parámetros geométricos y físicos del tanque cilíndrico:
*   **Fracción de vacío ($\epsilon$):** Relación entre el volumen vacío y el volumen total.
    *   *Ecuación:* $\epsilon = \frac{V_{HTF}}{V_{total}} = 1 - \frac{V_{solid}}{V_{total}}$
    *   *Variable:* $V_{HTF}$ (volumen del fluido), $V_{solid}$ (volumen del sólido).
*   **Superficie específica ($a_s$):** Área de partículas por unidad de volumen.
    *   *Ecuación:* $a_s = \frac{6(1 - \epsilon)}{d_p}$
    *   *Variable:* $d_p$ (diámetro de partícula).
*   **Velocidad intersticial ($u$):** Velocidad real del fluido en los huecos.
    *   *Ecuación:* $u = \frac{U_s}{\epsilon} = \frac{\dot{m}}{\epsilon \rho_f A_i}$
    *   *Variables:* $U_s$ (velocidad superficial), $\dot{m}$ (flujo másico), $\rho_f$ (densidad del fluido), $A_i$ (área transversal).
*   **Coeficientes de transferencia de calor:** Se usan correlaciones para el Número de Nusselt ($Nu$).
    *   *Ecuación:* $Nu = 2.0 + 1.1 Re_p^{0.6} Pr^{1/3}$
    *   *Variables:* $Re_p$ (Reynolds de partícula), $Pr$ (Prandtl).
    *   *Coeficiente de convección ($h$):* $h = \frac{K_f \cdot Nu}{d_p}$ ($K_f$ = conductividad del fluido).
*   **Coeficiente global de pérdidas ($U$):** Calcula las pérdidas a través de la pared y el aislamiento.
    *   *Ecuación:* $U^{-1} = r_{in} \left( \frac{1}{r_{in}h_{in}} + \sum_{n=1}^{N} \frac{\log(r_n/r_{n-1})}{K_n} + \frac{1}{r_{ext}(h_{ext} + h_{rad})} \right)$
    *   *Variables:* $r_{in}$ (radio interno), $h_{in}$ (convección interna), $r_n$ (radios de capas), $K_n$ (conductividad de capas), $h_{ext}$ (convección externa), $h_{rad}$ (radiación externa).
![[Comprehensive review of dynamical simulation models of packed-bed systems for thermal energy storage applications in renewable power production-1793680806042.webp|391]] ![[Comprehensive review of dynamical simulation models of packed-bed systems for thermal energy storage applications in renewable power production-1793680815096.webp|359]]
	*Fig. 6 y Fig. 7 (Pág. 15) para ver el esquema de las capas del tanque y el perfil de temperatura de las pérdidas.*
### 3. Modelos de Ecuaciones de Calor en el Tiempo
Se presentan los modelos de conservación de energía según el nivel de detalle:
*   **Modelo Monofásico (1-phase):** Asume que sólido y fluido están en equilibrio térmico ($T_f = T_s = T$). Se usa cuando la conductividad del sólido es muy alta.
    *   *Ecuación (1D):* $[(1 - \epsilon)\rho_s c_{p,s} + \epsilon \rho_f c_{p,f}] \frac{\partial T}{\partial t} + \rho_f c_{p,f} \epsilon u \frac{\partial T}{\partial z} = K_{t,eff,z} \frac{\partial^2 T}{\partial z^2} + U a_b (T_\infty - T)$
*   **Modelo de Schumann (2-phases):** Ignora la conducción en el fluido y el sólido, y las pérdidas.
    *   *Ecuación Fluido:* $\epsilon \rho_f c_{p,f} (\frac{\partial T_f}{\partial t} + u \frac{\partial T_f}{\partial z}) = h a_s (T_s - T_f)$
    *   *Ecuación Sólido:* $(1 - \epsilon)\rho_s c_{p,s} \frac{\partial T_s}{\partial t} = h a_s (T_f - T_s)$
*   **Modelo de Fase Sólida Continua (2-phases):** **El más recomendado.** Incluye conducción efectiva y pérdidas.
    *   *Ecuación Fluido:* $\epsilon \rho_f c_{p,f} (\frac{\partial T_f}{\partial t} + u \frac{\partial T_f}{\partial z}) = \frac{\partial}{\partial z}(K_{f,eff,z} \frac{\partial T_f}{\partial z}) + h a_s (T_s - T_f) + U a_b (T_\infty - T_f)$
    *   *Ecuación Sólido:* $(1 - \epsilon)\rho_s c_{p,s} \frac{\partial T_s}{\partial t} = \frac{\partial}{\partial z}(K_{s,eff,z} \frac{\partial T_s}{\partial z}) + h a_s (T_f - T_s)$
*   **Modelo de Gradiente Térmico en Partículas:** Considera que la temperatura dentro de la partícula no es uniforme ($\eta$ es la coordenada radial de la partícula).
*   **Modelo Trifásico:** Incluye la pared del tanque como una tercera fase.

**Condiciones de Frontera e Iniciales:** Temperatura inicial igual a la ambiente. En la entrada ($z=0$) se fija la temperatura del fluido. En los extremos ($z=L$) se aplica condición de Neumann (derivada cero, sin fuga de calor).
### 4 y 5. Métodos Numéricos (Euler)
Se explican los métodos de diferencias finitas:
*   **Euler Explícito:** 
	* Avanza en el tiempo usando valores anteriores. 
	* Es simple pero **inestable si el paso de tiempo es grande o si la conductividad del solido es alta**. 
	* Evalúa las derivadas espaciales usando los valores conocidos del tiempo anterior
$$\frac{\partial T}{\partial t} \approx \frac{T_n^t - T_n^{t-1}}{\Delta t}, \quad \frac{\partial T}{\partial z} \approx \frac{T_n^t - T_{n-1}^t}{\Delta z}, \quad \frac{\partial^2 T}{\partial z^2} \approx \frac{T_{n+1}^{t-1} - 2T_n^{t-1} + T_{n-1}^{t-1}}{\Delta z^2}$$
*   **Euler Implícito:** 
	* Resuelve un sistema de ecuaciones (matriz tridiagonal) para el nuevo paso de tiempo. 
	* Es más estable y rápido para este tipo de problemas.
	* Discretiza la segunda derivada espacial en el instante actual, lo que elimina las inestabilidades numéricas asociadas al paso temporal $\Delta t$
$$\frac{\partial^2 T}{\partial z^2} \approx \frac{T_{n+1}^t - 2T_n^t + T_{n-1}^t}{\Delta z^2}$$
![[Comprehensive review of dynamical simulation models of packed-bed systems for thermal energy storage applications in renewable power production-1793681141596.webp|409]]
	*Fig. 13 (Pág. 25). Es el diagrama de flujo del algoritmo de resolución con Euler implícito y caída de presión.*

El modelo de continuo de fase solida implícito es mejor computacionalmente hablando. 
![[Comprehensive review of dynamical simulation models of packed-bed systems for thermal energy storage applications in renewable power production-1793681404174.webp]] *Tabla: relación entre el tiempo de simulación de cada modelo y la fidelidad física de la termoclina predicha*
### 6. Selección del Modelo y Método
El **Número de Biot ($Bi$)** es el indicador clave para elegir el modelo:
*   *Ecuación:* $Bi = \frac{h \cdot d_p}{K_s}$
*   *Criterio:* Si $Bi < 0.5$ (partículas pequeñas o alta conductividad), el modelo monofásico o de Schumann es suficiente. Si $Bi$ es alto (partículas grandes), se debe usar el modelo de gradiente térmico.
*   *Simplificación:* Para evitar el costoso modelo de gradiente, se usa un **coeficiente de convección efectivo ($h_{eff}$)**.
    *   *Ecuación:* $h_{eff} = (\frac{1}{h} + \frac{d_p}{10 K_s})^{-1}$

> **Callout Imagen:** *Pega la **Fig. 11** (Pág. 24) para ver cómo el modelo de fase continua converge con el de gradiente térmico al usar $h_{eff}$.*

### 7. Influencia de los Pasos Espaciales y Temporales
*   **Paso Espacial:** Se recomienda $\Delta z / L \le 0.0025$ para evitar la difusividad numérica artificial (donde L es la longitud del lecho). Valores menores no mejoran significativamente la precisión pero aumentan el costo computacional.
*   **Paso Temporal:** $\Delta t = 1$ s es ideal para bajo error. Sin embargo, $\Delta t = 5$ s reduce el tiempo de cómputo por un factor de 5 con un error de solo 1%.

### 8. Validación del Modelo
El modelo de fase sólida continua (1D) con Euler implícito se valida contra experimentos reales (Cascetta, Meier, Izquierdo, Xie) abarcando diferentes fluidos (aire, aceite), materiales (alúmina, magnetita, PCM) y temperaturas (desde ambiente hasta 550 °C).

### 9. Pérdidas de Presión
Se usa la **Ecuación de Ergun** para calcular la caída de presión ($\Delta P$) en medios porosos.
*   *Ecuación:* $\frac{-\Delta P}{L} = 150 \frac{(1 - \epsilon)^2}{\epsilon^ 3} \frac{\mu_f}{d_p^2} u + 1.75 \frac{(1 - \epsilon)}{\epsilon^3} \frac{\rho_f}{d_p} u^2$
*   *Variables:* $\mu_f$ (viscosidad dinámica), $\rho_f$ (densidad del fluido).

### 10 y 11. Energía Almacenada, Eficiencia y Análisis de Pérdidas
*   **Energía Almacenada ($E_{stored}$):** Integral de la capacidad calorífica por la diferencia de temperatura en todo el lecho.
*   **Eficiencia de Carga ($\eta_{charge}$):** $E_{stored} / (E_{input} - E_{out,put})$.
*   **Eficiencia de Descarga ($\eta_{discharge}$):** $E_{recovered} / E_{stored}$.
*   **Eficiencia Total ($\eta_{total}$):** $\eta_{charge} \cdot \eta_{discharge}$.
*   *Análisis:* Se demuestra que al aumentar la velocidad de descarga, la eficiencia disminuye (el fluido no se calienta bien) y las pérdidas de presión se disparan. El tiempo de almacenamiento degrada la termoclina; tras 16 horas de almacenamiento, la eficiencia de descarga cae al 20%.
## 3. Parámetros Técnicos Clave
*   **Tipo de intercambiador:** **Flujo directo a través del lecho poroso**. No hay tuberías internas ni resistencias; el fluido (aire, aceite térmico, sales fundidas, argón) se inyecta directamente por la parte superior (carga) o inferior (descarga) y percola a través de los huecos entre las partículas sólidas.
*   **Material aislante:** Para el caso de validación experimental (Cascetta), se utilizó una capa de **lana mineral (mineral wool) de 100 mm** de espesor. El paper también discute el uso de aislamientos multicapa y el impacto de la radiación en altas temperaturas.
*   **Eficiencia reportada:**
    *   **Eficiencia de descarga (caso base simulado):** 0.62 (62%).
    *   **Eficiencia total (caso base):** 0.62 (62%).
    *   **Eficiencia de descarga (tras 16 h de almacenamiento):** Cae a **0.20 (20%)**.
    *   **Eficiencia PTES (prototipo):** 55% a 76%.
    *   **Eficiencia AA-CAES (planta demostración):** 60% a 70%.
    *   **Eficiencia LAES:** 40-50% actual (75-85% esperada con recuperación de calor).
## 4. Hallazgos Críticos
*   **Selección del Modelo Óptimo:** El modelo de **fase sólida continua 1D resuelto con Euler implícito** es el mejor compromiso. Es más preciso que Schumann (incluye conducción) y mucho más rápido que el modelo de gradiente térmico (9.6 a 57.2 veces más lento).
*   **Criterio del Número de Biot:** Es fundamental para simplificar. Si $Bi < 0.5$, se puede usar el modelo monofásico. Si $Bi$ es alto, se puede evitar el modelo de gradiente térmico usando un **coeficiente de convección efectivo ($h_{eff}$)**, que da resultados casi idénticos con una fracción del costo computacional.
*   **Optimización de Malla:** El paso espacial debe ser $\Delta z \le 0.0025 L$ para un equilibrio entre error y tiempo. El paso temporal de 1 s es seguro, pero 5 s acelera el cálculo 5 veces con solo un 1% de error.
*   **Impacto de la Velocidad de Descarga:** Aumentar la velocidad del fluido en la descarga reduce drásticamente la eficiencia (el fluido no tiene tiempo de thermalizarse con el sólido) y provoca **caídas de presión prohibitivas** (calculadas con la ecuación de Ergun).
*   **Degradación de la Termoclina:** El tiempo de almacenamiento estático es el enemigo de la eficiencia. Aunque las pérdidas de calor globales no son enormes, la termoclina se "difumina" por la conducción axial, reduciendo la temperatura de salida y, por ende, la eficiencia de descarga (cayendo al 20% tras 16 horas).
*   **Innovaciones en Diseño:** Se sugiere el uso de lechos con **capas alternas de material y aire** (para reducir la conducción axial y mantener la termoclina) y configuraciones de **flujo radial** (para reducir las pérdidas de presión).
* **Impacto de la variacion de propiedades fisicas:** ignorar la variacion de la capacidad calorifica especifica y de la conductividad con la T genera desviaciones superiores al 12% en la prediccion del almacenamiento de energia. 