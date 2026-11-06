---
Titulo esp.: Evaluación de mezclas de arena y arena-cobre para un almacenamiento eficiente de energía térmic
Año: 2025
Padre: "[[CUDAR - Desarrollo de Pila de Arena]]"
Importancia:
  - B
URL: https://www.sciencedirect.com/science/article/pii/S2590123025037752?via%3Dihub#fig0006
---
## 1. Idea central
El paper evalúa si la arena del desierto y de la costa de los Emiratos Árabes Unidos puede servir como medio de almacenamiento térmico sensible de baja a media temperatura, y si agregarle cobre (en virutas o polvo) mejora su desempeño. Se midieron las propiedades termofísicas de tres arenas (desierto, playa y montaña) y de seis mezclas arena-cobre, y luego se probó en un tanque de laboratorio con serpentín helicoidal de cobre: 4 h de carga con agua a 80 °C y 12,5 h de almacenamiento aislado.

**Conclusión fundamental:** el cobre aumenta la conductividad térmica de la arena (hasta +85 % con virutas), por lo que la carga y descarga son más rápidas, pero reduce el calor específico, y por eso la arena pura retiene más energía en el tiempo (845 kJ frente a 671 kJ con virutas y 632 kJ con piezas pequeñas). La elección depende de si se prioriza velocidad de transferencia o retención prolongada.

**Glosario**

|Sigla|Significado|
|---|---|
|TES|_Thermal Energy Storage_: almacenamiento de energía térmica|
|SHS|_Sensible Heat Storage_: almacenamiento por calor sensible (sube la temperatura sin cambiar de fase)|
|PCM|_Phase Change Material_: material de cambio de fase|
|TCES|_Thermochemical Energy Storage_: almacenamiento termoquímico|
|CSP|_Concentrated Solar Power_: energía solar concentrada|
|PV|_Photovoltaic_: fotovoltaico|
|GSHP|_Ground Source Heat Pump_: bomba de calor geotérmica|
|XRF|_X-ray Fluorescence_: fluorescencia de rayos X, análisis de composición elemental|
|DSC|_Differential Scanning Calorimeter_: calorímetro diferencial de barrido, mide calor específico|
|TC|_Thermocouple_: termocupla|
|HTF|_Heat Transfer Fluid_: fluido caloportador|
|Cp|Calor específico a presión constante [J/(g·K)]|
|k|Conductividad térmica [W/(m·K)]|
|ρ|Densidad [kg/m³]|
|τ|Constante de tiempo térmica [s]|
|Q|Energía almacenada [kJ o kWh]|
|ASTM|_American Society for Testing and Materials_|

## 2. Resumen por secciones
### 1. Introducción
El paper contextualiza la necesidad de almacenamiento para la energía solar intermitente. Compara los medios de almacenamiento sensible (rocas, agua, aceite, sales, hormigón) y destaca sus problemas: las sales son corrosivas y caras de contener, y el hormigón debe mantenerse por debajo de 500 °C. La arena aparece como alternativa barata, abundante, no tóxica y tolerante a hasta 1000 °C.

Revisa antecedentes: calor específico de arena de desierto a 1100 °C (0,98 kJ/kg·K), uso de arena como aislante en pilotes geotérmicos, y un sistema con arena calentada directamente por radiación solar. El vacío que señala es la mejora sistemática de la arena con aditivos de bajo costo.
### 2. Metodología
Describe el flujo general: caracterización de tres arenas, mezcla con cobre y prueba del prototipo.

**Muestras.** Tres arenas de la UAE:
- **Desierto** (Sharjah): naranja rojiza, textura muy suave.
- **Montaña** (Ras Al-Khaimah): colores variados, muy gruesa, con fragmentos rocosos.
- **Playa** (Ras Al-Khaimah): grisácea, muy uniforme, con conchillas.

**Cobre.** Se usó cobre de desecho en dos formas:
- _Virutas largas_ (6–9 cm): caminos de conducción a lo largo del lecho.
- _Piezas pequeñas_ (0,5 × 0,5 cm): menor distancia de difusión y más contacto entre granos.

**Caracterización:**
- **XRF:** composición química (SiO₂, CaO, etc.).
- **Análisis granulométrico (tamizado ASTM):** clasifica la arena. El desierto resultó _poorly graded_ (granulometría uniforme, muchos poros de aire), la playa _well graded_ y la montaña _silty sand_ (arena limosa).
- **Densidad:** por compactación según ASTM D 698 (húmeda y seca) y por caída libre, que simula el llenado real del tanque.
- **Conductividad térmica:** sonda KD 2 Pro con aguja TR-1, 5 minutos por medición, a 25 °C.
- **Calor específico:** calorímetro DSC de flujo de calor, de 0 a 300 °C, calibrado con zafiro.

### 3. Resultados: arena pura
- **Composición:** el desierto tiene 25 % de SiO₂; la playa tiene ~69 % de CaO (conchillas).
- **Densidad en caída libre** (la más representativa del llenado de un tanque): playa 1,747 g/cm³, desierto 1,625, montaña 1,382.
- **Conductividad térmica:** playa 0,209 W/m·K, desierto 0,201, montaña 0,135. Los valores coinciden con la literatura (arena gruesa ~0,25, fina ~0,15).
- **Calor específico** (a ~300 °C): desierto 1,316 J/g·K, playa 1,075, montaña 0,983. Coincide con el contenido de sílice: más sílice, más calor específico.
- **Estabilidad:** la montaña muestra picos a 114 °C y 256 °C, atribuidos a descomposición de calcio.

**Elección:** la arena de desierto es la más conveniente por su calor específico alto y su comportamiento estable.
### 4. Resultados: mezclas arena-cobre
- **Conductividad térmica** (desierto + cobre, a 10/20/30 %): virutas 0,355 / 0,343 / 0,414 W/m·K; polvo 0,241 / 0,284 / 0,308 W/m·K. Base sin cobre: 0,201. Las virutas aumentan hasta un 85 %, pero el resultado no es monótono con la proporción, lo que los autores atribuyen a una distribución irregular.
- **Calor específico a 298 °C:** la arena pura da 1,321 J/g·K y todas las mezclas bajan (entre 0,875 y 1,101 J/g·K, es decir, caídas de hasta 34 %). Esto se explica porque el cobre tiene un calor específico de ~0,385 J/g·K.
### 5. Interpretación: inercia térmica
Introduce la idea de inercia térmica, producto de ρ, Cp y k. Cuando se agrega cobre sube k pero baja Cp, y el sistema responde más rápido pero guarda menos energía.
Constante de tiempo de un sistema concentrado:
$$\tau=\frac{\rho,C_p,V}{h,A}$$
- **ρ·Cp·V:** capacidad térmica total del medio (cuánta energía puede guardar).
- **h·A:** conductancia térmica hacia el exterior (qué tan rápido la pierde).
- **τ:** tiempo que tarda el sistema en responder. Menos Cp → τ menor → respuesta más rápida pero menos almacenamiento.
### 6. Experimento del tanque
**Montaje:**
- Tanque de acero inoxidable, aislado con espuma, de 20 cm de diámetro y 47 cm de alto, con 18 kg de arena tamizada.
- Serpentín de cobre de 9 vueltas, 4,5 cm de paso y 15 cm de diámetro, por el que circula agua.
- Circulador CARIO CD-200 F: agua a 80 °C y 1,52 L/min, entrando por arriba.
- Termocuplas: dos en la entrada y salida de agua, y tres dentro de la arena (TC-1 al centro, TC-3 a 42 mm, TC-2 a 91,5 mm, cerca del serpentín).
**Procedimiento:**
- **Carga:** 4 h (14 100 s) hasta que la arena se estabiliza cerca de 80 °C.
- **Almacenamiento:** 12,5 h con el tanque aislado y sin circulación.
**Casos:**
1. Arena pura.
2. Arena con virutas de cobre largas (2 % en peso).
3. Arena con piezas pequeñas de cobre (4 % en peso).
**Resultados clave:**
- **Carga:** la arena pura es la más lenta, con gran diferencia entre TC-2 (cerca del serpentín) y TC-1 (centro). Con virutas largas las temperaturas se igualan rápido.
- **Almacenamiento:** la arena pura pierde calor más lento. Con virutas, la temperatura baja rápido. Con piezas pequeñas la caída es escalonada.
- **Energía retenida** (método concentrado, promedio de los tres termopares entre 14 100 s y 45 000 s):

|Caso|Cp (kJ/kg·K)|T inicial → final (°C)|Energía (kJ)|Energía (kWh)|
|---|---|---|---|---|
|Arena pura|1,234|71,8 → 33,7|845,5|0,235|
|Virutas largas (2 % Cu)|0,942|71,7 → 32,1|671,5|0,187|
|Piezas pequeñas (4 % Cu)|0,924|71,2 → 33,8|632,0|0,176|

Se usó Q = m·Cp·ΔT. La arena pura retiene ~26 % más energía que la versión con virutas.

### 7. Cambios en la arena
- **Aglomeración:** tras varios ciclos a ~75 °C aparecen grumos por fusión de impurezas. Son frágiles, pero los autores advierten que a más de 700 °C podría ser un problema.
- **Color:** la arena se aclara levemente después de los ciclos, de forma poco notoria.
### 8. Discusión y conclusiones
Comparan la arena con otros medios: las sales tienen Cp ~1,5 J/g·K y k 0,5–0,6 W/m·K, pero son corrosivas y se degradan por encima de 565 °C; las rocas y el hormigón tienen Cp de 0,7–0,9 J/g·K y no deben superar 500 °C. La arena pura (Cp 1,316 J/g·K, k 0,201 W/m·K) queda en un rango comparable y tolera hasta 1000 °C.

**Conclusión:** para almacenamiento prolongado o nocturno conviene arena pura; para ciclos rápidos o alta potencia, la mezcla con cobre.
## 3. Parámetros técnicos clave
- **Volumen / masa de arena:** 18 kg de arena de desierto tamizada, en un tanque de 20 cm de diámetro y 47 cm de alto. Volumen aproximado: 14,8 L (Ø 20 cm × 47 cm, cálculo propio). Densidad de referencia: 1,625 g/cm³ en caída libre.
- **Potencia y capacidad:**
    - Capacidad almacenada: 0,235 kWh (arena pura), 0,187 kWh (virutas), 0,176 kWh (piezas pequeñas), en 12,5 h.
    - Potencia de carga: **No especificado en el paper.** Solo se indica el caudal (1,52 L/min) y la temperatura del agua (80 °C). Se puede estimar la potencia térmica del agua como Q = ṁ·Cp·ΔT ≈ (1,52/60 kg/s)·4,18·(80 − T_retorno), pero el retorno no se reporta.
    - Potencia de entrega (descarga): **No especificado en el paper.** La descarga no fue ensayada.
- **ΔT de trabajo:** temperatura máxima de la arena ≈ 72–73 °C (agua de entrada a 80 °C), temperatura final tras 12,5 h ≈ 32–34 °C. ΔT de la arena ≈ 38–40 K. Temperatura mínima útil: **No especificado en el paper.**
- **Tipo de intercambiador:** serpentín helicoidal de cobre (9 vueltas, paso 4,5 cm, diámetro 15 cm, tubería de ½ pulgada) inmerso en la arena. El agua caliente circula por dentro y transfiere calor por conducción a la arena. No hay flujo de aire ni aletas.
- **Material aislante:** pared de acero inoxidable con una capa de espuma de 1 cm de espesor. **Material exacto de la espuma: No especificado en el paper.** El tanque no se aisló con lana de roca ni con materiales de alta temperatura.
- **Eficiencia reportada:** el paper no reporta eficiencia de ida y vuelta (_round-trip_). Indica explícitamente que queda para estudios futuros. Solo reporta energía retenida en 12,5 h, sin porcentaje sobre la energía de entrada. Si se quiere estimar: la energía de entrada no se calcula en el paper, así que **No especificado en el paper**.
## 4. Hallazgos críticos
- **Tradeoff central:** el cobre aumenta la conductividad térmica hasta un 85 % (virutas), pero reduce el calor específico entre un 17 % y un 34 %. Resultado: **carga más rápida pero menos energía retenida** (−25 % con virutas).
- **Conductividad:** la arena pura (0,201 W/m·K) es mala conductora, lo que limita la transferencia desde el serpentín. Las virutas largas, distribuidas en capas, forman caminos de conducción que aceleran la equilibración de temperaturas. Las piezas pequeñas tienen efecto menor pero retienen mejor.
- **Por qué la arena pura retiene más:** tiene el calor específico más alto y la menor tasa de pérdida hacia el serpentín y el exterior.
- **Granulometría:** la arena de desierto, uniforme, tiene más poros de aire, lo que reduce k pero facilita el paso de fluido. Un tamizado y una distribución de tamaños más amplia mejorarían la densidad y k (el paper lo menciona para la arena de playa).
- **Estabilidad térmica:** la arena tolera hasta 1000 °C, pero la aglomeración aparece tras pocos ciclos a 75 °C. Hay que monitorearla si se operan ciclos repetidos.
- **Limitaciones del estudio:** tanque de 20 cm (muy chico), solo carga y almacenamiento (sin descarga), sin eficiencia de ida y vuelta, y sin validación a escala real.
### Cómo te puede servir para el trabajo
- **Confirma la elección de arena pura** para el acumulador nocturno: si la prioridad es retener calor durante la noche, el paper respalda no mezclar cobre. 
- **Dato útil para simulación:** Cp ≈ 1,23–1,32 J/g·K, k ≈ 0,20 W/m·K, ρ ≈ 1,6 g/cm³ (en caída libre). Son insumos directos para cargar en COMSOL o Fluent en el modelo de arena.
- **Diseño del serpentín:** el caso con serpentín de cobre de 9 vueltas y paso 4,5 cm es una referencia de geometría para un intercambiador embebido, similar a lo que plantearías en el modelo C del apunte anterior.
- **Advertencia para el diseño térmico:** el paper confirma que la baja k de la arena genera gradientes marcados alrededor del serpentín (TC-2 cerca de la tubería siempre más caliente que el centro). Eso refuerza la idea de separar las fuentes de calor por unos 10 cm.
- **Validación experimental:** el protocolo (termocuplas en varias posiciones, carga de 4 h y retención de 12,5 h) es un buen modelo para tu plan de ensayos de la Fase 6.