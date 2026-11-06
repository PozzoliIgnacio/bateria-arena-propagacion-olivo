---
Titulo: "Formulario de dimensionamiento de la pila de arena"
Año: 2026
Padre: "[[CUDAR - Desarrollo de Pila de Arena]]"
Tipo:
  - Formulario
Estado:
  - Haciendo
---
# Formulario de dimensionamiento de la pila de arena
Ecuaciones de cálculo manual para dimensionar un prototipo o un módulo, ordenadas según los capítulos del informe [1]–[6]. No se incluyen las ecuaciones de simulación (modelo distribuido, correlaciones de $k_{ef}$ ni condiciones de borde de Fluent). Para esas, ver el Cap 3 y el Cap 6.

> [!info] Cómo usar este formulario
> - Las temperaturas van **en K dentro de las ecuaciones** (sobre todo en $c_p(T)$, $k(T)$ y radiación). En las diferencias de temperatura da lo mismo K o °C.
> - La columna "Valor de referencia" muestra el valor del caso base del Cap 5 [5] ($T_{max}$ = 300 °C, 1 m² de mesa) o un valor típico. **No es un dato del prototipo**: reemplazalo por el tuyo.
> - Las ecuaciones de ingeniería estándar que no salen de las notas están marcadas con **(IE)**; conviene contrastarlas con Incropera o Çengel.

---
## 0. Datos y propiedades de referencia

| Propiedad | Símbolo | Valor | Unidad | Fuente |
|---|---|---|---|---|
| Densidad aparente de la arena de cuarzo | $\rho_b$ | 1586 (1425–1747 según la arena) | kg/m³ | [7] |
| Densidad del grano | $\rho_s$ | 2650 | kg/m³ | [8] |
| Porosidad | $\varepsilon$ | 0,44 | – | [7] |
| Calor específico de la arena | $c_p$ | 850 a 20 °C; 1187 a 600 °C | J/(kg·K) | [7] |
| Conductividad del lecho seco | $k_{ef}$ | 0,15–0,30 a 20 °C; 0,25–0,33 a 300 °C | W/(m·K) | [3], [7], [8] |
| Conductividad de arena húmeda (8–13 % de agua) | $k_{ef}$ | 1,0–1,5 | W/(m·K) | [10] |
| Inversión α→β del cuarzo | $T_{lim}$ | 573 (límite **local**) | °C | [7] |
| Aire a 20 °C: densidad, $c_p$, $k$, $\nu$ | — | 1,20; 1007; 0,026; 1,5·10⁻⁵ | SI | IE |
| Aire a 100 °C: densidad, $k$, $\nu$, $Pr$ | — | 0,95; 0,031; 2,3·10⁻⁵; 0,70 | SI | IE |
| Lana de roca alta densidad, $k(T)$ | $k_{ais}$ | 0,037 / 0,054 / 0,071 / 0,093 a 50 / 200 / 300 / 400 °C | W/(m·K) | [5] (catálogo típico) |
| Acero al carbono / AISI 304: $k$ | $k_w$ | 45 / 16 | W/(m·K) | IE |
| Dilatación lineal: acero al carbono / AISI 304 / arena | $\alpha_L$ | 12,5 / 17,8 / ~12 ·10⁻⁶ | 1/K | IE |
| Calor latente de vaporización del agua | $h_{fg}$ | 2,26·10⁶ | J/kg | IE |
| Constante de Stefan-Boltzmann | $\sigma$ | 5,67·10⁻⁸ | W/(m²·K⁴) | — |

Valores de $k_{ef}(T)$ con ZBS más radiación para arena seca, que conviene usar en los cálculos manuales [3]:

| $T$ [°C] | 20 | 100 | 200 | 300 | 400 | 500 | 573 |
|---|---|---|---|---|---|---|---|
| $k_{ef}$, $d_p$ = 0,5 mm (banda inferior) | 0,156 | 0,183 | 0,218 | 0,256 | 0,298 | 0,344 | 0,380 |
| Ajuste lineal de Homa et al. [9] (banda superior) | — | 0,214 | 0,274 | 0,334 | 0,394 | 0,454 | 0,497 |

> [!warning] Dato faltante: propiedades de la arena real
> Hay que medir la arena que se compre: granulometría, $\rho_b$ en caída libre y compactada, y $k_{ef}$. Mientras tanto, usá la banda inferior para la extracción y la superior para la temperatura de las resistencias.

---
## Cap 1. Demanda, balance diario y eficiencia [1]

### F1.1 Potencia nominal de la cama
**Descripción.** Potencia eléctrica máxima que disipa hoy la resistencia del sustrato de una mesa. Es la potencia de referencia que la pila tiene que poder reemplazar.
$$
P_{nom} = q'\,L
$$
**Parámetros:**
- $P_{nom}$: potencia máxima de la resistencia de una mesa [W]. Referencia: 174.
- $q'$: potencia por metro de la resistencia [W/m]. Referencia: 20.
- $L$: largo de la resistencia [m]. Referencia: 8,70.
### F1.2 Potencia de una resistencia según la tensión
**Descripción.** Relación de Joule entre tensión, resistencia y potencia de un elemento resistivo. Sirve para especificar la resistencia de cada calefactor según la tensión con que se lo alimente, o para saber cuánto disipa con una tensión dada.
$$
P = \frac{V_{RMS}^2}{R}
\qquad\Longrightarrow\qquad
R = \frac{V^2}{P}
$$
**Parámetros:**
- $P$: potencia disipada [W]. Referencia: 105 por elemento.
- $V_{RMS}$, $V$: tensión eficaz aplicada [V]. Referencia: 220 CA, o la tensión del bus CC.
- $R$: resistencia eléctrica del elemento [Ω]. Referencia: 461 Ω para 105 W a 220 V.
> [!note] Uso en el prototipo
> Con esta ecuación se especifica cada calefactor a su tensión de trabajo real. Si va conectado directo al panel, la potencia sale de cruzar la curva I-V del panel con la recta $V/R$, no de la potencia nominal.
### F1.3 Energía nocturna
**Descripción.** Energía térmica que hay que entregar al sustrato durante una noche: la potencia demandada integrada en el tiempo. Con $\bar f$ = 1 da la cota superior.
$$
E_{noche} = \bar f\,P_{nom}\,t_n
$$
**Parámetros:**
- $E_{noche}$: energía que pide la cama en la noche [J (÷ 3,6·10⁶ → kWh)]. Referencia: 8,77 MJ = 2,44 kWh.
- $\bar f$: factor de uso medio (potencia media / nominal), $0 < \bar f \le 1$ [adimensional]. Referencia: 1 (cota superior).
- $t_n$: duración de la noche de diseño [s]. Referencia: 14 h = 50 400 s.
> [!warning] Dato faltante: $\bar f$
> Sale de registros de la resistencia actual en invierno o del balance térmico de la cama. Es el dato que más mueve el tamaño.
### F1.4 Balance diario en régimen periódico
**Descripción.** Balances de energía de un día en régimen periódico, en el que la arena vuelve cada 24 h al mismo estado. El primero reparte la producción del panel. El segundo dice que todo lo que entra a la arena sale como calor útil o como pérdidas.
$$
E_{FV} = E_{aux} + E_{carga} + E_{no\,aprov},
\qquad
E_{carga} = E_{entregada} + E_{perd,24h}
$$
**Parámetros:**
- $E_{FV}$: energía diaria que produce el panel [J].
- $E_{aux}$: consumo diario de nebulización, control y ventilador [J]. Referencia: ~0,2 kWh de la pila, sin nebulización.
- $E_{carga}$: energía eléctrica que entra a la arena [J]. Referencia: 4,20 kWh.
- $E_{no\,aprov}$: energía FV que no se puede usar (pila llena, escalones) [J].
- $E_{entregada}$: calor que llega a la cama [J]. Referencia: = $E_{noche}$.
- $E_{perd,24h}$: pérdidas por la envolvente en 24 h [J]. Referencia: 1,77 kWh.
### F1.5 Eficiencia térmica diaria y comparación con litio
**Descripción.** Fracción de la energía cargada que llega a la cama en el ciclo diario. También da la energía diaria que el panel tiene que producir para cubrir la misma noche, con la pila o con una batería de litio.
$$
\eta_{alm} = \frac{E_{entregada}}{E_{carga}} = 1 - \frac{E_{perd,24h}}{E_{carga}},
\qquad
E_{FV}^{\,arena} = \frac{E_{noche}}{\eta_{alm}},
\qquad
E_{FV}^{\,Li} = \frac{E_{noche}}{\eta_{rt}}
$$
**Parámetros:**
- $\eta_{alm}$: eficiencia térmica diaria del acumulador [adimensional]. Referencia: 0,58.
- $\eta_{rt}$: eficiencia eléctrica de ida y vuelta del litio [adimensional]. Referencia: 0,80–0,95.
- $E_{FV}^{\,arena}$, $E_{FV}^{\,Li}$: energía diaria que cada opción le pide al panel [J].
### F1.6 Potencia de pérdidas
**Descripción.** Calor que se escapa por la envolvente en cada instante: la diferencia de temperatura entre la arena y el invernadero dividida por la resistencia térmica total, o multiplicada por la conductancia.
$$
\dot Q_{perd} = \frac{T_{arena} - T_{inv}}{R_{env}} = UA\,(T_{arena} - T_{inv})
$$
**Parámetros:**
- $\dot Q_{perd}$: potencia perdida [W]. Referencia: 73 de media.
- $T_{arena}$: temperatura media de la arena [K].
- $T_{inv}$: temperatura del invernadero [K]. Referencia: 283 (10 °C, conservador).
- $R_{env}$: resistencia térmica total de la envolvente [K/W]. Referencia: 2,6.
- $UA$: conductancia total de pérdidas ($= 1/R_{env}$) [W/K]. Referencia: 0,378.
### F1.7 Condición de temperaturas
**Descripción.** Cadena de desigualdades que tienen que cumplir las temperaturas para que el calor fluya de la arena al sustrato sin superar los límites de los materiales. Fija el piso de $T_{min}$ y el techo de $T_{max}$.
$$
T_{sustrato} < T_{fluido} < T_{min} < T_{max} < T_{lim}
$$
**Parámetros:**
- $T_{sustrato}$: temperatura del sustrato [°C]. Referencia: 20–30.
- $T_{fluido}$: temperatura del aire de extracción (impulsión ≤ 60 °C) [°C]. Referencia: 35–60.
- $T_{min}$: temperatura media mínima útil de la arena [°C]. Referencia: ~105.
- $T_{max}$: temperatura media máxima de la arena [°C]. Referencia: 300.
- $T_{lim}$: límite de materiales y de la arena local [°C]. Referencia: 573.
## Cap 2. Órdenes de magnitud del estado del arte [2]
### F2.1 Energía y densidad energética (calor sensible)
**Descripción.** Energía de calor sensible con un calor específico medio, y su versión por unidad de volumen. Es la primera estimación del tamaño del lecho para un salto térmico dado.
$$
Q_{th} = m\,\bar c_p\,\Delta T,
\qquad
q_{th} = \frac{Q_{th}}{V} = \rho_b\,\bar c_p\,\Delta T
$$
**Parámetros:**
- $Q_{th}$: energía térmica almacenada [J].
- $m$: masa de arena [kg]. Referencia: 85.
- $\bar c_p$: calor específico medio en el rango [J/(kg·K)]. Referencia: ~900 entre 105 y 300 °C.
- $\Delta T$: salto térmico [K]. Referencia: 195.
- $q_{th}$: densidad energética volumétrica [J/m³].
- $V$: volumen de arena [m³]. Referencia: 0,054.
### F2.2 Difusividad y profundidad de penetración
**Descripción.** Velocidad con que se difunde el calor en la arena y distancia que alcanza por conducción en un tiempo dado. Define el paso máximo entre resistencias y entre tubos.
$$
\alpha = \frac{k_{ef}}{\rho_b\,c_p},
\qquad
\delta \approx \sqrt{\alpha\,t}
$$
**Parámetros:**
- $\alpha$: difusividad térmica efectiva [m²/s]. Referencia: 1,3–2,2·10⁻⁷.
- $k_{ef}$: conductividad efectiva del lecho [W/(m·K)]. Referencia: 0,20–0,35.
- $\delta$: distancia que avanza el calor por conducción [m]. Referencia: ~6 cm en 5,5 h; ~10 cm en 14 h.
- $t$: tiempo [s].
> [!note] Uso en el prototipo
> Define el paso máximo entre resistencias y entre tubos: ningún punto del lecho debería quedar más lejos que $\delta$ de un elemento.
### F2.3 Potencia extraída por el aire y relación de descarga
**Descripción.** Potencia que se lleva el aire según su caudal y su calentamiento, y fracción de la energía de descarga que sale útil con el aire frente a la que se pierde por la envolvente.
$$
\dot Q_{ext} = \dot m_a\,c_{p,a}\,(T_{a,sal} - T_{a,ent}),
\qquad
DR = \frac{E_{outlet}}{E_{outlet} + E_{loss}}
$$
**Parámetros:**
- $\dot Q_{ext}$: potencia que se lleva el aire [W]. Referencia: 174.
- $\dot m_a$: caudal másico de aire [kg/s]. Referencia: 6,9·10⁻³ (25 kg/h).
- $c_{p,a}$: calor específico del aire [J/(kg·K)]. Referencia: 1007.
- $T_{a,ent}$, $T_{a,sal}$: temperaturas de entrada y salida del aire [K].
- $DR$: relación de descarga [adimensional]. Referencia: 0,88–0,97 en Homa et al. [9].
- $E_{outlet}$, $E_{loss}$: energía que sale con el aire y la que se pierde en la descarga [J].
## Cap 3. Fundamentos: propiedades, tubos y envolvente [3]
### F3.1 Calor específico de la arena y energía específica
**Descripción.** Ajuste lineal del calor específico de la arena de cuarzo en función de la temperatura, y su integral cerrada entre dos temperaturas. Da la energía por kg almacenada entre $T_{min}$ y $T_{max}$ sin suponer $c_p$ constante.
$$
c_p(T) = T + 427,
\qquad
\Delta h = \frac{T_2^2 - T_1^2}{2} + 427\,(T_2 - T_1),
\qquad
\bar c_p = 427 + \frac{T_1 + T_2}{2}
$$
**Parámetros:**
- $c_p(T)$: calor específico (válido entre 323 y 846 K) [J/(kg·K)]. Referencia: 850 a 150 °C.
- $T$, $T_1$, $T_2$: temperatura; inicial y final del intervalo [**K**]. Referencia: 378 y 573 K.
- $\Delta h$: energía específica entre $T_1$ y $T_2$ [J/kg]. Referencia: 175,8 kJ/kg entre 105 y 300 °C.
- $\bar c_p$: calor específico medio del intervalo [J/(kg·K)]. Referencia: ~902.
> [!note] Margen conservador
> El ajuste subestima $c_p$ por debajo de ~100 °C y lo sobreestima cerca de 573 °C. Por debajo de 50 °C usá ~800 J/(kg·K).
### F3.2 Densidad energética volumétrica
**Descripción.** Energía útil por m³ de lecho. Permite pasar de la energía requerida al volumen de arena.
$$
e_v = \rho_b\,\Delta h
$$
**Parámetros:**
- $e_v$: energía por m³ de lecho [J/m³ (÷ 3,6·10⁶ → kWh/m³)]. Referencia: 77 kWh/m³ entre 105 y 300 °C.
- $\rho_b$: densidad aparente [kg/m³]. Referencia: 1586.
### F3.3 Energía para evaporar la humedad
**Descripción.** Energía que se consume en evaporar el agua que contiene la arena, en el primer secado o si reabsorbe humedad del invernadero. Justifica un contenedor estanco con venteo.
$$
E_{lat} = w\,m\,h_{fg}
$$
**Parámetros:**
- $E_{lat}$: energía consumida en el secado [J]. Referencia: ~19 MJ con $w$ = 0,10 y 85 kg.
- $w$: contenido de agua (kg de agua / kg de arena seca) [adimensional].
- $m$: masa de arena seca [kg]. Referencia: 85.
- $h_{fg}$: calor latente de vaporización [J/kg]. Referencia: 2,26·10⁶.
### F3.4 Capacidad térmica de una mezcla arena–virutas (IE)
**Descripción.** Capacidad térmica por volumen de un lecho mezclado con virutas metálicas, ponderada por fracción volumétrica. Sirve para evaluar cuánta capacidad se pierde (o se gana) al mejorar la conductividad.
$$
(\rho c)_{mez} = (1 - \phi_m)\,\rho_b\,c_{p,arena} + \phi_m\,\rho_{b,m}\,c_{p,m}
$$
**Parámetros:**
- $(\rho c)_{mez}$: capacidad térmica volumétrica de la mezcla [J/(m³·K)]. Referencia: arena sola ≈ 1,3·10⁶.
- $\phi_m$: fracción volumétrica de virutas [adimensional]. Referencia: 0,20 (umbral de percolación).
- $\rho_{b,m}$: densidad aparente del lecho de virutas [kg/m³]. Referencia: a medir.
- $c_{p,m}$: calor específico del metal [J/(kg·K)]. Referencia: Al 897; Cu 385.
### F3.5 Pérdida de carga si el aire atraviesa el lecho (Ergun)
**Descripción.** Ecuación de Ergun: pérdida de presión del aire que atraviesa un lecho granular, suma de un término viscoso y uno inercial. Solo aplica a la alternativa de aire a través de la arena.
$$
\frac{\Delta P}{L} = 150\,\frac{(1-\varepsilon)^2}{\varepsilon^3}\,\frac{\mu_f\,U_s}{d_p^2} + 1{,}75\,\frac{1-\varepsilon}{\varepsilon^3}\,\frac{\rho_f\,U_s^2}{d_p}
$$
**Parámetros:**
- $\Delta P/L$: gradiente de presión en el lecho [Pa/m].
- $\varepsilon$: porosidad [adimensional]. Referencia: 0,35–0,50.
- $\mu_f$: viscosidad dinámica del aire [Pa·s]. Referencia: 1,8·10⁻⁵ a 20 °C.
- $U_s$: velocidad superficial (caudal / sección total) [m/s].
- $d_p$: diámetro de grano [m]. Referencia: 0,5–2·10⁻³.
- $\rho_f$: densidad del aire [kg/m³]. Referencia: 1,2.
> [!note] Solo para la alternativa de aire por el lecho
> Con aire por tubos (la configuración elegida) no aplica.
### F3.6 Convección interna en el tubo (IE)
**Descripción.** Coeficiente de convección entre la pared interior del tubo y el aire. Se obtiene a partir del régimen (número de Reynolds) y la correlación de Nusselt que corresponda, y se expresa como resistencia por metro de tubo.
$$
Re = \frac{u\,D_i}{\nu_a},
\qquad
h_i = \frac{Nu\,k_a}{D_i},
\qquad
R'_{conv} = \frac{1}{h_i\,\pi\,D_i}
$$
$$
Nu =
\begin{cases}
3{,}66 & Re < 2300 \text{ (laminar, pared isoterma)} \\[4pt]
\dfrac{(f/8)(Re - 1000)\,Pr}{1 + 12{,}7\sqrt{f/8}\,(Pr^{2/3} - 1)}, \quad f = (0{,}790\ln Re - 1{,}64)^{-2} & 3000 \le Re \le 5\cdot10^6 \text{ (Gnielinski)} \\[4pt]
0{,}023\,Re^{0{,}8}\,Pr^{0{,}4} & Re \ge 10^4 \text{ (Dittus-Boelter)}
\end{cases}
$$
**Parámetros:**
- $Re$: número de Reynolds [adimensional]. Referencia: 7400 (2 circuitos, 25 kg/h).
- $u$: velocidad media del aire en el tubo [m/s]. Referencia: 5,2.
- $D_i$: diámetro interior del tubo [m]. Referencia: 0,029.
- $\nu_a$: viscosidad cinemática del aire [m²/s]. Referencia: 2,3·10⁻⁵ a 100 °C.
- $Nu$: número de Nusselt [adimensional].
- $Pr$: número de Prandtl del aire [adimensional]. Referencia: 0,70.
- $f$: factor de fricción de Darcy [adimensional].
- $h_i$: coeficiente de convección interno [W/(m²·K)]. Referencia: 5–20.
- $k_a$: conductividad del aire [W/(m·K)]. Referencia: 0,031 a 100 °C.
- $R'_{conv}$: resistencia de convección por metro de tubo [m·K/W]. Referencia: 0,26–2,8.
### F3.7 Resistencia de la pared y de la arena alrededor del tubo (IE)
**Descripción.** Resistencias por metro de tubo de dos conducciones: la de la pared, como cilindro hueco, y la de la arena que rodea al tubo dentro de su celda, con el factor de forma de un cilindro centrado en un cuadrado.
$$
R'_{pared} = \frac{\ln(D_o/D_i)}{2\pi\,k_w},
\qquad
R'_{arena} = \frac{\ln(1{,}08\,w/D_o)}{2\pi\,k_{ef}}
$$
**Parámetros:**
- $R'_{pared}$: resistencia de la pared por metro [m·K/W]. Referencia: ~0,001 (despreciable en acero).
- $D_o$: diámetro exterior del tubo [m]. Referencia: 0,032.
- $k_w$: conductividad de la pared [W/(m·K)]. Referencia: 16 (AISI 304).
- $R'_{arena}$: resistencia de la arena en una celda cuadrada [m·K/W]. Referencia: ~1,05 con paso de 10 cm.
- $w$: paso entre tubos (lado de la celda) [m]. Referencia: 0,094–0,10.
- $k_{ef}$: conductividad efectiva a la temperatura de trabajo [W/(m·K)]. Referencia: banda inferior.
### F3.8 Cadena de resistencias y potencia por metro de tubo
**Descripción.** Suma en serie de las resistencias entre la arena y el aire, y calor que pasa por metro de tubo para una diferencia de temperatura dada.
$$
R'_{tot} = R'_{arena} + R'_c + R'_{pared} + R'_{conv},
\qquad
q' = \frac{T_s - T_a}{R'_{tot}}
$$
**Parámetros:**
- $R'_{tot}$: resistencia total arena–aire por metro [m·K/W]. Referencia: 1,47–1,66.
- $R'_c$: resistencia de contacto arena–tubo [m·K/W]. Referencia: 0,15 (supuesto).
- $q'$: calor por metro de tubo [W/m].
- $T_s$: temperatura de la arena lejos del tubo [K].
- $T_a$: temperatura del aire [K].

> [!warning] Dato faltante: $R'_c$
> Sale de suponer un huelgo de 0,5 mm de aire. Hace falta un dato de literatura o un ensayo.
### F3.9 Temperatura de salida y potencia de un tubo (método NTU, IE)
**Descripción.** Balance del aire integrado a lo largo del tubo, con la arena a temperatura uniforme: da la temperatura de salida y la potencia extraída. Con NTU alto el aire sale casi a la temperatura de la arena.
$$
NTU_t = \frac{L_t}{\dot m\,c_{p,a}\,R'_{tot}},
\qquad
T_{a,out} = T_s - (T_s - T_{a,in})\,e^{-NTU_t},
\qquad
\dot Q = \dot m\,c_{p,a}\,(T_s - T_{a,in})\left(1 - e^{-NTU_t}\right)
$$
**Parámetros:**
- $NTU_t$: número de unidades de transferencia del tubo [adimensional].
- $L_t$: largo de tubo dentro de la arena [m]. Referencia: 5,1.
- $\dot m$: caudal de aire por la pila [kg/s]. Referencia: ≤ 6,9·10⁻³.
- $T_{a,in}$, $T_{a,out}$: temperaturas del aire a la entrada y la salida [K]. Referencia: 35 °C a la entrada.
- $\dot Q$: potencia extraída [W].
### F3.10 Tiro de un termosifón (IE)
**Descripción.** Presión que genera la diferencia de densidad entre el aire frío y el caliente en una columna de altura $H$. Permite saber si un circuito puede funcionar sin ventilador.
$$
\Delta p_{tiro} = g\,H\,(\rho_{a,frío} - \bar\rho_{a,caliente})
$$
**Parámetros:**
- $\Delta p_{tiro}$: presión motriz por diferencia de densidad [Pa]. Referencia: 0,6–1,7.
- $g$: gravedad [m/s²]. Referencia: 9,81.
- $H$: altura entre la entrada fría y la salida caliente [m]. Referencia: 0,4–0,8.
- $\rho_{a,frío}$, $\bar\rho_{a,caliente}$: densidad del aire frío y caliente medio [kg/m³].

> [!note] Uso en el prototipo
> Comparalo con la pérdida de carga del circuito (F5.9). Si $\Delta p_{tiro}$ es mucho menor, hace falta ventilador.
### F3.11 Coeficiente global de una pared plana multicapa (IE)
**Descripción.** Coeficiente global de transferencia de una pared plana de varias capas: las resistencias de conducción de cada capa en serie con la convección y la radiación exteriores.
$$
\frac{1}{U} = \sum_{n=1}^{N}\frac{t_n}{k_n(\bar T_n)} + R''_c + \frac{1}{h_{ext} + h_{rad}}
$$
**Parámetros:**
- $U$: coeficiente global de la pared [W/(m²·K)].
- $t_n$: espesor de la capa $n$ [m]. Referencia: 0,20 de lana de roca.
- $k_n(\bar T_n)$: conductividad de la capa a su temperatura media [W/(m·K)]. Referencia: tabla de la sección 0.
- $R''_c$: resistencias de contacto entre capas [m²·K/W]. Referencia: ≈ 0.
- $h_{ext}$: convección natural exterior (F3.12) [W/(m²·K)]. Referencia: 1–3 con 20 cm de aislación.
- $h_{rad}$: radiación exterior linealizada (F3.13) [W/(m²·K)]. Referencia: ~5.
### F3.12 Convección natural exterior por cara (IE)
**Descripción.** Coeficiente de convección natural del aire alrededor de cada cara exterior, con correlaciones de Nusselt en función del número de Rayleigh según la orientación de la cara.
$$
Ra = \frac{g\,\beta\,\Delta T\,L_c^3}{\nu\,\alpha_a},
\qquad
h_{ext} = \frac{Nu\,k_a}{L_c}
$$
- Cara superior (caliente hacia arriba): $Nu = 0{,}54\,Ra^{1/4}$ / $Nu = 0{,}15\,Ra^{1/3}$ (rango: 10⁴–10⁷ / 10⁷–10¹¹).
- Cara lateral (Churchill-Chu): $Nu = \left(0{,}825 + \dfrac{0{,}387\,Ra^{1/6}}{[1 + (0{,}492/Pr)^{9/16}]^{8/27}}\right)^2$ (válida en todo el rango).
- Cara inferior (caliente hacia abajo): $Nu = 0{,}27\,Ra^{1/4}$ (rango: 10⁵–10¹¹).

**Parámetros:**
- $Ra$: número de Rayleigh [adimensional].
- $\beta$: coeficiente de expansión del aire ($\approx 1/T_{film}$) [1/K]. Referencia: ~3,5·10⁻³.
- $\Delta T$: diferencia entre la cara y el ambiente [K]. Referencia: ~4 con 20 cm de aislación.
- $L_c$: longitud característica (vertical: altura; horizontal: área/perímetro) [m].
- $\nu$, $\alpha_a$: viscosidad cinemática y difusividad del aire [m²/s]. Referencia: 1,5·10⁻⁵ y 2,1·10⁻⁵.
### F3.13 Radiación exterior linealizada (IE)
**Descripción.** Radiación de la superficie exterior hacia el ambiente, expresada como un coeficiente equivalente para sumarlo a la convección. Hay que iterar, porque depende de la temperatura de la superficie.
$$
h_{rad} = \varepsilon_{ext}\,\sigma\,(T_{ext}^2 + T_\infty^2)(T_{ext} + T_\infty)
$$
**Parámetros:**
- $h_{rad}$: coeficiente de radiación [W/(m²·K)]. Referencia: 5,5–6,8 con superficie a 30–70 °C.
- $\varepsilon_{ext}$: emisividad de la superficie exterior [adimensional]. Referencia: 0,9 pintada; ~0,1 aluminio.
- $T_{ext}$: temperatura de la superficie exterior [**K**].
- $T_\infty$: temperatura del ambiente [**K**]. Referencia: 283.
### F3.14 Constante de autodescarga
**Descripción.** Tiempo característico de enfriamiento del módulo sin extracción, con modelo concentrado. Indica cuánto conserva el calor en reposo.
$$
\tau = \frac{m\,\bar c_p}{UA}
$$
**Parámetros:**
- $\tau$: tiempo en que el exceso de temperatura cae a $1/e$ sin extracción [s]. Referencia: ~56 h.
- $UA$: conductancia total de pérdidas [W/K]. Referencia: 0,378.
### F3.15 Radio crítico de aislación (IE)
**Descripción.** Radio por debajo del cual agregar aislante a un cilindro aumenta las pérdidas en lugar de reducirlas. Sirve para verificar tubos chicos y pasamuros.
$$
r_c = \frac{k_{ais}}{h_{ext}}
$$
**Parámetros:**
- $r_c$: radio por debajo del cual aislar aumenta las pérdidas [m]. Referencia: 4–8 mm.
- $k_{ais}$: conductividad del aislante [W/(m·K)]. Referencia: 0,04.
> [!note] Implicación
> Cualquier tanque es mucho más grande que $r_c$: más aislación siempre baja las pérdidas. Útil sí para tubos chicos y pasamuros.
## Cap 4. Ingeniería conceptual: criterios de selección [4]
### F4.1 Paso máximo entre resistencias (filtro F2)
**Descripción.** Criterio de separación de resistencias: la mitad del paso no debe superar lo que penetra el calor durante la carga. Así todo el lecho se carga dentro de la ventana solar.
$$
\frac{w}{2} \lesssim \delta_c = \sqrt{\alpha_{ef}\,t_c}
$$
**Parámetros:**
- $w$: paso entre resistencias [m]. Referencia: ≤ 0,12–0,15.
- $\delta_c$: penetración térmica durante la carga [m]. Referencia: 0,06–0,08.
- $\alpha_{ef}$: difusividad efectiva [m²/s]. Referencia: F2.2.
- $t_c$: duración de la ventana de carga [s]. Referencia: 5–6 h.
### F4.2 Caudal mínimo y largo de tubo en la cama
**Descripción.** Caudal mínimo de aire para entregar la potencia de la cama sin superar la temperatura de impulsión, y largo de tubo bajo el sustrato necesario para transferirla (método NTU del lado de la cama).
$$
\dot m_{min} = \frac{P_{cama}}{c_{p,a}\,(T_{mez,max} - T_{sus})},
\qquad
L_s = -\dot m\,c_{p,a}\,R'_s\,\ln\!\left(1 - \frac{P_{cama}}{\dot m\,c_{p,a}\,(T_{mez} - T_{sus})}\right)
$$
**Parámetros:**
- $\dot m_{min}$: caudal mínimo para entregar la potencia [kg/s]. Referencia: 4,9·10⁻³ (18 kg/h).
- $P_{cama}$: potencia a entregar al sustrato [W]. Referencia: 174.
- $T_{mez,max}$, $T_{mez}$: temperatura máxima y real de impulsión a la cama [K]. Referencia: 60 °C.
- $T_{sus}$: temperatura del sustrato [K]. Referencia: 25 °C.
- $L_s$: largo de tubo de aire bajo el sustrato [m]. Referencia: ~4 con 25 kg/h y Ø32 mm.
- $R'_s$: resistencia por metro del tubo enterrado ($R'_{conv}$ + sustrato húmedo) [m·K/W]. Referencia: 0,45–0,52 turbulento.
### F4.3 Potencia del ventilador (IE)
**Descripción.** Potencia eléctrica que consume el ventilador para mover un caudal contra una pérdida de carga, según su rendimiento global.
$$
P_{vent} = \frac{\dot m\,\Delta p}{\rho_a\,\eta_v} = \frac{\dot V\,\Delta p}{\eta_v}
$$
**Parámetros:**
- $P_{vent}$: potencia eléctrica del ventilador [W]. Referencia: ~7,4.
- $\Delta p$: pérdida de carga total del lazo [Pa]. Referencia: ~370.
- $\rho_a$: densidad del aire en el ventilador [kg/m³]. Referencia: 1,1–1,2.
- $\dot V$: caudal volumétrico [m³/s].
- $\eta_v$: rendimiento global del ventilador [adimensional]. Referencia: 0,2–0,35.
### F4.4 Regulación por mezcla (bypass)
**Descripción.** Balance de la caja de mezcla: temperatura de impulsión que resulta de mezclar el aire de la pila con el de retorno, y potencia que llega a la cama. Sirve para dimensionar la compuerta de bypass y su rango de apertura.
$$
T_{mez} = x\,T_{pila,sal} + (1 - x)\,T_{ret},
\qquad
P_{cama} = x\,\dot m\,c_{p,a}\,(T_{pila,sal} - T_{ret}),
\qquad
T_{ret} = T_{mez} - \frac{P_{cama}}{\dot m\,c_{p,a}}
$$
**Parámetros:**
- $x$: fracción del caudal que pasa por la pila [adimensional]. Referencia: 0,13 al inicio → ~0,9 al final de la noche.
- $T_{pila,sal}$: temperatura del aire a la salida de la pila [K]. Referencia: hasta ~230 °C.
- $T_{ret}$: temperatura del aire que vuelve de la cama [K]. Referencia: ~35 °C.
### F4.5 Pérdidas de N módulos frente a una pila central
**Descripción.** Cuánto más pierden $N$ módulos que una pila única del mismo volumen total, con la misma forma y aislación, porque el área crece con $V^{2/3}$.
$$
\frac{\dot Q_{p,\,N}}{\dot Q_{p,\,central}} = N^{1/3}
$$
**Parámetros:**
- $N$: número de módulos que reemplazan a una pila central [adimensional]. Referencia: 2 → 1,26.
### F4.6 Área por volumen según la relación de aspecto (IE)
**Descripción.** Área por volumen, normalizada, de un prisma de base cuadrada y de un cilindro en función de la relación de aspecto. El mínimo de pérdidas está cerca de $\lambda$ = 1.
$$
\frac{A}{V^{2/3}}\bigg|_{prisma} = \frac{2 + 4\lambda}{\lambda^{2/3}},
\qquad
\frac{A}{V^{2/3}}\bigg|_{cilindro} = \frac{\pi/2 + \pi\lambda}{(\pi\lambda/4)^{2/3}}
$$
**Parámetros:**
- $A$: área exterior del lecho [m²].
- $V$: volumen del lecho [m³].
- $\lambda$: relación de aspecto: $H/a$ (prisma) o $H/D$ (cilindro) [adimensional]. Referencia: 1 → 6,00 (cubo) y 5,54 (cilindro).
## Cap 5. Predimensionamiento [5]
### F5.1 Pérdidas del ciclo diario
**Descripción.** Pérdidas de las 24 h divididas en tramos (descarga, reposos y carga), cada uno con su temperatura media de arena.
$$
E_{perd,24h} = UA\Big[(\bar T - T_{inv})(t_n + t_c) + (T_{min} - T_{inv})\,t_{r1} + (T_{max} - T_{inv})\,t_{r2}\Big],
\qquad
\bar T = \frac{T_{max} + T_{min}}{2}
$$
**Parámetros:**
- $t_n$: duración de la descarga [s]. Referencia: 14 h.
- $t_{r1}$: reposo con la arena cerca de $T_{min}$ [s]. Referencia: 2 h.
- $t_c$: duración de la carga [s]. Referencia: 5,5 h.
- $t_{r2}$: reposo con la arena cerca de $T_{max}$ [s]. Referencia: 2,5 h.
- $\bar T$: temperatura media de la arena en carga y descarga [K].
### F5.2 Energía diaria de carga
**Descripción.** Energía eléctrica que tiene que entrar cada día a la arena: la de la noche más las pérdidas diarias.
$$
E_{carga} = E_{noche} + E_{perd,24h}
$$
(Parámetros en F1.3 y F5.1. Valor de referencia: 4,20 kWh/día.)
### F5.3 Temperatura mínima útil de la arena
**Descripción.** Temperatura media de la arena por debajo de la cual el intercambiador, aun con todo el caudal, ya no entrega la potencia de la cama. Es el piso del salto térmico útil.
$$
T_{min} = T_{ret} + \frac{P_{cama}}{\dot m\,c_{p,a}\left(1 - e^{-UA_x/(\dot m\,c_{p,a})}\right)},
\qquad
UA_x = \frac{L_t}{R'_{tot}}
$$
**Parámetros:**
- $T_{min}$: temperatura media de la arena a la que ya no se entrega $P_{cama}$ [K]. Referencia: ~105 °C.
- $UA_x$: conductancia arena–aire del intercambiador [W/K]. Referencia: ~3.
- $L_t$: largo total de tubo en la arena [m]. Referencia: 4,5–5,1.
> [!note] Atajo
> Cuando $UA_x \ll \dot m\,c_{p,a}$, vale $T_{min} \approx T_{ret} + P_{cama}/UA_x$. Más tubo o aletas bajan $T_{min}$.
### F5.4 Masa, volumen y lado del lecho
**Descripción.** Masa de arena que cubre la noche y las pérdidas desde el final de la carga con el salto útil entre $T_{min}$ y $T_{max}$, y tamaño del lecho cúbico que le corresponde.
$$
m = \frac{E_{noche} + E_{perd,n} + E_{perd,r2}}{\varphi_u\,\Delta h(T_{min}, T_{max})},
\qquad
V = \frac{m}{\rho_b},
\qquad
a = H = V^{1/3}
$$
**Parámetros:**
- $E_{perd,n}$: pérdidas durante la descarga: $UA\,(\bar T - T_{inv})\,t_n$ [J]. Referencia: 3,67 MJ.
- $E_{perd,r2}$: pérdidas en el reposo vespertino: $UA\,(T_{max} - T_{inv})\,t_{r2}$ [J]. Referencia: 0,99 MJ.
- $\varphi_u$: factor de utilización del lecho [adimensional]. Referencia: 0,90 (supuesto).
- $\Delta h$: energía específica (F3.1) [J/kg]. Referencia: 175,8 kJ/kg.
- $a$, $H$: lado y altura del lecho cúbico [m]. Referencia: 0,377.
> [!warning] Cálculo iterativo
> $m$ depende de $UA$ y de $T_{min}$, que a su vez dependen del tamaño. Arrancá con un $UA$ estimado, calculá $m$ y $a$, recalculá $UA$ (F5.11) y $T_{min}$ (F5.3), y repetí hasta que $m$ no cambie.
### F5.5 Energía de la primera carga
**Descripción.** Energía de la primera puesta en marcha. Primero hay que calentar la arena desde la temperatura del invernadero hasta $T_{min}$ (energía que nunca se extrae) y después hasta $T_{max}$.
$$
E_{muerta} = m\left[\bar c_{p,0}\,(50\ ^\circ\text{C} - T_{inv}) + \Delta h(50\ ^\circ\text{C}, T_{min})\right],
\qquad
E_{arranque} = E_{muerta} + m\,\Delta h(T_{min}, T_{max})
$$
**Parámetros:**
- $E_{muerta}$: energía para llevar la arena hasta $T_{min}$ (no se extrae nunca) [J]. Referencia: 6,4 MJ.
- $\bar c_{p,0}$: calor específico medio por debajo de 50 °C [J/(kg·K)]. Referencia: 800.
- $E_{arranque}$: energía de la primera carga completa (sin secado ni aislación) [J]. Referencia: 21,3 MJ = 5,9 kWh.
### F5.6 Energía y potencia que se le piden al panel
**Descripción.** Energía diaria y potencia pico de panel que necesita un módulo, según las horas solares pico y el rendimiento de la cadena FV. También da la potencia máxima que llega a las resistencias.
$$
E_{FV,req} = E_{carga} + \frac{E_{aux,pila}}{\eta_{bat}},
\qquad
P_{FV,p} = \frac{E_{FV,req}}{HSP\cdot PR},
\qquad
P_{inst} = PR\cdot P_{FV,p}
$$
**Parámetros:**
- $E_{FV,req}$: energía diaria requerida al panel [kWh]. Referencia: ≈ 4,4.
- $E_{aux,pila}$: consumo propio de la pila (ventilador + control) [kWh]. Referencia: ~0,18.
- $\eta_{bat}$: rendimiento del almacenamiento eléctrico auxiliar [adimensional]. Referencia: 0,85.
- $P_{FV,p}$: potencia pico del panel [Wp]. Referencia: ≈ 1230.
- $HSP$: horas solares pico de invierno del sitio [h]. Referencia: 4,5 (genérico).
- $PR$: rendimiento global de la cadena FV → resistencias [adimensional]. Referencia: 0,80.
- $P_{inst}$: potencia máxima que llega a las resistencias [W]. Referencia: ≈ 930 (0,80 × 1167 Wp destinados a la carga).

> [!warning] Dato faltante: $HSP$ del sitio
> Con $HSP$ = 3,5 h la potencia pico sube a ~1,6 kWp.

### F5.7 Potencia admisible por metro de resistencia
**Descripción.** Potencia por metro de resistencia que mantiene la arena junto a la vaina por debajo de $T_{lim}$, con conducción radial cuasi estacionaria, y largo calefactado mínimo que resulta.
$$
q'_{adm} = \frac{2\pi\,k_{ef}\,(T_{lim} - T_{max})}{\ln(r_2/r_{eq})},
\qquad
r_{eq} = F_a\,(r_g + h_a),
\qquad
L_{res} \ge \frac{P_{inst}}{q'_{adm}}
$$
**Parámetros:**
- $q'_{adm}$: potencia por metro que no lleva la arena local por encima de $T_{lim}$ [W/m]. Referencia: 313 sin aletas; 525 con aletas (a 300 °C).
- $k_{ef}$: conductividad a $(T_{max} + T_{lim})/2$, banda inferior [W/(m·K)]. Referencia: ~0,32.
- $r_2$: radio de influencia de cada elemento (≈ medio paso) [m]. Referencia: 0,045.
- $r_{eq}$: radio equivalente de la vaina (con aletas) [m]. Referencia: 0,016.
- $F_a$: factor de forma de las aletas [adimensional]. Referencia: 0,7 (supuesto).
- $r_g$: radio exterior de la vaina guía [m]. Referencia: 0,008.
- $h_a$: altura de las aletas [m]. Referencia: 0,015.
- $L_{res}$: largo calefactado total mínimo [m]. Referencia: 1,8.

### F5.8 Carga superficial y temperatura de la vaina del calefactor

**Descripción.** Carga de superficie del calefactor y temperatura de su vaina. Se suma a la temperatura de la arena el salto en el huelgo de aire entre el calefactor y la vaina guía, con conducción y radiación en paralelo.

$$
q''_s = \frac{P_{el}}{\pi\,D_r\,L_{cal}},
\qquad
T_{vaina} = T_{ar,loc} + q'\,R'_h
$$

$$
R'_h = \left[\frac{2\pi k_a}{\ln(r_{gi}/r_r)} + \frac{\pi D_r\,\sigma\,4\bar T^3}{1/\varepsilon + (r_r/r_{gi})(1/\varepsilon - 1)}\right]^{-1}
$$

**Parámetros:**

- $q''_s$: carga de superficie del calefactor [W/m² (÷ 10⁴ → W/cm²)]. Referencia: 1,2 W/cm².
- $P_{el}$: potencia de un elemento [W]. Referencia: 105.
- $D_r$: diámetro del calefactor [m]. Referencia: 0,010.
- $L_{cal}$: largo calefactado de un elemento [m]. Referencia: 0,28.
- $T_{vaina}$: temperatura de la vaina del calefactor [K]. Referencia: ~620 °C.
- $T_{ar,loc}$: temperatura de la arena junto a la vaina guía [K]. Referencia: ~490 °C (≤ 573 °C).
- $q'$: potencia por metro del elemento ($P_{el}/L_{cal}$) [W/m]. Referencia: 371.
- $R'_h$: resistencia por metro del huelgo calefactor–vaina guía [m·K/W]. Referencia: ~0,27.
- $r_r$, $r_{gi}$: radio del calefactor y radio interior de la vaina guía [m]. Referencia: 0,005 y 0,007.
- $\bar T$: temperatura media del huelgo [**K**].
- $\varepsilon$: emisividad de superficies oxidadas [adimensional]. Referencia: 0,7.

### F5.9 Pérdida de carga en los tubos (IE)

**Descripción.** Pérdida de carga del aire en un circuito de tubos: fricción de Darcy-Weisbach más pérdidas localizadas en curvas y accesorios. Es el $\Delta p$ que entra en F4.3.

$$
\Delta p = \left(f\,\frac{L_c}{D_i} + \sum K\right)\frac{\rho_a\,u^2}{2},
\qquad
f =
\begin{cases}
64/Re & Re < 2300 \\
(0{,}790\ln Re - 1{,}64)^{-2} & Re \ge 3000
\end{cases}
$$

**Parámetros:**

- $\Delta p$: pérdida de carga de un circuito [Pa]. Referencia: ~98 en la pila.
- $L_c$: largo de un circuito [m]. Referencia: 2,55 por serpentina.
- $\sum K$: suma de coeficientes de pérdidas localizadas [adimensional]. Referencia: 0,6 por curva de 180°.
- $u$: velocidad media [m/s]. Referencia: 5,2.

### F5.10 Factor de forma de una caja aislada (IE)

**Descripción.** Conductancia de las paredes de una caja aislada. Usa el factor de forma de conducción (paredes, aristas y vértices) en serie con la convección y la radiación exteriores.

$$
S_i = \frac{6\,a_i^2}{t_i} + 12\cdot0{,}54\,a_i + 8\cdot0{,}15\,t_i,
\qquad
UA_w = \left[\sum_i \frac{1}{k_i(\bar T_i)\,S_i} + \frac{1}{\sum_j (h_{ext,j} + h_{rad,j})\,A_j}\right]^{-1}
$$

**Parámetros:**

- $S_i$: factor de forma de conducción de la capa $i$ [m].
- $a_i$: lado interior de la capa [m]. Referencia: 0,377.
- $t_i$: espesor de la capa [m]. Referencia: 0,20.
- $k_i(\bar T_i)$: conductividad de la capa a su temperatura media [W/(m·K)].
- $A_j$: área exterior de cada cara [m²].
- $UA_w$: conductancia de las paredes [W/K]. Referencia: 0,291.

> [!note] Por qué no alcanza la pared plana
> Si la aislación es gruesa respecto del lado del lecho, las aristas y los vértices pesan: con 20 cm sobre 38 cm, la pared plana subestima ~39 % de las pérdidas.

### F5.11 Puentes térmicos y conductancia total

**Descripción.** Conductancia de los elementos que atraviesan la aislación, modelados como barras, y conductancia total del módulo.

$$
UA_b = \frac{1}{t}\sum_b n_b\,(kA)_b,
\qquad
UA = UA_w + UA_b
$$

**Parámetros:**

- $UA_b$: conductancia de los puentes térmicos (cota superior) [W/K]. Referencia: 0,087 (23 % de las pérdidas).
- $t$: espesor de aislación que atraviesan [m]. Referencia: 0,20.
- $n_b$: cantidad de elementos de cada tipo [adimensional]. Referencia: 2 tubos, 9 vainas, 6 termocuplas, 4 apoyos.
- $(kA)_b$: conductividad × sección conductora de cada elemento [W·m/K]. Referencia: tubo 32 × 1,5 AISI 304: 2,6·10⁻³.

### F5.12 Conductividad equivalente de una cámara de aire (IE)

**Descripción.** Conductividad equivalente de una cámara de aire con conducción y radiación entre sus caras. Sirve para decidir si una capa de aire puede reemplazar aislante.

$$
k_{eq} \approx k_a + 4\,\sigma\,\bar T^3\,\frac{e}{2/\varepsilon - 1}
$$

**Parámetros:**

- $k_{eq}$: conductividad equivalente de la cámara [W/(m·K)]. Referencia: 0,23–0,43 a 200 °C con $\varepsilon$ = 0,9.
- $e$: espesor de la cámara [m]. Referencia: 0,01–0,02.
- $\bar T$: temperatura media de la cámara [**K**].
- $\varepsilon$: emisividad de las superficies [adimensional]. Referencia: 0,9 oxidada; 0,1 lámina de aluminio.

### F5.13 Descarga con modelo concentrado (para planilla, paso explícito)

**Descripción.** Enfriamiento de la arena durante la descarga, integrado paso a paso (Euler explícito) con la potencia de la cama y las pérdidas. Permite armar la curva de descarga en una planilla.

$$
T_s^{\,n+1} = T_s^{\,n} - \frac{\Delta t\,\big[P_{cama} + UA\,(T_s^{\,n} - T_{inv})\big]}{\varphi_u\,m\,c_p(T_s^{\,n})}
$$

**Parámetros:**

- $T_s^{\,n}$: temperatura media de la arena en el paso $n$ [K]. Referencia: arranca en ~287 °C.
- $\Delta t$: paso de tiempo [s]. Referencia: 600–1800.

> [!note] Fin de la descarga útil
> La descarga útil termina cuando $T_s$ llega a $T_{min}$ (F5.3). Con $\Delta t$ de hasta 30 min el error es chico, porque $\tau$ ≫ $\Delta t$.

### F5.14 Presión del material granular (Janssen, IE)

**Descripción.** Presión lateral y vertical del material granular sobre el contenedor, con la fricción contra las paredes incluida (Janssen).

$$
\sigma_h(z) = \frac{\rho_b\,g\,D_h}{4\,\mu_w}\left(1 - e^{-4\mu_w K z/D_h}\right),
\qquad
K = 1 - \sin\phi,
\qquad
\sigma_v = \frac{\sigma_h}{K}
$$

**Parámetros:**

- $\sigma_h$, $\sigma_v$: presión horizontal sobre las paredes y vertical [Pa]. Referencia: ~2,0 kPa y ~4,3 kPa en el fondo.
- $z$: profundidad desde la superficie libre [m]. Referencia: 0–0,38.
- $D_h$: diámetro hidráulico ($4A/P$; para sección cuadrada, $= a$) [m]. Referencia: 0,377.
- $\mu_w$: coeficiente de fricción arena–pared [adimensional]. Referencia: 0,35 (supuesto).
- $K$: coeficiente de empuje de Jaky [adimensional]. Referencia: 0,47.
- $\phi$: ángulo de fricción interna de la arena [°]. Referencia: 32 (supuesto).

> [!note] Cota simple
> Sin fricción, $\sigma_h \le K\,\rho_b\,g\,z$: es conservador y alcanza para un prototipo chico.

### F5.15 Flexión de una pared cuadrada (Roark, IE)

**Descripción.** Tensión y flecha máximas de una pared cuadrada simplemente apoyada bajo presión uniforme. Verifica el espesor de chapa.

$$
\sigma_{max} = \beta\,\frac{p\,b^2}{e^2},
\qquad
w_{max} = \alpha\,\frac{p\,b^4}{E\,e^3}
$$

**Parámetros:**

- $\sigma_{max}$: tensión de flexión máxima [Pa]. Referencia: 28 MPa con 2 mm.
- $w_{max}$: flecha máxima [m]. Referencia: 1,7 mm con 2 mm.
- $p$: presión uniforme sobre la pared [Pa]. Referencia: 2,8 kPa (sin fricción).
- $b$: lado de la pared [m]. Referencia: 0,38.
- $e$: espesor de la chapa [m]. Referencia: 0,002.
- $E$: módulo de elasticidad del acero a ~300 °C [Pa]. Referencia: 1,8·10¹¹.
- $\beta$, $\alpha$: coeficientes de placa cuadrada simplemente apoyada (ν = 0,3) [adimensional]. Referencia: 0,2874 y 0,0444.

### F5.16 Dilatación térmica diferencial (IE)

**Descripción.** Movimiento relativo entre el contenedor y la arena por la diferencia de dilatación, y dilatación libre de la pared en el ciclo. Define las holguras.

$$
\Delta a = a\,\lvert\alpha_w - \alpha_s\rvert\,\Delta T,
\qquad
\Delta a_{libre} = a\,\alpha_w\,\Delta T
$$

**Parámetros:**

- $\Delta a$: movimiento relativo entre pared y arena [m]. Referencia: 0,05 mm con acero al carbono.
- $\Delta a_{libre}$: dilatación libre de la pared [m]. Referencia: 1,3 mm entre 20 y 300 °C.
- $\alpha_w$, $\alpha_s$: coeficientes de dilatación de la pared y de la arena [1/K]. Referencia: sección 0.
- $\Delta T$: salto de temperatura del ciclo [K]. Referencia: 280.

### F5.17 Peso y presión sobre el piso

**Descripción.** Peso total del módulo y presión que transmite al piso.

$$
W = g\left(m + m_{ch} + m_{ais} + m_{ext} + m_{int}\right),
\qquad
p_{piso} = \frac{W}{A_{huella}}
$$

**Parámetros:**

- $W$: peso total del módulo [N]. Referencia: ~1,8 kN (≈ 180 kg).
- $m_{ch}$: masa de la chapa interior [kg]. Referencia: 13,5.
- $m_{ais}$: masa de la aislación ($\rho \approx$ 120 kg/m³) [kg]. Referencia: 50.
- $m_{ext}$: masa de la carcasa exterior [kg]. Referencia: 23.
- $m_{int}$: masa de tubos, vainas y resistencias [kg]. Referencia: ~11.
- $A_{huella}$: área de apoyo [m²]. Referencia: ~0,6.
- $p_{piso}$: presión sobre el piso [Pa]. Referencia: ~2,9 kPa.

---
## Cap 6. Indicadores para verificar un ensayo o una simulación [6]

### F6.1 Indicadores de almacenamiento y descarga

**Descripción.** Indicadores de eficiencia de un ensayo o una simulación. Miden qué fracción de la energía entregada queda almacenada, qué fracción de la descarga sale útil y cuál es la eficiencia diaria.

$$
SR = \frac{E_{nett}}{E_{in}},
\qquad
DR = \frac{E_{out}}{E_{out} + E_{loss}},
\qquad
\eta_{alm} = \frac{E_{out,24h}}{E_{in,24h}}
$$

**Parámetros:**

- $SR$: relación de almacenamiento [adimensional]. Referencia: 0,61–0,85 en Homa et al. [9].
- $E_{nett}$: energía neta almacenada (aumento de energía interna) [J].
- $E_{in}$: energía eléctrica entregada a las resistencias [J].
- $E_{out}$: energía extraída por el aire [J].
- $E_{loss}$: energía perdida por la envolvente [J].

### F6.2 Cierre del balance de energía

**Descripción.** Error de cierre del balance de energía. Verifica la consistencia de las mediciones de un ensayo o de una simulación.

$$
\epsilon_E = \frac{E_{in} - E_{out} - E_{loss} - \Delta U}{E_{in}},
\qquad
\Delta U \approx m\,\Delta h(T_{s,0}, T_{s,f})
$$

**Parámetros:**

- $\epsilon_E$: error relativo del balance [adimensional]. Referencia: < 0,5 % en simulación; en un ensayo depende de la instrumentación.
- $\Delta U$: variación de energía interna de la arena (y de la aislación, si se puede estimar) [J].
- $T_{s,0}$, $T_{s,f}$: temperatura media de la arena al inicio y al final [K].

> [!note] Uso en el prototipo
> Con 3 o más termocuplas en la arena y medición de la potencia eléctrica y del caudal y las temperaturas del aire, F6.1 y F6.2 permiten evaluar un ensayo sin simulación.

---
## Referencias
1. *Capítulo 1. Introducción, objetivo y alcance*. [[Cap 1 - Introduccion, objetivo y alcance]]
2. *Capítulo 2. Estado del arte y matriz comparativa*. [[Cap 2 - Estado del arte y matriz comparativa]]
3. *Capítulo 3. Fundamentos físicos, propiedades y modelos matemáticos*. [[Cap 3 - Fundamentos físicos, propiedades y modelos matemáticos]]
4. *Capítulo 4. Ingeniería conceptual: alternativas y selección*. [[Cap 4 - Ingenieria conceptual, alternativas y seleccion]]
5. *Capítulo 5. Ingeniería básica: predimensionamiento*. [[Cap 5 - Ingenieria basica, predimensionamiento]]
6. *Capítulo 6. Modelo térmico y plan de simulación*. [[Cap 6 - Modelo termico y plan de simulacion]]
7. *Properties of granular materials as heat transfer and storage medium in CSP application* (2015). [[Properties of granular materials as heat transfer and storage medium in CSP application]]
8. Tetteh et al. *Improved effective thermal conductivity of sand bed in thermal energy storage systems* (2024). [[Improved effective thermal conductivity of sand bed in thermal energy storage systems]]
9. Homa et al. *Numerical analysis of the prototype of the high-temperature thermal energy storage based on sand bed* (2025). [[Numerical analysis of the prototype of the high-temperature thermal energy storage based on sand bed]]
10. *Experimental determination and finite element modeling of thermal conductivity in moist sand* (2026). [[Experimental determination and finite element modeling of thermal conductivity in moist sand]]
