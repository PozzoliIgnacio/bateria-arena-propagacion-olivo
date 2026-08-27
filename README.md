# Batería Térmica de Arena para Propagación de Olivo

**Sistema híbrido solar-térmico para calefacción autónoma de camas calientes de enraizamiento**

!\[Status](https://img.shields.io/badge/estado-en%20desarrollo-yellow)
!\[Fase](https://img.shields.io/badge/fase-ingenier%C3%ADa%20b%C3%A1sica-blue)

> Proyecto de diseño mecánico dentro del \*\*Sistema Automático y Telemetrizado de Propagación de Olivo\*\*. Este repositorio documenta el diseño, cálculo, simulación y construcción de un \*\*acumulador térmico de arena\*\* que reemplaza el uso de baterías químicas (litio) para independizar el sistema de la red eléctrica domiciliaria.

\---

## Tabla de contenidos

* [Sobre el proyecto](#-sobre-el-proyecto)
* [Objetivos](#-objetivos)
* [Mapa del repositorio](#-mapa-del-repositorio)

\---

## Sobre el proyecto

El sistema actual de propagación de olivo por esquejes bajo nebulización usa una **cama caliente** con resistencias eléctricas (20 W/m) para mantener el sustrato a temperatura óptima de enraizamiento. Ese sistema funciona bien en laboratorio, pero depende 100% de la red eléctrica, lo cual es una limitación crítica para su uso en zonas rurales/productivas.

La solución propuesta es hibridar el sistema con **energía solar fotovoltaica** y sustituir el almacenamiento electroquímico (baterías de litio, caras y de mantenimiento complejo) por **almacenamiento térmico en arena**. 

Este repo cubre la parte de **ingeniería mecánica**: estado del arte, modelo matemático, diseño estructural del tanque, intercambiador de calor, simulación térmica, instrumentación y validación experimental.

## Objetivos

**General:** incorporar al sistema existente un sistema híbrido de energía que combine generación solar fotovoltaica con un acumulador térmico de arena, garantizando funcionamiento autónomo, eficiente y sostenible.

**Específicos (área mecánica):**

* Diseñar, construir e integrar un prototipo funcional de acumulador térmico de arena.
* Implementar un subsistema de extracción y control térmico capaz de regular la liberación de la energía acumulada.
* Asegurar la transferencia efectiva de esa energía hacia la mesa de propagación (cama caliente).

## 🗺️ Mapa del repositorio

|Carpeta|Contenido|Detalle|
|-|-|-|
|[`docs/`](docs)|Documentación formal del proyecto (requerimientos, entregables, etc.)|[→](docs/README.md)|
|[`bibliografia/`](bibliografia)|Papers + apuntes de cada uno|[→](bibliografia/README.md)|
|[`notas/`](notas)|Aprendizajes personales (simulación, modelados, software, etc.)|[→](notas/README.md)|
|[`calculos/`](calculos)|Modelos matemáticos y balances energéticos, notebooks de calculo. |[→](calculos/README.md)|
|[`cad/`](cad)|Modelos CAD (conceptual, detalle, planos 2D)|[→](cad/README.md)|
|[`simulaciones/`](simulaciones)|Simulación térmica (modelos, resultados)|[→](simulaciones/README.md)|
|[`datos\_experimentales/`](datos_experimentales)|Datos de ensayos reales|[→](datos_experimentales/README.md)|
|[`prototipo/`](prototipo)|Fotos, videos y BOM del armado físico |[→](prototipo/README.md)|

\---

*Repositorio en desarrollo activo — la estructura y el contenido se van a ir actualizando a medida que avancen las etapas de ingeniería básica y de detalle.*

