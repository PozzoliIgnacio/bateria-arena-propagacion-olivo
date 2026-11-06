---
Titulo esp.: "Baterías de arena para almacenamiento de energía térmica: una revisión de principios operativos, tecnologías, desafíos y perspectivas futuras"
Año: 2026
Padre: "[[CUDAR - Desarrollo de Pila de Arena]]"
Importancia:
  - A
URL: https://www.mdpi.com/2571-8797/8/5/165
---
## 1. Idea Central
El paper  es una **revisión crítica y multidimensional** de las baterías térmicas de arena para almacenamiento de energía térmica de alta temperatura. Su objetivo es sintetizar principios de operación, materiales granulares, configuraciones, desempeño térmico, modelado CFD/IA, aspectos económicos, ambientales, de seguridad, confiabilidad y comercialización, conectando trade-offs entre ellos. 
La conclusión fundamental es que la tecnología es **técnicamente prometedora y relativamente madura para calor de distrito y calor industrial** —especialmente el lecho empacado de arena de alta temperatura, con TRL 8–9—, pero aún presenta brechas importantes: baja conductividad térmica de la arena, degradación de la termoclina, pérdidas en almacenamiento prolongado, costos iniciales altos, dependencia de electricidad renovable barata, falta de datos comerciales de largo plazo y validación limitada de IA/gemelos digitales en sistemas comerciales. El texto no reporta experimentos propios: es una revisión estructurada basada en literatura, principalmente 2016–2026.
## 2. **Resumen por Secciones**
### 2.1. Introducción
Plantea que el almacenamiento térmico es clave para la descarbonización porque el calor representa cerca del **50% del consumo final mundial de energía**. Las baterías de arena almacenan calor sensible a alta temperatura usando arena u otros materiales granulares; son atractivas por bajo costo, disponibilidad, estabilidad térmica y larga vida útil, pero enfrentan baja conductividad térmica, pérdidas térmicas, degradación de termoclina y optimización del intercambio de calor. La revisión busca integrar aspectos técnicos, operativos, económicos, ambientales, de seguridad, confiabilidad, optimización y digitalización.
### 2.2. Materiales y Métodos
Revisión estructurada de literatura bajo **PRISMA 2020**. Bases: Scopus, Web of Science, SpringerLink, MDPI, IEEE Xplore, ScienceDirect y Google Scholar. Énfasis en publicaciones 2016–2026. Criterios de inclusión: publicaciones peer-reviewed, TES en arena/materiales granulares, aspectos técnicos/económicos/ambientales/operativos, resultados experimentales, modelos numéricos o revisiones, en inglés. Se excluyeron trabajos sin datos técnicos o sin credibilidad científica. El análisis fue cualitativo y clasificado por áreas: principios, materiales, experimentos, CFD, conductividad, termoclina, economía, ambiente, IA/ML/gemelos digitales y desarrollo futuro. **Limitación declarada:** no hay mediciones experimentales ni simulaciones originales; muchos datos provienen de prototipos y plantas piloto, con datos comerciales limitados.
### 2.3. Resultados
#### 2.3.1. Materiales granulares
- Los materiales estudiados se dividen en: minerales naturales (arena de cuarzo), materiales derivados de la construcción (arena de construcción), subproductos industriales (arena de fundición, escorias), minerales de rocas y medios compuestos/diseñados (arena modificada con aluminio o grafito).
- La arena de cuarzo es el medio natural más establecido; la arena de fundición y residuos pueden reducir costos y apoyar economía circular, pero requieren evaluar composición, contaminantes y estabilidad térmica. 
- Las modificaciones con aluminio, grafito u otros aditivos buscan aumentar la conductividad efectiva.
#### 2.3.2. Principio de operación
Tres fases: **carga, almacenamiento y descarga**.
- **Carga:** electricidad excedente de renovables alimenta calentadores eléctricos que calientan aire; el aire transfiere calor a la arena. Temperaturas reportadas: **500–1000 °C**; sistemas comerciales finlandeses: **500–600 °C**.
- **Almacenamiento:** calor retenido en partículas de arena dentro de tanque aislado. La energía almacenada se calcula como calor sensible.
- **Descarga:** aire frío pasa por arena caliente, absorbe calor y luego calienta agua, vapor o aire de proceso mediante intercambiador. 

Ecuaciones clave:
$$
E_{el} \rightarrow E_{th}
$$
Conversión casi completa de electricidad en calor; $E_{el}$ es energía eléctrica de entrada y $E_{th}$ energía térmica almacenada.
$$
Q = m \cdot c_p \cdot \Delta T
$$
- $Q$: calor almacenado [J].
- $m$: masa de arena [kg].
- $c_p$: capacidad calorífica específica [J/(kg·K)].
- $\Delta T$: cambio de temperatura [K].
#### 2.3.3. Tipos de tecnologías
Se describen configuraciones solapadas:

- **Lecho empacado fijo:** tanque con arena inmóvil y aire forzado circula por los poros entre los granos mediante tuberías perforadas, canales e intercambiadores. 
	- Ventajas: Simple, barato, confiable; baja conductividad y transferencia lenta. Es la mas comun
	- Desventajas: baja conductividad térmica efectiva y transferencia de calor lenta 
![[Sand Batteries for Thermal Energy Storage - A Review of Operating Principles, Technologies, Challenges and Future Perspectives-1793684267928.webp]]

- **Lecho empacado con termoclina:** un solo tanque contiene las zonas calientes y fría separadas por un frente con fuerte gradiente térmico (termoclina). Durante la carga el frente desciende, durante la descarga asciende
	- Menor costo e impacto que dos tanques
	- La conducción axial y la dispersión degradan la termoclina con el tiempo, ensanchando la zona de transición y reduciendo la energía útil recuperable 
	- En el diseño con termoclina se busca que el gradiente sea delgado, estable y movil (baja durante la carga y sube durante la descarga)
		- La estabilidad de esa capa define cuanta energia util se puede recuperar, si la termoclina se engrosa la diferencia de T entre la zona caliente y la fria se reduce por lo que se pierde calidad energetica 
	- *Todo lecho empaquetado desarrolla una termoclina durante la carga y descarga, la diferencia es que en este tipo de lecho el sistema esta diseñado para explotar esa estratificacion*
![[Sand Batteries for Thermal Energy Storage - A Review of Operating Principles, Technologies, Challenges and Future Perspectives-1793684303436.webp]]

- **Lecho fluidizado:** Aire inyectado a alta velocidad suspende las particulas de arena, haciendolas comportarse como un fluido
	- alta transferencia y temperatura uniforme, carga/descarga rapida 
	- mayor consumo de ventiladores, abrasión de las particulas  y complejidad mecanica.
![[Sand Batteries for Thermal Energy Storage - A Review of Operating Principles, Technologies, Challenges and Future Perspectives-1793684331083.webp]]

- **Lecho móvil:** la arena circula mecánica (mediante tornillos sin fin por ejemplo) desde una zona de calentamiento a un tanque de almacenamiento y luego a un intercambiador. *Es decir que la arena fria entra en la zona de calentamiento, se calienta, se transfiere a un tanque, la arena pasa por un intercambiador de calor donde transfiere calor*
	- Operación continua e independiente del flujo de arena y fluido. Ideal para T>600
	- Desventajas: complejidad mecánica y desgaste de partes moviles
![[Sand Batteries for Thermal Energy Storage - A Review of Operating Principles, Technologies, Challenges and Future Perspectives-1793684348276.webp]]

- **Híbrido arena + PCM:** combinan el calor sensible de la arena con el calor latente de cambio de fase (PCM) encapsulados para aumentar la densidad de energía volumétrica
	- Dado que la arena opera a alta T (>500°C), la zona del PCM debe estar separada térmicamente o controlada de forma independiente para no degradar el PCM ni sobrepasar su punto de fusión. 
	- combina calor sensible y latente; aumenta densidad energética, pero requiere compatibilidad térmica y separación térmica; el PCM debe mantenerse dentro de su rango admisible.
	- En la imagen se ve la camara superior de arena a alta temperatura, la barrera aislante intermedia y la camara inferior con capsulas de PCM e intercambiador aire-liquido
![[Sand Batteries for Thermal Energy Storage - A Review of Operating Principles, Technologies, Challenges and Future Perspectives-1793684363068.webp]]

- **Arena con conductividad mejorada:** aditivos metálicos, grafito, aletas o intercambiadores mejorados.
#### 2.3.4. Comparación de desempeño
El paper advierte que **eficiencia térmica** y **eficiencia eléctrica de ida y vuelta** no son equivalentes. Para baterías de arena, la eficiencia térmica describe retención/recuperación de calor; para baterías eléctricas, la eficiencia suele ser electricidad→electricidad. Por eso las tablas comparativas no deben leerse como ranking directo.

Ecuaciones:
**$q_{th}$ Densidad energética térmica [J/m³ o kWh/m³].**
$$
q_{th} = \frac{Q_{th}}{V} = \frac{m c_p \Delta T}{V} = q_{bulk} c_p \Delta T
$$
- $Q_{th}$: energía térmica almacenada (total).
- $V$: volumen de almacenamiento.
- $q_{bulk}$: densidad aparente del lecho empacado.
 **Densidad de energía eléctrica $e_{el}$** [kWh/m³].
$$
e_{el} = \frac{E_{el}}{V_{sys}}
$$
- $E_{el}$: energía eléctrica almacenada/entregada.
- $V_{sys}$: volumen del sistema definido.
**Eficiencia de conversion de carga $\eta_{ch}$ e Insumo electrico $E_{el,in}$**
$$
\eta_{ch} = \frac{Q_{th}}{E_{el,in}}
$$
- $\eta_{ch}$: fracción de electricidad de entrada convertida en calor almacenado. Normalmente entre 95 y 99%
- $E_{el,in}$: electricidad de entrada. Electricidad consumida durante el calentamiento
$$
E_{el,in} = \frac{Q_{th}}{\eta_{ch}}
$$
La densidad térmica de una batería de arena **no debe interpretarse directamente** como densidad eléctrica equivalente.
#### 2.3.5. Madurez tecnológica, TRL (Technology Readiness Level)
TRL es una escala estandarizada que se usa para medir que tan desarrollada esta una tecnologia en su camino dsede la investigacion basica hasta su implementacion comercial. 
TRL 1-3 corresponden a una investigacion temprana y desarrollo de laboratorio, TRL 4-6 a validacion tecnologica, desarrollo piloto y demostracion, y a TRL 7-9 a demostracion en entornos relevantes y aplicacaion comercial. 

| TRL   | Etapa                             | Qué significa en la práctica                                       |
| ----- | --------------------------------- | ------------------------------------------------------------------ |
| **1** | Investigación básica              | Solo principios físicos identificados; nada construido.            |
| **2** | Concepto tecnológico              | Se formula la idea o aplicación potencial.                         |
| **3** | Prueba de concepto                | Validación experimental a escala de laboratorio.                   |
| **4** | Validación en laboratorio         | Componentes integrados y probados en condiciones de laboratorio.   |
| **5** | Validación en entorno relevante   | El sistema se prueba en un entorno que se parece al real (piloto). |
| **6** | Demostración en entorno relevante | Prototipo completo probado en condiciones relevantes.              |
| **7** | Demostración en entorno operativo | Prototipo probado en condiciones reales de operación.              |
| **8** | Sistema completo y calificado     | Tecnología terminada y calificada; lista para operar.              |
| **9** | Aplicación comercial              | Tecnología probada en operación real y disponible comercialmente.  |

- Lecho empacado de alta temperatura (500-600): **TRL 8–9**, aplicaciones comerciales.
- Lecho con termoclina: **TRL 7–8**, demostración.
- Lecho móvil: **TRL 5–7**.
- Lecho fluidizado: **TRL 4–6**.
- Híbrido arena + PCM: **TRL 3–5**.
- Sistemas de recuperación eléctrica del calor: **TRL 3–5**.

La conversión electricidad→calor puede superar **95%**, pero calor→electricidad suele ser **25–45%**, con eficiencia global de ida y vuelta a menudo **<40%**.

*Los valores de TRL son una estimacion aproximada hecha por los autoroes*
#### 2.3.7. Modelado y optimización
Distingue tres niveles de evidencia:
1. **Estudios validados directamente en arena:** CFD comparado con experimentos en lecho empacado.
2. **Evidencia transferible:** resultados de sistemas TES granulares similares, no validación directa de baterías de arena.
3. **Aplicaciones propuestas/prospectivas:** IA, ML, PINN, mantenimiento predictivo y gemelos digitales aún no demostrados en baterías comerciales.

**CFD:** útil para campos de temperatura, termoclina y eficiencia; limitado por turbulencia, correlaciones de transferencia y conductividad efectiva; requiere validación experimental.

**IA/ML:** Para superar el costo computacional de CFD, se desarrollan *modelos surrogate* respaldados por MAchine Learning y redes neurales informadas por la fisica (PINNs).
	- **PINN en baterias de arena**: Ananth et al. entrenaron una red PINN con mediciones experimentales e incorporaron la ecuación de conducción de calor en la función de pérdida (_loss function_), logrando un $R^2 = 0.9616$ y un RMSE de $1.493^\circ\text{C}$ en la reconstrucción del campo de temperatura 3D
	- **Modelos hibridos Numerico-ML**: Resuelven modelos linealizados en mallas gruesas y aplican ML para aproximar la solución no lineal de alta resolución, acelerando los cálculos hasta **350 veces más rápido** con errores $\approx 0.16\%$.
	- se aplica a predicción, monitoreo, optimización, diagnóstico y mantenimiento. 
	- **Limitacion**: la falta de bases de datos operacionales de plantas comerciales limita el entrenamiento de modelos de Deep Learning puros, por ello es que se usan los PINNs (Physics-Informed Neural Networks), las cuales incorporan las leyes de conservacion de masa y energia directamente en la funcion de perdida del algoritmo. 

**Gemelos digitales:** integran CFD, IA, sensores y control para monitoreo en tiempo real, para predecir en tiempo real la estratificacion de la termoclina, las perdidas perimetrales y el estado de carga acumulado. 
![[Sand Batteries for Thermal Energy Storage - A Review of Operating Principles, Technologies, Challenges and Future Perspectives-1793687208366.webp]]
#### 2.3.9. Aspectos económicos
- El modelo LCCA (Analisis de costo de ciclo de vida) indica que la mayor parte del costo es **CAPEX** (tanque de acero, aislamiento, resistencias, intercambiadores, ventiladores); el **OPEX**  y mantenimiento es sumamente bajo porque la arena no sufre degradación química ni requiere reemplazo
- Vida útil estimada: **20–40 años**. 
- LCOH reportado: **20–70 USD/MWh**, pero suele ser costo asociado al almacenamiento y en algunos estudios **excluye la electricidad de carga**; no debe interpretarse como costo total del calor entregado.
**Costo de ciclo de vida global**
$$
LCC = CAPEX + OPEX + M + R + D
$$
- $CAPEX$: inversión.
- $OPEX$: operación.
- $M$: mantenimiento.
- $R$: reemplazo de componentes.
- $D$: desmantelamiento/disposición.

**Costo nivelado del calor**
$$
LCOH = \frac{\sum_t I_t + O_t + M_t}{Q_t/(1+r)^t}
$$

Tal como se presenta en el paper: $I_t$ inversión, $O_t$ costo operativo, $M_t$ mantenimiento, $Q_t$ calor producido, $r$ tasa de descuento. La comparación requiere declarar si incluye electricidad de carga, tasa de descuento, factor de utilización, ciclos anuales y vida útil.

Riesgos: dependencia de electricidad renovable barata, alta utilización requerida, pérdidas térmicas en almacenamiento estacional, costos de fin de vida bajos.
#### 2.3.10. Seguridad y confiabilidad
- **Incendio:** arena no combustible, pero el sistema completo puede tener riesgos eléctricos, sobrecalentamiento, fallas de aislamiento, superficies calientes y expansión térmica.
- **Explosión:** opera a presión atmosférica o muy baja; no almacena energía en medio altamente presurizado, pero pueden existir riesgos en componentes asociados.
- **Alta temperatura:** riesgo de sobrecalentamiento local, fatiga térmica, daño de aislamiento y quemaduras; requiere monitoreo, apagado automático y procedimientos.
- **Fin de vida:** desmontaje simple, sin electrolitos peligrosos.
- **Confiabilidad:** arena químicamente inerte y estable; no hay degradación electroquímica. La termoclina se degrada por conducción, dispersión y mezcla; el aislamiento y geometría son críticos. Partes mecánicas (ventiladores, intercambiadores, calentadores, aislamiento) son los puntos débiles. Buena resiliencia a cortes eléctricos y climas fríos.

#### 2.3.11. Desafíos de comercialización
1. **Alcance limitado:** Orientado principalmente a usos térmicos directos (calefacción urbana, procesos industriales); la reconversión a electricidad mediante turbinas reduce severamente la eficiencia global.
2. **Baja conductividad térmica:** La arena pura ($0.2-2.5\text{ W/(m}\cdot\text{K)}$) desacelera las tasas de carga y descarga.
3. **Degradación de la termoclina:** La conducción interna degrada el gradiente de temperatura durante periodos de espera prolongedos (_standby_).
4. **Baja densidad energetica**
#### 2.3.12. Discusión y conclusiones
**Resumen y Conceptos Clave:**
- **Mejoras en transferencia de calor:** La adición de virutas de aluminio a la arena incrementa la tasa máxima de transferencia de calor hasta en un **70%**.
- **Almacenamiento a Ultra-Alta Temperatura:** La investigación evoluciona hacia rangos de $800^\circ\text{C} - 1200^\circ\text{C}$ para descarbonizar industrias electro-intensivas (acero, cemento, vidrio y química).
- **Almacenamiento estacional:** Aunque prometedor para almacenar calor durante meses, aún requiere mayor validación experimental de pérdidas acumuladas y mantenimiento de la termoclina en ciclos anuales reales.
## 4. **Hallazgos Críticos**
- **La baja conductividad térmica de la arena ($0.2–2.5\ \mathrm{W\,m^{-1}K^{-1}}$)** limita la velocidad de carga/descarga y genera gradientes térmicos; es el principal cuello de botella técnico.
- **Geometría del Contenedor y Aislamiento Óptimo:** La relación volumen-superficie favorece a los tanques cilíndricos de gran escala, logrando tasas de autodescarga (_self-discharge_) **inferiores al 1% diario**.
- **La mejora con virutas de aluminio** puede aumentar la tasa máxima de transferencia de calor en aproximadamente **70%** frente a arena pura, según Tetteh et al.; también se exploran grafito, aletas, inserciones metálicas y compuestos.
- **La degradación de la termoclina** es un mecanismo dominante de pérdida durante el reposo; depende de geometría, tamaño de partícula, aislamiento y distribución de flujo. Un tanque más grande reduce pérdidas relativas por relación volumen/superficie, pero no elimina el problema.
- **El lecho empacado de alta temperatura es la configuración más madura:** TRL 8–9 y aplicaciones comerciales en calefacción de distrito; las configuraciones fluidizadas, móviles e híbridas con PCM siguen en laboratorio/piloto.
- **La IA y los gemelos digitales son prometedores pero no validados comercialmente:** los mejores resultados (PINN con $R^2=0.9616$; modelo híbrido con error ~0.16% y ~350× más rápido) provienen de lechos empacados de arena manufacturada o PBTES, no de baterías comerciales.
- **Las comparaciones de eficiencia deben manejarse con cuidado:** eficiencia térmica de batería de arena ≠ eficiencia eléctrica de ida y vuelta de baterías de litio. El paper insiste en declarar límites del sistema.
- **Ventajas ambientales claras:** ausencia de metales críticos, electrolitos peligrosos y emisiones directas en operación; arena reutilizable y acero reciclable. Pero persisten impactos por acero, aislamiento y minería de arena.
- **La seguridad es favorable pero no absoluta:** baja presión y medio no combustible reducen riesgos catastróficos, pero existen riesgos térmicos, eléctricos y mecánicos que deben evaluarse caso a caso.
- **El almacenamiento estacional verdadero no está demostrado comercialmente:** retener calor días o semanas no equivale a suministro útil continuo durante meses; faltan datos de pérdidas acumuladas, energía recuperada y ciclos reales.