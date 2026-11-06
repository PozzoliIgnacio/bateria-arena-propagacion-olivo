---
Titulo esp.: Determinación experimental y modelado de elementos finitos de la conductividad térmica en arena húmeda
Año: 2026
Padre: "[[CUDAR - Desarrollo de Pila de Arena]]"
Importancia:
  - B
URL: https://www.sciencedirect.com/science/article/pii/S2451904925012636#fig5
---
## 1. Idea Central
El estudio **estima la conductividad térmica efectiva de arena húmeda con ensayos de banco simples, la teoría clásica de factores de forma de conducción y simulaciones por elementos finitos (FEM) con software abierto (FEniCS + Gmsh)**. 
Se probaron dos fuentes de calor enterradas: un **tubo de aluminio en U** con agua caliente y un **cilindro macizo de aluminio** con calentador interno. En ambos casos se despejó _k_ a partir del calor medido y las diferencias de temperatura.

**Conclusión fundamental:** _k_ efectiva ≈ **1,0-1,5 W/m·K** (U: 0,99-1,09; cilindro: 1,34-1,62), coherente con la literatura para arena húmeda y con la humedad medida (8,6 y 12,6 % en peso). La incertidumbre declarada es de **20-30 %**, y el FEM es un chequeo cruzado 2D, no una validación completa.
### Glosario

|Sigla / símbolo|Significado|
|---|---|
|**FEM**|_Finite Element Method_, método de elementos finitos|
|**FEniCS / Gmsh**|Librería FEM de código abierto / generador de mallas de código abierto|
|**k** (W/m·K)|Conductividad térmica (aquí, la _efectiva_ de la arena húmeda)|
|**S** (m)|**Factor de forma de conducción**: depende solo de la geometría. Ojo: el paper usa "S" también para el _grado de saturación_ ($S_1$, $S_2$ en la Sec. 4.1)|
| $S_v$, $S_h$, $S_{int}$ |Factor de forma vertical, horizontal y de interacción entre cilindros|
|Q|Potencia térmica (W)|
| $T_\infty$, $h$, $h_{air}$ |Temperatura ambiente / coeficiente de convección (lado aire)|
| $T_{in}, T_{out}$ |Temperatura del agua a la entrada/salida del tubo|
| $T_1, T_2, T_3, T_4, T_S$ |Termocuplas (cambian de lugar según el ensayo)|
| $\Gamma_D, \Gamma_N, \Gamma_R$ |Bordes con condición de **Dirichlet** (T fija), **Neumann** (flujo fijo) y **Robin** (convección)|
| $p$ |Orden del polinomio de Lagrange de los elementos|
| $n_\lambda$ |Parámetro de refinamiento de malla ($h \approx 1/n_\lambda$)|
| $T_{top,mean}$ |Temperatura media superficial sobre el calentador (métrica de convergencia)|
| $w$ (wt %)|Contenido gravimétrico de agua (masa de agua / masa de arena seca)|
| $n$ |Porosidad|
| $\rho_{bulk}, \rho_s, \rho_w$ |Densidad aparente / del grano / del agua|
| $\delta k/k$ |Incertidumbre relativa de _k_|
|MSC|_Mathematics Subject Classification_ (código de clasificación)|

## 2. Resumen por Secciones
### 2.1 Introducción (Sec. 1)
- La _k_ de la arena depende fuertemente de la humedad:

|Estado|_k_ (W/m·K)|
|---|---|
|Seca|0,2-0,4|
|Húmeda / parcialmente saturada|> 1,0 (típico 1,0-1,5)|
|Saturada|2-3|

- El agua en los poros reemplaza al aire (que aísla) por un camino conductivo.
- Se cita la literatura (Nikiforova, Smits, Brandon & Mitchell, Haigh, Campanale, Zeng) y aplicaciones: concretos, geotermia, moldes de fundición y **baterías de arena**. Del ítem de baterías, el paper dice que la baja _k_ intrínseca **limita las velocidades de carga/descarga** y que se estudian aditivos o inclusiones conductoras para subirla.
- **Vacío que declara cubrir:** faltan flujos de trabajo baratos y de código abierto para estimar _k_ de una arena _específica_ sin instrumentos dedicados (placa caliente guardada, aguja transitoria).
- **Tres contribuciones:** (1) metodología de banco con factores de forma, (2) validación cruzada con FEM abierto, (3) puente pedagógico entre teoría, experimento y simulación.
### 2.2 Ecuaciones gobernantes y factores de forma (Sec. 2.1)
**Ley de Fourier (Ec. 1):**
$$\mathbf{q} = -k,\nabla T$$
$\mathbf{q}$ es el flujo de calor (W/m²) y $\nabla T$ el gradiente de temperatura.

**Ecuación de difusión del calor (Ec. 2):**
$$\rho c,\frac{\partial T}{\partial t} = k,\nabla^2 T + q'''$$
$\rho$ es la densidad, $c$ el calor específico y $q'''$ la generación volumétrica de calor (W/m³). La Ec. 3 es la misma en coordenadas cilíndricas $(r,\phi,z)$.

**Régimen permanente sin generación (Ec. 4), ecuación de Laplace:**
$$\nabla^2 T = 0$$

**Cilindro largo, caso radial (Ecs. 5-6):**
$$\frac1r\frac{d}{dr}!\left(r\frac{dT}{dr}\right)=0 ;\Rightarrow; T(r)=C_1\ln r + C_2$$

$C_1$ y $C_2$ son constantes fijadas por las condiciones de borde.

**Conducción cilíndrica (Ec. 7) y forma general con factor de forma (Ec. 8):**
$$Q=\frac{2\pi k L,(T_{s,1}-T_{s,2})}{\ln(r_2/r_1)} \qquad\Longrightarrow\qquad Q = k,S,(T_1-T_2)$$
$L$ es la longitud, $r_1, r_2$ los radios interior y exterior, y $S$ el factor de forma, que depende solo de la geometría de las superficies isotérmicas.

**Factores de forma usados:**
- **Cilindro vertical** de diámetro $D$ y largo $L$ en medio semi-infinito (Ec. 9): $;S_v=\dfrac{2\pi L}{\ln(4L/D)}$
- **Cilindro horizontal** con eje a profundidad $z$ (Ec. 10): $;S_h=\dfrac{2\pi L}{\cosh^{-1}(2z/D)}$

**Despeje de _k_ (Ec. 11):**
$$k=\frac{Q}{S,(T_1-T_2)}$$
Esta es la idea central del método: si se mide $Q$ y las temperaturas, y se conoce $S$ por geometría, _k_ sale directo.
### 2.3 Montaje experimental (Sec. 2.2)
**Contenedor:** caja de plexiglás de **210 × 320 × 455 mm** (interior), con termocuplas tipo K y lectores digitales (resolución ±0,1 °C).
#### 2.3.1 Caracterización de la arena
- Arena de playa del Mar de Mármara (Turquía), principalmente **cuarzo**.
- Tamaño medio de grano: **449 ± 72 µm** (250 partículas medidas con microscopio).
- Se vertió en capas sin compactación intencional: $\rho_{bulk}\approx 1650$ kg/m³.
- **Humedad residual** (por secado en horno a 105 °C durante 24 h): **8,6 wt %** en el ensayo del tubo U y **12,6 wt %** en el del cilindro.
#### 2.3.2 Tubo en U
- Aluminio, $D_{ext}=10$ mm, pared ≈ 1 mm, $k_{Al}\approx205$ W/m·K.
- Dos patas verticales de 0,150 m enterradas y un tramo horizontal de 0,395 m.
- Agua en circuito cerrado desde un baño termostático a **40 °C**, caudal ≈ **0,1 L/min**.
- Termocuplas: $T_1$ (pata izquierda), $T_2$ (punto medio horizontal), $T_3$ (pata derecha) sobre la superficie del tubo, y $T_s$ en la arena sobre el tubo.
- Representa un intercambiador enterrado tipo geotermia somera.
![[Experimental determination and finite element modeling of thermal conductivity in moist sand-1793744945703.webp]]***Fig. 2 (a y b)**, foto del montaje y esquema con los puntos de medición.*

#### 2.3.3 Cilindro sumergido verticalmente
- Aluminio macizo, $r_2=43{,}5$ mm, altura $L_1=194$ mm, con **cartucho calefactor** axial (Ø11 mm, 194 mm, 200 W a 220 V).
- Apoyado sobre arena y con la cara superior al ras de la superficie.
- Termocuplas (±0,5 °C): $T_2$ en la pared lateral a media altura, $T_3$ en la superficie de arena, $T_4$ en la cara superior. $T_\infty$ es la temperatura ambiente.
- Lecturas cada minuto hasta que el termostato ciclaba (cuasi-estacionario).
- Es el análogo de una resistencia en una batería térmica de arena.
![[Experimental determination and finite element modeling of thermal conductivity in moist sand-1793745095061.webp]]***Fig. 3 (a y b)**, foto y esquema del cilindro con cartucho y termocuplas.*
### 2.4 Formulación FEM 2D estacionaria (Sec. 2.3)
Se implementa en FEniCS 2019.1.0, con Python 2.7, mallas de Gmsh y Docker. La arena es un dominio $\Omega$ homogéneo e isótropo, sin generación interna.

**Ecuación fuerte (Ec. 12):** $-\nabla\cdot(k\nabla T)=0 \text{ en } \Omega$

**Condiciones de borde (Ecs. 13-15):**
- Dirichlet: $T=\bar T$ en $\Gamma_D$ (superficies isotérmicas del objeto enterrado).
- Neumann: $-k\nabla T\cdot\mathbf n=\bar q_n$ en $\Gamma_N$ (flujo prescrito; $\mathbf n$ es la normal exterior).
- Robin: $-k\nabla T\cdot\mathbf n=h(T-T_\infty)$ en $\Gamma_R$ (convección con el aire; $h$ es el coeficiente convectivo; $T_{\infty}$ es la T ambiente).

**Forma débil (Ecs. 16-18):** se multiplica por una función de prueba $v$, se integra y se aplica integración por partes:
$$\int_\Omega k\nabla T\cdot\nabla v,d\Omega+\int_{\Gamma_R}hTv,d\Gamma=\int_{\Gamma_R}hT_\infty v,d\Gamma+\int_{\Gamma_N}\bar q_n v,d\Gamma$$

**Problema discreto (Ecs. 19-21):** se busca $T_h$ tal que $a(T_h,v_h)=L(v_h)$ para todo $v_h$, con la forma bilineal $a(T,v)=\int_\Omega k\nabla T\cdot\nabla v + \int_{\Gamma_R} hTv$ y el funcional lineal $L(v)=\int_{\Gamma_R}hT_\infty v+\int_{\Gamma_N}\bar q_n v$. Los elementos son triangulares de Lagrange de grado $p$.
	- $T_{h}$ *es la temperatura aproximada (discreta) que resuelve el FEM*. 
	- T es la solucion exacta y continua de la ecuacion de Laplace, T_h es la solucion aproximada que el metodo de elementos finitos calcula sobre una malla concreta
**Balance global (Ec. 22):** el calor que entra por $\Gamma_D$ debe igualar al que sale por $\Gamma_R$ y $\Gamma_N$:
$$\int_{\Gamma_D}-k\nabla T\cdot\mathbf n,d\Gamma=\int_{\Gamma_R}h(T-T_\infty),d\Gamma+\int_{\Gamma_N}\bar q_n,d\Gamma$$
Sirve como chequeo de consistencia entre simulación y balance experimental.
### 2.5 Sensibilidad de malla y orden polinómico (Sec. 2.4)
Se estudió la convergencia $hp$ para el cilindro: $n_\lambda=50\text{-}300$, $p=1,2,3$, con $T_{top,mean}$ como métrica (temperatura media en la superficie de arena sobre el calentador). La referencia es $p=3,\ n_\lambda=300$, con $T_{top,mean}=30{,}486$ °C.

**Error relativo (Ec. 23):**
$$e(p,n_\lambda)=\left|\frac{T_{top,mean}(p,n_\lambda)-T^{ref}_{top,mean}}{T^{ref}_{top,mean}}\right|$$

| $p$ |Error|Tasa de convergencia observada|
|---|---|---|
|1|2,5 % ($n_\lambda=50$) → 0,19 % ($n_\lambda=300$)|≈ 1,6|
|2|0,49 % ($n_\lambda=50$) → 0,025 % ($n_\lambda=250$)|≈ 2,2|
|3|< 0,04 % a $n_\lambda=100$ |≈ 3,7|

**Elegido:** $p=2$, $n_\lambda=200$ (diferencia de 0,012 °C, 0,04 %, despreciable frente a los ±0,1 °C de medición).
### 2.6 Resultados (Sec. 3)
**Tabla 1 (literatura):** rangos de _k_ para arenas: 0,17-3,0 W/m·K según la fuente (Nikiforova 0,23-2,2; Smits 0,22-2,9; Liu 0,25-3,0; Tarnawski 0,25-2,8; Grassmann 0,3-1,5; Haigh 0,2-3,0; Campanale 0,17-2,0).
![[Experimental determination and finite element modeling of thermal conductivity in moist sand-1793745658782.webp]]
#### 3.1 Tubo en U
**Datos medidos:** 
- $T_{in}=40$ °C, $T_{out}=38$ °C
- tubo $T_L=34{,}1$ / $T_M=34{,}0$ / $T_R=33{,}9$ °C
- superficie de arena $T_S=22{,}2$ °C
-  $\dot m=1{,}66\times10^{-3}$ kg/s, $c_p=4180$ J/kg·K.

**Calor cedido a la arena (Ec. 24):**
$$Q_{tot}=\dot m,c_p,(T_{in}-T_{out})=13{,}88\ \text{W}$$

**Conductividad por factores de forma (Ec. 25):**
$$Q_i=k,S_i,(T_i-T_S) \qquad\Rightarrow\qquad k=\frac{Q_{tot}}{\sum_i S_i,\Delta T_i}$$
con $i$ = pata izquierda L, pata derecha R, tramo horizontal H.
- Factores de forma: $S_L=S_R=0{,}230$ m, $S_H=0{,}730$ m. Diferencias de temperatura: $\Delta T_L=11{,}9$, $\Delta T_H=11{,}8$, $\Delta T_R=11{,}7$ K.
- **Sin interacción entre patas: $k_1=0{,}99$ W/m·K** (cota inferior).

**Factor de interacción entre dos cilindros paralelos iguales (Ec. 26):**
$$S_{int}=\frac{2\pi L_{leg}}{\cosh^{-1}!\left(\dfrac{4w^2-2D^2}{2D^2}\right)}$$
$w$ es la distancia entre ejes de las patas y $D$ el diámetro. Se resta (ponderado por el $\Delta T$ promedio) porque las patas se "estorban" térmicamente, y se obtiene **$k_2=1{,}09$ W/m·K** (mejor estimación).

**Chequeo con FEM 2D:** patas como segmentos Dirichlet, superficie libre con Robin ($h=150$ W/m²K, $T_\infty=20$ °C), resto adiabático. Con $k=1{,}0$ reproduce el nivel de temperatura superficial y la dispersión lateral, y el balance de calor cierra.
![[Experimental determination and finite element modeling of thermal conductivity in moist sand-1793745781202.webp]]
#### 3.2 Cilindro sumergido
**Datos medidos:** $T_2\approx100$ °C (pared del cilindro), $T_4\approx90$ °C (cara superior/calefactor), $T_3\approx30{,}6$ °C (superficie de arena). **Potencia eléctrica:** $P=I^2R_L=84{,}2$ W.

**Balance de potencia (Ec. 27):**
$$P=Q_{conv.cyl}+Q_{rad}+Q_{cond}+Q_{conv.sand}$$

| Término         | Expresión                                       | Significado                                                                                              |
| --------------- | ----------------------------------------------- | -------------------------------------------------------------------------------------------------------- |
| $Q_{conv.cyl}$  | $h_{air},\pi r_2^2,(T_4-T_\infty)$              | Convección desde la cara superior del cilindro                                                           |
| $Q_{rad}$       | $\varepsilon\sigma\pi r_2^2,(T_4^4-T_\infty^4)$ | Radiación desde esa cara (despreciada); $\varepsilon$ emisividad, $\sigma$ constante de Stefan-Boltzmann |
| $Q_{cond}$      | $k,S_v,(T_2-T_3)$                               | **Conducción hacia la arena (el término que contiene _k_)**                                              |
| $Q_{conv.sand}$ | $h_{air}(W_cL_c-\pi r_2^2)(T_3-T_\infty)$       | Convección desde la superficie libre de la arena                                                         |

Como $h_{air}$ no se mide, se hace un barrido (**Ec. 28**):

|$h_{air}$ (W/m²K)|_k_ (W/m·K)|
|---|---|
|20|1,62|
|25|1,48|
|30|1,34|

**FEM 2D:** el cilindro se representa como una "muesca" rectangular en la superficie. Se imponen 85 °C en las paredes verticales y 80 °C en el fondo (Dirichlet), Robin arriba y adiabático en el resto. Muestra la pluma de calor y las isotermas, pero queda como **visualización**, no como validación cuantitativa.
![[Experimental determination and finite element modeling of thermal conductivity in moist sand-1793745802748.webp]]
### 2.7 Discusión (Sec. 4)
#### 4.1 Efecto de la humedad
Con un modelo lineal entre _k_ seca (0,27) y saturada (2,5 W/m·K), los valores medidos ($k=1{,}1$ y $1{,}5$) corresponden a grados de saturación $S_1\approx 0{,}37$ y $S_2\approx 0{,}54$. Luego se pasa a humedad gravimétrica con:
$$w=S,\frac{n}{1-n},\frac{\rho_w}{\rho_s}$$
- $w$: contenido de agua (kg agua / kg arena seca)
- $S$: grado de saturación (fracción de poros llenos de agua)
- $n$: porosidad (≈ 0,38)
- $\rho_w=1000$ kg/m³, $\rho_s=2650$ kg/m³

Resultado: ≈ 8,6 % y ≈ 12,6 %, que **coincide con lo medido en el horno**. Esto respalda que la diferencia entre ensayos (~4 puntos porcentuales de agua) explica la mayor _k_ del cilindro. (La coincidencia es un chequeo de consistencia, no una validación independiente, porque _k_ medida y humedad se vinculan con el mismo modelo simple.)
#### 4.2 Incertidumbre
Incertidumbres de los instrumentos: caudal ≈ 5 %, termocuplas ±0,5 °C, dimensiones ±1 mm. Con propagación lineal (**Ec. 30**), suponiendo errores no correlacionados:
$$\left(\frac{\delta k}{k}\right)^2\approx\left(\frac{\delta\dot m}{\dot m}\right)^2+\left(\frac{\delta\Delta T_w}{\Delta T_w}\right)^2+\left(\frac{\delta\left(\sum_i S_i\Delta T_i\right)}{\sum_i S_i\Delta T_i}\right)^2$$
$\Delta T_w$ es la caída de temperatura del agua. **Resultado (Ec. 31): $\delta k/k\approx 0{,}2\text{-}0{,}3$**, o sea ±0,2-0,3 W/m·K, **mayor que el intervalo 0,99-1,09**, que por eso es un "rango de modelado", no un intervalo de confianza. Para el cilindro (Ec. 32, sin radiación) es parecido (20-30 %), dominado por $P$, $T_2$, $T_3$ y $h_{air}$ (asumido con ~20 % de incertidumbre).
#### 4.3 Limitaciones
1. Humedad no controlada (valores promedio del lote; posible redistribución del agua al calentar).
2. Pocas corridas, sin réplicas estadísticas.
3. FEM 2D como sustituto de geometrías 3D (el cilindro axisimétrico no se captura bien); sensible a $h_{air}$ y a las pérdidas por las paredes.
4. Análisis de incertidumbre aproximado (sin Monte Carlo). Trabajo futuro: FEM 3D, humedad controlada y réplicas.
### 2.8 Conclusiones (Sec. 5)
Las dos configuraciones convergen en _k_ efectiva **1,0-1,5 W/m·K**. El tubo en U da 0,99 (sin interacción) y 1,09 (con interacción). El cilindro da 1,34-1,62, según $h_{air}$. El FEM reproduce las temperaturas medidas para el tubo con $k=1{,}0\text{-}1{,}1$. El método es un marco pedagógico extensible a otros problemas de fuentes enterradas.
## 4. Hallazgos Críticos
- **La humedad domina la conductividad.** Una diferencia de ~4 puntos de humedad (8,6 → 12,6 wt %) acompaña un salto de _k_ de ~1,1 a ~1,5 W/m·K. La arena seca ronda 0,2-0,4 W/m·K, un factor 3 a 5 menos.
- **Método de bajo costo y reproducible.** $k=Q/(S,\Delta T)$ con factores de forma clásicos, más FEM en software libre (FEniCS + Gmsh), sin equipos especializados.
- **La conclusión depende de supuestos poco controlados.** Variar $h_{air}$ de 20 a 30 W/m²K mueve _k_ de 1,62 a 1,34 W/m·K (−17 %). La incertidumbre declarada es de 20-30 %, mayor que el rango 0,99-1,09 que se presenta como resultado del tubo.
- **Pérdidas de calor.** No se resuelven ni se mitigan: no hay aislante, las paredes de plexiglás permiten fugas, y el FEM las trata como adiabáticas. Es una limitación explícita del propio paper.
- **Convergencia numérica sólida.** Con elementos cuadráticos y $n_\lambda=200$ el error es 0,04 %, irrelevante frente a la incertidumbre experimental.
- **Contexto de baterías de arena.** La introducción señala que la baja _k_ limita las velocidades de carga/descarga y que se investigan aditivos conductores. Remite a Tetteh et al. 2024 (refs. [11] y [12], que son el **mismo** artículo duplicado; también lo cita el paper de Abera como ref. [8]), una buena lectura si te interesa mejorar la conducción en el lecho.

**Lectura para tu pila de arena (observación mía, no del paper):**
- Los valores de 1,0-1,5 W/m·K corresponden a arena **húmeda por debajo de ~100 °C**. En un acumulador a 500 °C la arena estará seca, así que conviene diseñar con _k_ de arena seca (orden 0,2-0,4 W/m·K a temperatura ambiente; el paper no cubre alta temperatura).
- Con la Ec. 9 se ve el problema. Un tubo vertical de 1 m y Ø20 mm da $S_v\approx 1{,}2$ m. Con $k=0{,}3$, $Q\approx 0{,}36\ \text{W/K}\cdot\Delta T$, y para extraer 20 W haría falta un $\Delta T\approx 55$ K entre el tubo y la arena lejana. Tu requerimiento es ≈ 174 W (8,7 m × 20 W/m), lo que sugiere intercambiadores de gran superficie y poco espaciados, o aletas/rellenos que mejoren la conducción.
- Si querés practicar simulación abierta antes de pasar a ANSYS, el flujo FEniCS + Gmsh de este paper es un buen ejemplo de partida (conducción estacionaria con Dirichlet y Robin).