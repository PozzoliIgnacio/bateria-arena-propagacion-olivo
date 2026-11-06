---
Titulo esp.: Estudio experimental de un sistema de almacenamiento térmico sensible de arena de sílice mejorado con aletas
Año: 2024
Padre: "[[CUDAR - Desarrollo de Pila de Arena]]"
Importancia:
  - B
---
## Apunte breve del paper
### 1. Resumen
El paper evalúa el desempeño térmico de arena de sílice como medio de almacenamiento de calor sensible en un sistema “shell-and-tube” que usa agua como fluido de transferencia de calor (HTF). Compara arena fina y gruesa, y luego prueba cuatro configuraciones de aletas de cobre —10 y 20 anulares; 4 y 8 radiales— contra un caso base sin aletas, manteniendo la misma cantidad de cobre en todas las configuraciones con aletas. La arena fina se carga más rápido que la gruesa, aunque se descarga más lento en el caso base. Las aletas reducen fuertemente los tiempos de carga y descarga; la mejor configuración fue la de 8 aletas radiales, con reducciones de 63,74% en carga y 78,50% en descarga frente al caso base.
![[Experimental Study of a Silica Sand Sensible Heat Storage System Enhanced by Fins-1792542410270.webp]]
### 2. Introducción / contexto
- El almacenamiento térmico de energía (TES) es clave para integrar renovables. Se clasifica en latente, termoquímico y sensible.
- El almacenamiento sensible (SHTES) es simple, relativamente barato y usa materiales como roca, concreto, agua o arena; su limitación principal es la menor densidad de almacenamiento frente a sistemas latentes.
- La literatura ha estudiado varios materiales sensibles, pero los autores identifican un vacío en el uso de **arena de sílice** como medio de almacenamiento sensible y en la comparación sistemática de aletas radiales/anulares con igual cantidad de cobre.
- La novedad declarada es evaluar tamaño de partícula de arena y distintas aletas manteniendo equivalente la cantidad de material de cobre.
### 3. Objetivos
- Evaluar el desempeño térmico de arena de sílice en un sistema SHTES de tipo shell-and-tube con agua como HTF.
- Comparar arena fina vs. arena gruesa para carga y descarga.
- Evaluar cuatro configuraciones de aletas de cobre frente a un caso base sin aletas.
- Mantener la misma cantidad de cobre entre configuraciones con aletas para comparar mejoras sin aumentar el costo de material.
### 4. Desarrollo: cómo lo hicieron y cómo funciona
**Montaje experimental:**
- Contenedor acrílico: 30,58 cm de alto, 19,05 cm de diámetro interno, aislado con espuma de 2,54 cm.
- Tubo central de cobre de 2,54 cm de diámetro y 30,58 cm de largo, por donde circula el agua.
- Arena de sílice como medio de almacenamiento; se usan dos distribuciones de tamaño: arena fina y gruesa.
- Nueve termocuplas tipo K (±0,5 °C), RTDs, adquisición National Instruments y cámara térmica.

**Operación:**
- Carga: agua caliente a ~70 °C, caudal de 2 GPM (7,57 L/min).
- Descarga: agua fría a 15 °C, caudal de 1 GPM (3,79 L/min).
- Carga completa: promedio de todas las termocuplas ≥57 °C.
- Descarga completa: todas las termocuplas <25 °C.

**Configuraciones de aletas:**
- 10 anulares: espesor 1,59 mm, longitud 4,0 cm, separación 2,63 cm.
- 20 anulares: espesor 0,79 mm, longitud 4,0 cm, separación 1,31 cm.
- 4 radiales: espesor 1,59 mm, longitud 7,87 cm, a 90°.
- 8 radiales: espesor 0,79 mm, longitud 7,87 cm, a 45°.
- Todas usan la misma cantidad de cobre; por eso al aumentar número de aletas se reduce su espesor.
### 5. Resultados principales
**Caso base sin aletas:**
- Arena fina: carga 11,86 h; descarga 17,58 h.
- Arena gruesa: carga 13,36 h; descarga 16,55 h.
- La arena fina carga más rápido, pero en el caso base tarda más en descargar que la gruesa. Los autores señalan que la arena fina tuvo mayor tasa de almacenamiento/transferencia y la seleccionan para probar las aletas.

**Con aletas, usando arena fina:**

| Configuración | Carga (h) | Reducción vs. base | Descarga (h) | Reducción vs. base |
|---|---:|---:|---:|---:|
| 10 anulares | 6,81 | 42,58% | 6,61 | 62,40% |
| 20 anulares | 5,19 | 56,24% | 5,58 | 68,26% |
| 4 radiales | 4,86 | 59,02% | 5,42 | 69,17% |
| 8 radiales | 4,30 | 63,74% | 3,78 | 78,50% |

- Las aletas radiales fueron mejores que las anulares en este estudio.
- La mejor configuración global fue **8 aletas radiales**.
- La incertidumbre experimental del cálculo de potencia térmica se reporta como 8,2%.
### 6. Conclusiones de los autores
- La arena de sílice es un medio de almacenamiento sensible viable, económico y abundante.
- **La arena fina mejoró la transferencia térmica/carga frente a la gruesa**, aunque el dato de descarga es matizable: en el caso base la arena fina tardó más en descargar.
- **Las aletas reducen significativamente los tiempos de carga y descarga.**
- Las aletas radiales superaron a las anulares; 8 radiales fue la mejor configuración.
- El sistema sería prometedor para aplicaciones de energía solar de concentración, recuperación de calor residual industrial y almacenamiento térmico de bajo/moderado costo.
- Limitaciones: menor densidad energética que sistemas latentes, necesidad de estudiar escalamiento, ciclos repetidos, durabilidad y mantenimiento.
### 7. Evaluación final
**Fortalezas:**
- Estudio experimental claro, con caso base y varias configuraciones comparables.
- Control interesante: igual cantidad de cobre entre configuraciones con aletas.
- Métricas directas: tiempos de carga/descarga, temperaturas y potencia térmica.
- Material económico y abundante; relevancia práctica para almacenamiento sensible de moderada temperatura.

**Debilidades / cautelas:**
- Solo se prueban dos tamaños de arena, seleccionados por disponibilidad comercial; no cubren todo el espectro posible.
- El estudio es a escala laboratorio y a temperaturas moderadas (70 °C carga / 15 °C descarga).
- No se reportan análisis económico, de ciclado largo, durabilidad o escalamiento.
- La arena fina carga más rápido pero descarga más lento que la gruesa en el caso base; la elección de arena fina para las aletas se justifica por tasa energética, pero el compromiso carga/descarga merece atención.
- La comparación “igual cantidad de cobre” no equivale necesariamente a igual área superficial o igual facilidad de fabricación; eso no se analiza en profundidad.

> [!NOTE] Aplicación a mi desarrollo 
> - usar arena fina ya que mejora la transferencia térmica 
> - las aletas reducen significativamente los tiempos de carga y descarga

