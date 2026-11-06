---
Titulo esp.: Análisis numérico de un prototipo de almacenamiento térmico de alta temperatura basado en arena
Tipo:
  - Articulo
Año: 2025
URL: https://www.sciencedirect.com/science/article/pii/S0360544225031147
Padre: "[[CUDAR - Desarrollo de Pila de Arena]]"
Importancia:
  - A
---
# 1. Idea Central
**Objetivo Principal:** Desarrollar y analizar numérica y experimentalmente un prototipo de almacenamiento térmico estacional de alta temperatura que utiliza arena de cuarzo como medio de almacenamiento, con calentamiento mediante resistencias eléctricas y extracción de calor a través de un intercambiador de tubos con flujo de aire.

**Conclusión Fundamental:** El estudio demuestra que los sistemas de almacenamiento térmico basados en arena son técnica y económicamente viables para aplicaciones de calefacción de edificios y procesos industriales. La baja conductividad térmica de la arena resulta beneficiosa para retener el calor a alta temperatura durante periodos prolongados, minimizando pérdidas. El sistema puede operar eficazmente con diferentes esquemas de carga (continua, tarifa G12, fotovoltaica) y la velocidad del aire en el intercambiador debe optimizarse para equilibrar la potencia instantánea y la estabilidad de la descarga.

### Glosario de Abreviaciones

|**Abreviatura**|**Significado en Inglés**|**Significado en Español**|
|---|---|---|
|TES|Thermal Energy Storage|Almacenamiento de Energía Térmica|
|CFD|Computational Fluid Dynamics|Dinámica de Fluidos Computacional|
|PCM|Phase Change Materials|Materiales de Cambio de Fase|
|PLC|Programmable Logic Controller|Controlador Lógico Programable|
|PV|Photovoltaic|Fotovoltaico|
|CAES|Compressed Air Energy Storage|Almacenamiento de Energía por Aire Comprimido|
|CSP|Concentrated Solar Power|Energía Solar Concentrada|
|FEM|Finite Element Method|Método de Elementos Finitos|
|SR|Storage Ratio|Relación de Almacenamiento|
|DR|Discharge Ratio|Relación de Descarga|
|Nu|Nusselt Number|Número de Nusselt|
|Ra|Rayleigh Number|Número de Rayleigh|
|Pr|Prandtl Number|Número de Prandtl|
![[Numerical analysis of the prototype of the high-temperature thermal energy storage based on sand bed-1790903406690.webp]]
# 2. Resumen por Secciones
## Sección 1: Introducción
- La calefacción representa más del 60% del consumo energético final en edificios de la UE.
- Los nuevos edificios deben cumplir estándares de cero emisiones de carbono.
- Se necesitan sistemas de almacenamiento estacional que puedan cargarse con energía solar.
**Tipos de Almacenamiento Energético Mencionados:**
1. Baterías y supercondensadores
2. Almacenamiento por aire comprimido (CAES)
3. Almacenamiento por bombeo hidráulico
4. Almacenamiento térmico (TES):
    - Depósitos de agua
    - Almacenamiento subterráneo estacional
    - Reacciones químicas reversibles
    - Materiales de cambio de fase (PCM)
    - Sales fundidas
    - Materiales sólidos (arena, rocas)

**Ventajas de la Arena como Medio de Almacenamiento:**
- Alta capacidad calorífica
- Abundante y de bajo costo
- Ecológica
- Puede alcanzar temperaturas de hasta 800°C
- Permite almacenamiento a largo plazo
> [!NOTE] 
> - La arena tiene una **elevada T de funcionamiento admisible** y **alta inercia térmica** lo que lo hace ideal para sistemas de energía renovable donde el suministro de energía no es constante 
> - Alta inercia térmica significa que el sistema tarda mucho en cambiar su temperatura cuando se le entrega o quita calor. En este caso la arena almacena una gran cantidad de calor en su masa y su temperatura sube y baja lentamente, el sistema puede mantener temperaturas altas durante mucho tiempo aunque el aporte de energía sea intermitente. 
> - Como el calor no se distribuye rapido, **pueden aparecer zonas muy calientes cerca de los calefactores y zonas frias cerca de las paredes**, es decir que **puede haber un gradiente de T muy marcado**.
> - La **baja conductividad impide que el calor se disipe rapidamente por lo que los calefactores pueden alcanzar T peligrosas**, por eso el paper implementa logica de control.

> [!NOTE] Mejora a futuro
> - aumentar la T de los conductos de aire (por ende el aire) hace que se aumente la transferencia de calor dentro del lecho de almacenamiento, por ende este se podría calentar por medio de electricidad generada por red eléctrica o por aire procedente de la recuperación de gases industriales

**Novedad del Estudio:**
- Desarrollo de un concepto novedoso de carga de lecho de arena mediante resistencias eléctricas con modos de operación individualmente controlados.
- Estrategia de calentamiento multicriterio que considera radiación solar y tarifas eléctricas.
- Combinación de calentamiento eléctrico y por aire caliente (híbrido).
- Modelo numérico validado experimentalmente.

En la siguiente tabla se muestran estudios realizados sobre sistemas de almacenamiento de energía térmica a alta T

| Objetivos del estudio                                                                                                                                                                                                                                                                  | Materiales utilizados en el estudio                                                                 | Hallazgos                                                                                                                                                                                                                                                                                                               | Referencia                                                                                               |
| -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------- |
| Evaluación de arena de dunas del desierto como material de almacenamiento de energía térmica, transferencia de calor y absorción solar directa                                                                                                                                         | Siete muestras de arena del desierto de los Emiratos Árabes Unidos                                  | Se ha demostrado el funcionamiento del almacenamiento de energía térmica a base de arena hasta 1000 °C, a pesar de una pérdida de masa inicial durante el primer ciclo de calentamiento                                                                                                                                 | Diago y otros. [[16](https://www.sciencedirect.com/science/article/pii/S0360544225031147#bib16)]         |
| Evaluación del rendimiento térmico de la arena de sílice como medio de almacenamiento de calor en un sistema de energía térmica de almacenamiento de calor sensible de carcasa y tubos que funciona con agua como fluido de transferencia de calor                                     | Dos tipos de arena de sílice, incluida la arena fina y la arena gruesa                              | Se descubrió que la arena fina, que tenía partículas más pequeñas en comparación con la arena gruesa, mejoraba la transferencia de calor en el sistema                                                                                                                                                                  | Niksiar y otros. [[31](https://www.sciencedirect.com/science/article/pii/S0360544225031147#bib31)]       |
| Verificación de un concepto de almacenamiento solar térmico estacional en lecho de arena que requiere controles adicionales para aplicaciones de calefacción residencial                                                                                                               | Arena de sílice                                                                                     | Los sistemas estacionales de almacenamiento solar térmico en lechos de arena podrían ser una opción viable para almacenar calor en regiones con climas caracterizados por largos períodos de temperaturas gélidas                                                                                                       | Hailu y otros. [[32](https://www.sciencedirect.com/science/article/pii/S0360544225031147#bib32)]         |
| Investigación de la influencia del paso de la bobina, la temperatura del fluido de entrada y la velocidad del fluido caliente en una unidad de almacenamiento de energía térmica a base de arena                                                                                       | Dos tipos de arena comunes en los Emiratos Árabes Unidos                                            | Los resultados mostraron que los tres factores, incluida la temperatura de entrada del fluido, la velocidad y el número de vueltas de la bobina, afectan significativamente la energía térmica almacenada                                                                                                               | Basria y otros. [[14](https://www.sciencedirect.com/science/article/pii/S0360544225031147#bib14)]        |
| Desarrollo de recubrimientos negros de bajo costo, simples y escalables sobre partículas sólidas con alta capacidad de absorción solar y demostración de un método simple y escalable para convertir arena de cuarzo de bajo costo en un material de almacenamiento de energía térmica | Arena de sílice recubierta con una cubierta de sílice que contiene nanopartículas de espinela negra | Recubrir arena de sílice de bajo costo con nanopartículas de óxido de espinela negra es un método conveniente y rentable para mejorar la capacidad de absorción solar mientras se mantiene una alta conductividad térmica a temperaturas elevadas (400–700 °C)                                                          | Chung y otros. [[33](https://www.sciencedirect.com/science/article/pii/S0360544225031147#bib33)]         |
| Mejora de la conductividad térmica de la arena mediante la incorporación de virutas metálicas residuales procedentes de talleres mecánicos                                                                                                                                             | Arena mezclada con chatarra                                                                         | Una compactación adecuada de la arena puede mejorar la conductividad térmica hasta en un 20%, y esa configuración óptima del lecho puede minimizar las pérdidas de energía y aumentar la eficiencia del almacenamiento                                                                                                  | Tetteh y otros. [[20](https://www.sciencedirect.com/science/article/pii/S0360544225031147#bib20)]        |
| Verificación de la idoneidad de diferentes tipos de rocas y revisión de sus propiedades térmicas y degradación en torno a 500 °C para el almacenamiento térmico en lecho rocoso en plantas de energía solar                                                                            | Tipos de rocas: ígneas, metamórficas y sedimentarias                                                | Se descubrió que las rocas ígneas y metamórficas de alto grado eran adecuadas para aplicaciones de almacenamiento térmico                                                                                                                                                                                               | Allen y otros. [[34](https://www.sciencedirect.com/science/article/pii/S0360544225031147#bib34)]         |
| Desarrollo de un nuevo modelo de tanque de termoclina lleno de PCM para evaluar el comportamiento de almacenamiento y determinar la viabilidad del concepto de termoclina de calor latente                                                                                             | Roca convencional con sal fundida                                                                   | El uso de un solo PCM no proporciona una mejora significativa en la capacidad de almacenamiento anual en comparación con las rocas convencionales como elementos de embalaje para un sistema de igual tamaño                                                                                                            | Flueckiger y Garimella [[35](https://www.sciencedirect.com/science/article/pii/S0360544225031147#bib35)] |
| [36]Evaluación de la calefacción de lechos de arena utilizando calentadores eléctricos con una estrategia de calefacción multicriterio[](https://www.sciencedirect.com/science/article/pii/S0360544225031147#bib36)                                                                    | Arena de sílice                                                                                     | El uso de programas de calentamiento por almacenamiento de arena funcionará mejor con sistemas RES (fuentes intermitentes) o tarifas variables, mientras que se debe proporcionar la distribución adecuada de los calentadores para lograr una alta eficiencia operativa y una distribución homogénea de la temperatura | Este estudio                                                                                             |

## Sección 2: Materiales y Métodos
Se desarrolla un prototipo de laboratorio para validar el modelo numérico o computacional, hecho en ANSYS Workbench. El paso a paso del articulo se divide en:
![[Numerical analysis of the prototype of the high-temperature thermal energy storage based on sand bed-1791475382959.webp]]
### 2.1. Prototipo Físico de Laboratorio
**Especificaciones del Prototipo:**
- **Tanque:** Cilíndrico de acero
- **Volumen:** 205 dm³ (205 litros)
	- Diametro de 59 cm, altura de 70 cm
- **Aislamiento:** Lana mineral de 10 cm de espesor (λ = 0.040 W/mK)
- **Arena:** Cuarzo, 300 kg
- **Resistencias Eléctricas:** 5 unidades × 1400 W cada una
- **Sensores:** Termopares tipo K (NiCr-NiAl), rango -200°C a 1150°C, tolerancia ±2.0°C
![[Numerical analysis of the prototype of the high-temperature thermal energy storage based on sand bed-1791475455788.webp]]*Figura 1: vista del banco de prueba experimental en (a) sección transversal esquemática y (b) vista real. 1- creo q son las resistencias calentadoras, 2- sensores de T, 3- tanque con aislamiento, 4- arena, 5- sistema de registro automático de datos basado en PLC*

**Sistema de Control:**
- PLC con control modular, equipado con sensores de temperatura tipo PTTK dedicados a determinar la distribución de T dentro del lecho
- Relés para encendido/apagado de resistencias según programación horaria
- Visualización en CoDeSys con registro de datos cada 5 segundos
- Considerando la potencia de los calentadores eléctricos y el tiempo de su funcionamiento fue posible determinar la cantidad de energía de entrada entregada para cargar el lecho de arena
### 2.2. Implementación de Parámetros del Lecho de Arena
Un lecho de arena es un cuerpo poroso lo cual significa que sus propiedades termodinámicas dependen del tamaño y tipo de los granos de arena, cuanto menor sea el tamaño de grano del lecho menos aire habrá entre los granos lo que da un mayor coeficiente de transferencia de calor efectivo y calor especifico de todo el lecho. 
Hay 3 formas de modelar un lecho de arena: 
- Modelo discreto: supone el conocimiento del tamaño de las partículas de arena y sus parámetros exactos, se basa en el modelado discreto de partículas suspendidas en un fluido. Computacionalmente exigente y no adecuado para el análisis variacional basado en simulaciones transitorias 
- Medio poroso: modela el material como medio poroso, es decir que tiene en cuenta la caída de presión que fluye a través de los poros del aire. Esta caída se calcula según la ley de Darcy y requiere conocimiento de la porosidad y permeabilidad del lecho. Complejo y mucho tiempo. 
- Parámetros sustitutos (el adoptado): se basa en una simplificación modelando como un solido completo o continuo con propiedades termodinámicas equivalentes o sustitutas. Requiere estudios separados del lecho 
	- Baumann y Zunft demostraron el uso del método Hot Wire al estudiar la conductividad térmica de un lecho de arena. Ellos demuestran que el coeficiente de conductividad térmica varia parabólicamente o aproximadamente linealmente en el rango de temperaturas de 300-1073 K
		- [Articulo mencionado](https://www.sciencedirect.com/science/article/abs/pii/S0927024815003062)

|**Enfoque**|**Descripción**|**Ventaja**|**Desventaja**|
|---|---|---|---|
|Modelado discreto|Partículas suspendidas en fluido|Alta precisión|Computacionalmente demandante|
|Medio poroso|Modelado como zona porosa (Ley de Darcy)|Considera caída de presión|Complejidad de convección|
|Parámetros sustitutos|Modelo de sólido completo|Rápido, baja demanda|No universal, requiere estudios previos|

**El cuarzo sufre un cambio de fase polimórfica** (de cuarzo alfa a cuarzo beta) a los 846 K que es a los 570º **que altera sus propiedades térmicas**. Para mantener la viabilidad computacional, y simplificar, los autores simplificaron las relaciones mediante tendencias lineales validas entre 323K y 846K, lo que permitió importarlos al modelo numerico
$$  
\mathbf{C_p(T) = T + 427} \quad \left[\frac{\text{J}}{\text{kg}\cdot\text{K}}\right] \quad \text{(Ecuación 1)}  
$$
$$  
\mathbf{k_c(T) = 0.0006 T - 0.0102} \quad \left[\frac{\text{W}}{\text{m}\cdot\text{K}}\right] \quad \text{(Ecuación 2)}  
$$
**Donde:**
- **Cₚ(T):** Calor específico en función de la temperatura
- **k꜀(T):** Conductividad térmica en función de la temperatura
- **T:** Temperatura en Kelvin
**Nota Importante:** A ~846 K ocurre la transición de fase polimórfica del cuarzo α a β, cambiando sus propiedades físicas y térmicas.
### 2.3. Modelo Numérico
#### a) Geometría
- se hizo usando el programa de Wb, SpaceClaim. Contenía únicamente el dominio de lecho de arena (un solido sólido). 
- Se supuso que la capa aislante era una pared infinitamente delgada para limitar el numero de celdas de malla. 
    - esto para ahorrar millones de celdas de malla y por ende tiempo de simulación.
    - En ANSYS Fluent cuando definimos la condición de contorno en una superficie (Wall), se puede activar la opción **"Shell Conduction"** (Conducción en Cáscara).
    - Esto le dice al solver: _"Esta pared no tiene volumen en la malla, pero tiene un espesor real (0.1 m) y una conductividad térmica real (λ = 0.040 W/mK)"_.
    - El solver añade una resistencia térmica extra (δ/λ) a la ecuación de transferencia de calor en esa frontera. Por lo tanto, aunque la geometría sea "infinitamente delgada" (2D en la malla), la física es 3D en la resistencia térmica.
- Simetría axial: 1/5 del volumen total
- Resistencias eléctricas implementadas como recortes de volumen del lecho de arena. Cuya ubicación coincide con el prototipo de validación. 
![[Numerical analysis of the prototype of the high-temperature thermal energy storage based on sand bed-1791484994645.webp]]*Fig. 2: Geometría del modelo, incluyendo las dimensiones de los elementos individuales*
![[Numerical analysis of the prototype of the high-temperature thermal energy storage based on sand bed-1791485147051.webp]]*Fig. 3. Geometría de una quinta parte del volumen del lecho de arena utilizado en los cálculos junto con la ubicación de los puntos de medición.*

#### b) Malla Numérica: 
se creo con el software ANSYS Fluent Meshing. Además de la configuración global, se introdujo en el algoritmo la agregación local de celdas de malla cerca de los calentadores. Un análisis de sensibilidad de malla determino que el tamaño máximo global optimo de celda era de 0.005m y en la superficie de calentamiento 0.0005m. 
- Celdas poliédricas: 828,081 celdas
- Nodos: 4,279,874
- Tamaño global: 0.05 m
- Agregación local de malla en superficies de calefacción: 0.0005 m
![[Numerical analysis of the prototype of the high-temperature thermal energy storage based on sand bed-1791485429193.webp|se ve como las resistencias se modelan como vacío de volumen]]
**Parámetros de Calidad de la Malla:**
![[Numerical analysis of the prototype of the high-temperature thermal energy storage based on sand bed-1791485489696.webp]]

#### c) Modelo Matemático:
Debido a las simplificaciones mencionadas en la sección 2.2, **todo el dominio computacional consistió en un solido**. Para los cálculos se uso el software ANSYS Fluent que normalmente se usa para CFD, en el modelo utilizado para la validación no hay fluido en movimiento, sin embargo eligieron este software ya que permite realizar cálculos rápidos de transporte de calor en un solido, y además en análisis posteriores metieron un intercambiador de calor por lo que en este habrá un flujo de aire. Por ende conviene usar el mismo software para todos los análisis. 
El solver de ANSYS Fluent se basa en las ecuaciones básicas que rigen: continuidad, conservación del momento y la energía. Al analizar únicamente el transporte de calor en un solido el solver utiliza únicamente este ultimo representado por la ecuación de **conducción de calor**
$$   
\mathbf{\rho \frac{\partial T}{\partial t} = \frac{k_c}{C_p} \left( \frac{\partial^2 T}{\partial x^2} + \frac{\partial^2 T}{\partial y^2} + \frac{\partial^2 T}{\partial z^2} \right)} \quad \text{(Ecuación 3)}   $$
**Donde:**
- **ρ:** Densidad del material (kg/m³)
- t es el tiempo y _x,y,z_ son las coordenadas cartesianas
- **∂T/∂t:** Variación temporal de la temperatura
- **k꜀:** Conductividad térmica (W/mK)
- **Cₚ:** Calor específico (J/kgK)
- **∂²T/∂x², ∂²T/∂y², ∂²T/∂z²:** Segundas derivadas espaciales

Las paredes exteriores del modelo (superficies aisladas y calentadores eléctricos) se modelaron como superficies infinitamente delgadas y se describieron mediante la condición limite correspondiente (tabla 5). 

| **Límite**                                 | **Condición de contorno**                    | **Definición**                                                                                                                                 | **Descripción**                                                                                                          |
| ------------------------------------------ | -------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------ |
| **Superficie del calentador**              | Pared, flujo de calor fijo                   | $Q = 4.77 \cdot 10^4 \, [\frac{W}{m^2}]$                                                                                                       | Potencia eléctrica del calentador (1400 W) distribuida sobre la superficie del calentador ($2.93 \times 10^{-2} \, m^2$) |
| **Pared divisoria**                        | Simetría                                     | [37]                                                                                                                                           | Permite obtener una distribución correcta de temperatura en todo el volumen de almacenamiento                            |
| **Superficie superior del lecho de arena** | Pared, transferencia de calor por convección | $Nu = \begin{cases} 0.54 \cdot Ra^{1/4} & \text{para } 10^4 < Ra < 10^7 \\ 0.15 \cdot Ra^{1/3} & \text{para } 10^7 < Ra < 10^{11} \end{cases}$ | Intercambio de calor mediante convección natural sobre toda la superficie                                                |
| **Superficie lateral del lecho de arena**  | Pared, transferencia de calor por convección | $Nu = \left(0.825 + \frac{0.387 \cdot Ra^{1/6}}{\left[1+\left(\frac{0.492}{Pr}\right)^{9/16}\right]^{8/27}}\right)^2$                          | —                                                                                                                        |
| **Superficie inferior del lecho de arena** | Pared, transferencia de calor por convección | $Nu = 0.27 \cdot Ra^{1/4} \quad \text{para } 10^5 < Ra < 10^{11}$                                                                              | —                                                                                                                        |
Las ubicaciones de todas las condiciones de contorno dentro del dominio computacional se muestran en la siguiente figura 
![[Numerical analysis of the prototype of the high-temperature thermal energy storage based on sand bed-1791502047397.webp]]*Fig. 5: ubicación de las condiciones de borde individuales en la geometría del dominio computacional.*
El intercambio de las paredes con el entorno ambiental se modelo como convección natural utilizando el coeficiente de transferencia de calor por convección ($h_c$) y el número de Nusselt ($Nu$)
$$  
\mathbf{h_c = \frac{Nu \cdot \lambda}{L}} \quad \left[\frac{\text{W}}{\text{m}^2\cdot\text{K}}\right] \quad \text{(Ecuación 4)}  
$$
_Donde:_  
• $\lambda$ es la conductividad térmica del aire circundante.  
• $L$ es la longitud característica de las paredes verticales u horizontales.  
• $Nu$ se calcula individualmente para cada superficie del tanque utilizando correlaciones empíricas basadas en el número de Rayleigh ($Ra$) y Prandtl ($Pr$). 
	- en la tabla 5 se muestran las formulas para determinar Nu para las paredes horizontales y verticales del almacenamiento térmico. 

> [!NOTE] Dominio computacional
> - es la región geométrica que el software va a resolver numéricamente. Es el volumen que se discretiza en una malla y donde se aplican las ecuaciones de gobierno 

> [!NOTE] Numero de Rayleigh (Ra)
> es un numero adimensional que se usa en transferencia de calor para caracterizar la convección natural. $Ra=Gr\cdot Pr$ donde $Pr$ es el numero de Prandtl ($Pr=\frac{v}{\alpha}$). Este valor **mide la intensidad de la convección natural**:
> - Ra bajo (<$10^{3}$) el calor se transmite principalmente por conducción, el fluido esta casi quieto 
> - Ra intermedio ($10^{3}<Ra<10^{9}$): se da convección natural laminar, el fluido se mueve suavemente en capas 
> - Ra alto ($Ra>10^{9}$): convección natural turbulenta, el fluido se mezcla caóticamente


> [!NOTE] Análisis de las condiciones de borde
> - En el modelado solo se dibujo el volumen de la arena, el acero y la lana mineral no. Cuando el articulo habla de ‘paredes externas’ hace referencia a las caras o fronteras del dominio de la arena las cuales representan físicamente a la superficie exterior del aislamiento, la que da al aire de la habitación.
> 	- Es decir que el solver aplica la perdida de calor directamente sobre la superficie de la arena pero usando la opción de ‘Shell Conduction’ para atravesar la lana mineral.
> - Para las paredes externas (perdidas al ambiente) se plantea que el calor se pierde por convección natural hacia el aire de la habitación. Pero el **coeficiente de transferencia de calor calculado no es solo del aire exterior, es el coeficiente combinado**
> 	- Se calcula mediante las correlaciones de la tabla 5 y asume que, como el espesor del aislamiento es fijo, el modelo ya integra esa resistencia.
> - La física de la convección es distinta, y por ende el coeficiente de convección, según la orientación de la superficie (por que el aire caliente va subiendo):
> 	- **Techo (Superficie Superior - Horizontal):** El aire caliente que toca el techo se caliente, se vuelve menos denso y asciende libremente sin obstáculos. Esto genera mucha renovación de aire y por lo tanto una mayor perdida de calor
> 	- **Pared Lateral (Cilindro - Vertical):** El aire caliente sube pegándose a la pared vertical. La correlación (Churchull y Chu) es mas compleja ya que combina régimen laminar y turbulento a lo largo de la altura.
> 	- **Fondo (Superficie Inferior - Horizontal):** El aire caliente toca la base fría, tiene a quedarse atrapado debajo del tanque y no tiene una vía de escape natural clara por lo que la convección es mas débil por lo que pierde menos calor 
> - **Condición de contorno de las resistencias**
> 	- se modelan como flujo de calor constante con un valor de 4.77 x10^4 W/m^2. Esto sale de dividir la potencia nominal del calefactor (1400W) por la superficie del tubo calefactor
> 	- Esta condición convierte la superficie del calefactor en una fuente de calor pero como la arena conduce mal, la T de esa superficie se dispara. En la sección 6 tuvieron que implementar una lógica de control para apagar los calefactores si su T superaba los 1000K  
#### Resultados del análisis de sensibilidad de la malla 
se hizo un análisis de sensibilidad para determinar el tamaño de celda optimo para la cuadricula numérica. El proceso se dividió en dos etapas: ajustar el tamaño global de la celda y modificar el tamaño de la agregación local en la región del calentador 
![[Numerical analysis of the prototype of the high-temperature thermal energy storage based on sand bed-1791505456380.webp]]*Fig. 6: comparación de valores de T en puntos de medición en función del numero de celdas de la malla numérica. A) modificación del tamaño global de la celda, B) modificación del tamaño local de la celda en la superficie del calentador. Muestra los valores de T en los puntos de medición ($T_{1},T_{2},T_{3}$), la T máxima y media de los calentadores ($T_{h,max},T_{h,ave}$) y la temperatura máxima y media de la arena ($T_{s,max},T_{s,ave}$)*
La primera etapa mostro que cambiar el tamaño global de la celda en el rango de 0,1-0,0025m no tiene ningún efecto sobre los valores de T en los puntos de medición y en la temperatura promedio de la arena. Pero las T en la superficie del calentador y la T máxima de la arena, que esta cerca de los calentadores, no se estabiliza al aumentar el tamaño global de las celdas, por este motivo se hizo un segundo análisis del efecto de la densidad de red local. Se revelo que el resto de los parámetros muestran estabilización para tamaños de células locales menores a 0,0005 m. 
Los ajustes finales de la malla que se implementaron en el modelo asumieron un tamaño de celda global de 0,05m y un tamaño local de 0,0005 m en la superficie del calentador. 
## Sección 3: Validación del Modelo Numérico
**Procedimiento de Validación:**
- Calentamiento de 2 horas
- Estabilización de 22 horas
- Comparación de 3 puntos de medición (T₁, T₂, T₃) entre la simulación y los valores del experimento. 
![[Numerical analysis of the prototype of the high-temperature thermal energy storage based on sand bed-1791506541409.webp]]*Fig. 7: Comparación de lecturas de T en puntos de medición del experimento y la simulación*

**Resultados de Validación:** el modelo numérico demostró una convergencia excelente con las mediciones experimentales de los puntos medidos. Esto valido el uso del modelo para análisis de variantes geométricas mas complejas
- **T₁:** Diferencia promedio de 14 K
- **T₂:** Diferencia promedio de 9 K
- **T₃:** Diferencia promedio de 20 K
Los parámetros parámetros termodinámicos del lecho de arena son de la referencia mencionada anteriormente ([Propiedades de los materiales granulares como medio de transferencia y almacenamiento de calor en aplicaciones CSP](https://www.sciencedirect.com/science/article/pii/S0927024815003062))

**Observaciones:**
- Las desviaciones se atribuyen a diferencias en la difusividad térmica de la arena utilizada vs. la de referencia (la del artitulo)
- El modelo subestima ligeramente la velocidad de calentamiento y enfriamiento
- Las diferencias no impactan significativamente el análisis variacional
- El modelo es suficiente para estudios comparativos

**Distribuciones de Temperatura:** se tomaron contornos en dos secciones transversales de la geometría de almacenamiento, como se muestra en la siguiente figura. 
![[Numerical analysis of the prototype of the high-temperature thermal energy storage based on sand bed-1791507314429.webp]]*Fig. 8: Ubicación de las secciones transversales de las cuales se tomaron las distribuciones de temperatura.*

- **A - Plano vertical**
- **B - Plano horizontal**
![[Numerical analysis of the prototype of the high-temperature thermal energy storage based on sand bed-1791507842668.webp]]*Fig. 9: Distribución de T dentro del lecho de arena para las seccione transversales A y B. La fila 1 es para 2 horas de simulación, la fila 2 es para 12 horas y la fila 3 es para 24 horas.*

**Analisis**: 
- a t=2h, justo despues de apagar los calentadores, hay una diferencia de temperatura significativa en el volumen del lecho 
- después de 10h de estabilización, se observa una distribución uniforme de la T en la sección horizontal. La distribución de T (Disminuye a medida que se aleja del centro) persiste hasta el final de la simulación. 
- A medida que pasa el tiempo disminuye la T media del lecho y también la diferencia entre la T de las zonas mas frías y mas cálidas. 

En la siguiente tabla se ve la comparación de valores de temperatura dentro del lecho de arena para diferentes pasos de tiempo.

| Tiempo [h] | Temperatura media de la arena [K] | Temperatura máxima de la arena [K] | Temperatura mínima de la arena [K] | Diferencia de temperatura dentro del lecho de arena [K] |
| ---------- | --------------------------------- | ---------------------------------- | ---------------------------------- | ------------------------------------------------------- |
| 2          | 470                               | 1392                               | 293                                | 1099                                                    |
| 12         | 469                               | 554                                | 391                                | 163                                                     |
| 24         | 436                               | 491                                | 400                                | 91                                                      |
Esto demuestran un alto potencial de almacenamiento de calor en la arena debido al bajo coeficiente de conductividad térmica de la arena, que forma una barrera aislante natural cerca de las paredes de almacenamiento, aumentando así el tiempo necesario para enfriar el lecho. 
## Sección 4: Coeficiente de Conductividad Térmica Efectiva del Fluido Encerrado
Para preparar el modelo de descarga, se añadió un intercambiador de tubos helicoidales con aire estacionario en su interior. Se usa aire ya que es de bajo costo y puede alcanzar altas T.
Durante el proceso de descarga el aire fluye de forma forzada lo cual requiere ecuaciones de turbulencia dinámicas, pero durante las fases de carga (calentamiento) y estabilización térmica (reposo) las válvulas de aire están cerradas y el fluido dentro de las tuberías esta estacionario o encerrado
Aun estando estacionario el fluido no permanece completamente inmóvil, debido a los intensos gradientes térmicos de la arena, las capas de aire cercanas a las paredes calientes del tubo disminuyen su densidad y ascienden, mientras que las capas mas frías en el centro descienden, provocando un fenómeno de convección natural interna. Simular este movimiento para periodos de tiempo muy largos demandaría un tiempo de computo impráctico, por ello los autores simplificaron e la siguiente manera: **representar la convección del fluido estacionario mediante un modelo puramente de conducción solida equivalente**

Todo el fenómeno de transferencia de calor combinada (conducción + convección natural) se agrupo en un único parámetro llamado **coeficiente de conductividad térmica efectiva**
$$  
k_{eff}=k_c \cdot Nu \quad \text{W/m.K}  
$$
**Donde:**
- **k_eff:** Conductividad térmica efectiva del fluido encerrado (aire inmóvil) (W/mK)
- **k꜀:** Conductividad térmica del fluido (tablas)
- **Nu:** Es una variable adimensional que define la relación entre la transferencia de calor convectiva y la conductiva pura.
$$  
\mathbf{Nu} = \frac{h_c \cdot L}{k_c} \quad \text{(Ecuación 6)}  
$$
Si Nu=1 el calor se transmite únicamente por conducción (las corrientes de convección son inexistentes o despreciables). SI Nu>1 existe convección natural que incrementa la forma transferencia de calor a través del fluido

El coeficiente de transferencia de calor esta estrechamente relacionado con la naturaleza del flujo, se puede determinar con la ayuda de la correlación de Nusselt, que en consecuencia permite determinar la expresión correspondiente para Nu.
Para estimar este numero de Nusselt bajo complejas condiciones físicas del lecho los autores asimilaron la geométrica helicoidal del tubo con la correlación de un fluido encerrado en un contenedor inclinado un cierto Angulo. La compleja ecuación empírica es:
$$  
\mathbf{Nu} = 1 + 1.44 [ 1 - \frac{1708}{Ra \cdot \cos \theta}]^+ + ( 1 - \frac{1708(\sin 1.8\theta)^{1.6}}{Ra \cdot \cos \theta}) + [ \frac{(Ra \cdot \cos \theta)^{1/3}}{18} - 1 ]+ \quad \text{(Ecuación 7)}  
$$
*Las expresiones que tienen un símbolo + de exponente quiere decir que si toma valor negativo entonces se debe establecer en cero*

**Numero de Rayleigh (Ra)**: cuantifica la fuerza de flotabilidad (convección) frente a las fuerzas viscosas y de difusión térmica del fluido:
$$  
\mathbf{Ra = Gr \cdot Pr = \left\{ \frac{g \beta \Delta T L^3}{\nu^2} \right\} \cdot \left\{ \frac{\nu}{\alpha} \right\}} \quad \text{(Ecuación 8)}  
$$
_Donde:_  
• $Gr$ es el número de Grashof (relación entre fuerzas de flotación y viscosas).  
• $Pr$ es el número de Prandtl (difusividad de momentum vs. difusividad térmica).  
•$g$ es la aceleración de la gravedad.  
• $\beta$ es el coeficiente de expansión térmica volumétrica del aire.  
•$\nu$ es la viscosidad cinemática y $\alpha$ es la difusividad térmica.  
• $\Delta T$ es el diferencial térmico crítico entre las paredes opuestas del contenedor/tubo.

Para aplicar con precisión el termino $k_{eff}$ el programa tendría que calcular de forma dinámica el termino $\Delta T$ para cada celda individual del fluido en cada paso de tiempo. Sin embargo la arena presenta una distribución de T heterogénea y dinámica durante la carga (zonas calientes cerca de los calentadores y zonas frías en la periferia)
Es muy demandante y complejo calcular dinámicamente el $\Delta T$ por lo que se opto por una simplificación que se justifica en una comparación de dos simulaciones (las simulaciones se hicieron para la primera variante de distribución de calentadores que se muestra en la sección 5):
- Conducción pura simplificada: se configuro el aire encerrado dentro del tubo simplemente con su conductividad térmica molecular como si fuera un solido inmóvil
- Peor escenario térmico (convección exagerada): se calculo el valor máximo posible de conductividad efectiva bajo las condiciones térmicas mas extremas:
    - diferencial máximo: la simulación inicia a T ambiente y el lecho alcanza T de hasta 407K en la periferia de los tubos, lo que da un diferencial absoluto de $\Delta T \approx 114\text{ K}$. Al proyectar este diferencial en la curva de la fig. 10 se obtiene un coeficiente de conductividad efectiva máxima de $k_{\text{eff}} \approx \mathbf{0.21} \text{ W/(m.K)}$
    - se corío la simulación completa forzando a que todo el aire del tubo tuviera este valor constante y sobredimensionando. 
Al comparar ambos extremos (conducción mínima vs convección extrema) la desviación relativa máxima en el comportamiento térmico general de la cama de arena no supero el 0.2%

Además se demostró que a medida que el proceso de calentamiento avanza, la T de la arena y del aire dentro del tubo tienden a igualarse térmicamente lo que provoca que el gradiente real $\Delta T$ local disminuya drásticamente hacia cero, reduciendo aun mas cualquier posible aporte de la convección natural.
![[Numerical analysis of the prototype of the high-temperature thermal energy storage based on sand bed-1791510055473.webp]]*Fig. 10: Dependencia del coeficiente de transferencia de calor efectivo en la diferencia de temperatura en lados opuestos del encerramiento*
![[Numerical analysis of the prototype of the high-temperature thermal energy storage based on sand bed-1791510269344.webp]]*Fig. 11: comparación de los resultados de la simulación para variantes que suponen diferentes coeficientes de transferencia de calor del fluido, con la desviación relativa resaltada*

Por ende se concluye en que es físicamente valido y optimo tratar el aire estacionario de los tubos como si fuera un material puramente solido utilizando su conductividad molecular estándar (sin convección) durante las simulaciones de carga y reposo.

> [!NOTE] que implica para el desarrollo de pila de arena
> - se pueden omitir mallas fluidas complejas en las fases donde la bomba de aire esta apagada, el modelo puede tratar los tubos metálicos y el aire interno como simples volúmenes solidos con parámetros físicos, reduciendo el costo computacional de sus cálculos de diseño
> - **Reducir perdidas térmicas de diseño:** el aire estancado actúa como un aislante adicional transitorio durante las horas de sol, evitando que el calor inyectado al núcleo de arena se escape. 
> - **cuanto mas homogénea sea la distribución de la T dentro del lecho de arena, menor será la contribución de convección natural para el transporte de calor dentro del dominio fluido cerrado.**
## Sección 5: Efecto de la Distribución de Calefactores en la Eficiencia de Carga
> [!NOTE] Resumen de sección
> - en la validación (sección 3) el modelo funciona. En esta sección se estudia como conviene colocar los calefactores dentro del lecho para que el almacenamiento sea lo mas eficiente posible. 
> - se añade un intercambiador de tubos y se cambia a 6 calefactores de 1kW

Al añadir el intercambiador de tubos para la descarga, la geometría pierde la simetría axial por lo que se elimina la condición de simetría y se tiene que simular el tanque entero
![[Numerical analysis of the prototype of the high-temperature thermal energy storage based on sand bed-1791516367717.webp]]
	*Fig. 12: geometría modificada del modelo con intercambiadores de calor de tuberías*
**Modificaciones del Modelo:**
- Añadido intercambiador de tubos
- 6 calefactores × 1000 W. Esto facilita una distribución uniforme de los calentadores. 
- Geometría completa (sin simetría axial)
El cambio de geometría genero un cambio en la malla de calculo que se realizo de acuerdo a los análisis de sensibilidad anteriores. 
Debido a que no se consideran fenómenos convectivos dentro del dominio del fluido, el aire estuvo estacionario durante la simulación. Por esto, fue suficiente un tamaño de las celdas fluidas igual al tamaño de las celdas solidas elegidas en base al análisis de sensibilidad previo. 
	- Esto quiere decir que el aire que esta dentro del intercambiador de tubos no se movió, se modelo como fluido estacionario con velocidad 0 por lo que no se resolvieron las ecuaciones de movimiento del fluido y el calor se transmitió solo por conducción.
	- El aire esta quieto ya que el tubo esta cerrado y no hay entrada ni salida de aire, solo esta para futuras simulaciones de descarga. 
	- Como no hay capas limites ni gradientes de velocidad, no se necesita refinar la malla cerca de las paredes del tubo y por esto se puede usar el mismo tamaño de malla que el de la arena 

A continuación se muestra el mallado y los parámetros de la misma. 
![[Numerical analysis of the prototype of the high-temperature thermal energy storage based on sand bed-1791517405283.webp]]
**Parámetros de la Nueva Malla:**

| **Parámetro**                   | **Valor**     | **Valor permitido según la documentación del Manual de banco de trabajo de ANSYS [[36](https://www.sciencedirect.com/science/article/pii/S0360544225031147?cf_chl_tk=qkDfwx3jrMlA.bIpSE53PTz6VuQ0NJP7xw2IuWqzB.0-1789323009-1.0.1.1-j4QdxQ28596BuYYBoNwZKqKSkUfpL0icD5NnjT7CP7A#bib36)]** |
| ------------------------------- | ------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Número de nodos                 | 25 334 927    | –                                                                                                                                                                                                                                                                                         |
| Número de celdas                | 4 903 347     | –                                                                                                                                                                                                                                                                                         |
| Calidad ortogonal máxima/mínima | 0,998/0,5     | >0,05/∼1                                                                                                                                                                                                                                                                                  |
| Calidad ortogonal promedio      | 0,960         | >0,6                                                                                                                                                                                                                                                                                      |
| Asimetría mínima/máxima         | 0,00134/0,498 | ∼0/<0,95                                                                                                                                                                                                                                                                                  |
| Asimetría promedio              | 0,039         | <0,4                                                                                                                                                                                                                                                                                      |
Se investigaron 7 variantes diferentes de distribución del calentador dentro del lecho de arena, como se ve a continuación. Luego se simula de la siguiente manera: 2 horas de calentamiento (los calefactores están encendidos) y 46 horas de estabilización (los calefactores se apagan y el calor se redistribuye). 
	- 1 distribución uniforme 
	- 2 calefactores cerca del eje central 
	- 3 calefactores cerca de las paredes 
	- 4 a 7 distribuciones mixtas 
![[Numerical analysis of the prototype of the high-temperature thermal energy storage based on sand bed-1791518113571.webp]]
Se comparan los resultados de cada variante usando: temperatura mínima, máxima y promedio del lecho de arena $T_{s,max},T_{s,{min} \land T_{s,ave}}$ y diferencia de temperatura entre la máxima y la mínima $\Delta T$
También se determina la cantidad de energía neta almacenada en el lecho $E_{nett}$. 
Se evalúa con los siguientes parámetros

| Métrica                        | Qué mide                                            | Interpretación                                                                                                               |
| ------------------------------ | --------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------- |
| **SR (Storage Ratio)**         | $SR=\frac{E_{nett}}{E_{input}}$                     | Fracción de la energía eléctrica (energía de entrada) que queda almacenada en la arena. Un SR alto significa pocas pérdidas. |
| $\Delta T=T_{s,max}-T_{s,min}$ | Diferencia entre la zona más caliente y la más fría | Un ΔT bajo indica buena uniformidad térmica.                                                                                 |
| $T_{h,max}$                    | Temperatura máxima del calefactor                   | Un valor alto es peligroso.                                                                                                  |
Los resultados para t=2h, t=24h y t=48 se muestran en la siguiente tabla y gráficos 
![[Numerical analysis of the prototype of the high-temperature thermal energy storage based on sand bed-1791519705322.webp]]
![[Numerical analysis of the prototype of the high-temperature thermal energy storage based on sand bed-1791519786469.webp]]
**Selección de la Mejor Variante (Variant 2):** la que los calefactores están agrupados cerca del eje. 
- Alto valor de SR
- Temperatura máxima de calefactor más baja (1240 K)
- Distribución de temperatura más estable
- es la mejor ya que los calefactores cerca del eje están rodeados de arena por todos lados, el calor se distribuye mejor y no escapa tan fácilmente hacia las paredes. 

**Observaciones:**
- colocar los calentadores cerca del centro del lecho de arena produce menos perdidas al medio ambiente, pero esto aumenta significativamente su temperatura ya que el calor no se disipa bien y se sobrecalientan. 
- Colocar calefactores cerca de las paredes (Variant 3) provoca mayores pérdidas
- Aislamiento subóptimo (10 cm) resulta en pérdidas significativas. Esto es así ya que incluso en la mejor variante, el SR es solo de 0.67 lo cual significa que un tercio de la energía eléctrica se perdió. Esto se ve en la sección 6
**Conclusión**: entonces la distribución optima es con calefactores cerca del eje central, pero no demasiado juntos. Esto maximiza la retención de calor y minimiza el riesgo de sobrecalentamiento. Además el aislamiento de 10 cm es insuficiente y debe optimizarse. 
## Sección 6: Análisis de Diferentes Esquemas de Calentamiento
> [!NOTE] de que trata esta sección?
> - la anterior sección plantea dos problemas: 1- aislamiento insuficiente, cual es el espesor optimo?; 2- riesgo de sobrecalentamiento, como se controlan los calefactores?
> - en esta sección se busca optimizar el espesor del aislamiento mediante un problema de optimización y se implementa la lógica de control binario

se detectaron 2 problemas y se prodcedio al estudio de diferentes esquemas de calentamiento
### 1. Aislamiento Insuficiente: 
Se encontró el problema de que el aislamiento era insuficiente. Tampoco se puede aumentar tanto el espesor ya que esto también aumenta la superficie de transferencia de calor (por convección) al exterior aumentando así las perdidas. 
Se determina el espesor optimo de aislamiento para el cual las perdidas alcanzan un valor mínimo resolviendo la ecuación diferencial de conductividad térmica para un cilindro y para una pared plano en el caso de las bases 

**Ecuación de Conducción para Cilindro:**
$$ \frac{ \partial  }{ \partial r } \left( r \frac{ \partial T }{ \partial r } \right)=0 $$
**Ecuación de Conducción para Pared Plana:**
$$ \frac{ \partial^{2} T }{ \partial x^{2} } =0 $$
**Donde:**
- **r:** Distancia desde el eje del cilindro (m)
- **x:** Distancia desde el lado interior del aislamiento (m)
Las ecuaciones anterior son simplificaciones de la ecuación de conducción de calor completa e incorporan los siguientes supuestos: el calor especifico, la conductividad térmica y la densidad del material son valores constantes y el análisis en si es para un problema estacionario. A pesar de estas simplificaciones, el modelo calculado muestra el problema del aumento de la superficie de transferencia de calor. 
Los resultados se muestran en el siguiente grafico de flujo de calor perdido en función del espesor de la capa aislante. El mínimo de la función se puede observar para un **espesor de 0,403 m**. 
![[Numerical analysis of the prototype of the high-temperature thermal energy storage based on sand bed-1791578416839.webp]]
**Resultado:** Espesor óptimo ≈ 0.403 m

### 2. Sobrecalentamiento de Calefactores: 
la T de los calentadores es muy alta durante el funcionamiento. 
- Temperatura máxima segura (datos proporcionados por fabricantes): ~1073 K
- Solución: Implementación de lógica de control binario que impidiera que el elemento se derritiera en condiciones reales 

**Lógica de Control (Histeresis):**
Para evitar que los calefactores se fundan, implementan una **histéresis**:
- Si $T_{calefactor}\leq 673 K \to \text{encender}$
- Si $673K<T_{calefactor}< 1073 K \to \text{mantener estado anterior}$
- Si $T_{calefactor}\geq_{1}073 K \to \text{apagar}$
Se llama $T_{res}$ a la T de reinicio del calentador, cuanto mas alta sea, antes vuelve a encenderse y mas frecuentemente cicla. En la implementación anterior $T_{res}=673 K$.
Implementar este enfoque para controlar el funcionamiento de los calentadores era complejo ya que la alta T es riesgosa para los sensores
### Esquemas de Calentamiento Analizados: 
Se realizaron varias simulaciones para distintos programas de calefacción, cada uno de ellos durante un periodo de 168h (7 días), durante el cual se analizo el cambio de T promedio en el lecho y la T de los calentadores, así como los momentos de arranque y apagado. 
Los esquemas son:
1. **Calentamiento continuo con T_res= 673 K**  
    Las resistencias pueden funcionar en cualquier momento, pero ciclan según el control de temperatura.
2. **Calentamiento continuo con T_res​= 773 K**  
    Igual que el anterior, pero la resistencia se reinicia a mayor temperatura.
3. **Calentamiento continuo con T_res= 883 K**  
    Este caso es solo ilustrativo, porque supera la transición de cuarzo alfa a beta (~846 K), y el modelo simplificó las propiedades térmicas para temperaturas menores.
4. **Tarifa G12**  
    Es una tarifa eléctrica polaca con horas de precio bajo y alto. En la simulación, las resistencias solo se encienden durante las horas de precio bajo. Se usa T_res= 673 K.
5. **Fotovoltaica de verano (PVs​) e invierno (PVw)**  
    Se crean perfiles de operación según la disponibilidad solar en un día estadístico de verano y de invierno. Las resistencias solo funcionan cuando hay suficiente energía solar. También usan T_res=673K

**Resultados de la Simulación (168h):**

![[Numerical analysis of the prototype of the high-temperature thermal energy storage based on sand bed-1791579321269.webp]]
![[Numerical analysis of the prototype of the high-temperature thermal energy storage based on sand bed-1791579336580.webp]]
	*Fig. 17: variación de la T media del lecho de arena para variantes que suponen calentamiento continuo*

**Hallazgo 1:** El calentamiento continuo es mas rápido y alcanza una mayor T final. 
**Hallazgo 2**: Todos los esquemas pueden cargar el lecho a $\approx{6}50K$ en 7 días, aunque el continuo es mas rápido. 

| Esquema          | Tiempo para alcanzar 650 K |
| ---------------- | -------------------------- |
| Continuo (673 K) | 71.03 h                    |
| G12              | 91.00 h                    |
| PV verano        | 113.50 h                   |
| PV invierno      | 130.14 h                   |

Esto demuestra **flexibilidad**: el sistema funciona con tarifas variables, con solar intermitente, o con ambas.

**Hallazgo 2: El SR es similar en todos los esquemas (~0.83).**, lo que indica que independientemente de cómo se cargue, la **eficiencia final es parecida**. Lo que cambia es el **tiempo** necesario para cargar.

**Hallazgo 3**: el control de la T limita la cantidad máxima de energía que se puede almacenar por día 

**Hallazgo 4**: un $T_{res}$ mas alto hace que las resistencias se enciendan mas seguido lo que puede dañar contactores o relés. 
![[Numerical analysis of the prototype of the high-temperature thermal energy storage based on sand bed-1791759790711.webp]]
	*Fig. 18: variación de la T media del lecho de arena para: A) T mínima del calentador Tres=673 K, B) T mínima del calentador Tres=873 K*. 
En la figura 18 se ve como el que tiene el Tres mas alto tiene una mayor cantidad de activaciones. 
- Con T_res=873, los calefactores se encienden y apagan **cada 8 minutos**, con T_res=673, la frecuencia es mucho menor (~1 activación cada 30 min).

**Hallazgo 5: La densidad energética de la arena es ~3 veces mayor que la del agua.**
- **Arena (a 883 K):** 860.44 MJ/m³ (239.01 kWh/m³)
- **Agua (a 363 K):** 394 MJ/m³ (81.7 kWh/m³)
Esto confirma que la arena es un medio de almacenamiento mucho más compacto.

**Conclusión:** el sistema puede cargarse con cualquier esquema realista sin perder eficiencia. Sin embargo, **se debe elegir una T de reinicio baja (673 K)** para evitar el desgaste de los calefactores. 


> [!NOTE] A posterior
> - se puede investigar los intervalos óptimos entre los ciclos de carga 
> - una solución a este problema podría ser la creación de una serie de unidades de almacenamiento térmico mas pequeñas que se cargarían secuencialmente. Seria posible mantener una ingesta continua de exceso de energía evitando al mismo tiempo el sobrecalentamiento de los calentadores

## Sección 7: Descarga del Almacenamiento Térmico
> [!NOTE] Resumen de sección
> - hasta ahora solo se vio como cargar el almacenamiento, en esta se sección se ve como descargar y extraer calor 
> - Que se hace?
> 	- se modifica el modelo 
> 	- define 6 variantes de velocidad de aire 
> 	- simula la descarga completa 
> 	- evalúa con dos métricas (DR y $P_{max}$). 
> 	- Mide la caída de potencia después de 2 horas y después de 10
> 	- Evalúa los resultados 
### Modificaciones del Modelo:
- Flujo de aire a través del intercambiador de tubos. Se añaden las ecuaciones de continuidad, momentum, energía y turbulencia.
- Se define una velocidad de entrada (constante y a T ambiente) y una presión de Salida (P atmosférica constante. 
![[Numerical analysis of the prototype of the high-temperature thermal energy storage based on sand bed-1791760909261.webp]]
	*Fig. 21: ubicación de las condiciones de contorno modificadas que permiten el flujo de fluido en tuberías*
**Ecuaciones Adicionales (Flujo de Fluido):**
La consideración del flujo de fluido en el modelo afecto las ecuaciones rectoras utilizadas en el solver de ANSYS Fluent. Se incluyen las siguientes ecuaciones. 
**Conservación de Energía (convección incluida):**
$$ \rho\frac{ DT}{Dt}=\frac{k_{c}}{C_{p}}\left( \frac{ \partial^{2}T }{ \partial x^{2} } + \frac{ \partial^{2}T }{ \partial y^{2} } + \frac{ \partial^{2}T }{ \partial z^{2} }  \right) $$
**Conservación de Masa (Continuidad):**
$$ \frac{Dp}{Dt}+\rho  \nabla\vec{\cdot V}=0$$

**Conservación de Momento (Ecuación de Navier-Stokes):**
$$\rho\frac{ Du}{Dt}=-\frac{ \partial p }{ \partial x } +\mu \nabla^{2}\mu$$
$$\rho\frac{ Dv}{Dt}=-\frac{ \partial p }{ \partial y } +\mu \nabla^{2}v$$
$$\rho\frac{ Dw}{Dt}=-\frac{ \partial p }{ \partial x } +\mu \nabla^{2}w$$

**Modelo de Turbulencia k-ε:** El flujo del aire en la tubería, independientemente de la velocidad analizada del medio, era turbulento. Se utilizo el siguiente modelo para calcular el flujo cerca de las paredes del intercambiador:
Transporte de la energía cinética turbulenta k: 
$$ \frac{Dk}{Dt}=\frac{G_{k}}{\rho}-\varepsilon+\nabla \cdot\left( \frac{\nu_{t}}{\sigma_{k}}\nabla k \right) $$
Transporte de la tasa de disipación de esa energía turbulenta $\varepsilon$:
$$ \frac{D\varepsilon}{Dt}=\frac{C_{1\varepsilon}\varepsilon}{k} \frac{G_{k}}{\rho}-\frac{C_{2\varepsilon}\varepsilon^{2}}{k}+\nabla  \cdot \left( \frac{\nu_{t}}{\sigma_{\varepsilon}}\nabla \varepsilon \right) $$

**Donde:**
- **D/Dt:** Derivada sustancial (material). Es la derivada material (cambio local + transporte por el flujo medio). 
- **u, v, w:** Componentes de velocidad en x, y, z (m/s)
- **p:** Presión (Pa) o es la densidad del aire? 
- **μ:** Viscosidad dinámica (Pa·s)
- **k:** Energía cinética turbulenta (m²/s²)
- **ε:** Tasa de disipación de energía cinética turbulenta (m²/s³)
- **G_k:** Producción de energía cinética turbulenta por los gradientes de velocidad media. 
- **ν_t:** Viscosidad turbulenta (m²/s)
- **σ_k, σ_ε:** Números de Prandtl turbulentos
- **C₁ε, C₂ε:** Constantes empíricas del modelo

Además se modifico la malla numérica para el dominio del fluido dentro del lecho de arena. Las celdas dentro de este volumen se redujeron para permitir valores $y+$ satisfactorios en las paredes de la tubería. Para el modelo $k-\varepsilon$, estos valores deben estar en el rango entre 20 y 200. A continuación se muestra la malla y se la describe en la siguiente tabla 
![[Numerical analysis of the prototype of the high-temperature thermal energy storage based on sand bed-1791786282292.webp]]
![[Numerical analysis of the prototype of the high-temperature thermal energy storage based on sand bed-1791786307865.webp]]
	*Tabla 11: se ve que el numero de celdas es similar al caso anterior pero en esta nueva malla la distribución cambio: mas fina cerca de las paredes del tubo y mas gruesa en otras zonas*

> [!NOTE] Que quiere decir todo esto?
> - en las secciones anteriores el aire estaba estacionario, en esta sección el aire fluye por la tubería. Este flujo es turbulento y para modelarlo usan el modelo $k-\varepsilon$ en ANSYS Fluent
> - **Que es $y^{+}$?**: es una distancia adimensional a la pared:
> 	$$ y^{+}=\frac{u_{r}y}{\nu} $$
> 	Donde:
> 		- y: distancia desde la pared hasta el centro de la primera celda de la malla 
> 		- $u_{r}$: velocidad de fricción
> 		- $\nu$: viscosidad cinemática del aire 
> 	- Físicamente, $y^{+}$ te dice en que región de la capa limite turbulenta esta tu primera celda:
> 		- $y^{+}<5$: subcapa viscosa (flujo casi laminar)
> 		- $5<y^{+}<30$: capa de transición o buffer 
> 		- $y^{+}>30:$ capa logarítmica (turbulencia totalmente desarrollada)
> - El modelo $k-\varepsilon$ estándar no resuelve esta subcapa viscosa, usa funciones de pared (wall functions) para puentear esa zona. Esas funciones son validas solo si el primer nodo de la malla cae en la capa logarítmica, por eso se recomienda que $20\leq y^{+}\leq{2}00$.
> 	- es lo que menciona el articulo
> 	- Si $y^{+}$ es mas bajo entonces la primera celda esta dentro de la subcapa viscosa o en la zona de transición. Las funciones de pared estándar ya no son validas, necesitaríamos un modelo de bajo Reynolds o un tratamiento de pared mejorado 
> 	- Si $y^{+}$ es demasiado alto entonces la primera celda esta fuera de la capa limite o demasiado lejos de la pared. No se capturan bien los gradientes de velocidad y T cerca de la pared y se cometen errores en la transferencia de calor
> - Por esto, para que el modelo $k-\varepsilon$ de valores confiables, hay que ajustar la malla de modo que el primer centro de celda junto a la pared de la tubería tengo un $y^{+}$ dentro de ese rango
> - **Que hicieron entonces con la malla?**
> 	- redujeron el tamaño de las celdas en el dominio fluido. Al hacerlas mas pequeñas cerca de la pared, el primer centro de celda queda mas cerca de la pared y así $y^{+}$ disminuye hasta entrar en el rango 20-200
> 	- esto se hace refinando la malla en la región cercana a la pared de la tubería (por ejemplo con capas de frontera) y quizás engrosando las celdas en el centro del tubo para no disipar el costo computacional. 
### Simulación: 
Define 6 variantes de velocidad de aire que se ven a continuación. Luego simula la descarga completa de forma que cada simulación dura hasta que el lecho se enfrié a 300 K (T ambiente), esto puede tomar 108 horas o mas 
Luego se evalúa con dos métricas:
- **Relación de Descarga (DR):** Fracción de la energía extraída que sale por el aire (vs la que se pierde en el ambiente). Un DR alto implica una descarga eficiente. $$ DR=\frac{E_{\text{outlet}}}{(E_{outlet}+E_{loss})} $$ **Donde:**
	- ($E_{outlet}$) Energía extraída por el flujo de aire (MJ)
	- $E_{loss}$: Pérdidas de energía al ambiente (MJ)
- Potencia máxima del flujo de aire a la salida del dominio a las 2 y 10 horas

> [!NOTE] Consideración
> - **Condiciones iniciales para la arena:** las condiciones iniciales del modelo coincidieron con los valores obtenidos tras la simulación de calentamiento continuo (673 K). Quiere decir que la arena ya estaba caliente al inicio de la descarga. 
> - La distribución espacial de la T dentro del lecho es la que se obtuvo anteriormente. Así la descarga simula como se enfría ese lecho ya cargado térmicamente
> - **Condiciones iniciales para el aire:** El flujo de aire se calculo por separado y su perfil estabilizado se inicializo para que coincidiera con el modelo calentado
> 	- Que significa esto?
> 		- resolvieron por separado el flujo de aire en la tubería (sin transferencia de calor). Eso les da un **perfil estabilizado**: velocidades, presiones, energía cinética turbulenta $k$ y disipación $\varepsilon$ ya estabilizadas para un caudal dado 
> 		- Ese perfil de flujo estabilizado lo usan como condición inicial del dominio fluido en la simulación de descarga. Es decir, al tiempo t=0 de la descarga, el aire ya esta circulando por la tubería con un flujo totalmente desarrollado, no parte de velocidad cero. 
> 	- luego en la simulación de descarga, se acoplan ambos dominios: la arena caliente transfiere calor al aire que ya esta fluyendo y el aire se va calentando a medida que avanza por la tubería. 
> - se hace así ya que si se arrancara la simulación de descarga con el aire en reposo y la arena caliente, durante las primeras horas el flujo tendría que desarrollarse desde cero. AL inicializar el flujo ya desarrollado, la simulación de descarga comienza directamente en el régimen que interesa: aire fluyendo de forma estable a través de la arena caliente. 
> - Además separa el calculo del flujo del calculo térmico ahorra tiempo computacional 

| **Velocidad (m/s)** | **Flujo másico (kg/h)** | **DR** | **P_max (W)** | **P@0.25h (%)** | **P@0.10h (%)** |
| ------------------- | ----------------------- | ------ | ------------- | --------------- | --------------- |
| 0.5                 | 2.64                    | 0.88   | 280.49        | 0.92%           | 6.40%           |
| 0.75                | 3.97                    | 0.91   | 417.28        | 2.60%           | 11.39%          |
| 1.0                 | 5.29                    | 0.93   | 551.78        | 5.62%           | 17.63%          |
| 2.0                 | 10.58                   | 0.95   | 1028.16       | 17.79%          | 37.24%          |
| 3.0                 | 15.86                   | 0.96   | 1425.42       | 24.24%          | 47.69%          |
| 5.0                 | 26.44                   | 0.97   | 2082.76       | 32.80%          | 59.75%          |

![[Numerical analysis of the prototype of the high-temperature thermal energy storage based on sand bed-1791787438164.webp]]
![[Numerical analysis of the prototype of the high-temperature thermal energy storage based on sand bed-1791787452622.webp]]
### Observaciones Clave de la Descarga:
1. Mayor velocidad de aire → Mayor DR (0.88 a 0.97). 
	- Esto es así ya que a mayor velocidad, el aire se lleva el calor mas rápido y hay menos tiempo para que el calor se pierda al ambiente, por eso el DR sube
2. Mayor velocidad → Mayor potencia máxima (280W a 2082W)
	- El aire frio que entra enfría rápidamente la zona de la arena cercana a las tuberías, esta zona pierde T y como la arena conduce mal, el calor de las zonas mas lejanas no llega a tiempo y se crea un *cuello de botella térmico*
3. Mayor velocidad → Enfriamiento local más rápido cerca de las tuberías
4. Velocidades bajas (0.5 m/s) → Descarga más estable y prolongada
5. Después de ~33h, la potencia converge (~257W) independientemente de la velocidad
	- Esto significa que, a largo plazo, la descarga esta limitada por la conducción de calor dentro de la arena y no por la velocidad del aire. La baja conductividad de la arena se convierte en el factor dominante. 
6. Para velocidades de flujo bajas (0,5 en el grafico), la T del aire en la salida durante todo el periodo analizado es mayor que la T promedio del lecho de arena. 
7. Para v=1 m/s se da que la temperatura del aire a la salida iguala la temperatura promedio del lecho. Esto significa que el aire se lleva el calor de manera uniforme en todas las zonas del lecho, sin crear puntos fríos localizados. 

**Trade-off Identificado:**
- **Alta velocidad:** Mayor potencia instantánea pero enfriamiento local rápido y descarga corta
- **Baja velocidad:** Menor potencia pero descarga más estable y prolongada

> [!NOTE] Conclusión
> - no hay una velocidad optima, si se necesita potencia pico alta (por ejemplo para calentar rápido algo) entonces conviene usar velocidades altas 
> - en nuestra aplicación se necesita descarga estable y prolongada, por lo que es mas conveniente usar velocidades bajas 

![[Numerical analysis of the prototype of the high-temperature thermal energy storage based on sand bed-1791788463330.webp]]
![[Numerical analysis of the prototype of the high-temperature thermal energy storage based on sand bed-1791788467767.webp]]
	*Fig. 26: Distribución de temperatura del lecho de arena para diferentes pasos de tiempo y velocidades de flujo - sección transversal A*
![[Numerical analysis of the prototype of the high-temperature thermal energy storage based on sand bed-1791788488695.webp]]
	*Fig 27. Distribución de temperatura del lecho de arena para diferentes pasos de tiempo y velocidades de flujo - sección transversal B).*
# 3. Parámetros Técnicos Clave

| **Parámetro**                   | **Valor**                                                                                                                         | **Notas**                                                    |     |
| ------------------------------- | --------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------ | --- |
| **Volumen / Masa de arena**     | 205 dm³, 300 kg de arena de cuarzo                                                                                                | Prototipo de laboratorio                                     |     |
| **Capacidad de Almacenamiento** | 860.44 MJ/m³ (239.01 kWh/m³)                                                                                                      | Para T_res=883K, referenciado a 293K                         |     |
| **Potencia de Calefacción**     | 5 × 1400W (experimental) / 6 × 1000W (análisis)                                                                                   | No especificado para el sistema final                        |     |
| **ΔT de trabajo**               | 293K - ~850K (557K de rango útil)                                                                                                 | Temperatura máxima de diseño ~1073K; límite operativo seguro |     |
| **Tipo de Intercambiador**      | - Calefacción: Resistencias eléctricas (tubulares) enterra  Extracción: Intercambiador de tubos con flujo de aire forzado forzado | -                                                            |     |
| **Material Aislante**           | Lana mineral (λ=0.040 W/mK)                                                                                                       | Espesor óptimo calculado: 0.403 m                            |     |
| **Eficiencia Reportada (SR)** | 0.608 a 0.847 (dependiendo de variante) | El máximo SR=0.847 para calentamiento continuo con T_res=883K |  
| **DR (Descarga)** | 0.88 a 0.97 | Dependiendo de la velocidad del aire (0.5 a 5 m/s) |

**Nota:** La potencia de salida máxima observada fue de ~2083W para v=5 m/s, pero con una caída rápida después de 10h (solo 59.75% de la potencia inicial).

# 4. Hallazgos Crítico
### Problema de Conductividad Térmica 
1. **Paradoja Resuelta:** La baja conductividad térmica de la arena (0.6 W/mK a 1073K) no es una desventaja sino una **ventaja estratégica**:
    - Actúa como **aislamiento natural** cerca de las paredes del contenedor
    - Prolonga la retención de alta temperatura durante largos periodos
    - Reduce las pérdidas de calor al ambiente
2. **Control de Sobrecalentamiento:** Implementación de lógica de control binario con histéresis:
    - Temperatura de reinicio: 673K, 773K, 873K
    - Límite máximo seguro: ~1073K (antes de la fusión de la resistencia)
    - Frecuencia de activación: más de 8 minutos para T_res=873K
- Software: ANSYS Woekbench. 
### Optimización del Diseño del Contenedor
1. **Distribución Óptima de Calefactores (Variant 2):**
    - Colocar calefactores **cerca del eje central** del tanque
    - Evitar ubicación cercana a paredes (aumenta pérdidas)
    - Balance entre uniformidad térmica y prevención de sobrecalentamiento
2. **Aislamiento Óptimo:**
    - Espesor calculado: **0.403 m**
    - Demuestra que existe un espesor óptimo (no el máximo posible)
    - Más espesor aumenta superficie de transferencia y puede empeorar pérdidas
### Estrategias de Carga Inteligente
1. **Flexibilidad con Fuentes Renovables y Tarifas:**
    - **Tarifa G12:** Calentamiento solo durante horas de bajo costo eléctrico
    - **PV Verano:** 11.5 horas de carga disponible
    - **PV Invierno:** 5-6 horas de carga disponible
    - Todos los esquemas alcanzan >650K en 7 días
    - SR similar (~0.83) independientemente del esquema
2. **Control de Frecuencia de Activación:**
    - Menor T_res (673K) → Menos ciclos de encendido/apagado → Mayor vida útil
    - T_res=873K → Activación cada 8 minutos → Mayor desgaste
### Rendimiento de Descarga - Trade-off Crítico
1. **Relación Velocidad-Potencia-Estabilidad:**
    - **Baja velocidad (0.5 m/s):**
        - Menor potencia pico (280W)
        - Descarga más estable y prolongada
        - Mayor tiempo para extraer energía almacenada
    - **Alta velocidad (5 m/s):**
        - Mayor potencia pico (2083W)
        - Enfriamiento local rápido cerca de las tuberías
        - Caída de potencia después de las primeras horas
        - **DR más alto (0.97) debido a descarga más rápida**
2. **Punto de Equilibrio Identificado:** v=1 m/s
    - Temperatura de aire iguala temperatura promedio del lecho
    - Flujo de calor equilibrado en toda la superficie del intercambiador
    - Rendimiento óptimo para extracción prolongada
### Innovaciones Metodológicas
1. **Modelo CFD Eficiente:**
    - Simplificación de propiedades sustitutas del lecho de arena
    - Malla de ~4.9 millones de celdas para geometría completa
    - Simulaciones de hasta 168h (7 días) con precisión aceptable
    - Error máximo de validación: 20K (2.3% a 850K)
2. **Simplificación de Convección Natural:**
    - Conductividad efectiva (k_eff) para fluido encerrado
    - Desviación máxima <0.2% usando valores tabulados
    - Ahorro computacional significativo
### Implicaciones Prácticas
1. **Comparación con Almacenamiento por Agua:**
    - **Arena:** 860 MJ/m³ (239 kWh/m³)
    - **Agua (363K):** 394 MJ/m³ (81.7 kWh/m³)
    - **Ventaja:** 3× mayor densidad energética que el agua
2. **Aplicaciones Identificadas:**
    - Calefacción de edificios (residencial y comercial)
    - Procesos industriales de alta temperatura (>500°C)
    - Integración con fuentes renovables intermitentes
    - Recuperación de calor residual industrial
3. **Escalabilidad y Flexibilidad:**
    - Sistema híbrido (eléctrico + aire caliente)
    - Múltiples cargas secuenciales posibles
    - Compatible con excedentes de producción renovable
    - Coste-efectivo y ecológico (arena abundante)
4. **Aplicación a futuro**: se podría implementar inteligencia artificial para optimizar la carga y descarga. 
# Resumen de Recomendaciones para Diseño
1. **Aislamiento:** 40 cm de lana mineral (espesor optimizado)
2. **Calefactores:** Colocar cerca del eje, evitar paredes
3. **Control:** T_res alrededor de 673K para balancear eficiencia y vida útil
4. **Carga:** Adaptar a tarifas o disponibilidad renovable
5. **Descarga:** Velocidad de aire ≤1 m/s para descarga estable y prolongada
6. **Temperatura:** No superar ~1073K (límite de seguridad de calefactores)
7. **Material:** Arena de cuarzo con caracterización previa de propiedades térmicas



