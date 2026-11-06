---
Titulo esp.: Revisión de enfoques de modelado para sistemas de almacenamiento térmico de lecho empaquetad
Año: 2021
Padre: "[[CUDAR - Desarrollo de Pila de Arena]]"
Importancia:
  - B
URL: https://www.sciencedirect.com/science/article/pii/S1364032121001933
---
## 1. Idea Central
El artículo es una **revisión académica** de los enfoques de modelado, correlaciones empíricas, materiales, estructuras y fenómenos de transferencia de calor en sistemas de almacenamiento térmico de lecho empacado (*packed-bed TES*). Su objetivo principal es comparar modelos 1D/2D/3D, modelos monofásicos/bifásicos/trifásicos, correlaciones de conductividad y convección, y evaluar especialmente el rol de la **radiación térmica** entre partículas. 
La conclusión fundamental es que los modelos simplificados son útiles, pero deben elegirse según escala, fluido, tamaño de partícula y régimen térmico; la radiación entre partículas **no debe despreciarse a temperaturas superiores a ~750 °C**, ya que el coeficiente radiativo puede alcanzar hasta **~32 % del coeficiente convectivo**. El paper también reporta que los sistemas de lecho empacado de un solo tanque pueden reducir costos ~33 % frente a sistemas de dos tanques.

**Glosario de abreviaciones:**  
- **STES:** *Sensible Thermal Energy Storage* / Almacenamiento térmico sensible.  
- **TES:** *Thermal Energy Storage* / Almacenamiento de energía térmica.  
- **HTF:** *Heat Transfer Fluid* / Fluido de transferencia de calor.  
- **CSP:** *Concentrated Solar Power* / Energía solar de concentración.  
- **SHS:** *Sensible Heat Storage* / Almacenamiento de calor sensible.  
- **1D/2D/3D:** modelos unidimensional, bidimensional y tridimensional.  
- **C-S:** modelo continuo de fase sólida (*Continuous Solid-phase*).  
- **D-C:** modelo disperso concéntrico (*Dispersed Concentric*).  
- **PDE:** ecuación diferencial parcial.  
- **CFD:** dinámica de fluidos computacional.  
- **DEM:** método de elementos discretos.  
- **sCO₂:** dióxido de carbono supercrítico.  
- **EAF/BOF/IFS:** escorias de horno de arco eléctrico, horno de oxígeno básico y horno de inducción.  
- **JaCCO:** aceite crudo de *Jatropha curcas*.  
- **Bi, Re, Nu, Pr:** números de Biot, Reynolds, Nusselt y Prandtl.  
- **$k_{eff}$:** conductividad térmica efectiva.  
- **$h_v$:** coeficiente volumétrico de transferencia de calor.  
- **$U_T$:** coeficiente global de pérdidas del tanque.
## 2. Resumen por Secciones
### 2.1. Introducción
Presenta los STES como sistemas que almacenan energía sensible calentando un material mediante un HTF. Se usan entre **120 °C y 1250 °C**. Sus componentes esenciales son: medio de almacenamiento, mecanismo de transferencia de energía y sistema de confinamiento. Se clasifican en sistemas con fluidos calientes como medio directo, sólidos calentados por fluido intermedio, y procesos con un tercer material. El lecho empacado de un solo tanque usa sólidos y HTF en contacto directo; la separación térmica se logra por **estratificación por flotabilidad** y una zona de gradiente llamada **termoclina**. Esto permite cargar por arriba y descargar por abajo, con ahorros de ~33 % frente a dos tanques. También se menciona que el uso de materiales de relleno puede aumentar la densidad energética teórica ~50 % y reducir el HTF ~70 %.
![[Review on modeling approaches for packed-bed thermal storage systems-1793386479211.webp]]
	*Fig. 1 del paper — esquema de operación round-trip de un STES.*  
![[Review on modeling approaches for packed-bed thermal storage systems-1793386572598.webp]]
	*Fig. 3 del paper — mecanismos internos de transferencia de calor en lecho empacado.*
### 2.2. Operación y variables clave
> Describe la dinámica de carga y descarga, la geometría de los contenedores (cilíndricos vs. cónicos) y analiza materiales sólidos de relleno (rocas, concreto, escorias industriales) y fluidos portadores (aire, sales fundidas, aceites).

La carga consiste en hacer fluir HTF (Heat Transfer Fluid) caliente a través del sólido; la descarga hace fluir HTF frío para recuperar el calor. 
	- El flujo calentado de salida se suministra luego al sistema de demanda
	- 
Los **parámetros críticos** son: 
	Tamaño de partícula, caudal másico por área superficial, propiedades del fluido, longitud del lecho, pérdidas por paredes, fracción de vacío, material de empaque, temperatura de entrada, estructura de pared y condiciones ambientales. 
Se discuten escenarios de carga/descarga, estratificación inicial, control de temperatura, intermitencia solar y retrasos por fallas. También se analiza la geometría del tanque: cilíndrico, cónico truncado, cono invertido, relación de aspecto, etc. Para tanques cilíndricos, relaciones de aspecto mayores mejoran la estratificación, pero valores >2 no representan una mejora considerable.![[Review on modeling approaches for packed-bed thermal storage systems-1793386928852.webp|417]]*Fig. 4 del paper — enfoque general de modelado y ecuaciones de balance.*
![[Review on modeling approaches for packed-bed thermal storage systems-1793387142330.webp|359]]
	*Fig. 5 del paper — estructura típica de un tanque de lecho empacado.*
En general, los contenedores de lecho empaquetado son cilíndricos, una forma que presenta bajos problemas mecánicos y minimiza el área de superficie lateral. 
[Este articulo](https://pubs.aip.org/aip/acp/article/1850/1/080021/616761/Parametric-analysis-of-a-packed-bed-thermal-energy) concluyo que se debería seleccionar un tanque cilíndrico para optimizar el rendimiento térmico
### 2.3. Estructura de almacenamiento, materiales y propiedades
La estructura típica incluye tanque de contención, material de almacenamiento, placas soporte, homogenizadores de flujo, plenums superior e inferior y aislamiento. Los tanques suelen ser cilíndricos para reducir problemas mecánicos y superficie lateral. Los materiales sólidos incluyen concreto, cerámicos fundibles, alúmina, rocas, magnetita, cuarcita, cipolino, hierro fundido, acero y escorias industriales. 
Las propiedades clave son **capacidad térmica volumétrica $\rho C_p$**, conductividad térmica, tamaño de partícula, estabilidad térmica y costo. Los fluidos incluyen aire, aceites térmicos, sales fundidas, agua, CO₂ supercrítico, aceites vegetales y JaCCO. Las sales fundidas dominan en CSP de receptor central; el aire es barato, disponible y estable a alta temperatura; el sCO₂ es atractivo para ciclos Brayton avanzados.
### 2.4. Coeficientes empíricos de transferencia de calor
Se revisan correlaciones para:
- **Conducción efectiva:** $k_{eff}^0$, $k_{eff}^{0,rad}$, $k_{eff}^a$, $k_{eff}^r$. Se discuten modelos monofásicos y bifásicos. Las correlaciones de conductividad estancada no consideran radiación; las que sí la incluyen provienen en gran parte de aplicaciones nucleares.
	- La conducción de calor entre dos puntos en contacto depende del área de contacto. El aire puede quedar atrapado entre partículas de modo que genera convección
- **Convección:** coeficiente volumétrico $h_v = c_1 G^{c_2}$, donde $c_1$ y $c_2$ dependen de geometría y fracción de vacío, y $G$ del caudal másico. Hay grandes dispersiones entre correlaciones.
- **Pared/fluido:** teorías de película límite, penetración y mezcla; dependen de $Re = Gd/\mu$.
- **Caída de presión:** ecuación de Ergun y correlaciones asociadas.

Ecuaciones relevantes:
$$
Re=\frac{Gd}{\mu}
$$
donde $G=\dot m/A$ es el flujo másico por área, $d$ el diámetro de partícula y $\mu$ la viscosidad dinámica.
$$
\nabla P=-\frac{\mu}{K}u_D-\frac{C_E}{K^{1/2}}\rho u_D|u_D|
$$
donde $K$ es permeabilidad, $C_E$ parámetro empírico, $u_D$ velocidad superficial o Darcy y $\rho$ densidad del fluido. El primer término representa esfuerzo viscoso y el segundo la resistencia inercial.
$$
h_v=c_ 1 G^{c_2}
$$
donde $h_v$ es el coeficiente volumétrico de convección y $G$ el flujo másico por unidad de área.
![[Review on modeling approaches for packed-bed thermal storage systems-1793388500881.webp]]
	*Fig. 6 del paper — fenómenos físicos de la conductividad efectiva.*  
### 2.5. Modelado numérico
Se describen:
- **Modelos monofásicos:** fluido y sólido en equilibrio térmico; válidos si la capacidad térmica del fluido es pequeña frente a la del sólido. Ecuación típica:
$$
(1-\epsilon)\rho_s C_{p_s}\frac{\partial T_s}{\partial t}
=
\left(k _0+\frac{G ^2 C_{p_f}^2}{h_p a}\right)\frac{\partial^2 T_f}{\partial z^2}
-
GC_{p_f}\frac{\partial T_f}{\partial z}
$$
donde $\epsilon$ es porosidad, $\rho_s$ densidad sólida, $C_{p_s}$ calor específico sólido, $T_s$ temperatura sólida, $T_f$ temperatura fluido, $G$ flujo másico por área, $k_0$ conductividad axial efectiva, $h_p$ coeficiente partícula-fluido y $a$ superficie específica por volumen.

- **Modelo bifásico de Schumann / C-S:** 
$$
\frac{\partial T_f}{\partial t}
=
-u\frac{\partial T_f}{\partial z}
+
\frac{h_p a}{\epsilon\rho_f C_{p_f}}(T_s-T_f)
$$
$$
\frac{\partial T_s}{\partial t}
=
\frac{h_p a}{(1-\epsilon)\rho_s C_{p_s}}(T_f-T_s)
$$
donde $u$ es velocidad axial del fluido, $\rho_f$ densidad del fluido y $C_{p_f}$ calor específico del fluido. Este modelo supone tapón ideal y no conducción en sólido; la versión extendida C-S agrega conducción axial efectiva en ambas fases.
Es el modelo de transferencia de calor mas común para lechos empaquetados
El modelo de Schumann es aplicable para regímenes con números de Reynolds grandes, para dominios de Reynolds pequeños se incluye un termino en la ecuación y se obtiene el modelo continuo en fase solida CS

- **Modelo D-C:** considera gradientes intrapartícula y simetría radial:
$$
\frac{\partial T_f}{\partial t}
=
\kappa_{f_{ax}}\frac{\partial^2 T_f}{\partial z^2}
-
u\frac{\partial T_f}{\partial z}
+
\frac{h_p a}{\epsilon\rho_fC_{p_f}}\left(T_s|_{r=R}-T_f\right)
$$
$$
\frac{\partial T_s}{\partial t}
=
\kappa_s\frac{1}{r^2}\frac{\partial}{\partial r}\left(r^2\frac{\partial T_s}{\partial r}\right)
$$
con condición de borde:
$$
k_s\frac{\partial T_s}{\partial r}=-h_p(T_s-T_f)\quad \text{en }r=R
$$
donde $r$ es coordenada radial, $R$ radio de partícula, $\kappa_s$ difusividad térmica del sólido y $\kappa_{f_{ax}}=k_{eff_{ax}}/(\epsilon C_{p_f}\rho_f)$ coeficiente de dispersión axial.

- **Modelos trifásicos:** agregan ecuación para la pared del tanque:
$$
\rho_w C_{p_w}\frac{\partial T_w}{\partial t}
=
k_w\frac{\partial^2 T_w}{\partial z^2}
+
h_wA_w^i(T_f-T_w)
+
h_{ext}A_w^o(T_w-T_{ext})
$$
donde $T_w$ temperatura de pared, $T_{ext}$ temperatura exterior, $h_w$ coeficiente pared-fluido, $h_{ext}$ coeficiente global de pérdidas, $A_w^i/A_w^o$ áreas internas/externas y $\rho_w,C_{p_w},k_w$ propiedades de la pared.

- **Modelos multiescala / partículas de distinto tamaño:** ecuación tipo bidispersa:
$$
\epsilon\rho_fC_{p_f}\frac{\partial T_f}{\partial t}
+
\rho_fC_{p_f}u\frac{\partial T_f}{\partial z}
=
h_{p_ 1}a_ 1(T_{s 1}-T_f)+h_{p_ 2}a_ 2(T_{s 2}-T_f)
$$
$$
w_v(1-\epsilon)\rho_{s 1}C_{p_{s 1}}\frac{\partial T_{s 1}}{\partial t}
=
h_{p_ 1}a_ 1(T_f-T_{s 1})
$$
$$
(1-w_v)(1-\epsilon)\rho_{s 2}C_{p_{s 2}}\frac{\partial T_{s 2}}{\partial t}
=
h_{p_ 2}a_ 2(T_f-T_{s 2})
$$
donde $w_v$ es fracción volumétrica de partículas grandes, subíndices 1 y 2 denotan partículas grandes y pequeñas.
### 2.6. Estudios experimentales
Se revisan validaciones experimentales: Meier et al. con código PACKBEDA 1D; Zanganeh et al. con unidad de **6.5 MWh** y forma cónica truncada; Anderson et al. con alúmina y aire a **120 °C y 700 °C**; Odenthal et al. con modelo bidisperso para sales fundidas; Hoffmann et al. con tanques de **8.3 kWh, 2.3 MWh y 170 MWh**; Beasley y Clark con modelo 2D trifásico; Aly y El-Sharkawy con efecto de temperatura de pared; Rodrigues y de Lemos con CFD 2D; Bai et al. con generación de entropía y relaciones de aspecto. Hallazgo importante: modelos bifásicos son más precisos en tanques pequeños; monofásicos se acercan mejor a escala industrial. Las pérdidas y efectos de pared son críticos en tanques pequeños.
### 2.7. Intercambio por radiación
La radiación térmica es relevante a alta temperatura; se recomienda no despreciarla por encima de **900 °C** y, según la conclusión del paper, por encima de **750 °C**. Se presentan modelos de radiación:
- **Corto alcance:** partículas vecinas; puede subestimar radiación si la suma de factores de visión es baja.
- **Largo alcance:** interacción hasta un radio $R_{int}$, con criterio:
$$
\left|\sum_{i=1}^{n}F_{ij}-1\right|>\tau
\longrightarrow
R_{int}=R_{int}+\nabla\delta
$$
donde $F_{ij}$ es el factor de visión entre partículas $i$ y $j$, $\tau$ tolerancia y $\nabla\delta$ corrección del radio de interacción.
- **Escala de partícula:** discretización de superficie; preciso pero costoso.

El paper realiza un modelo simplificado de columna de esferas con balance explícito de radiación hasta tres diámetros:
$$
\rho_sV_{cell}(1-\phi)C_{p_s}\frac{dT_{s,i}}{dt}
=
\dot Q_{cond,s,i-1}
-
\dot Q_{cond,s,i+1}
+
\dot Q_{conv,i}
+
\sum_{n=1}^{3}\left(\dot Q_{rad,i-n,i}-\dot Q_{rad,i+n,i}\right)
$$
donde $\phi$ es porosidad de la celda, $V_{cell}$ volumen de celda, $\dot Q_{cond}$ conducción, $\dot Q_{conv}$ convección y $\dot Q_{rad}$ radiación entre esferas vecinas. Resultados: diferencias importantes entre radiación explícita y correlación implícita de Zehner-Schlunder; la radiación puede llegar a **32 %** del coeficiente convectivo y el modelo explícito muestra interacción a distancia.
### 2.8. Conclusiones
Las correlaciones empíricas varían mucho y dependen de configuraciones específicas. Los modelos avanzados son más precisos pero computacionalmente costosos; los simplificados aproximan bien tanques piloto. La interacción partícula-fluido-pared es clave, especialmente en tanques pequeños. Asumir propiedades constantes introduce errores de **1–5 %**. La radiación suele despreciarse, pero a alta temperatura su contribución es significativa; las correlaciones de conductividad efectiva radiativa no capturan bien el gradiente alrededor de la partícula. El coeficiente radiativo puede ser hasta **32 %** del convectivo, por lo que no debe ignorarse por encima de **750 °C**.
## 4. **Hallazgos Críticos**
- **La radiación entre partículas no es despreciable a alta temperatura:** puede representar hasta **~32 %** del coeficiente convectivo; debe considerarse por encima de **750 °C** y tratarse como interacción de largo alcance.
- **Las correlaciones empíricas de convección y conductividad efectiva tienen dispersión considerable:** dependen de porosidad, distribución de partículas, geometría y fluido; no son universalmente generalizables.
- **Los modelos bifásicos son mejores para tanques pequeños**, mientras que los monofásicos pueden ser adecuados para tanques industriales; el efecto de pared y pérdidas térmicas es crítico en escala pequeña.
- **El modelo bidisperso es recomendable** cuando hay al menos dos tamaños de partícula y fluidos densos como sales fundidas o aceites térmicos; las desviaciones pueden ser de varios kelvin y mayores en operación cíclica.
- **Usar propiedades constantes introduce errores de 1–5 %**, pero reduce costo computacional; a temperaturas cercanas a 700 °C las diferencias son más críticas.
- **La estructura de pared y el aislamiento** deben modelarse con una ecuación adicional o un coeficiente global $U_T$; ignorarlos puede predecir mal la temperatura de salida en tanques pequeños.
- **El diseño del tanque** (cilíndrico, cónico truncado, relación de aspecto) afecta estratificación, pérdidas y energía almacenada; relaciones de aspecto >2 no mejoran sustancialmente el rendimiento.
- **Materiales de relleno de bajo costo** (rocas, escorias, concreto, magnetita) son viables, pero deben evaluarse compatibilidad con el HTF, estabilidad térmica y propiedades termofísicas.