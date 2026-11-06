---
Titulo esp.: Análisis numérico del impacto de varios parámetros en la distribución de temperatura axial en un lecho empaquetado para almacenamiento de energía termoclina
Año: 2025
Padre: "[[CUDAR - Desarrollo de Pila de Arena]]"
Importancia:
  - B
URL: https://www.sciencedirect.com/science/article/abs/pii/S2451904925011461?via%3Dihub
---
### Resumen
El estudio realiza un análisis paramétrico de un sistema de almacenamiento térmico de energía (TES) sensible de tipo termoclina, en configuración de tanque único y utilizando aire como fluido caloportador. Mediante un modelo numérico 1D basado en las ecuaciones de Schumann (diferencias finitas explícitas), validado con datos experimentales de referencia, se evalúa cómo influyen el tamaño de partícula, la porosidad del lecho, la relación de aspecto del tanque, las propiedades termofísicas del material sólido, la presión de entrada y los ciclos térmicos sucesivos sobre la distribución axial de temperatura durante las fases de carga y descarga. Los resultados permiten establecer rangos de diseño recomendados para optimizar el equilibrio entre capacidad de almacenamiento, uniformidad térmica y pérdidas de presión.
### Introducción y contexto
Entre las distintas tecnologías TES, el almacenamiento en lecho fijo de tipo termoclina destaca por su simplicidad, robustez y rentabilidad, especialmente en plantas termosolares de concentración (CSP) y en la recuperación de calor industrial. 
El sistema se basa en la acumulación de calor sensible en un lecho de materiales sólidos (rocas, cerámicas, escorias), a través del cual fluye un fluido caloportador (aire, aceite térmico o sales fundidas), formándose una zona de transición térmica (termoclina) entre las regiones caliente y fría.

A pesar de la abundante literatura paramétrica sobre sistemas de termoclina, los autores señalan que existe una carencia significativa de información sobre los criterios necesarios para seleccionar un tanque de almacenamiento adecuado con tamaños de partícula específicos y propiedades de material definidas. El presente trabajo busca cubrir ese vacío desarrollando un modelo numérico que permita identificar los parámetros clave de diseño y analizar en profundidad el comportamiento térmico de un sistema de tanque único.
### Objetivos
El objetivo principal es desarrollar un modelo numérico basado en el enfoque de Schumann, con mejoras recientes, para identificar los parámetros clave de diseño y analizar el comportamiento térmico de un sistema de almacenamiento termoclina de lecho fijo en configuración de tanque único. Específicamente, se evalúa la influencia de:
- **Parámetros geométricos:** diámetro de partícula, relación altura-diámetro (H/D) y porosidad del lecho.
- **Parámetros operativos:** presión de entrada y ciclos térmicos sucesivos.
- **Parámetros termofísicos:** conductividad térmica y capacidad calorífica específica del material sólido.
El análisis se centra en las fases de carga (calentamiento) y descarga (enfriamiento).
### Desarrollo: cómo lo hicieron y cómo funciona
**Modelo físico y numérico.** El depósito estudiado se considera un medio poroso a través del cual fluye un fluido caloportador. Durante la carga, un fluido caliente se transfiere de arriba hacia abajo a través del lecho, cediendo calor al material sólido esférico. Durante la descarga, un fluido frío fluye hacia arriba para recuperar el calor almacenado en el sólido. Para establecer el balance de energía, se define un elemento de control de longitud *dx* en el lecho de almacenamiento.

El modelo numérico empleado es un modelo 1D basado en las ecuaciones de Schumann, resuelto mediante diferencias finitas explícitas. Este enfoque considera dos ecuaciones de energía (una para el fluido y otra para el sólido) acopladas por la transferencia de calor interfacial, e incorpora la resistencia a la transferencia de calor fluido-partícula y las pérdidas térmicas del tanque.

**Validación.** El programa desarrollado se valida contra datos experimentales ampliamente utilizados en la literatura para modelos de sistemas de termoclina, obtenidos por Meier et al. utilizando un banco de pruebas de rocas de esteatita con aire como fluido caloportador. Los autores también mencionan la validación frente al benchmark de Pacheco.

**Análisis paramétrico.** Una vez validado, el modelo se emplea para simular sistemáticamente el efecto de los parámetros geométricos, operativos y termofísicos sobre la distribución axial de temperatura y el rendimiento global del sistema durante ciclos de carga y descarga.
### Resultados principales
Los hallazgos más relevantes reportados por los autores son los siguientes:
- **Diámetro de partícula:** diámetros más pequeños mejoran la difusión térmica y agudizan el frente térmico (termoclina más estrecha), lo que mejora la uniformidad de temperatura, aunque a costa de mayores pérdidas de presión.
- **Porosidad:** un rango de porosidad entre el 35 % y el 50 % ofrece un equilibrio óptimo entre capacidad de almacenamiento y eficiencia del flujo (caída de presión).
- **Relación de aspecto (H/D):** una **relación altura-diámetro de hasta 3 favorece una distribución de calor más uniforme con menores pérdidas a través de las paredes**.
- **Propiedades termofísicas del material:** los materiales adecuados para almacenamiento termoclina presentan capacidades caloríficas específicas de 0.6–1.6 kJ·kg⁻¹·K⁻¹ y conductividades térmicas ≤ 12 W·m⁻¹·K⁻¹, lo que garantiza un amortiguamiento energético adecuado sin fugas de calor radial excesivas.
- **Presión de entrada:** una mayor presión de entrada acelera la carga y la descarga, pero incrementa los requisitos de bombeo, por lo que debe ajustarse a las restricciones del sistema.
- **Ciclos térmicos:** las diferencias entre el primer ciclo y los posteriores se atribuyen a la energía no recuperada en los ciclos iniciales, tras lo cual el sistema se estabiliza.
- **Densidad energética útil:** se reporta la densidad de energía utilizable Q (kWh·m⁻³) como métrica energética, calculada a partir de la capacidad calorífica del material, la densidad aparente, la porosidad y el salto de temperatura de operación.
### Conclusiones de los autores
Los autores concluyen que el modelado numérico desarrollado permite identificar los parámetros clave para el diseño eficiente de un sistema de almacenamiento térmico de termoclina. Las recomendaciones prácticas derivadas del estudio son:
- Emplear una porosidad del lecho entre 35 % y 50 % para equilibrar capacidad de almacenamiento y fluidez.
- Seleccionar un diámetro de partícula suficientemente pequeño para lograr una mejor difusión térmica y un frente térmico más definido.
- Limitar la relación de aspecto del tanque a valores de H/D ≲ 3 para favorecer la uniformidad térmica y reducir pérdidas.
- Escoger materiales con capacidad calorífica específica en el rango 0.6–1.6 kJ·kg⁻¹·K⁻¹ y conductividad térmica ≤ 12 W·m⁻¹·K⁻¹.
- Ajustar la presión de entrada a las restricciones de bombeo de cada instalación.
- Considerar que las discrepancias térmicas iniciales se estabilizan tras los primeros ciclos.

El programa desarrollado se valida contra resultados experimentales, confirmando su fiabilidad y relevancia para simular sistemas de almacenamiento de lecho fijo con aire caliente.
