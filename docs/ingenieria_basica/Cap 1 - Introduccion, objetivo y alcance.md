---
Titulo: "Capítulo 1. Introducción, objetivo y alcance"
Año: 2026
Padre: "[[CUDAR - Desarrollo de Pila de Arena]]"
Tipo:
  - Informe
Estado:
  - Haciendo
---
# Capítulo 1. Introducción, objetivo y alcance
## 1.1 Contexto 
El proyecto se aplica a la propagación de olivo por **enraizamiento de esquejes bajo nebulización en cama caliente**, un método de reproducción asexual. Para que un esqueje forme raíces adventicias hay que controlar dos variables:
- **Humedad foliar.** La mantienen microaspersores, que evitan la deshidratación del esqueje y limitan la proliferación de hongos.
- **Temperatura del sustrato.** El sustrato se calefacciona para estimular el enraizamiento y compensar las variaciones del clima exterior.

Las condiciones térmicas que fija el proyecto son las siguientes:

| Variable | Valor | Efecto |
|---|---|---|
| Aire confinado bajo el cobertor | $\le 30\ ^\circ\text{C}$ | Por encima aumentan la respiración y la transpiración, el esqueje puede marchitarse y el sistema activa la nebulización más seguido |
| Temperatura en la zona de raíces | $< 20\ ^\circ\text{C}$ retrasa la brotación de raíces | Fija el piso térmico que debe sostener la calefacción |
| Invernadero | $10$ a $35\ ^\circ\text{C}$ garantizados | Permite regular la atmósfera confinada |
| Exterior (NOA/Cuyo) | $-9{,}2$ a $47\ ^\circ\text{C}$ | Perturbación sobre el invernadero y, a través de él, sobre la cama |

Estas cifras definen la **ventana de trabajo del sustrato, entre 20 y 30 °C**. También muestran que la calefacción tiene que ser **regulada**: sobrecalentar la cama es tan perjudicial como dejarla fría.
## 1.2 Sistema actual
La instalación actual tiene **dos mesas de propagación de 1 m²** cada una, protegidas con un cobertor. Se usan dos para comparar el enraizamiento de distintas variedades de olivo. Cada mesa tiene un sistema de riego por microaspersión: dos microaspersores por mesa, una bomba monofásica de 0,5 HP, un tanque de 40 L y electroválvulas para dirigir el agua a cada cama.
La calefacción del sustrato es eléctrica directa [1]:

| Parámetro | Valor |
|---|---|
| Elemento calefactor | Resistencia eléctrica flexible embebida en el sustrato |
| Potencia lineal | $q' = 20\ \text{W/m}$ |
| Longitud por mesa | $L = 8{,}70\ \text{m}$ |
| Temperatura máxima del elemento | $60\ ^\circ\text{C}$ |
| Alimentación | 220 V, 50 Hz, monofásica |
| Regulación | Control de fase con TRIAC |

La potencia nominal por mesa es:
$$
P_{nom} = q' \cdot L = 20\ \tfrac{\text{W}}{\text{m}} \times 8{,}70\ \text{m} = 174\ \text{W}
$$
donde $P_{nom}$ [W] es la potencia máxima que puede disipar la resistencia de una mesa de 1 m², $q'$ [W/m] la potencia por metro lineal y $L$ [m] la longitud del elemento.

El TRIAC recorta la onda senoidal y así baja la tensión eficaz aplicada:
$$
P = \frac{V_{RMS}^2}{R}
$$
donde $P$ [W] es la potencia disipada, $V_{RMS}$ [V] la tensión eficaz después del recorte y $R$ [Ω] la resistencia eléctrica del elemento. En consecuencia, **174 W es un máximo y no la demanda real**: el controlador entrega en cada instante la fracción que pide la temperatura del sustrato. Esto pesa en el dimensionamiento. La energía de una noche es:
$$
E_{noche} = \int_0^{t_n} P_{cama}(t)\, dt = \bar{f}\, P_{nom}\, t_n, \qquad 0 < \bar{f} \le 1
$$
> [!warning] hay que determinar este valor de factor de uso 

donde $E_{noche}$ [J] es la energía térmica que necesita la cama durante la noche, $P_{cama}(t)$ [W] la potencia instantánea demandada, $t_n$ [s] la duración de la noche de diseño y $\bar{f}$ [–] el factor de uso medio (potencia media sobre potencia nominal). Con los datos disponibles solo se puede fijar una **cota superior**, la que corresponde a $\bar{f} = 1$ con $t_n \approx 14\ \text{h}$:
$$
E_{noche} \le P_{nom}\, t_n = 174\ \text{W} \times 14\ \text{h} \approx 2{,}44\ \text{kWh} \approx 8{,}77\ \text{MJ}
$$
El valor real de $\bar{f}$ sale del balance térmico de la cama (capítulo 3) o de registros del sistema actual. Todo lo que se dimensione con $\bar{f} = 1$ queda del lado de la seguridad.
## 1.3 Problema y justificación del almacenamiento térmico
El sistema funcionó en laboratorio, pero **depende de la red eléctrica**, y muchas zonas rurales no tienen un suministro estable [1]. Con energía fotovoltaica aparece un desfase: el panel genera de día y la cama necesita calor de noche. El problema es **trasladar energía del día a la noche**.

Cualquier alternativa termina en calor entregado al sustrato. Las dos cadenas de conversión son:
- **Con batería de litio:** FV → batería (electroquímica) → resistencia de la cama → calor.
- **Con pila de arena:** FV → resistencias en la arena → calor sensible almacenado → extracción → calor en la cama.
Para entregar la misma $E_{noche}$, la energía diaria que cada alternativa le pide al panel es:
$$
E_{FV}^{\,Li} = \frac{E_{noche}}{\eta_{rt}}, \qquad E_{FV}^{\,arena} = \frac{E_{noche}}{\eta_{alm}}
$$
donde $\eta_{rt}$ [–] es la eficiencia eléctrica de ida y vuelta de la batería y $\eta_{alm}$ [–] la eficiencia térmica del acumulador en el ciclo diario:
$$
\eta_{alm} = \frac{E_{entregada}}{E_{carga}} = 1 - \frac{E_{perd,24h}}{E_{carga}}
$$
con $E_{carga}$ [J] la energía eléctrica convertida en calor dentro de la arena, $E_{entregada}$ [J] el calor que llega a la cama y $E_{perd,24h}$ [J] las pérdidas por la envolvente durante las 24 h del ciclo. La conversión electricidad → calor en una resistencia es prácticamente total, así que en la cadena de la arena todas las pérdidas son térmicas.
Se desprenden dos consecuencias:
1. **Las bajas eficiencias de la literatura no aplican.** Los 47,4 % [4] y los 20–35 % [5] reportados para baterías de arena incluyen la reconversión de calor a electricidad, que acá no existe. Una eficiencia térmica no se compara con una eléctrica de ida y vuelta [3].
2. **La arena no gana por eficiencia.** El litio tiene $\eta_{rt}$ de 80–95 % [4] [5] . Si $\eta_{alm} < \eta_{rt}$, la pila le pide más energía diaria al panel que una batería de litio. Su ventaja está en el costo, la vida útil y los materiales:

| Aspecto                    | Arena                                                                 | Ion-litio                          | Ref.      |
| -------------------------- | --------------------------------------------------------------------- | ---------------------------------- | --------- |
| Vida útil                  | 20–50 años                                                            | 10–20 años                         | [3][4][5] |
| Costo de inversión         | 69 $/kWh, 6 veces menos que litio en 2020                             | Referencia                         | [4]       |
| Mantenimiento y materiales | OPEX muy bajo; sin materiales críticos                                | Litio y cobalto, riesgo de escasez | [3][4]    |
| Seguridad                  | No combustible, presión atmosférica; riesgo por superficies calientes | Electrolitos peligrosos            | [3]       |
| Densidad energética        | 10–15 kWh/m³                                                          | 200–250 kWh/m³                     | [5]       |


> [!warning] Alcance de las cifras de costo
> - Las cifras de costo corresponden a otras escalas y alcances: 88 kWh con motor Stirling y un sistema residencial con reconversión a electricidad. 
> - Sirven como tendencia, no como estimación para este módulo. 

La tecnología está madura a escala comercial: el lecho empacado alcanza TRL 8–9 en calefacción de distrito, y los sistemas finlandeses (Polar Night Energy) operan a 500–600 °C [3]. Frente al agua, que a presión atmosférica no supera los 100 °C, la arena admite un salto térmico mucho mayor. 

Las desventajas que el diseño tiene que resolver son:
- **Baja conductividad** (0,2–2,5 W/m·K): la carga y la descarga son lentas [3].
- **Baja densidad energética:** condiciona dónde se ubica el módulo. Ocupa mas volumen que una batería para la misma energía
- **Pérdidas en un equipo chico:** la autodescarga menor al 1 % diario corresponde a tanques grandes [3]. Como $A/V \propto V^{-1/3}$, un módulo por m² tiene proporcionalmente más superficie de pérdida. **Es el problema central del proyecto.**
## 1.5 Objetivos
**Objetivo general del proyecto.** Incorporar al sistema de propagación existente un sistema híbrido de generación fotovoltaica y acumulador térmico de arena que permita operar de forma autónoma, sin red eléctrica ni baterías químicas [1]. El acumulador convierte los excedentes fotovoltaicos diurnos en calor, lo almacena y lo transfiere de noche al sustrato de las camas 

**Objetivo general del subsistema mecánico.** Diseñar, calcular, simular y construir el acumulador de arena y su subsistema de extracción y control. Debe almacenar de forma segura la energía fotovoltaica y entregar de noche al sustrato una potencia equivalente a la de la resistencia actual (174 W por mesa).

**Objetivos específicos del subsistema mecánico**:

| N.º | Objetivo específico                                                                                                                                            | Meta             |
| --- | -------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------- |
| OE1 | Traducir los objetivos en requerimientos medibles y definir el caso de diseño (demanda térmica nocturna de una mesa de 1 m²)                                   | Diseño           |
| OE2 | Relevar el estado del arte y elegir, con criterios explícitos, la configuración del lecho, el método de extracción, la escala y la ubicación del módulo        | Diseño           |
| OE3 | Definir el modelo físico y las propiedades de la arena en función de la temperatura                                                                            | Cálculo          |
| OE4 | Predimensionar masa de arena, rango de temperaturas, aislación, resistencias, extracción y contenedor, y calcular la energía diaria que se le pide al panel    | Cálculo          |
| OE5 | Diseñar un subsistema de extracción y control que regule la descarga y entregue al sustrato la potencia requerida, sin superar 60 °C en el elemento calefactor | Diseño y cálculo |
| OE6 | Construir el modelo numérico transitorio del módulo y validarlo contra resultados publicados                                                                   | Simulación       |
| OE7 | Especificar instrumentación, lógica de control y protecciones, y su interfaz con el subsistema electrónico                                                     | Diseño           |
| OE8 | Emitir la especificación técnica preliminar del módulo y el plan de ingeniería de detalle                                                                      | Diseño           |
| OE9 | Fabricar, montar y poner en marcha el primer módulo                                                                                                            | Construcción     |

## 1.5 Alcance
**Incluye:**
- **Pila final modular**: un módulo por mesa de 1 m², replicable para ampliar la superficie de propagación según el requerimiento de modularidad. Todo se dimensiona por m² y se muestra cómo escala.
- **Autonomía de una noche** (~14 h) con ciclo diario de carga, reposo y descarga.
- **Fuente de energía:** un panel FV cuya potencia es **dato de entrada**. El informe no elige el panel: entrega como resultado la energía diaria que necesita la pila, para quien lo seleccione.
- **Fases conceptual y básica** en un solo informe: requerimientos, estado del arte, fundamentos, arquitectura, selección de alternativas, predimensionamiento, plan de simulación, instrumentación, fabricación, costos y riesgos preliminares, y especificación.
- Fases conceptual y básica, con validación por cálculo y simulación contrastada con papers.
- Entorno definido por los rangos de 1.1. La localidad se incorpora más adelante.

**Excluye:**
- La selección del panel FV y de la electrónica: el informe entrega la energía diaria requerida y las interfaces.
- La ingeniería de detalle: CAD, planos, simulación detallada, construcción y ensayos.
- La autonomía de varios días (días nublados seguidos), que se trata como riesgo. .
- Los aspectos agronómicos.

La especificación anterior era un contenedor cúbico de 40 × 40 × 40 cm, es decir 0,064 m³ o unos 90–100 kg de arena. Ese tamaño no surgía de la demanda de la cama. Se decidió diseñar directamente la pila final.
	*Un prototipo de otro tamaño no reproduce la relacion A/V ni las perdidas del modulo real, por lo que no se diseña*
## 1.6 Ciclo de funcionamiento
### Esquema
![[Cap 1 - Introduccion, objetivo y alcance-1793828999007.webp]]
1. **Carga (día).** El panel alimenta primero los consumos del sistema de la cama (nebulización, control). El excedente se convierte en calor en resistencias embebidas en la arena, cuya temperatura sube hacia $T_{max}$.
2. **Reposo.** La arena guarda el calor como energía sensible. Las pérdidas por la envolvente siguen activas todo el tiempo, no solo de noche.
3. **Descarga (noche).** El sistema de extracción toma calor de la arena y lo lleva al sustrato. La regulación ajusta la potencia a la demanda y limita la temperatura del elemento a 60 °C. La arena se enfría hacia $T_{min}$.
4. **Control.** Mide la temperatura del sustrato y de la arena, y gobierna la carga (resistencias) y la descarga (caudal o mezcla). La carga y la descarga simultáneas, por ejemplo en días nublados o en el atardecer, se tratan como modo de operación en el capítulo 6.
### Planteo del problema de diseño
En régimen periódico la energía interna de la arena vuelve al mismo valor cada 24 h. Los balances del ciclo son:
$$
E_{FV} = E_{aux} + E_{carga} + E_{no\,aprov}
$$
$$
E_{carga} = E_{entregada} + E_{perd,24h}
$$
donde $E_{FV}$ [J] es la energía diaria que produce el panel, $E_{aux}$ [J] el consumo diario de los sistemas de la cama, $E_{carga}$ [J] la energía que entra a la arena, $E_{no\,aprov}$ [J] la energía FV que no puede aprovecharse (por ejemplo, con la pila ya cargada), $E_{entregada}$ [J] el calor que llega a la cama y $E_{perd,24h}$ [J] las pérdidas por la envolvente en el ciclo.

La energía útil almacenada entre los extremos de temperatura es:
$$
E_{util} = m \int_{T_{min}}^{T_{max}} c_p(T)\, dT \;\ge\; E_{noche} + E_{perd,noche}
$$
donde $m$ [kg] es la masa de arena, $c_p(T)$ [J/(kg·K)] su calor específico en función de la temperatura, $T_{max}$ y $T_{min}$ [K] las temperaturas al final de la carga y de la descarga, y $E_{perd,noche}$ [J] las pérdidas durante la descarga. Las pérdidas en cada instante son:
$$
\dot{Q}_{perd}(t) = \frac{T_{arena}(t) - T_{inv}(t)}{R_{env}}
$$
donde $\dot{Q}_{perd}$ [W] es la potencia perdida, $T_{arena}$ [K] la temperatura media de la arena, $T_{inv}$ [K] la temperatura del invernadero y $R_{env}$ [K/W] la resistencia térmica total de la envolvente, que depende del espesor y la conductividad de la aislación y del área exterior.

> [!note] Qué implican estas ecuaciones (sin fijar valores)
> - **El salto térmico es la variable dominante.** La masa necesaria es inversamente proporcional a $\int_{T_{min}}^{T_{max}} c_p\,dT$. Un salto chico exige mucha arena; uno grande, poca.
> - **$T_{min}$ tiene un piso fijado por los datos.** Para que la arena todavía pueda entregar calor, tiene que estar más caliente que el fluido de extracción, y este más caliente que el sustrato: $T_{min} > T_{fluido} > T_{sustrato}$, con $T_{sustrato}$ entre 20 y 30 °C. 
> 	- El límite de 60 °C se aplica al elemento que calienta el sustrato, no a la arena. Si la arena está por encima de 60 °C, la regulación tiene que limitar lo que se entrega. 
> 	- El valor exacto de $T_{min}$ depende del método de extracción (capítulos 7 y 8).
> - ** $T_{max}$ tiene techos de material.** La inversión α→β del cuarzo a 573 °C, con un pico de $c_p$ y un aumento de volumen, es un umbral de riesgo [6]. Los límites de aceros, aislantes y resistencias también acotan $T_{max}$ (capítulo 8.6).
> - **Subir $T_{max}$ tiene un costo.** Achica la masa y el área, pero aumenta el término $T_{arena} - T_{inv}$ de las pérdidas y exige materiales más caros. Bajar $T_{max}$ reduce esa diferencia, pero aumenta la masa y el área ($A \propto m^{2/3}$). Hay un compromiso que se resuelve con el estudio de $T_{max}$ del capítulo 8.2.
> - **El panel se dimensiona con todo el ciclo.** $E_{carga}$ tiene que cubrir $E_{noche}$ más las pérdidas de las 24 h, y $E_{FV}$ además tiene que cubrir $E_{aux}$. Ese requisito es la salida del informe hacia la selección del panel.

> [!warning] hace falta medir o estimar el consumo $E_{aux}$ 
## 1.7 Requerimientos

Cada requerimiento tiene un método de verificación: cálculo (C), simulación (S), inspección (I) o ensayo futuro (E). La estructura sigue [7].
### 1.7.1 Requerimientos generales

|ID|Requisito|Valor o criterio|Verif.|
|---|---|---|---|
|RG1|Costo mínimo|Dentro del límite del organismo de financiación [1]|C|
|RG2|Modularidad|Un módulo por m² de mesa; la superficie se amplía sumando módulos [1]|I|
|RG3|Adaptabilidad experimental|El acople térmico no debe impedir cambiar el sustrato ni la especie [1]|I|
|RG4|Autonomía de la red|La energía de carga proviene solo del panel FV|C|
|RG5|Fabricabilidad local|Materiales y componentes comerciales disponibles en el país|I|

### 1.7.2 Requerimientos funcionales térmicos

| ID  | Requisito                                        | Valor o criterio                                                                                                | Verif. |
| --- | ------------------------------------------------ | --------------------------------------------------------------------------------------------------------------- | ------ |
| RT1 | Potencia entregada al sustrato                   | $P_{entregada}(t) = P_{cama}(t)$, con $P_{cama} \le 174$ W por m²                                               | C, S   |
| RT2 | Energía nocturna                                 | $E_{noche}$ según la ec. (1.5)                                                                                  | C      |
| RT3 | Autonomía                                        | $t_n \approx 14$ h sin recarga                                                                                  | S      |
| RT4 | Temperatura del elemento calefactor del sustrato | $\le 60\ ^\circ\text{C}$ [1]                                                                                    | C, S   |
| RT5 | Temperatura del sustrato y del aire confinado    | Sustrato entre 20 y 30 °C; aire $\le 30$ °C, incluido el calor que pierda el módulo si se ubica junto a la cama | S, E   |
| RT6 | Rango de temperaturas de la arena                | Debe cumplir la ec. (1.8); $T_{max}$ y $T_{min}$ son variables de diseño (cap. 8)                               | C      |
| RT7 | Energía diaria requerida al panel                | Resultado de la ec. (1.6); dato de salida hacia quien elija el panel                                            | C      |
### 1.7.3 Requerimientos mecánico-estructurales y operativos

|ID|Requisito|Valor o criterio|Verif.|
|---|---|---|---|
|RM 1|Ambiente de uso|Interior de invernadero (10–35 °C) con humedad alta por nebulización: la arena debe quedar protegida de la humedad, y los materiales resistir la corrosión [1]|I|
|RM 2|Dimensiones y peso|Compatibles con el espacio junto a la mesa o debajo de ella|I|
|RM 3|Aislación térmica|Espesor y material que limiten $E_{perd,24h}$ según el objetivo de $\eta_{alm}$ y de temperatura superficial (cap. 8.5)|C, S|
|RM 4|Temperatura superficial exterior|Segura para el operario|C, S|
|RM 5|Resistencia de materiales|Aptos para $T_{max}$ y para el ciclado térmico diario|C|
|RM 6|Cargas estructurales|Peso de la arena ($\rho \approx 1400$ – $1600$ kg/m³ [8]) y presión lateral del material granular sobre paredes y fondo|C|
|RM 7|Dilatación térmica diferencial|Holguras entre lecho, contenedor y aislación para evitar fallas por expansión cíclica [8]|C|
|RM 8|Mantenibilidad|Poder reemplazar resistencias y sensores sin vaciar la arena|I|
|RM 9|Seguridad|Protección por sobretemperatura independiente del control; aislación eléctrica apta para ambiente húmedo [3]|I|

> [!warning] Datos faltantes: espacio, peso y temperatura superficial
> 
> - Hacen falta el espacio disponible junto a cada mesa o debajo de ella, y la carga que admite la estructura de la mesa o el piso (RM 2, RM 6).
> - Hay que definir la temperatura superficial máxima admisible, según la norma o el criterio de seguridad que se adopte (RM 4).
### 1.7.4 Indicadores de desempeño

|Indicador|Definición|Qué mide|
|---|---|---|
|Energía útil almacenada|$E_{util}$, ec. (1.7) [kWh]|Capacidad del módulo|
|Eficiencia térmica diaria|$\eta_{alm}$, ec. (1.4) [–]|Fracción de la carga que llega a la cama; la referencia de comparación es el $\eta_{rt}$ del litio|
|Fracción diaria de pérdidas|$\varphi = E_{perd,24h}/E_{util}$ [–]|Autodescarga del módulo|
|Cobertura de la demanda|$CD = E_{entregada}/E_{noche} \ge 1$, con el sustrato dentro de 20–30 °C durante $t_n$|Cumplimiento de la función principal|
|Densidad energética|$e_v = E_{util}/V_{ext}$ [kWh/m³], con $V_{ext}$ el volumen exterior incluida la aislación|Ocupación de espacio|
|Energía diaria requerida al panel|$E_{FV,req} = E_{aux} + E_{carga}$ [kWh/día]|Requisito para elegir el panel|
|Costo específico|$c_E = C_{modulo}/E_{util}$ [$/kWh]|Comparación con litio|
|Temperatura superficial máxima|$T_{sup,max}$ [°C]|Seguridad (RM4)|
## 1.8 Metodología
El trabajo sigue el esquema de tres niveles:

| Etapa          | Pregunta que responde                          | Entregables                                                                                                               |
| -------------- | ---------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------- |
| **Conceptual** | ¿Qué hay que resolver y con qué configuración? | Requerimientos, caso de diseño, estado del arte, arquitectura, matrices de selección                                      |
| **Básica**     | ¿De qué tamaño y con qué materiales? ¿Cumple?  | Memoria de cálculo, estudio de $T_{max}$, plan de simulación, instrumentación, costos, riesgos, especificación preliminar |
| **Detalle**    | ¿Cómo se fabrica y se verifica?                | Simulación detallada, CAD en CATIA, verificación estructural, planos, construcción y ensayos                              |

Criterios de trabajo que atraviesan todo el informe:
1. **Datos y variables de diseño separados.** Son datos solo los valores del documento del proyecto y de la tabla de decisiones. 
	- El **salto térmico, $T_{max}$, $T_{min}$, la masa, el espesor de aislación y la geometría se tratan como incógnitas**: se plantean las ecuaciones, se muestran sus implicaciones en todo el rango posible y se elige el valor con un criterio explícito.
2. **Validación escalonada:** estimación analítica (capítulo 8), simulación transitoria (capítulo 9) y contraste con resultados de prototipos publicados.
3. **Trazabilidad:** cada dato de literatura cita su ficha en la base de investigación, y cada requerimiento tiene un método de verificación.
## Cierre del capítulo

**Supuestos usados**
- S1. Los 174 W por mesa son la potencia **máxima** de la resistencia actual. Se usan como cota superior de la demanda ($\bar{f} = 1$) hasta que el capítulo 3 dé el valor real.
- S2. "Prototipo funcional" se interpreta como el primer módulo a escala real (a confirmar).
- S3. La energía FV se destina primero a los consumos de la cama y el excedente a la pila, según [[Introducción y Objetivos]].

**Datos faltantes**
- Motivo documentado de saltear el prototipo de laboratorio (1.6.3).
- Factor de uso real $\bar{f}$ de la resistencia en invierno (registros o capítulo 3).
- Consumo diario $E_{aux}$ de la cama: bomba de 0,5 HP, electroválvulas, control.
- Potencia del panel FV y localidad (horas solares pico de invierno).
- Confirmación de que la autonomía de varios días queda fuera de alcance.
- Límite de costo del organismo de financiación.

**Capítulos que dependen de este**
- Cap. 0: el resumen ejecutivo toma el objetivo y el alcance.
- Cap. 2: los requerimientos se derivan de los objetivos específicos y del alcance.
- Cap. 3: tiene que fijar $\bar{f}$ y $E_{noche}$.
- Cap. 6: los modos de operación parten del ciclo de 1.7.
- Cap. 8: resuelve el planteo de 1.7.2.
- Cap. 14: verifica el cumplimiento de OE1–OE8.
## Referencias
1. [[Introducción y Objetivos]]: documento del proyecto.
2. [[Cap 0 - Plan informe ingenieria conceptual y basica]]
3. [[Sand Batteries for Thermal Energy Storage - A Review of Operating Principles, Technologies, Challenges and Future Perspectives]] (2026)
4. [[Cost-effective Electro-Thermal Energy Storage to balance small scale renewable energy systems]]
5. [[Viabilidad tecnica y economica del uso de baterias de arena para el almacenamiento termico en el autoabastecimiento energetico residencial]]
6. [[Properties of granular materials as heat transfer and storage medium in CSP application]]
7. [[Desarrollo de una bateria de arena para almacenamiento de energia renovable en zonas rurales]] (2023)
8. [[Comenzar con un informe de ingeniera conceptual y basica]]