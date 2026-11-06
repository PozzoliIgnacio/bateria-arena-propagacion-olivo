---
Titulo: Plan del informe de ingeniería conceptual y básica de la pila de arena
Año: 2026
Padre: "[[CUDAR - Desarrollo de Pila de Arena]]"
Tipo:
  - Plan
Estado:
  - Por hacer
---
# Plan del informe de ingeniería conceptual y básica: pila de arena final

> [!info] Cómo usar esta nota
> 1. Leé la sección 0 (decisiones) y la sección 1 (datos faltantes). Completá lo que falte antes de empezar.
> 2. Para cada capítulo, abrí una conversación con el modelo más barato, pegá el **prompt maestro** (sección 4) y después el **prompt del capítulo**, y adjuntá las notas que figuran en "Insumos".
> 3. Pegá cada capítulo terminado en una nota nueva dentro de `CUDAR/Desarrollo` y unilas al final.
> 4. Seguí el orden de redacción de la sección 5, no el orden del índice: hay capítulos que dependen de otros.

---
## 0. Decisiones de base (04/11/2026)

| Decisión           | Valor adoptado                                                           | Consecuencia para el informe                                                                 |
| ------------------ | ------------------------------------------------------------------------ | -------------------------------------------------------------------------------------------- |
| Prototipo          | Se saltea el prototipo de 40×40×40 cm                                    | Se diseña directamente la pila final; el 40×40×40 deja de ser una especificación             |
| Escala             | **Módulo por mesa**: una pila por cada m² de cama, replicable            | Todo se dimensiona por m² y se muestra cómo escala (requerimiento de modularidad)            |
| Autonomía          | **Una noche (~14 h)** sin recarga                                        | Ciclo diario: carga de día, almacenamiento, descarga nocturna                                |
| Extracción         | Se comparan alternativas; hipótesis preferida: **aire por tubos**        | Hay que decidir convección natural (termosifón) o forzada (ventilador)                       |
| Fuente de energía  | Se compra un panel FV; la potencia de carga es un **dato de entrada**    | El informe define la energía diaria que necesita la pila y la entrega a quien elige el panel |
| Temperatura máxima | **Se define en el informe** con un estudio de compromiso                 | Es una variable de diseño, no un dato                                                        |
| Validación         | **Cálculo analítico + simulación**, validada contra resultados de papers | No hay ensayos en esta etapa; la instrumentación se especifica para el equipo final          |
| Alcance            | **Conceptual + básica** en un solo informe                               | Va desde requerimientos hasta predimensionamiento y especificación preliminar                |
| Fecha              | Fin de ingeniería básica: **02/12/2026**                                 | Quedan unas 4 semanas (ver sección 5)                                                        |

## 1. Datos de entrada
### 1.1 Datos conocidos

| Dato                                              | Valor                                                                                                                                                              | Fuente                                                                                                   |
| ------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------ | -------------------------------------------------------------------------------------------------------- |
| Superficie de una mesa                            | 1 m²                                                                                                                                                               | Doc. del proyecto                                                                                        |
| Resistencia actual del sustrato                   | 20 W/m × 8,7 m = **174 W por m²** (potencia nominal máxima)                                                                                                        | Doc. del proyecto                                                                                        |
| Temperatura máxima de la resistencia del sustrato | 60 °C                                                                                                                                                              | Doc. del proyecto                                                                                        |
| Temperatura del aire confinado                    | ≤ 30 °C (por encima, marchitamiento); < 20 °C retrasa el enraizamiento                                                                                             | Doc. del proyecto                                                                                        |
| Invernadero                                       | Debe garantizar 10–35 °C                                                                                                                                           | Doc. del proyecto                                                                                        |
| Exterior (NOA/Cuyo)                               | −9,2 °C a 47 °C                                                                                                                                                    | Doc. del proyecto                                                                                        |
| Pérdidas al suelo de la cama                      | ≈ 10 % de las pérdidas totales                                                                                                                                     | Doc. del proyecto                                                                                        |
| Alimentación actual                               | 220 V, 50 Hz monofásica; control por TRIAC                                                                                                                         | Doc. del proyecto                                                                                        |
| Arena de cuarzo                                   | ρ_aparente ≈ 1586 kg/m³, ε ≈ 0,44, c_p ≈ 850 J/kg·K (20 °C) a 1187 J/kg·K (600 °C), k_lecho ≈ 0,25–0,30 W/m·K (20 °C) a 0,85–0,90 (800 °C), inversión α→β a 573 °C | [[Properties of granular materials as heat transfer and storage medium in CSP application]]              |
| Correlaciones lineales de la arena                | c_p(T) = T + 427 J/kg·K; k(T) = 0,0006·T − 0,0102 W/m·K (T en K, válidas 323–846 K)                                                                                | [[Numerical analysis of the prototype of the high-temperature thermal energy storage based on sand bed]] |

### 1.2 Datos que faltan (completar antes de los capítulos 3 y 8)
- [ ] **Sitio exacto** (provincia/localidad del invernadero): define horas solares pico de invierno y la temperatura nocturna de diseño.
- [ ] **Panel FV**: potencia pico (Wp) y cuántos paneles por módulo. Si todavía no está comprado, el capítulo 8 entrega la energía diaria requerida para elegirlo.
- [ ] **Fracción del panel para la nebulización** (bomba de 0,5 HP, electroválvulas, control): esa energía no va a la pila.
- [ ] **Demanda real nocturna de la cama**: los 174 W son el máximo nominal. Si existen registros del sistema actual (potencia media de la resistencia en invierno), usarlos.
- [ ] **Espacio físico disponible** junto o debajo de cada mesa (limita dimensiones y peso).
- [ ] **Presupuesto** aproximado por módulo.
- [ ] **Software** de simulación disponible (ANSYS Workbench/Fluent, COMSOL o Abaqus) y de CAD (CATIA).
## 2. Chequeo de orden de magnitud (orienta el informe, no es un resultado)
> [!warning] Estimación preliminar
> Son cuentas gruesas para mostrar qué decisiones pesan más. El informe debe rehacerlas con c_p(T), la demanda real y pérdidas calculadas.

- **Energía nocturna por m² en el peor caso:** 174 W × 14 h ≈ 2,4 kWh ≈ 8,8 MJ.
- **Masa de arena útil:** con un salto aprovechable de 400 °C a 100 °C (300 K) y c_p medio ≈ 1000 J/kg·K, resultan unos 30 kg (≈ 20 L de arena). La pila final por m² es chica.
- **Pérdidas:** un cubo de arena de unos 27 cm con 10 cm de lana de roca (k ≈ 0,06 W/m·K a temperatura media) a 400 °C pierde del orden de **150–200 W**, lo mismo que la demanda de la cama. A 200 °C las pérdidas bajan a la mitad, pero la masa se duplica.
- **Carga diaria:** la pila necesitaría unos 2,4 kWh útiles más las pérdidas, es decir 3–5 kWh por día. Un panel de ~550 Wp con unas 4,5 horas solares pico en invierno entrega del orden de 2 kWh/día. **Probablemente haga falta más de un panel por módulo en invierno.**

**Consecuencias que el informe tiene que tratar explícitamente:**
1. En una pila chica, la relación superficie/volumen hace que las pérdidas dominen. La temperatura máxima, el espesor de aislación y la opción "un módulo por mesa vs. una pila centralizada para varias mesas" son las decisiones críticas.
2. Si la pila se ubica **debajo de la mesa**, parte de las pérdidas calientan la cama o el invernadero. De noche eso suma, pero de día puede llevar el aire confinado por encima de 30 °C. Hay que evaluarlo como alternativa.
3. La energía diaria que pide la pila es un requisito para elegir el panel. Se entrega como dato de salida a quien lo compre.
## 3. Estructura del informe
Cada capítulo tiene: objetivo, contenido, insumos de la vault, entregables y prompt.
### Cap. 0. Preliminares
- **Contenido:** portada, resumen ejecutivo (1 página: objetivo, solución elegida, cifras principales de la especificación preliminar y próximos pasos), índice, nomenclatura con unidades y glosario de siglas (TES, HTF, LTE, LTNE, ZBS, TRL, SR, DR, NTU, Bi, etc.).
- **Se redacta al final.**
```prompt
Capítulo 0. Con los capítulos 1 a 15 adjuntos, redactá: resumen ejecutivo de una página (objetivo, alternativa seleccionada, cifras clave de la especificación preliminar, próximos pasos), tabla de nomenclatura con símbolo, descripción y unidad SI de todas las variables usadas, y glosario de siglas. No agregues datos que no estén en los capítulos.
```

### Cap. 1. Introducción, objetivo y alcance
- **Objetivo:** justificar el acumulador y fijar qué cubre el informe.
- **Contenido:**
  - Contexto: enraizamiento de esquejes de olivo bajo nebulización en cama caliente; sistema actual con resistencia de 20 W/m; dependencia de la red en zonas rurales.
  - Justificación del acumulador térmico: almacenar excedentes FV diurnos y entregar calor continuo a la cama de noche; por qué no baterías de litio.
  - Objetivo general y objetivos específicos del área mecánica. Declaración de las metas de diseño, cálculo, simulación y construcción.
  - Alcance: pila final modular (un módulo por m²), autonomía de una noche, fase conceptual + básica. Aclarar que se saltea el prototipo y por qué. Qué queda para ingeniería de detalle.
  - Metodología del informe: ingeniería conceptual → básica → detalle (tomar el esquema de [[Desarrollo de una bateria de arena para almacenamiento de energia renovable en zonas rurales]]).
- **Insumos:**[[CUDAR - Desarrollo de Pila de Arena]], doc. "Proyecto Actual: Contexto, Requerimientos…", [[Introducción y Objetivos]].
```prompt
Capítulo 1 (Introducción, objetivo y alcance). Usá las notas adjuntas y la tabla de decisiones de base. Incluí: contexto agronómico y técnico, problema de dependencia de la red, justificación del almacenamiento térmico frente a baterías de litio, objetivo general y específicos del subsistema mecánico, alcance (pila final modular por m², autonomía de una noche, sin prototipo, conceptual + básica) y metodología conceptual/básica/detalle. Proponé un esquema del ciclo de funcionamiento como diagrama Mermaid.
```

### Cap. 2. Requerimientos y criterios de diseño
- **Objetivo:** convertir el objetivo en requisitos medibles y verificables.
- **Contenido:**
  - **Requerimientos generales:** restricción de costo, diseño modular para escalar, adaptabilidad a experimentación fitotécnica (cambio de sustrato, distintas especies).
  - **Mecánico-estructurales y operativos:** uso en interiores (invernadero), dimensiones y peso máximos, aislación para limitar pérdidas, resistencia de materiales a la temperatura máxima, ciclado diario, vida útil, temperatura superficial exterior máxima (seguridad del operario).
  - **Funcionales térmicos:** energía nocturna a entregar, potencia de descarga, temperatura de entrega compatible con el sustrato (≤ 60 °C en el elemento, sustrato 20–30 °C), autonomía de 14 h, energía diaria de carga disponible.
  - **Automatización y telemetría:** variables a monitorear y controlar (temperatura del sustrato, humedad foliar, ambiente interior y exterior, temperaturas de la pila); arquitectura de instrumentación: unidades de sensores (UIS), control de actuadores (UCA), registro (URT), protocolo Modbus/RS-485. Interfaz con el subsistema electrónico.
  - **Árbol de requerimientos:** objetivo → funciones → subfunciones → medios.
  - **Restricciones:** costo, tiempo (cronograma), recursos, técnicas, legales (seguridad eléctrica, superficies calientes) y geográficas.
  - **Indicadores de desempeño (KPI):** energía almacenada útil, eficiencia de almacenamiento (SR), relación de descarga (DR), pérdidas diarias (autodescarga), costo por kWh térmico entregado.
  - **Preguntas abiertas convertidas en criterios:** valores de transferencia que debe dar la pila, calor a almacenar, diseño nominal vs. peor caso, temperatura de almacenamiento.
- **Insumos:** doc. del proyecto, [[Introducción al Proyecto]], [[Desarrollo de una bateria de arena para almacenamiento de energia renovable en zonas rurales]] (árbol de requisitos y KPI).
- **Entregables:** matriz de requerimientos (ID, requisito, valor/tolerancia, tipo, método de verificación, fuente); árbol de requerimientos (Mermaid).
```prompt
Capítulo 2 (Requerimientos y criterios de diseño). Construí una matriz de requerimientos con columnas: ID, requisito, valor o rango, tipo (general / mecánico-estructural / térmico / automatización / seguridad), método de verificación (cálculo, simulación, inspección, ensayo futuro) y fuente. Agrupá: generales (costo, modularidad, adaptabilidad experimental), mecánico-estructurales y operativos (interiores, dimensiones, aislación, materiales), térmicos (energía nocturna, potencia, temperaturas admisibles del sustrato y del aire confinado, autonomía 14 h) y automatización/telemetría (UIS, UCA, URT, Modbus/RS-485). Agregá un árbol de requerimientos en Mermaid, las restricciones (costo, tiempo, recursos, técnicas, legales, geográficas) y KPIs medibles. Los valores que no estén definidos marcalos como "A definir en cap. X".
```

### Cap. 3. Entorno operativo y demanda térmica de la cama
- **Objetivo:** definir el caso de diseño (cuánto calor necesita la cama y en qué condiciones).
- **Contenido:**
  - Caracterización climática del sitio (NOA/Cuyo): extremos −9,2/47 °C, noches de invierno, radiación disponible (horas solares pico por mes).
  - Condiciones dentro del invernadero (10–35 °C garantizados) y dentro del cobertor (≤ 30 °C). Humedad alta por nebulización: efecto sobre la arena (humedad sube k y agrega calor latente), corrosión y aislación; necesidad de sellado.
  - **Balance térmico de la cama:** aportes por radiación a través del cobertor; pérdidas por convección/ventilación, por transpiración (calor latente), por condensación y por conducción al suelo (~10 %).
  - Demanda nocturna: potencia horaria y energía total para la noche de diseño. Comparar con el máximo nominal de 174 W/m².
  - Definición de casos: **nominal** (noche típica de invierno) y **peor caso** (noche más fría con día anterior nublado de baja carga). Justificar cuál se usa para dimensionar.
- **Insumos:** doc. del proyecto (sección Transmisión de calor), PDF "Automatización y Telemetría de un sistema de propagación de olivos bajo nebulización", datos climáticos del sitio.
- **Entregables:** tabla de condiciones de diseño; perfil horario de demanda; energía nocturna de diseño (kWh/m²).
```prompt
Capítulo 3 (Entorno operativo y demanda térmica). Con el doc. del proyecto y el PDF de automatización adjuntos, caracterizá el entorno: clima del sitio [completar localidad], condiciones dentro del invernadero y del cobertor, y efecto de la humedad de nebulización sobre la pila. Planteá el balance térmico de la cama de 1 m² (radiación por el cobertor, convección/ventilación, transpiración, condensación, conducción al suelo ~10 %) con ecuaciones y variables definidas. Calculá la demanda nocturna para un caso nominal y uno de peor caso, comparala con los 174 W nominales de la resistencia y entregá una tabla de condiciones de diseño. Si falta un dato, usá un supuesto explícito y justificado.
```

### Cap. 4. Estado del arte y matriz comparativa
- **Objetivo:** mostrar qué existe y qué se puede transferir al proyecto.
- **Contenido:**
  - Relevamiento tecnológico (comercial: Polar Night Energy) y bibliográfico (21 fichas de la base de investigación).
  - **Tipos de baterías de arena:** lecho empacado fijo, con termoclina, empaquetado con tuberías intercambiadoras, fluidizado, móvil, híbrido arena-PCM, arena con conductividad mejorada. TRL de cada uno.
  - **Matriz comparativa de estudios:** escala/masa, T de trabajo, método de carga, método de extracción, aislante, eficiencia reportada, qué se aplica a este proyecto.
  - Lecciones agrupadas por eje: (a) baja conductividad de la arena y cómo mitigarla (virutas, aletas, placas de cobre, distribución de resistencias); (b) aislación y pérdidas, incluida la tensión entre papers (espesor óptimo de 0,403 m vs. "insensible a pérdidas" vs. 64 % de pérdidas por puentes térmicos en el prototipo Stirling); (c) modelado; (d) extracción y caudales.
  - Comparación de los modelos físicos y matemáticos usados en los papers (tarea pendiente de la nota principal).
- **Insumos:** todas las notas de `CUDAR/Investigacion`, [[Leer articulos de investigacion]] (tabla comparativa de enfoques), [[Artículos de almacenamiento hibrido (calor latente y calor sensible)]].
- **Entregables:** tabla de tipos de tecnología con TRL; matriz comparativa de estudios; tabla de lecciones aplicables.
```prompt
Capítulo 4 (Estado del arte). Con las fichas de papers adjuntas, redactá: (1) un panorama de tipos de baterías de arena (lecho fijo, termoclina, con tuberías, fluidizado, móvil, híbrido con PCM, conductividad mejorada) con ventajas, desventajas y TRL; (2) una matriz comparativa de los estudios con columnas: referencia, escala/masa, T máx, carga, extracción, aislante, eficiencia reportada (aclarando si es térmica o eléctrica), aplicabilidad; (3) lecciones por eje: conductividad, aislación/pérdidas (presentá las posiciones contradictorias con sus condiciones), modelado y extracción; (4) comparación de modelos matemáticos usados. Usá solo cifras de las fichas y citá la ficha de cada dato. Tratá como un único estudio los dos papers híbridos arena-PCM que reportan 1347,1 kJ/kg y 95,61 %/96,79 %, y marcá como no verificado el 89,91 % del paper de viabilidad residencial.
```

### Cap. 5. Fundamentos físicos, propiedades y modelos matemáticos
- **Objetivo:** fijar la física y el modelo que se usa en los capítulos 8 y 9.
- **Contenido:**
  - Calor sensible: Q = m·c_p(T)·ΔT con integración de c_p(T); densidad energética volumétrica.
  - **Propiedades de la arena:** c_p(T), k_eff(T), densidad aparente, porosidad, granulometría; inversión del cuarzo a 573 °C (pico de c_p, +0,8 % de volumen, riesgo de fractura con enfriamiento brusco); humedad y aglomeración. Corregir la afirmación de "estabilidad > 800 °C" con esta salvedad.
  - **Conductividad efectiva:** por qué no se usa k del cuarzo; correlaciones (Yagi-Kunii, Kunii-Smith, ZS, **ZBS**, Hadley, Gonzo); término de radiación intergranular y desde qué temperatura importa.
  - **Mejora de conductividad:** virutas metálicas de descarte (aluminio, latón) en mezcla o capas (+70–80 % en la tasa de calentamiento), umbral de percolación (~20 % en volumen), trade-off con c_p (arena-cobre). Aletas.
  - **Granulometría vs. fluido:** grano fino mejora contacto pero impide el paso de aire; si el aire va por tubos, conviene arena fina y compactada; si atraviesa el lecho, grano de 0,5–2 mm (Ergun).
  - **Modelos de lecho:** medio continuo efectivo (una ecuación), Schumann, fase sólida continua, LTNE; criterios de selección (Bi, NTU). Justificar que con aire por tubos y arena estática alcanza el modelo de medio continuo efectivo.
  - Ecuación gobernante transitoria: ρ·c_p(T)·∂T/∂t = ∇·(k_eff(T)∇T) + Q_v.
  - Transferencia en los tubos de extracción: convección interna forzada (Dittus-Boelter/Gnielinski) o natural; resistencia térmica arena–tubo; coeficiente global de pérdidas U de la envolvente multicapa (convección + radiación exterior).
- **Insumos:** [[Improved effective thermal conductivity of sand bed in thermal energy storage systems]] (tablas S1 y S2 de correlaciones), [[Properties of granular materials as heat transfer and storage medium in CSP application]], [[Comprehensive review of dynamical simulation models of packed-bed systems for thermal energy storage applications in renewable power production]], [[Review on modeling approaches for packed-bed thermal storage systems]], [[Parametric Optimization of Sensible Thermocline Packed Bed Thermal Energy Storage Systems - A Computation Fluid Dynamics Study]], [[Evaluation of sand and sand-copper mixtures for efficient thermal energy storage]], [[Experimental determination and finite element modeling of thermal conductivity in moist sand]], [[Experimental Study of a Silica Sand Sensible Heat Storage System Enhanced by Fins]].
- **Entregables:** tabla de propiedades de diseño con su fuente; gráfico k_eff(T) con ZBS con y sin radiación (script en Python); tabla comparativa de modelos y el elegido.
```prompt
Capítulo 5 (Fundamentos y modelos). Con las fichas adjuntas, desarrollá: calor sensible con c_p(T); propiedades de la arena de cuarzo con sus fuentes (incluida la inversión α→β a 573 °C y el efecto de la humedad); conductividad efectiva con las correlaciones de la Tabla S1 y el modelo ZBS con radiación (escribí las ecuaciones con todas las variables de la Tabla S2); mejora de conductividad con virutas y aletas y su trade-off con c_p; criterio de granulometría según el tipo de extracción (Ergun); comparación de modelos de lecho (continuo efectivo, Schumann, fase sólida continua, LTNE) con los criterios Bi y NTU, y justificación del modelo elegido para arena estática con aire por tubos; ecuación gobernante; convección interna en tubos y coeficiente global de pérdidas U de la envolvente. Agregá un script de Python que grafique k_eff(T) entre 20 y 600 °C con y sin radiación.
```

### Cap. 7. Ingeniería conceptual: alternativas y selección
- **Objetivo:** elegir la configuración con criterios explícitos.
- **Contenido:** quiero una comparacion con la mejor opcion y la que voy a desarrollar. 
  1. **Configuración del lecho:** lecho estático con tubos embebidos, lecho con termoclina atravesado por aire, híbrido con PCM (como mejora futura).
  2. **Extracción hacia el sustrato:** aire por tubos con convección natural (termosifón), aire por tubos con ventilador, agua por serpentín y tubos en el sustrato, aire que atraviesa el lecho. Considerar compatibilidad con el sustrato (temperatura ≤ 60 °C en el elemento) y si hace falta un intercambiador o mezcla con aire frío (bypass).
  3. **Geometría del contenedor:** cilíndrico vs. prismático; relación de aspecto.
  4. **Temperatura máxima de almacenamiento:** rangos bajo (< 250 °C), medio (300–450 °C) y alto (~500 °C); el valor final sale del estudio del cap. 8.2.
  5. **Mejora de conductividad:** arena pura, virutas en mezcla o capas, aletas, placas.
  6. **Carga:** resistencias tubulares blindadas enterradas, su distribución. Que tipo de resistencias se usarian. 
- **Criterios sugeridos:** costo, pérdidas, simplicidad/fiabilidad, autonomía eléctrica (consumo del ventilador), seguridad, modularidad, fabricabilidad local, madurez tecnológica.
- **Insumos:** caps. 2–5, [[Numerical analysis of the prototype of the high-temperature thermal energy storage based on sand bed]], [[Sand Batteries for Thermal Energy Storage - A Review of Operating Principles, Technologies, Challenges and Future Perspectives]], [[Cost-effective Electro-Thermal Energy Storage to balance small scale renewable energy systems]].
```prompt
Capítulo 7 (Alternativas y selección). Con los capítulos 2 a 5 y las fichas adjuntas, armá matrices de decisión ponderadas (criterios: costo, pérdidas, simplicidad, consumo eléctrico propio, seguridad, modularidad, fabricabilidad local, TRL) para: configuración del lecho; método de extracción (aire por tubos natural, aire por tubos forzado, agua, aire por el lecho), incluyendo cómo se limita la temperatura de entrega al sustrato; módulo por mesa vs. pila centralizada; ubicación debajo de la mesa vs. separada; geometría del contenedor; rango de temperatura máxima; mejora de conductividad; disposición de resistencias. Justificá cada peso. Cerrá con la configuración seleccionada y un croquis descriptivo. La hipótesis inicial del autor es aire por tubos; evaluala sin darla por ganadora.
```

### Cap. 8. Ingeniería básica: predimensionamiento
- **Objetivo:** dimensionar la configuración elegida con cálculos analíticos.

**8.1 Balance energético y masa de arena**
- Energía útil nocturna (cap. 3) + pérdidas de la noche + energía no extraíble (arena por debajo de la temperatura mínima útil).
- Temperatura mínima útil según la extracción (la arena tiene que estar más caliente que el aire que alimenta la cama).
- Masa y volumen de arena integrando c_p(T). Premisas de cálculo y estimaciones analíticas iniciales.

**8.2 Estudio de la temperatura máxima**
- Curvas de masa, volumen, pérdidas diarias, espesor de aislación, costo de materiales y riesgo vs. T_max (por ejemplo de 150 a 550 °C).
- Considerar la inversión del cuarzo a 573 °C y los límites de aceros y aislantes. Recomendar un valor.

**8.3 Sistema de carga**
- Potencia eléctrica de resistencias según la energía diaria y el perfil del panel (rango de referencia anterior: 1–2 kW para ~100 kg; recalcular para la masa nueva).
- Tipo: calefactores tubulares blindados con vaina de Incoloy 800 o acero inoxidable refractario y núcleo de MgO compactado.
- Geometría y **distribución** de resistencias: evitar un punto muy caliente mientras los bordes quedan fríos; separación de ~10 cm (difusividad de la arena); ubicarlas cerca del eje pero no juntas.
- Carga de superficie (W/cm²) y temperatura de vaina admisible.
- Energía diaria requerida → dato de salida para elegir el panel.

**8.4 Sistema de extracción y regulación**
- Dimensionamiento de los tubos (diámetro, longitud, paso, aletas), coeficiente interno, resistencia arena–tubo y potencia extraíble vs. tiempo.
- Convección natural (termosifón, tiro por diferencia de densidad) vs. forzada (caudal y potencia del ventilador). Caudales moderados o bajos: a velocidad alta el aire no llega a absorber la energía y la arena junto al tubo se enfría.
- Regulación para entregar una potencia estable (equivalente a 20 W/m): modulación de caudal (PWM del ventilador o compuerta) y/o mezcla con aire frío.
- Cómo llega el calor al sustrato: tubos de aire en la cama u otro elemento; temperatura de entrega ≤ 60 °C.

**8.5 Aislación**
- Envolvente multicapa: capa caliente (manta cerámica tipo Superwool 607 HT, hasta 1300 °C, o lana de roca/mineral de alta densidad, λ ≈ 0,040 W/m·K a temperatura ambiente, con k(T)) y capa fría más económica. Capas de aire como opción.
- **Cómo se calcula el espesor óptimo:** coeficiente U, pérdidas vs. espesor, radio crítico de aislación, costo vs. energía perdida.
- Pérdidas radiales y axiales, puentes térmicos (soportes, pasamuros de tubos y resistencias), constante de autodescarga.
- Temperatura superficial exterior (seguridad).

**8.6 Contenedor y verificación estructural preliminar**
- Materiales: acero al carbono vs. aceros ferríticos resistentes a temperatura (EN 1.4713 / 1.4724, aptos 550–850 °C) según la T_max elegida; aislación interior vs. exterior (aislación interior mantiene la chapa fría).
- **Cargas gravitatorias:** peso de la arena (1400–1600 kg/m³) sobre paredes y fondo; presión lateral del material granular (Janssen).
- **Dilatación térmica diferencial** entre lecho y contenedor y entre capas: holguras, tolerancias, juntas; ciclado diario (fatiga térmica).
- Soporte y anclaje respecto de la mesa.

- **Insumos:** caps. 3, 5 y 7; [[Numerical analysis of the prototype of the high-temperature thermal energy storage based on sand bed]], [[Stirling engine-based Carnot battery with sand as heat storage medium - 1 kWe prototype]], [[Viabilidad tecnica y economica del uso de baterias de arena para el almacenamiento termico en el autoabastecimiento energetico residencial]], [[Cost-effective Electro-Thermal Energy Storage to balance small scale renewable energy systems]], [[Comprehensive review of dynamical simulation models of packed-bed systems for thermal energy storage applications in renewable power production]] (coeficiente U).
- **Entregables:** memoria de cálculo con ecuaciones, supuestos y resultados; script de Python para el balance y el estudio de T_max; tablas de dimensiones preliminares; croquis acotado.
```prompt
Capítulo 8 (Predimensionamiento). Con los capítulos 3, 5 y 7 y las fichas adjuntas, hacé la memoria de cálculo de un módulo de 1 m², con ecuaciones, supuestos numerados y resultados en tablas: 8.1 balance energético y masa de arena integrando c_p(T), con temperatura mínima útil según la extracción; 8.2 estudio de T_max entre 150 y 550 °C (masa, volumen, pérdidas diarias, espesor de aislación, costo) con recomendación; 8.3 resistencias (potencia, tipo, distribución, carga superficial, temperatura de vaina) y energía diaria requerida al panel; 8.4 tubos de extracción (geometría, coeficiente interno, potencia extraíble en el tiempo, convección natural vs. forzada, regulación hacia 174 W y límite de 60 °C); 8.5 aislación multicapa con k(T), espesor óptimo, puentes térmicos, autodescarga y temperatura superficial; 8.6 contenedor (material según T_max, presión de Janssen, dilatación diferencial y holguras). Entregá un script de Python que reproduzca 8.1, 8.2 y 8.5.
```

### Cap. 9. Modelo térmico y plan de simulación
- **Objetivo:** dejar listo el modelo numérico que valida el predimensionamiento (y que se profundiza en la ingeniería de detalle).
- **Contenido:**
  - Enfoque de medio continuo efectivo: arena como sólido homogéneo con propiedades efectivas, para que las simulaciones transitorias largas sean viables.
  - Ecuación gobernante con c_p(T) y k_c(T) (ZBS con radiación).
  - **Condiciones de borde e iniciales:** fuente en las resistencias como flujo superficial Q_s = P/A o término volumétrico Q_v; pérdidas exteriores por convección natural (−k∇T = h(T − T_amb), h ≈ 5 W/m²·K o correlaciones de Nu por cara) más radiación de cuerpo gris (emisividad ψ 0,1–0,9); planos de simetría adiabáticos; aislación como "shell conduction"; condición inicial T = T_amb del invernadero.
  - Tubos de extracción: aire estanco como sólido equivalente en carga y reposo; flujo (k-ε, y⁺ 20–200) o modelo 1D de tubería en descarga.
  - **Casos de simulación:** carga, reposo y descarga; ciclo diario repetido hasta régimen periódico (7 días); noche nominal y peor caso; variantes de distribución de resistencias y de caudal.
  - Control de resistencias en el modelo (histéresis por temperatura).
  - Malla: estudio de sensibilidad global y local cerca de resistencias y tubos.
  - **Validación sin prototipo:** reproducir un caso publicado (prototipo de 300 kg de arena o el lecho con virutas) y comparar errores con los reportados.
  - Plataforma: ANSYS Fluent/Workbench (o COMSOL/Abaqus) y CAD en CATIA. Plan de estudio para modelado térmico.
- **Insumos:** cap. 5 y 8, [[Numerical analysis of the prototype of the high-temperature thermal energy storage based on sand bed]], [[Improved effective thermal conductivity of sand bed in thermal energy storage systems]], [[Comprehensive review of dynamical simulation models of packed-bed systems for thermal energy storage applications in renewable power production]], [[Experimental determination and finite element modeling of thermal conductivity in moist sand]].
- **Entregables:** tabla de condiciones de borde; matriz de casos de simulación con salidas (T media/máx/mín, SR, DR, potencia extraída); plan de validación; plan de estudio de modelado.
```prompt
Capítulo 9 (Modelo térmico y plan de simulación). Con los capítulos 5 y 8 y las fichas adjuntas, definí el modelo numérico del módulo: enfoque de medio continuo efectivo, ecuación gobernante con propiedades función de T, tabla de condiciones de borde e iniciales (resistencias como Q_s=P/A o Q_v, convección natural y radiación exterior, simetría, aislación como shell conduction, T inicial), tratamiento de los tubos en carga/reposo y descarga, lógica de control con histéresis, estudio de malla, matriz de casos (carga, reposo, descarga, ciclo de 7 días, nominal y peor caso, variantes de resistencias y caudal) con las salidas a medir (T media/máx/mín, SR, DR, potencia), plan de validación reproduciendo un caso de los papers, y un plan de estudio paso a paso para aprender a hacerlo en [software].
```

### Cap. 10. Instrumentación, control y seguridad
- **Contenido:**
  - Termocuplas tipo K en núcleo, zona intermedia, pared, superficie exterior, vainas de resistencias y entrada/salida de aire; integración a PLC o módulos de adquisición (UIS/URT).
  - **Lógica de control de carga:** corte On/Off o modulación PID/PWM según la temperatura del núcleo; histéresis con temperatura de reinicio baja para no ciclar contactores; consigna máxima de seguridad (500–600 °C o la que surja del cap. 8.2).
  - Lógica de descarga: control de caudal/mezcla según temperatura del sustrato.
  - Protecciones: sobretemperatura independiente del control, falla de sensor, falla del ventilador, superficies calientes, aislación eléctrica en ambiente húmedo.
- **Insumos:** caps. 6 y 8, [[Numerical analysis of the prototype of the high-temperature thermal energy storage based on sand bed]].
- **Entregables:** lista de puntos de medición (P&ID simplificado), diagrama de flujo de la lógica de control, tabla de protecciones.
```prompt
Capítulo 10 (Instrumentación, control y seguridad). Definí la lista de puntos de medición del módulo (ubicación, variable, sensor, rango, propósito), un P&ID simplificado, la lógica de carga (On/Off con histéresis o PID/PWM, temperatura de reinicio y consigna máxima) y de descarga (caudal o mezcla según el sustrato) como diagramas de flujo Mermaid, y una tabla de protecciones (sobretemperatura independiente, falla de sensor o ventilador, superficies calientes, aislación eléctrica en ambiente húmedo).
```


---
### Cap. 11. Fabricación, montaje, operación y mantenimiento (preliminar)
- **Contenido:** cómo se fabrica y ensambla (chapa, soldadura, pasamuros, llenado y compactación de la arena, colocación de aislación y resistencias), cómo se reemplaza una resistencia, secuencia de puesta en marcha (primer calentamiento lento para secar la arena), operación diaria y mantenimiento.
```prompt
Capítulo 11 (Fabricación y montaje preliminar). Con la configuración y el predimensionamiento adjuntos, describí la secuencia de fabricación y ensamblaje del módulo, cómo se llena y compacta la arena, cómo se instalan resistencias, tubos y aislación evitando puentes térmicos, cómo se reemplaza una resistencia, el procedimiento de primer calentamiento (secado) y un plan de mantenimiento básico.
```

### Cap. 12. Costos preliminares
- **Contenido:** lista de materiales por módulo (arena, chapa, aislantes, resistencias, tubos, ventilador, sensores, control) con costo estimado; costo por kWh térmico almacenado; comparación con la alternativa de baterías de litio para la misma energía nocturna.
```prompt
Capítulo 12 (Costos). Armá una lista de materiales del módulo con cantidad, especificación y costo estimado [en la moneda y fecha que indique], el costo total, el costo por kWh térmico almacenado y una comparación con baterías de litio para la misma energía nocturna. Marcá cada precio como cotizado o estimado.
```

### Cap. 13. Riesgos y supuestos
- **Contenido:** registro de riesgos (técnicos, de seguridad, de cronograma, de costo) con probabilidad, impacto y mitigación: pérdidas que superen la demanda, panel insuficiente en invierno, sobrecalentamiento de vainas, humedad en la arena, puentes térmicos, sobrecalentamiento diurno de la cama si la pila está debajo; lista consolidada de supuestos.
```prompt
Capítulo 13 (Riesgos y supuestos). Con los capítulos anteriores, armá un registro de riesgos (ID, descripción, causa, probabilidad, impacto, mitigación, responsable) y una lista consolidada de todos los supuestos usados, indicando en qué capítulo se usan y cómo se verificarán en la ingeniería de detalle.
```

### Cap. 14. Especificación técnica preliminar, conclusiones y pase a ingeniería de detalle
- **Contenido:** hoja de datos del módulo (masa de arena, T_max, energía almacenada, potencia de carga y de descarga, autonomía, dimensiones, peso, aislación, pérdidas diarias, energía diaria requerida al panel); cumplimiento de cada requerimiento del cap. 2; conclusiones; tareas e hitos de la ingeniería de detalle (simulación, diseño estructural, intercambiador con el sustrato, CAD en CATIA).
```prompt
Capítulo 14 (Especificación y conclusiones). Con todos los capítulos, redactá la hoja de datos preliminar del módulo, una tabla de cumplimiento de cada requerimiento del capítulo 2 (cumple / no cumple / a verificar, con referencia al cálculo), las conclusiones y el plan de ingeniería de detalle con hitos hasta el 04/11/2027.
```

### Cap. 15. Implementaciones futuras
- **Contenido:** almacenamiento híbrido (calor latente + sensible, PCM tipo parafina 30–60 °C desacoplado); aletas para mejorar carga y descarga; RSM (metodología de superficie de respuesta) combinada con CFD para optimizar factores de diseño (paso de bobina, paso de resistencias, temperatura, velocidad y presión de entrada del fluido) sin simular todas las combinaciones; tubos del intercambiador con fracciones de material muy conductor; virutas metálicas; modelos sustitutos o gemelo digital con IA.
- **Insumos:** [[Artículos de almacenamiento hibrido (calor latente y calor sensible)]], [[Performance evaluation of a sand energy storage unit using response surface methodology]], [[Hybrid sand-PCM thermal energy storage driven with a solar parabolic trough concentrator for enhanced charging - discharging performance]], [[Performance analysis of a hybrid PCM-packed bed thermal energy storage system for mitigating solar intermittency in concentrated solar power applications]], [[Experimental Study of a Silica Sand Sensible Heat Storage System Enhanced by Fins]].
```prompt
Capítulo 15 (Implementaciones futuras). Con las fichas adjuntas, describí brevemente cada mejora futura (híbrido arena-PCM desacoplado, aletas, RSM + CFD, tubos con insertos conductores, virutas metálicas, IA/gemelo digital): qué es, qué beneficio se espera según los papers, qué haría falta para evaluarla y en qué etapa del proyecto encaja.
```

### Anexos
- A. Bibliografía (base de investigación, ordenada por importancia A/B/C).
- B. Memoria de cálculo completa y scripts.
- C. Propiedades de materiales con fuentes.
- D. Fichas de componentes comerciales (resistencias, aislantes, ventiladores).

---
## 4. Prompt maestro (pegar al inicio de cada conversación)
Actuá como ingeniero mecánico especializado en almacenamiento térmico y transferencia de calor. Estás ayudando a redactar un informe de ingeniería conceptual y básica para tutores universitarios, sobre una "pila de arena" (acumulador térmico de calor sensible) que almacena excedente fotovoltaico diurno y calienta de noche el sustrato de una cama de enraizamiento de esquejes de olivo bajo nebulización. El informe debe ser corto y conciso pero a la vez servirme a mi para organizar mis ideas. 

En la nota de 'Plan informe ingenieria conceptual y basica' estan todos los supuestos y planificacion. 

Reglas:
1. Usá solo la información de las notas adjuntas (sobre todo los articulos que estan en el vault de obsidian) y conocimiento de ingeniería estándar. No inventes cifras de papers; si un dato falta, escribí un supuesto numerado y justificado, o "dato faltante".
2. Citá la nota de origen de cada dato de literatura con un numero y al final pon el enlace de Obsidian [[nombre de la nota]].O hazlo de tal forma que al exportar en pdf se pueda saber a q articulo hace referencia (nombre, no link)
3. Escribí en español técnico, en prosa, con tablas cuando ordenen datos. Ecuaciones en LaTeX con todas las variables definidas y sus unidades SI.
4. Formato: Markdown para Obsidian, títulos con ## y ###, diagramas en Mermaid, callouts > [!note] para observaciones y > [!warning] para supuestos críticos. 
5. Si tengo que agregar una imagen de algunas de las notas en el texto quiero que me indiques en el mismo texto que imagen tengo que agregar y su descripcion. 
6. Al final del capítulo, listá: supuestos usados, datos faltantes y qué capítulos dependen de este
7. Agrega un callout de WARNING cuando se necesite determinar un dato que no se tenga. 

---
## 5. Orden de redacción sugerido y calendario (04/11 → 02/12/2026)

| Semana | Capítulos | Depende de |
|---|---|---|
| 1 (04–10/11) | Completar sección 1.2 · Cap. 2 · Cap. 3 · Cap. 4 | Datos del sitio y del panel |
| 2 (11–17/11) | Cap. 5 · Cap. 6 · Cap. 7 | Caps. 2–4 |
| 3 (18–24/11) | Cap. 8 (con scripts) · Cap. 9 | Caps. 3, 5, 7 |
| 4 (25/11–02/12) | Caps. 10–15 · Cap. 1 · Cap. 0 · revisión general | Todos |

> [!tip] Para ahorrar tokens
> Adjuntá solo las notas listadas en "Insumos" de cada capítulo y, a partir del cap. 5, adjuntá los capítulos ya terminados de los que depende en lugar de las fichas completas.

---
## 6. Correcciones a tener en cuenta (detectadas en la vault)
- Unidades de la demanda: 20 W/**m lineal** × 8,7 m = 174 W **por m² de mesa**. No mezclar W/m con W/m².
- Los dos papers híbridos arena-PCM con 1347,1 kJ/kg y 95,61 %/96,79 % parecen el mismo estudio: citarlos como uno.
- El 89,91 % de eficiencia térmica del paper de viabilidad residencial no tiene método de cálculo: no usarlo como dato.
- Lana de vidrio y espuma de poliuretano **no** sirven para 500 °C: usar fibra cerámica, lana de roca o silicato de calcio en la capa caliente.
- "Arena estable por encima de 800 °C" necesita la salvedad de la inversión del cuarzo a 573 °C.
- El espesor óptimo de 0,403 m corresponde al tanque de 205 L de ese paper: se recalcula para la geometría propia.
- La recomendación previa de 1–2 kW de resistencias era para ~100 kg de arena del prototipo: se recalcula.