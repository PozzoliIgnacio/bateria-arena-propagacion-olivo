---
Titulo esp.:
Año: 2023
Padre: "[[CUDAR - Desarrollo de Pila de Arena]]"
Importancia:
  - A
URL:
---
## 1. Idea central
El paper presenta el diseño de ingeniería (conceptual, básica y de detalle) de una **batería de arena** que almacena energía de origen solar o eólico, y también calor residual de una cocina campesina (asador empotrado). Esa energía se guarda como calor en una mezcla de arena y arcilla y luego se convierte en calor de uso (agua caliente), electricidad o **hidrógeno verde** mediante un electrolizador. 
La conclusión principal es que el concepto es **innovador y sostenible** para zonas rurales aisladas, pero el trabajo sigue en etapa de prototipo: **todavía no hay datos experimentales** de capacidad, eficiencia ni cobertura de una vivienda. Los autores proponen completar esas pruebas como siguiente paso.
### Glosario

| Abreviatura | Significado |
|---|---|
| **ANSYS** | Software de simulación por elementos finitos y de ingeniería |
| **CAD** | Diseño asistido por computadora |
| **FEA / MEF** | *Finite Element Analysis* / Método de elementos finitos (usado en ANSYS) |
| **GAP** | Vacío o brecha de conocimiento identificada en la literatura |
| **HHO** | Gas oxihidrógeno (mezcla de hidrógeno y oxígeno producida por electrólisis) |
| **ISO 14224** | Norma de taxonomía y recolección de datos de confiabilidad y mantenimiento en industrias de petróleo y gas |
| **PRISMA 2020** | Guía para reportar revisiones sistemáticas de la literatura |
| **SICCE** | Sistema Inteligente de Captación y Conversión de Energía (propuesto en este paper) |
| **Bibliometrix** | Paquete de R para análisis bibliométrico |
| **Atlas.ti** | Software de análisis cualitativo (codificación de artículos) |
| **Electrolizador de placas** | Equipo que separa agua en H₂ y O₂ mediante corriente eléctrica |
| **Efecto Peltier / Seebeck** | Fenómenos termoeléctricos. Peltier: genera diferencia de temperatura con corriente. Seebeck: genera corriente con diferencia de temperatura (base de los generadores termoeléctricos) |

## 2. Resumen por secciones
### 2.0 Resumen y Abstract
Presentan el objetivo (una tecnología de almacenamiento amigable con el ambiente), el alcance (ingeniería en tres niveles) y la expectativa (validar capacidad y eficiencia reales, y cubrir las necesidades de una vivienda rural promedio). Las palabras clave son arena, energía y rural.
### 2.1 Introducción
- Presenta la batería como una forma de **almacenar energía renovable y aprovechar calor residual**.
- Explica que el material poroso de la batería es **arena común** que retiene calor durante largos periodos.
- Menciona el electrolizador para producir hidrógeno.
- Describe el enfoque de ingeniería en tres niveles: conceptual, básica (con simulaciones en ANSYS) y de detalle (planos de fabricación y soporte).
### 2.2 Revisión sistemática
Es la parte de metodología de la literatura:
- Se plantearon **10 ecuaciones de búsqueda** en **Scopus, Web of Science e IEEE**.
- Se aplicó el método **PRISMA 2020**, y al final se analizaron **26 artículos** en detalle.
- Un análisis bibliométrico con **Bibliometrix** (R) muestra las temáticas principales. La nube de palabras (Figura 1) es de baja utilidad técnica: los términos más grandes son *phase change materials*, *heat transfer*, *thermoelectric generators* y *nanofluids*.
- Un análisis cualitativo con **Atlas.ti** codifica los artículos según la pregunta de investigación.
- Se usa para identificar **desafíos** y **GAP** (vacíos de conocimiento) de la captación, almacenamiento y conversión térmica.
### 2.3 Ingeniería conceptual
Establece los conceptos preliminares y el marco de referencia:

**Descripción del proceso:** las fuentes renovables (solar, eólica) generan electricidad que a veces no se consume en el momento. Esa electricidad se convierte en calor con resistencias eléctricas y se guarda en contenedores de arena. El calor se devuelve después de tres formas:
1. Calentando agua.
2. Produciendo vapor.
3. Generando electricidad con **celdas termoeléctricas** (el paper cita efecto Peltier).

La electricidad se usa, además, para producir hidrógeno en un electrolizador de placas tipo Bod Boyce.

**Diagrama de bloques (Figura 2):** muestra el flujo completo: panel solar → resistencia eléctrica → batería de arena → intercambio de energía hacia agua caliente, agua tibia y agua fría → bomba → electrolizador → tanque de H₂. También aparece un asador empotrado que aporta calor a la batería.

**Taxonomía ISO 14224 (Figura 3):** clasifica el sistema en niveles: sistema, equipo, subequipo, componente y parte. Los equipos son: batería de arena, electrolizador, calentador de agua solar, estructura de soporte, panel solar y tanque de H₂.
### 2.4 Ingeniería básica
Incluye cuatro tareas:
**Requerimientos funcionales (árbol de requerimientos):** descompone el objetivo principal en funciones, subfunciones y medios. Ayuda a detectar inconsistencias antes de implementar. Las **restricciones** consideradas son de tiempo, costo, recursos, técnicas, legales y **geográficas**.

**Requerimientos operacionales:** garantizan que se cumplan las expectativas de usuarios durante operación y mantenimiento. Se apoyan en simulaciones ANSYS y cálculos termodinámicos y de transferencia de calor, sin mostrarlos en el paper.

**Funciones objetivo (Figura 6):** el sistema SICCE busca tres cosas:
- Maximizar la captación de energía.
- Maximizar la conversión de energía.
- Minimizar las pérdidas de energía.

**Fases del proceso energético (Figura 5):** el esquema tiene tres bloques: entrada de energía (calor residual, electricidad y luz solar concentrada), almacenamiento (con aislamiento) y conversión.
![[Desarrollo de una bateria de arena para almacenamiento de energia renovable en zonas rurales-1793781090493.webp]]*Muestra el contenedor de la batería con elementos internos, junto al electrolizador. Las dimensiones no son legibles en el paper.*
### 2.5 Prototipo y conclusiones
- El prototipo **está en construcción**. No hay resultados experimentales.
- Se planea evaluar la capacidad real de almacenamiento térmico, la eficiencia real y si puede cubrir una vivienda rural promedio.
- Sostienen que el sistema tiene **bajo costo de operación** y **fácil mantenimiento**, y que puede transferirse a comunidades rurales con capacitación local.
- Propuesta de valor: reducir la dependencia de fuentes no renovables y proteger el ambiente.
## 3. Parámetros técnicos clave

| Parámetro | Valor en el paper | Observación |
|---|---|---|
| **Volumen / masa de arena** | No especificado | Solo se dice que se usa "arena común" o "mezcla de arena y arcilla" |
| **Potencia y capacidad** | No especificado | Solo se menciona que el sistema debe cubrir una vivienda rural promedio, sin cifras |
| **Potencia del electrolizador** | No especificado | Solo se menciona el modelo tipo Bod Boyce |
| **ΔT de trabajo** | No especificado | No hay temperatura máxima, mínima ni rango útil |
| **Tipo de intercambiador (carga)** | Resistencias eléctricas alimentadas por solar o eólica, y calor residual de un asador empotrado | Sin detalle de disposición ni potencia |
| **Tipo de intercambiador (descarga)** | Intercambiador de calor hacia circuitos de agua (caliente, tibia y fría), generación termoeléctrica y electrolizador | El tipo de intercambiador no se especifica |
| **Material aislante** | No especificado | Solo aparece la palabra "aislamiento" en la Figura 5 |
| **Eficiencia reportada** | No especificado | El paper declara que se medirá en pruebas futuras |

## 4. Hallazgos críticos
### Aportes principales
- **Multi-entrada:** el sistema acepta calor residual, electricidad y luz solar concentrada. Es una ventaja frente a sistemas que solo usan electricidad.
- **Multi-salida:** entrega calor (agua caliente), electricidad y hidrógeno verde. El hidrógeno permite almacenar energía a largo plazo.
- **Proceso de ingeniería por niveles:** conceptual → básica → detalle, con planos de fabricación y soporte. Es una estructura clara que puedes reutilizar.
- **Metodología de requisitos:** árbol de requerimientos funcionales, operacionales y restricciones (incluidas las geográficas).
- **Funciones objetivo del SICCE:** maximizar captación, maximizar conversión y minimizar pérdidas. Son criterios medibles.

### Qué NO resuelve el paper
Es importante aclararlo, porque en tu consulta podría parecer que trae soluciones:
- **Conductividad térmica:** no propone ninguna mejora. Solo menciona la mezcla de arena y arcilla.
- **Diseño del contenedor:** no da dimensiones ni materiales. La CAD no es legible en cuanto a medidas.
- **Pérdidas de calor:** el aislamiento aparece en un diagrama, pero no hay cálculo ni material.
### Cómo me sirve para mi trabajo (pila de arena)
**1. Estructura del informe de ingeniería básica.** El paper organiza el trabajo en conceptual, básica y de detalle, igual que tu cronograma (ingeniería básica en 2026 y de detalle en 2026–2027). Puedes usar su esquema para tu informe a tutores: primero el proceso, luego los requerimientos, después la taxonomía y el diseño.

**2. Árbol de requerimientos.** Tu documento tiene requerimientos generales y específicos, pero no los descompone en funciones y subfunciones. Un árbol te ayudaría a detectar contradicciones antes de diseñar. Por ejemplo, "mantener el sustrato entre 20 y 30 °C" se convierte en una función, y de ahí salen subfunciones como "medir temperatura del sustrato" o "entregar calor al sustrato".

**3. Restricciones geográficas y de tiempo.** El paper incluye restricciones de costo, tiempo, recursos, técnicas, legales y geográficas. Las tuyas están bien cubiertas en costo y ambiente, pero conviene agregar las legales (normas eléctricas y de seguridad para resistencias de potencia en invernadero) y las de tiempo (los plazos del cronograma).

**4. Funciones objetivo como KPI.** Tu objetivo general se puede traducir en tres indicadores medibles: fracción de energía captada, fracción de energía transferida al sustrato y pérdidas en el acumulador. Esto te da criterios para comparar diseños y para validar el prototipo de 40 × 40 × 40 cm.

**5. Transferencia por agua como alternativa.** El paper transfiere calor de la arena a un circuito de agua caliente. Para tu caso, podrías evaluar un serpentín con agua en la cama en lugar de calentar el sustrato solo con resistencias. Eso es una alternativa de diseño que conviene comparar con tu diseño actual de intercambiador, no un requisito.

**6. Validación experimental.** El paper dice que su trabajo está pendiente de prueba. Tu proyecto sí tiene una fase de validación (Fase 6 de tu documento). Para esa parte te conviene leer **Pinto & Beausoleil-Morrison (2023)**, citado en este paper, que valida un modelo numérico de almacenamiento térmico con arena contra datos experimentales. Es una referencia más sólida que la mayoría de las del paper.

**7. Lo que no conviene copiar.**
- El **electrolizador y el hidrógeno** están fuera de alcance para tu proyecto. Tu cama necesita calor, no H₂. Incluirlo aumenta riesgos y costos sin aportar a tu objetivo.
- La **generación termoeléctrica con celdas Peltier** tiene el error de concepto que señalé arriba. No la uses como referencia técnica sin revisar la fuente original.
- El **asador como fuente de calor residual** es una idea interesante para zonas rurales con cocina a leña, pero no aplica a tu sistema, que se alimenta con solar.