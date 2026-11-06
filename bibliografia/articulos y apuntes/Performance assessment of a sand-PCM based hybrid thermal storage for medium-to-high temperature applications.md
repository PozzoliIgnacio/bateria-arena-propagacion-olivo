---
Titulo esp.: Evaluación del rendimiento de un almacenamiento térmico híbrido basado en arena y PCM para aplicaciones de temperatura media a alta
Año: 2024
Padre: "[[CUDAR - Desarrollo de Pila de Arena]]"
Importancia:
  - C
---

> [!abstract] Resumen en una frase
> Sistema híbrido de almacenamiento térmico que combina arena (calor sensible) y PCM/parafina (calor latente) para mejorar carga, descarga y estabilidad en aplicaciones solares de temperatura media.

![[Performance assessment of a sand-PCM based hybrid thermal storage for medium-to-high temperature applications-1791862070507.webp]]
## Objetivo
Evaluar un sistema híbrido de almacenamiento térmico (TES) que integra **calor sensible** (arena de río) y **calor latente** (material de cambio de fase, PCM) para mejorar la densidad de almacenamiento y la estabilidad de descarga en aplicaciones solares de **temperatura media** (precalentamiento industrial, calefacción, agua caliente sanitaria).

## Diseño del sistema
- **Concentrador solar de canal parabólico** con seguimiento solar en dos ejes.
- **Lecho de arena** atravesado por una serpentina de cobre: almacenamiento por calor sensible.
- **Cámara de PCM (parafina)** separada físicamente de la arena por una **partición metálica**.
- El calor pasa por conducción desde la arena hacia el PCM, almacenándose como calor latente durante la fusión.
- **Desacoplamiento térmico:** la arena se calienta rápido; el PCM actúa como amortiguador térmico y libera energía de forma más lenta y sostenida.
## Resultados principales
Se compararon tres configuraciones: solo arena, solo PCM y sistema híbrido (SP).

| Configuración | Almacenamiento | Eficiencia de carga | Eficiencia de descarga | Descarga sostenida |
|---|---|---|---|---|
| Solo arena | Limitado por saturación térmica | Rápida pero se agota pronto | — | Corta |
| Solo PCM | Mayor capacidad latente | Menor eficiencia de carga | — | Extendida |
| **Híbrido SP** | **1347.1 kJ/kg** | **95.61%** | **96.79%** | **135 min** |

- El sistema híbrido logró la mayor capacidad de almacenamiento.
- Mantuvo una **descarga estable entre 30 y 60 °C durante 135 minutos**.
- Superó a los sistemas de un solo medio y a los lechos empaquetados convencionales.
- La arena alcanzó 53.7 °C en 8 horas de carga, pero su descarga era limitada.
- El PCM solo ofrecía descarga prolongada pero con menor eficiencia de carga.
- La combinación resolvió ambas limitaciones.

## Caracterización de materiales
Se realizaron análisis de:
- XRD
- SEM-EDS
- Raman
- TGA
- DSC
- Propiedades térmicas (KD 2 Pro)

Estos confirmaron la idoneidad y estabilidad de la arena de río y la parafina como medios de almacenamiento.

## Conclusiones
- **Separar físicamente** los medios de almacenamiento sensible y latente es una estrategia robusta para mejorar el rendimiento del TES solar en el régimen de temperatura media.
- El sistema híbrido ofrece una solución **escalable y estable** para aplicaciones térmicas solares.
- Mitiga la **saturación térmica** y el **agotamiento prematuro de la descarga** que afectan a los sistemas de un solo material.

## Limitaciones / notas
- El resumen disponible no detalla limitaciones explícitas; conviene revisar la discusión del paper completo.
- Estudio experimental: la escalabilidad a mayor escala y la integración real en procesos industriales quedan como pasos posteriores.
