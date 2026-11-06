---
Titulo esp.: Modelado y simulacion del comportamiento termodinamico en un sistema de almacenamiento de energia termica en lecho empaquetado
Año: 2025
Padre: "[[CUDAR - Desarrollo de Pila de Arena]]"
Importancia:
  - A
URL: https://ieeexplore.ieee.org/document/11095475
---
## 1. **Idea Central**
El artículo investiga y simula el comportamiento termodinámico de un sistema de almacenamiento de energía térmica (TES) de calor sensible configurado como un lecho empacado de doble medio. A través de un modelo matemático transitorio de dinámica de fluidos computacional (CFD), evalúa la interacción entre un fluido caloportador y una matriz de partículas sólidas esféricas durante la fase de carga térmica. 
La conclusión fundamental determina que la eficiencia temporal de carga del tanque mejora drásticamente al incrementarse la porosidad del lecho y el tamaño de las partículas.
**Glosario de abreviaciones**
- **TES:** Thermal Energy Storage / Almacenamiento de Energía Térmica.
- **SHS:** Sensible Heat Storage / Almacenamiento por calor sensible.
- **LHS:** Latent Heat Storage / Almacenamiento por calor latente.
- **HTF:** Heat Transfer Fluid / Fluido de Transferencia de Calor.
- **CFD:** Computational Fluid Dynamics / Dinámica de Fluidos Computacional.
- **LTNE:** Local Thermal Non-Equilibrium / Equilibrio Térmico Local No Equilibrado.
- **REV:** Representative Elementary Volume / Volumen Elemental Representativo.
- **FEM:** Finite Element Method / Método de Elementos Finitos.
- **CAFLO:** aceite térmico comercial usado como HTF.
- **ΔT:** diferencia o rango de temperatura.
## 2. **Resumen por Secciones**
### I. Introducción
El paper contextualiza las tecnologías TES como clave para la transición energética, la integración de renovables y la recuperación de calor. Explica que el almacenamiento puede ser por calor sensible, latente o termoquímico. Se enfoca en el **lecho empacado TES de doble medio**, por su bajo costo y buena capacidad calorífica: el calor se almacena en partículas sólidas y un HTF circula por el lecho para cargar/descargar energía.

El problema central es que el comportamiento termodinámico depende de variables operativas, geométricas y termofísicas, y el sistema involucra conducción, convección y radiación. Sin embargo, en este estudio **la radiación se desprecia** y solo se consideran conducción y convección. Se propone un modelo 2D-axisimétrico con COMSOL y enfoque LTNE.

**Justifica la creación del modelo numérico 2D-Axisimetrico empleando FEM y el enfoque LTNE** para analizar por separado y con exactitud los desequilibrios térmicos entre las fases solida y fluida. 
### II. Modelo físico del sistema
Se estudia un tanque cilíndrico vertical lleno con guijarros esféricos. Durante la **carga**, el fluido caliente entra por arriba y circula axialmente hacia abajo, transfiriendo calor a los guijarros, inicialmente a $T_0$. La geometría se justifica por simplicidad, menor estrés mecánico, estabilidad, menores pérdidas y distribución más uniforme de temperatura/flujo. ![[Modeling and Simulation of Thermodynamic Behavior in a Packed Bed Thermal Energy Storage System-1793688520647.webp]] *Fig. 1, diagrama esquemático del sistema TES estudiado.*
![[Modeling and Simulation of Thermodynamic Behavior in a Packed Bed Thermal Energy Storage System-1793688549524.webp]]*Fig. 2, esquema de los fenómenos térmicos que gobiernan el sistema.*
**Deprecia el comportamiento de radiacion para enfocarse solamente en interacciones conductivas y convectivas.**
### III. Modelado matemático
Se usa el concepto **REV** (Volumen elemental representativo) y el lecho se modela como medio poroso. Las ecuaciones principales son continuidad, momentum y energía para fases sólida y fluida. ![[Modeling and Simulation of Thermodynamic Behavior in a Packed Bed Thermal Energy Storage System-1793688665733.webp]]*Fig. 3, concepto de Volumen Elemental Representativo, REV.*

**Continuidad**
$$
\vec{\nabla}\cdot \epsilon (\vec{\mathbf{u}})^f = 0
$$
donde $\epsilon$ es la porosidad, $(\vec{\mathbf{u}})^f$ es la velocidad media intrínseca del fluido y $\epsilon(\vec{\mathbf{u}})^f=\mathbf U$ es la velocidad de Darcy.

**Momentum: ley de Darcy-Forchheimer**
$$
\frac{\rho_f}{\epsilon}\frac{\partial \vec{\mathbf u}}{\partial t}
+\frac{\rho_f}{\epsilon^2}(\vec{\mathbf U}\cdot\nabla)\vec{\mathbf U}
=
-\nabla P+\rho_f\vec{\mathbf g}
-\frac{\mu}{\kappa}\vec{\mathbf U}
-C_F\frac{\rho_f}{\sqrt{\kappa}}|\vec{\mathbf U}|\vec{\mathbf U}
$$
Variables: $\rho_f$ densidad del fluido; $\mathbf U$ velocidad del fluido; $P$ presión; $\mathbf g$ gravedad; $\mu$ viscosidad dinámica; $\kappa$ permeabilidad; $C_F$ coeficiente de Forchheimer.

**Pérdida de presión tipo Ergun**
$$
\nabla P =
-\frac{\mu}{\kappa}\mathbf u
-1.75\frac{1-\epsilon}{d_p\epsilon^3}\rho|\mathbf u|\mathbf u
$$
donde $d_p$ es el diámetro de partícula. El PDF usa una notación tipo $d\rho$; aquí se interpreta como diámetro de partícula.

**Permeabilidad**
$$
\kappa=\frac{d_p ^2\epsilon^ 3}{150(1-\epsilon)^2}
$$
El paper la escribe con posible errata OCR como $d\rho^2$; dimensionalmente corresponde al diámetro de partícula al cuadrado.

**Ecaciones de conservacion de energia LTNE**
**Energía de la fase fluida**
$$
\frac{\partial T_f}{\partial t}
=
-u\frac{\partial T_f}{\partial x}
+\frac{h_c\alpha}{\epsilon \rho_f c_{pf}}(T_s-T_f)
$$
Variables: $T_f$ temperatura del fluido; $h_c$ coeficiente de convección interfacial; $\alpha$ área interfacial específica; $c_{pf}$ calor específico del fluido.

**Energía de la fase sólida**. 
$$
\frac{\partial T_s}{\partial t}
=
\frac{h_c\alpha}{(1-\epsilon)\rho_s c_{ps}}(T_f-T_s)
$$
Variables: $T_s$ temperatura del sólido; $\rho_s$ densidad del sólido; $c_{ps}$ calor específico del sólido.

### IV. Validación del modelo
El modelo se valida contra datos experimentales de Mawrie y McPherson. Se comparan cinco niveles axiales: A, C, E, G e I. El aceite caliente entra a $200^\circ C$ y el lecho inicia a $20^\circ C$. El modelo reproduce razonablemente la estratificación térmica; la mayor discrepancia se atribuye a radiación no considerada y conducción interna en las partículas. El Nivel A presenta el mejor ajuste por estar más cerca de la entrada y condiciones de frontera mejor definidas. ![[Modeling and Simulation of Thermodynamic Behavior in a Packed Bed Thermal Energy Storage System-1793688962468.webp]]*Fig. 4, esquema del tanque experimental y posiciones de medición.*
![[Modeling and Simulation of Thermodynamic Behavior in a Packed Bed Thermal Energy Storage System-1793689006366.webp]]*Fig. 5, comparación entre resultados experimentales y simulados.*

**Tabla I resumida del paper**
- Porosidad: $\epsilon=0.49$
- Diámetro de guijarro: $0.05\ m$
- Densidad del lecho de guijarros: $2801\ kg/m^3$
- Densidad del fluido: $-0.674 T_{av}+869$
- Altura del tanque: $0.3\ m$
- Diámetro del tanque: $0.29\ m$
- $c_p$ del lecho: $745\ J/(kg\cdot K)$
- $c_p$ del fluido: $0.00326 T_{av}+1.8$ — unidades no aclaradas explícitamente en la tabla.

### V. Resultados de simulación
- **Campo de velocidad:** la velocidad es mayor en entrada y salida del tanque; dentro del lecho poroso disminuye por la resistencia de las partículas y la caída de presión.
- **Campos de temperatura:** el fluido está siempre más caliente que el sólido durante la carga, porque recibe directamente la energía y la transfiere al sólido por convección; el sólido tiene mayor inercia térmica.
- **Capa límite térmica:** aparece junto a la pared interna por convección externa con aire ambiente a $20^\circ C$ y $h=10\ W/(m^2 K)$.
- **Termoclina:** zona intermedia que separa la zona caliente y fría; se desplaza de arriba hacia abajo. Se define entre el 80 % y el 20 % de $\Delta T$. Una termoclina más gruesa implica menor eficiencia de almacenamiento.
- **Efecto de la porosidad:** al pasar de $\epsilon=0.49$ a $0.8$, aumenta el contacto fluido-sólido y se acelera el aumento de temperatura; el sistema alcanza equilibrio térmico aproximadamente a las 4 h. Pero **mayor porosidad reduce la densidad de almacenamiento por menor fracción sólida**.
- **Efecto del tamaño de partícula:** al aumentar $d_p$, aumenta la permeabilidad $\kappa$, disminuye la resistencia al flujo y se facilita el paso del fluido. El paper reporta efecto significativo para $d_p=50\ cm$ y $80\ cm$, aunque estos valores parecen inconsistentes con la Tabla I ($0.05\ m=5\ cm$) y con la Fig. 9, que también muestra $dp=1\ cm$. Probable errata.
![[Modeling and Simulation of Thermodynamic Behavior in a Packed Bed Thermal Energy Storage System-1793689113023.webp]]*Fig. 6, campo de velocidad y dirección de flujo.*
*Fig. 7, distribución 2D de temperatura para sólido y fluido durante la carga.*
### VI. Conclusión
El modelo LTNE 2D-axisimétrico en COMSOL fue validado con datos experimentales y permitió describir el comportamiento termodinámico del lecho empacado. 
**La porosidad y el tamaño de partícula influyen fuertemente: mayores valores aceleran el calentamiento y reducen el tiempo de carga, aunque la porosidad alta penaliza la densidad energética**. El sistema se plantea como alternativa prometedora a los sistemas de dos tanques. Como trabajo futuro se propone evaluar energía almacenada/liberada, eficiencias de carga/descarga y eficiencia global.
## 3. **Parámetros Técnicos Clave**
- **Volumen / Masa de arena:** No es arena; es un lecho de guijarros esféricos. Tanque: $H=0.3\ m$, $D=0.29\ m$, $\epsilon=0.49$, $d_p=0.05\ m$, densidad del lecho $2801\ kg/m^3$. Volumen del tanque $\approx \pi(0.145)^2(0.3)\approx 0.0198\ m^3$. La masa no está explícita. Estimación: si $2801\ kg/m^3$ es densidad del sólido y $\epsilon=0.49$, masa sólida $\approx 28.3\ kg$; si se toma como densidad aparente del lecho, masa $\approx 55.5\ kg$. El paper no aclara cuál interpretación usar.
- **Potencia y Capacidad:** No especificado en el paper. No se reportan kW, kWh ni potencia de entrega.
- **$\Delta T$ de trabajo:** $20^\circ C$ inicial a $200^\circ C$ de entrada del HTF; $\Delta T=180\ K$.
- **Tipo de intercambiador:** Contacto directo. El aceite térmico circula axialmente de arriba hacia abajo a través del lecho de guijarros; hay un distribuidor. No se usan resistencias eléctricas ni tubos inmersos.
- **Material aislante:** No especificado. La Fig. 1 menciona “tank insulation”, pero no se indica material. Se modela convección externa con ambiente a $20^\circ C$ y $h=10\ W/(m^2 K)$.
- **Eficiencia reportada:** No especificado en el paper. No se entrega eficiencia porcentual; solo se discute cualitativamente la eficiencia de transferencia térmica y el efecto de la termoclina.
## 4. **Hallazgos Críticos**
- El modelo **LTNE** permite resolver por separado $T_f$ y $T_s$, capturando el no-equilibrio térmico local: durante la carga, el fluido está más caliente que el sólido.
- La validación experimental es aceptable; las diferencias se explican por la omisión de radiación y conducción interna en las partículas.
- La **termoclina** se desplaza de arriba hacia abajo y su espesor controla la eficiencia: una termoclina más gruesa reduce las zonas isotérmicas y baja la eficiencia de almacenamiento.
- Aumentar la **porosidad** de 0.49 a 0.8 acelera el calentamiento y reduce el tiempo de carga, pero disminuye la densidad de almacenamiento por menor fracción sólida.
- Aumentar el **diámetro de partícula** incrementa la permeabilidad y facilita el flujo; el paper reporta efecto significativo, aunque los valores de $50\ cm$ y $80\ cm$ parecen erróneos frente a la Tabla I.
- Se identifica una **capa límite térmica junto a la pared** por pérdidas hacia el ambiente, modelada con $20^\circ C$ y $h=10\ W/(m^2 K)$.
- El estudio no reporta eficiencia energética porcentual ni capacidad en kWh; queda como trabajo futuro evaluar energía almacenada/liberada y eficiencias de carga/descarga.