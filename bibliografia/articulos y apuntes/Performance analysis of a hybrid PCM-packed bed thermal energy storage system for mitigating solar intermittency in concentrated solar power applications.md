---
Titulo esp.: Análisis del rendimiento de un sistema híbrido de almacenamiento de energía térmica de lecho empaquetado en PCM para mitigar la intermitencia solar en aplicaciones de energía solar concentrada
Año: 2026
Padre: "[[CUDAR - Desarrollo de Pila de Arena]]"
Importancia:
  - C
---
El artículo aborda un desafío clave de la energía solar: su intermitencia. Propone una solución híbrida que combina el almacenamiento de calor sensible (en un lecho de partículas) con el calor latente (mediante un material de cambio de fase o PCM). Esta combinación mejora la estabilidad y la capacidad de almacenamiento en comparación con los sistemas tradicionales.
### Resumen del Artículo
![[Performance analysis of a hybrid PCM-packed bed thermal energy storage system for mitigating solar intermittency in concentrated solar power applications-1791866250051.webp]]
El estudio se centra en un sistema de almacenamiento de energía térmica (TES) para aplicaciones de energía solar concentrada (CSP).
-   **Configuración Híbrida**: El sistema acopla un receptor de cavidad basado en PCM directamente a una unidad de almacenamiento sensible de lecho empacado. Se utiliza **manitol** como PCM y **escoria volcánica** como material del lecho empacado.
-   **Objetivo Principal**: Mitigar las fluctuaciones a corto plazo de la energía solar, proporcionando una salida de calor más estable.
-   **Hallazgos Clave**:
    -   **Estabilización de Temperatura**: El PCM actúa como un amortiguador, manteniendo la temperatura del aire de salida dentro de un margen de **±2 °C** durante el cambio de fase. Esto suaviza las variaciones de energía solar.
    -   **Orientación Vertical**: Una orientación vertical de la cavidad del receptor acelera la fusión del PCM entre un **12% y un 15%** en comparación con una horizontal, debido a una mejor convección natural.
    -   **Eficiencia del Lecho Empacado**: El lecho empacado logra una eficiencia de ida y vuelta de aproximadamente **66%** y una densidad de energía volumétrica de **42.2 kWh/m³**. Además, presenta una termoclina nítida (la zona de gradiente térmico ocupa menos del 30% de la altura del lecho), lo que indica una buena estratificación térmica.
    -   **Control del Flujo Másico**: El análisis de sensibilidad global identificó que el **flujo másico** es el parámetro dominante, contribuyendo a más del **70%** de la varianza en la energía almacenada. Esto subraya la importancia de un control preciso del flujo para optimizar la operación.
### Implicaciones en el proyecto de Batería de Arena
Se podría transformar la batería de arena de un sistema puramente sensible a uno hibrido:
#### 1. Selección y Encapsulamiento del PCM
-   **Elección del PCM**: Debes seleccionar un PCM con un punto de fusión adecuado para el rango de temperatura de operación de la batería. El artículo usa manitol (para altas temperaturas), pero para aplicaciones de menor temperatura, las **parafinas** son una opción común y económica.
-   **Encapsulamiento**: El PCM debe ser encapsulado para evitar fugas al fundirse y para facilitar su integración en el lecho de arena. Se pueden usar **cápsulas esféricas** o **módulos** que se embeben dentro del lecho de arena. Investigaciones recientes también exploran el uso de **pellets con núcleo de arena** encapsulados en PCM para mejorar la transferencia de calor.
#### 2. Integración en el Lecho de Arena
Hay dos estrategias principales de diseño:
-   **Mezcla Directa (Lecho Empacado Híbrido)**: Consiste en mezclar los módulos de PCM encapsulado directamente con la arena. La ventaja es que el PCM aumenta la densidad energética del sistema y añade capacidad de almacenamiento por calor latente. Un estudio encontró que una mezcla volumétrica del **50% de PCM y 50% de arena** puede satisfacer la carga térmica de un bloque de potencia de 75 kW.
-   **Configuración Desacoplada (Sándwich Térmico)**: diseñar un sistema con una **partición metálica** que separe físicamente el lecho de arena de una cámara que contiene el PCM. Así, el calor se transfiere primero a la arena (calentamiento sensible rápido) y luego, por conducción a través de la partición, al PCM (almacenamiento latente). Este enfoque logró eficiencias de carga y descarga superiores al **95%** en un estudio experimental.
#### 3. Diseño de la Transferencia de Calor
-   **Fluido de Transferencia de Calor (HTF)**: El aire es un HTF común para lechos empacados. Sin embargo, para mejorar la transferencia de calor, puedes considerar **sumergir parcialmente los espacios porosos con un aceite térmico** o añadir aditivos conductivos como **grafito** a la arena. Un estudio demostró que una batería de arena con grafito y aceite térmico alcanzó una eficiencia del **87.8%**.
#### 4. Operación y Control
-   **Control del Flujo Másico**: El artículo es claro: el flujo másico del HTF es el parámetro más crítico. Hay que implementar un **sistema de control preciso** para regularlo, ya que impacta directamente en más del 70% de la energía almacenada.
-   **Estrategia de Carga/Descarga**: Aprovecha el PCM para **estabilizar la temperatura de salida**. Durante los picos de energía solar, el exceso de calor funde el PCM. Cuando la energía solar disminuye (por nubes o al atardecer), el PCM se solidifica, liberando calor a una temperatura casi constante y manteniendo la salida estable.
### Consideraciones Adicionales
-   **Materiales**: Si bien la escoria volcánica es una opción, la **arena de sílice** es un material de almacenamiento sensible probado, abundante y de bajo costo, con buena estabilidad térmica.
-   **Aislamiento**: Un buen aislamiento es crucial para reducir las pérdidas de calor. Hay técnicas avanzadas como el **doble muro con vacío** para mejorar la retención de calor durante largos periodos.

En resumen, la implementación práctica se centra en **seleccionar un PCM adecuado y encapsularlo**, **integrarlo en el lecho de arena** (ya sea mezclado o en una configuración desacoplada), **mejorar la transferencia de calor** con aditivos o aceite, y **controlar finamente el flujo de aire** para aprovechar al máximo la capacidad de amortiguación térmica del PCM.
