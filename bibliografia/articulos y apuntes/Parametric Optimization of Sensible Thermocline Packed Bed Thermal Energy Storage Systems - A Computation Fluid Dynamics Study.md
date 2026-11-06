---
Titulo esp.: "Optimización paramétrica de sistemas sensibles de almacenamiento de energía térmica en lecho empaquetado de termoclina: un estudio computacional de dinámica de fluidos"
Año: 2026
Padre: "[[CUDAR - Desarrollo de Pila de Arena]]"
Importancia:
  - B
URL: https://www.mdpi.com/2071-1050/18/7/3333#
---
## 1. Idea central y glosario
### Resumen
El trabajo construye y valida un modelo numérico 2D axisimétrico de un tanque de almacenamiento térmico por calor sensible de lecho empacado tipo termoclina, a escala industrial: un cilindro de acero de 9,17 m de alto y 4,72 m de diámetro, con 0,2 m de lana de roca y lleno de esferas de basalto. Un aceite térmico entra caliente por arriba a 390 °C y atraviesa el lecho, que arranca a 20 °C. Solo se simula la **fase de carga**.

El modelo acopla dos cosas:
- La hidrodinámica en medio poroso (Darcy–Forchheimer).
- Un balance de energía de **no equilibrio térmico local (LTNE)**, con una ecuación para el fluido y otra para el sólido.

Se resolvió en COMSOL 6.1 por elementos finitos y se validó contra los experimentos de Mawire y McPherson (tanque de 0,3 m), con un error medio del 3,62 %. Luego se barrieron tres parámetros: caudal (8–15 kg/s), porosidad (0,35–0,55) y diámetro de partícula (5–20 cm).

La conclusión fundamental es que **el tamaño de partícula y la porosidad controlan cuánto "se atrasa" el sólido respecto del fluido**, y con eso la eficiencia de carga:
- Partículas grandes (20 cm) generan un desfase de unos 34 °C y bajan la eficiencia final del 99 % al 83 %.
- Una porosidad mayor acelera la carga y sube la eficiencia de carga alrededor de un 8 %.
![[Parametric Optimization of Sensible Thermocline Packed Bed Thermal Energy Storage Systems - A Computation Fluid Dynamics Study-1793775558303.webp]]*Diagrama de flujo de la metodología: TES → calor sensible → medio sólido → lecho empacado → modelado matemático (2D axisimétrico, Darcy–Forchheimer, LTNE) y numérico (COMSOL, FEM) → validación → resultados.*
### Glosario

|Sigla|Significado|Comentario|
|---|---|---|
|TES|_Thermal Energy Storage_, almacenamiento de energía térmica|Categoría general.|
|SHS|_Sensible Heat Storage_, almacenamiento por calor sensible|El material sube de temperatura sin cambiar de fase. Es el caso de la arena.|
|PBTES|_Packed Bed TES_, almacenamiento en lecho empacado|Tanque relleno de partículas sólidas atravesado por un fluido.|
|HTF|_Heat Transfer Fluid_, fluido caloportador|Aceite en el paper; en tu caso probablemente aire o agua.|
|CFD|_Computational Fluid Dynamics_|Simulación numérica de flujo y calor. Es la disciplina, no el método de discretización.|
|FEM|_Finite Element Method_|Método de discretización que usa COMSOL. Fluent usa FVM (volúmenes finitos).|
|LTNE|_Local Thermal Non-Equilibrium_|En cada punto, fluido y sólido tienen temperaturas distintas, T_f ≠ T_s. Requiere dos ecuaciones de energía.|
|LTE|_Local Thermal Equilibrium_|T_f = T_s en cada punto. Basta una ecuación con propiedades efectivas.|
|REV|_Representative Elementary Volume_|Volumen "promedio" mucho mayor que un grano y mucho menor que el tanque. Sobre él se promedian las ecuaciones: no se modelan granos individuales sino un continuo poroso.|
|Termoclina|Zona de transición entre la parte caliente y la fría del tanque|Cuanto más delgada, mejor estratificación.|
|δ_th|Espesor de la termoclina|El paper lo define entre el 20 % y el 80 % de ΔT.|
|η_ch / η_st|Eficiencia de carga / eficiencia de almacenamiento|Definiciones en la sección 2.4.|
|Re_p, Pr, Pe|Números de Reynolds de partícula, Prandtl y Péclet|Re_p = ρ u d_p / μ.|
|Nu, NTU|Nusselt y número de unidades de transferencia|NTU indica si hace falta LTNE o alcanza con LTE.|
|Bi|Número de Biot de la partícula|Si Bi < 0,1, la partícula es isotérmica por dentro.|
|BDF|_Backward Differentiation Formula_|Integrador temporal implícito, el solver por defecto de COMSOL.|
|CSP|_Concentrated Solar Power_|Contexto de aplicación del paper.|

## 2. Formulación matemática (sección prioritaria)
### 2.0 Puente FEM → CFD 
En FEM una EDP se discretiza en una malla, se arma un sistema y se resuelve. En CFD de medios porosos las EDP son de **transporte**. Además del término difusivo (∇·k∇T, como en conducción) aparece un **término convectivo** (u·∇T): el calor es _arrastrado_ por el fluido.

Tres conceptos clave:
1. **Promediado volumétrico (REV).** No se modela cada grano de arena. Se trata el lecho como un continuo con propiedades "promedio": porosidad ε, permeabilidad κ y conductividad efectiva.
2. **Velocidad de Darcy vs. velocidad intersticial.**
    - La velocidad de Darcy (superficial) es U_D = caudal volumétrico / área total del tanque.
    - La velocidad real entre granos es la intersticial, u = U_D / ε, que es mayor porque el fluido solo pasa por los huecos.
    - Siempre verificá cuál pide el software.
3. **Acoplamiento.** Primero se resuelve (o se resuelve en simultáneo) el campo de velocidad. Ese campo entra en la ecuación de energía. Si las propiedades dependen de T, la energía también retroalimenta al flujo. COMSOL llama a esto _Nonisothermal Flow_.
![[Parametric Optimization of Sensible Thermocline Packed Bed Thermal Energy Storage Systems - A Computation Fluid Dynamics Study-1793775687040.webp]]*Esquema del tanque: entrada de HTF arriba, "medio libre" (sin partículas) en los plenos de entrada y salida, "medio poroso" (esferas) en el cuerpo, aislación en la pared y salida abajo.*
![[Parametric Optimization of Sensible Thermocline Packed Bed Thermal Energy Storage Systems - A Computation Fluid Dynamics Study-1793775700887.webp]]*Mecanismos de transferencia en el lecho: flujo de fluido entre esferas, conducción por contacto entre partículas, conducción, convección y radiación. El paper desprecia la radiación.*
### 2.1 Continuidad (conservación de masa)
$$\nabla\cdot\left(\varepsilon\langle\vec u\rangle^f\right)=\nabla\cdot\vec U_D=0$$
- ⟨u⟩^f es la velocidad intrínseca: el promedio sobre el volumen de fluido.
- ε⟨u⟩^f = U_D es la velocidad de Darcy.
**Por qué se usa.** El fluido se considera incompresible, así que "lo que entra, sale". Es la misma condición que impone un flujo de agua en una cañería.

**Qué implica.** Para aceite es correcto. Para **aire calentado de 20 a 300 °C** la densidad cae a la mitad, así que en nuestro caso conviene usar la formulación compresible (_weakly compressible_), que COMSOL ofrece como opción. 
### 2.2 Momento: Darcy–Forchheimer (Brinkman–Forchheimer)
$$\frac{\rho_f}{\varepsilon}\frac{\partial\vec U}{\partial t}+\frac{\rho_f}{\varepsilon^2}(\vec U\cdot\nabla)\vec U=-\nabla P+\rho_f\vec g-\frac{\mu}{\kappa}\vec U-C_F\frac{\rho_f}{\sqrt\kappa}|\vec U|\vec U$$
Es la ecuación de Navier–Stokes modificada para un medio poroso. Término por término:

|Término|Significado físico|
|---|---|
|(ρ_f/ε) ∂U/∂t|Inercia transitoria del fluido.|
|(ρ_f/ε²)(U·∇)U|Aceleración convectiva. Importa en los plenos sin partículas, casi nada dentro del lecho.|
|−∇P|Gradiente de presión: es lo que "empuja" el fluido.|
|ρ_f g|Gravedad. Importa si hay convección natural por diferencias de densidad.|
|−(μ/κ) U|**Arrastre viscoso (Darcy).** Lineal en la velocidad y dominante a bajo Re_p.|
|−C_F (ρ_f/√κ) \|U\|U|**Arrastre inercial (Forchheimer).** Cuadrático, importa a Re_p altos (de ~10 en adelante).|

Símbolos:
- ε: porosidad, la fracción de vacíos (adimensional).
- μ: viscosidad dinámica [Pa·s].
- ρ_f: densidad del fluido.
- κ: permeabilidad [m²], que mide qué tan "fácil" deja pasar fluido el lecho.
- C_F: coeficiente de Forchheimer (adimensional), habitualmente C_F = 1,75/(√150·ε^{3/2}).

**Caída de presión: ecuación de Ergun.** En régimen estacionario y despreciando gravedad, lo anterior se reduce a:
$$\frac{\Delta P}{L}=\underbrace{150\frac{(1-\varepsilon)^2}{\varepsilon^3}\frac{\mu,U}{d_p^2}}_{\text{viscoso},\propto,1/d_p^2}+\underbrace{1{,}75\frac{(1-\varepsilon)}{\varepsilon^3}\frac{\rho_f,U^2}{d_p}}_{\text{inercial},\propto,1/d_p}$$
**Permeabilidad (Kozeny–Carman / Ergun):**
$$\kappa=\frac{d_p^2,\varepsilon^3}{150(1-\varepsilon)^2}$$
**Qué implica.**
- La permeabilidad crece con d_p².
- Si reducís el grano a la mitad, la caída de presión viscosa se **cuadruplica**.
- El término ε³ es muy sensible: pasar de ε = 0,35 a 0,45 casi duplica κ.
- **Para la arena esta es la ecuación más importante del paper.**

**Por qué el paper usa "free and porous media flow".** Arriba y abajo del lecho hay plenos vacíos, el "medio libre", donde rige Navier–Stokes normal. COMSOL resuelve ambas regiones en un mismo dominio y empalma la interfaz (Brinkman).
### 2.3 Energía: modelo LTNE (dos ecuaciones)
**Fluido:**
$$\varepsilon(\rho C_p)_f\frac{\partial T_f}{\partial t}+(\rho C_p)_f(\vec u\cdot\nabla)T_f=\nabla\cdot(\lambda_{eff,f}\nabla T_f)+h_i,a,(T_s-T_f)$$
**Sólido:**
$$(1-\varepsilon)(\rho C_p)_s\frac{\partial T_s}{\partial t}=\nabla\cdot(\lambda_{eff,s}\nabla T_s)+h_i,a,(T_f-T_s)$$
Cómo leerlas:
- **Primer término:** acumulación de energía en cada fase, ponderada por la fracción de volumen que ocupa: ε el fluido y (1−ε) el sólido.
- **Término convectivo** (solo en el fluido): el fluido transporta energía. El sólido no se mueve, así que no lo tiene.
- **Término difusivo:** conducción dentro de cada fase, con conductividad efectiva. El paper no las define explícitamente. Lo habitual es λ_eff,f = ε·λ_f (más dispersión térmica) y λ_eff,s = (1−ε)·λ_s, o modelos más finos como Zehner–Schlünder.
- **Término de intercambio** h_i·a·(T_s − T_f): es el **acoplamiento**. Lo que pierde una fase lo gana la otra, con signo opuesto en cada ecuación.

**Área específica (interfacial) para esferas:**
$$a=\frac{A_{partículas}}{V_{lecho}}=\frac{6(1-\varepsilon)}{d_p}\quad[\text{m}^{-1}]$$

**Coeficiente interfacial (correlación de Wakao–Kaguei):**
$$Nu=\frac{h,d_p}{\lambda_f}=2+1{,}1,Pr^{1/3}Re_p^{0{,}6}\qquad (15<Re_p<8500)$$
$$h_v=h\cdot a=\frac{6(1-\varepsilon)\lambda_f}{d_p^2}\left(2+1{,}1,Pr^{1/3}Re_p^{0{,}6}\right)\quad[\text{W/m}^3\text{K}]$$

**Cómo se modela el desfase (lag) fluido–sólido.** No hay una ecuación especial: el lag **emerge** de tener dos ecuaciones con un h_v finito.
- Si h_v → ∞, T_f → T_s y se vuelve al modelo LTE.
- Cuanto menor es h_v (partículas grandes, _a_ chica) y mayor la capacidad térmica del sólido, más se atrasa T_s.

**Criterio para decidir si hace falta LTNE.** Se calcula el número de unidades de transferencia:
$$NTU=\frac{h_v,L}{\dot m,c_{p,f}/A_{sección}}$$
- Con NTU del orden de 1 a 10, el fluido avanza más rápido de lo que intercambia calor, así que hace falta LTNE. El paper reporta NTU ≈ 2,15.
- Con NTU de cientos o miles, fluido y sólido están en equilibrio y alcanza con LTE (una sola ecuación).
- Complemento: el número de Biot de la partícula, Bi = h(d_p/6)/λ_s. Si Bi < 0,1, el grano es isotérmico por dentro y no hace falta resolver su interior.

### 2.4 Condiciones iniciales y de borde
![[Parametric Optimization of Sensible Thermocline Packed Bed Thermal Energy Storage Systems - A Computation Fluid Dynamics Study-1793775993456.webp]]*Cilindro con condiciones de entrada y salida (caudal, temperatura, presión) arriba y abajo, condición de pared lateral, eje de simetría en r = 0 e indicación de las condiciones iniciales.*

|Frontera|Ecuación|Significado|
|---|---|---|
|Inicial (t = 0)|T_f = T_s = T_0 = 20 °C; u = v = 0|Tanque frío y quieto.|
|Entrada (arriba, z = 0)|T_f = T_in = 390 °C; ṁ = Q_in|Caudal y temperatura impuestos (Dirichlet).|
|Salida (abajo, z = h)|p = p_0 (atmosférica); ∂T_f/∂z = ∂T_s/∂z = 0|Presión fija y "salida libre": gradiente nulo (Neumann).|
|Pared lateral|−λ_f ∂T_f/∂r = h(T_f^w − T_ext); λ_s ∂T_s/∂r = h(T_s^w − T_ext); u = 0|No deslizamiento y pérdidas convectivas al ambiente (Robin).|
|Eje (r = 0)|∂u/∂r = ∂T_s/∂r = ∂T_f/∂r = 0|Simetría axial: se modela medio corte r-z.|

**Indicadores de desempeño.**
Espesor de termoclina (adimensional):  
$$\delta_{th}=\frac{H(T_H-0{,}2\Delta T)-H(T_C+0{,}2\Delta T)}{H}$$
Energías:  
$$E_{st}(t)=(1-\varepsilon)\rho_s C_{p,s}\int_V (T_s-T_0),dV;\quad E_{in}(t)=\dot m,C_{p,f},\Delta T,t;\quad E_{max}=(1-\varepsilon)\rho_s C_{p,s}V,\Delta T$$

Eficiencias:  
$$\eta_{ch}=E_{st}/E_{max};\qquad \eta_{st}=E_{st}/E_{in}$$
![[Parametric Optimization of Sensible Thermocline Packed Bed Thermal Energy Storage Systems - A Computation Fluid Dynamics Study-1793776098782.webp]]*Dos tanques: en carga el fluido caliente entra arriba y la termoclina (franja amarilla) baja; en descarga el fluido frío entra abajo y la termoclina sube.*

### 2.5 Implementación numérica 
- **COMSOL 6.1**, con tres piezas:
    - Interfaz _Free and Porous Media Flow_ (fp), con permeabilidad tipo Ergun.
    - Interfaz _Heat Transfer in Solids and Fluids_ (ht), con LTNE.
    - Acople _Nonisothermal Flow_.
- **Malla:** independencia verificada con 27 k, 51 k y 74 k elementos. Eligieron 51.276 elementos, con variación menor al 1 %. Usaron capas de contorno refinadas junto a la pared.
- **Tiempo:** BDF adaptativo, tolerancia de residuo 10⁻³, unas 350 iteraciones hasta converger.
![[Parametric Optimization of Sensible Thermocline Packed Bed Thermal Energy Storage Systems - A Computation Fluid Dynamics Study-1793776158791.webp|317]]*Malla 2D con zoom a la zona de pared, donde se ven los elementos refinados de capa límite.*
![[Parametric Optimization of Sensible Thermocline Packed Bed Thermal Energy Storage Systems - A Computation Fluid Dynamics Study-1793776176049.webp|378]]*Flujo de trabajo en COMSOL: parámetros → geometría 2D axisimétrica → materiales → físicas → condiciones de contorno → malla → solver → cálculo y post-proceso → convergencia. Sirve como checklist para tu propio modelo.*
## 3. Parámetros técnicos y trade-offs
### 3.1 Datos del caso

|Ítem|Valor|
|---|---|
|Tanque|Cilindro vertical de acero, 9,17 m × Ø 4,72 m, pared de 15 mm|
|Aislación|Lana de roca de 0,2 m; pérdidas menores al 0,2 % de la potencia|
|Volumen interior|≈ 160 m³|
|Medio|Esferas de basalto, d_p = 0,2 m nominal (barrido de 5 a 20 cm)|
|ρ_s / C_ps / λ_s|3000 kg/m³ / 1230 J/kg·K / 2,3 W/m·K|
|Porosidad|0,49 nominal (barrido de 0,35 a 0,55)|
|Masa de sólido (estimada)|≈ (1−0,49)·160·3000 ≈ 245 t|
|HTF|Aceite térmico: ρ = 897 kg/m³, C_p = 1630 J/kg·K, λ = 0,108 W/m·K, ν = 2,56 mm²/s|
|Caudal|8 a 15 kg/s (Re_p ≈ 36 y 68)|
|T_in / T_0 / ΔT|390 °C / 20 °C / 370 K|
|Velocidad|~0,017 m/s en los plenos; ~10⁻⁴ m/s dentro del lecho|
|Resultado nominal|η_ch = 92,3 % a 10 h; E_st ≈ 103 GJ|

Chequeo propio de consistencia: E_max ≈ 245.000 × 1230 × 370 ≈ 111 GJ, y 103/111 ≈ 92 %. Los números cierran.

**Caso de validación (Mawire y McPherson):**
- Tanque de 0,3 m × Ø 0,29 m con guijarros de 5 cm, ε = 0,49.
- Caudal de 0,0015 kg/s de aceite.
- Temperaturas medidas con termocuplas tipo K a cinco alturas (niveles A a I).
- Error medio del 3,62 %. El peor caso es el nivel E en la primera hora, con 10,8 %.
### 3.2 Efecto de la granulometría (d_p)

|Magnitud|Si d_p aumenta|
|---|---|
|Permeabilidad κ|↑ ∝ d_p², por lo que ΔP ↓ fuertemente|
|Área específica a = 6(1−ε)/d_p|↓ ∝ 1/d_p|
|h_v = h·a|↓ aproximadamente ∝ 1/d_p^1,4 a 1/d_p²|
|Desfase T_f − T_s|↑ (≈ 34 °C con d_p = 20 cm)|
|η_ch final (10 h)|↓ de 99 % (5 cm) a 83 % (20 cm)|
|Comportamiento temprano|Al principio T sube más rápido con granos grandes porque el fluido penetra más fácil, pero al final el sólido queda más frío|

**Trade-off:** grano chico da muy buena transferencia pero alta pérdida de carga; grano grande da poca pérdida de carga pero carga lenta e incompleta.
### 3.3 Efecto de la porosidad (ε)

|Magnitud|Si ε aumenta de 0,35 a 0,55|
|---|---|
|Masa y capacidad térmica del lecho|↓ (menos sólido)|
|Permeabilidad|↑ mucho (∝ ε³)|
|Velocidad del frente térmico|↑, carga más rápida|
|Desfase máximo fluido–sólido|↓ de ≈ 40 °C a ≈ 30 °C|
|η_ch|↑ ≈ 8 %|

### 3.4 Termoclina y pérdidas
- El frente térmico baja en el sentido del flujo, de arriba hacia abajo en la carga.
- Más caudal acelera la carga pero **engrosa la termoclina**, es decir, empeora la estratificación.
- La distribución radial es uniforme, con una capa límite fría junto a la pared por las pérdidas al ambiente.
- La velocidad dentro del lecho es baja y uniforme: el lecho actúa como "distribuidor" de flujo.
- A esta escala las pérdidas por pared son despreciables (menos del 0,2 %), porque la relación superficie/volumen del tanque es muy baja.
![[Parametric Optimization of Sensible Thermocline Packed Bed Thermal Energy Storage Systems - A Computation Fluid Dynamics Study-1793776266481.webp]]*Campo de velocidades: alta en los plenos (rojo) y baja y uniforme en el lecho (verde), con flechas descendentes.*
## 4. Transferencia al proyecto (pila de arena, PID UTN)
Lo que sí se transfiere: las ecuaciones de hidrodinámica porosa (Ergun) y el concepto de termoclina, ambos clave si la **descarga** se hace con aire que atraviesa la arena. También se transfiere el método: flujo de trabajo en COMSOL, estudio de malla y validación contra experimento.
### 4.1 Qué ecuaciones cargar en COMSOL / ANSYS
**Propiedades de base para arena de cuarzo seca** (valores típicos de literatura, a confirmar con la arena que consigan):
- ρ_s ≈ 2600–2650 kg/m³.
- c_s ≈ 800 J/kg·K a temperatura ambiente, subiendo a ~1000–1100 hacia 500 °C. Conviene cargar c(T).
- ε ≈ 0,35–0,45; densidad aparente ≈ 1500–1700 kg/m³.
- k_eff de lecho seco ≈ 0,25–0,35 W/m·K a temperatura ambiente. Es muy baja: del orden de un aislante pobre.

**Capacidad del prototipo** (supuestos: 40×40×40 cm llenos de arena, aislación por fuera, ε = 0,4):
- Masa ≈ 0,064 m³ × 1590 kg/m³ ≈ 100 kg.
- Con un ΔT útil de 300 → 60 °C: E ≈ 100 × 830 × 240 ≈ 20 MJ ≈ **5,5 kWh**.
- Como referencia, la resistencia actual de la cama (174 W por m²) consume 2,1 kWh en 12 h de noche.

Hay tres modelos, de menor a mayor complejidad:

**Modelo A: carga por resistencias embebidas, sin flujo.** Es el que corresponde a tu ingeniería básica.
- **Física:** _Heat Transfer in Porous Media_ con equilibrio local (LTE), o directamente _Heat Transfer in Solids_ con propiedades efectivas:
$$(\rho c)_{eff}\frac{\partial T}{\partial t}=\nabla\cdot(k_{eff}(T)\nabla T)+Q_{res}(t)$$
con (ρc)_eff = (1−ε)ρ_s c_s + ε ρ_a c_a ≈ (1−ε)ρ_s c_s.

- **Resistencias:** como _Line Heat Source_ (W/m) o como dominio con fuente volumétrica. Q(t) es el perfil diario del panel fotovoltaico menos el consumo de la cama.
- **k_eff(T):** incluí la radiación, que el paper desprecia pero a 400–500 °C en arena pesa. Una aproximación es k_rad ≈ 4·σ·F·d_p·T³; para d_p = 1 mm a 500 °C da ≈ 0,08–0,10 W/m·K, es decir un 25–30 % extra sobre k_eff. Se puede usar el modelo de Zehner–Bauer–Schlünder, que COMSOL tiene como opción de conductividad efectiva.
- **Contorno:** la aislación modelada como dominio sólido con k(T) y, por fuera, convección natural más radiación al invernadero (h ≈ 5–10 W/m²K, emisividad de la chapa).
- **ANSYS:** _Transient Thermal_ en Mechanical alcanza para este caso.

**Modelo B: descarga con aire que atraviesa la arena.** Este es el caso que más se parece al paper.
- **Físicas:** _Darcy's Law_ + _Heat Transfer in Porous Media_ + _Nonisothermal Flow_. Darcy alcanza: a Re_p < 1 el término de Forchheimer es despreciable. Brinkman solo si modelás plenos vacíos.
- **¿LTNE o LTE?** Calculá NTU. Con arena de 0,5 mm, a ≈ 7200 m⁻¹ y h_v ≈ 10⁵–10⁶ W/m³K da NTU de 10³ a 10⁴: **equilibrio térmico total, alcanza con LTE**. El modelo de dos ecuaciones del paper solo se justifica para granos de centímetros.
- **Wakao no aplica:** con aire a ~0,02 m/s, Re_p queda entre 0,5 y 2, fuera de su rango (15–8500). Si igual querés probar LTNE, usá Nu ≈ 2 como cota, y documentá que es una cota.
- **ANSYS Fluent:** _porous zone_ con _thermal equilibrium_ (o _non-equilibrium_ si querés comparar), resistencias viscosa (1/κ) e inercial (C_2) calculadas con Ergun.

**Modelo C: descarga por tubos embebidos** (aire o agua dentro de serpentinas, sin contacto con la arena).
- COMSOL tiene _Non-Isothermal Pipe Flow_ (tubería 1D) acoplado a un dominio 3D de arena (modelo A) mediante _Wall Heat Transfer_. Es liviano computacionalmente.
- Es la arquitectura de Polar Night Energy: el aire circula por tubos y la arena nunca toca el fluido.
### 4.2 Criterio de granulometría y fluidez
Apliqué Ergun al prototipo con estos supuestos:
- Descarga de 174 W, aire de 25 a 80 °C → ṁ ≈ 3·10⁻³ kg/s.
- Sección de 0,16 m² → velocidad superficial U ≈ 0,02 m/s.
- Aire a ~100 °C: μ ≈ 2,2·10⁻⁵ Pa·s, ρ ≈ 0,95 kg/m³.
- ε = 0,4 y un recorrido de 0,4 m.

|d_p|ΔP/L|ΔP en 0,4 m|Re_p|Comentario|
|---|---|---|---|---|
|0,2 mm (arena fina)|≈ 9,3 kPa/m|≈ 3,7 kPa|0,2|Exige soplador de alta presión. Riesgo de polvo y arrastre.|
|0,5 mm (arena media)|≈ 1,5 kPa/m|≈ 0,6 kPa|0,4|Viable con un soplador centrífugo chico.|
|1 mm (arena gruesa)|≈ 0,38 kPa/m|≈ 0,15 kPa|0,9|Cómodo.|
|2 mm (gravilla fina)|≈ 0,1 kPa/m|≈ 0,04 kPa|1,7|Muy cómodo. Mayor riesgo de canalización por la pared en un tanque chico.|

**Recomendación:** arena **lavada y tamizada entre 0,5 y 2 mm** si la descarga pasa aire a través del lecho. Conviene que la distribución sea estrecha: los finos tapan los poros y bajan ε.

A diferencia del paper, con arena la transferencia sólido–fluido **nunca es el cuello de botella**, porque el área específica es enorme. Engrosar el grano dentro de ese rango solo baja la pérdida de carga sin costo térmico.

Dos advertencias:
1. **La mezcla arena–arcilla** prevista en tu Fase 3 reduce la permeabilidad en órdenes de magnitud y es **incompatible con el paso de aire a través del lecho**. Solo tiene sentido con los modelos A y C.
2. **La relación D/d_p** debería superar 20–30 para que el lecho se comporte como medio continuo. Con 40 cm y granos de 2 mm da 200: se cumple. El efecto pared del paper no te preocupa.

Si la descarga es por tubos embebidos (modelo C), la granulometría deja de importar por la presión. Ahí conviene arena más fina y bien compactada, porque mejora levemente k_eff y elimina huecos junto a los tubos.
### 4.3 Estrategia de extracción de calor (baja conductividad de la arena)
**El problema cuantificado.** La difusividad de la arena es α = k/(ρc) ≈ 0,3/(1590 × 830) ≈ 2,3·10⁻⁷ m²/s. El tiempo característico de conducción es t ≈ L²/α:

|Distancia que tiene que recorrer el calor|Tiempo característico|
|---|---|
|20 cm (del centro al borde del cubo)|≈ 48 h|
|5 cm|≈ 3 h|
|2,5 cm|≈ 45 min|

**Consecuencias para el diseño:**
1. **Separación de elementos.** Tanto las resistencias de carga como los tubos de extracción deben ir separados unos 10 cm, para que el calor recorra 5 cm o menos. Con una sola resistencia central, en un día de sol solo se calienta un "cilindro" de pocos centímetros alrededor de ella, y su vaina puede sobrecalentarse. Este es un criterio de diseño directo para tu ingeniería de detalle.
2. **Usar el principio del paper: convección forzada a través del lecho.** Hacer pasar aire por la arena convierte la arena en un intercambiador con área gigante y evita el cuello de botella de k_eff. Es la recomendación más fuerte que sale de este paper.
    - **Sentidos de flujo:** cargar de arriba hacia abajo con aire caliente, si se carga por aire, y descargar de abajo hacia arriba. Así se preserva la termoclina (Figura 5) y el aire sale siempre a la máxima temperatura disponible.
    - **Caudal bajo** mejora la estratificación, según el paper.
3. **Aletas o tubos aleteados** si se opta por intercambiador embebido (modelo C). También ayuda un tubo de mayor diámetro o un haz de tubos chicos.
4. **Regulación de temperatura hacia la cama.** La arena puede estar a 300 °C, pero la resistencia actual de la cama trabaja con un máximo de 60 °C y el sustrato necesita entre 20 y 30 °C. La extracción debe incluir **mezcla con bypass** de aire frío, o un circuito intermedio de agua con válvula mezcladora. El control actual por TRIAC se reemplaza por control de caudal o de mezcla, ya sea con PWM del ventilador o con una válvula proporcional. Esto conecta con el subsistema electrónico.
5. **Pérdidas: el efecto de escala va en tu contra.** La relación superficie/volumen de un cubo de 0,4 m es unas 14 veces mayor que la del tanque del paper. Una estimación gruesa con 20 cm de lana de roca y arena a 300 °C da pérdidas de unos 150–200 W (k ≈ 0,065 W/m·K y área media ≈ 1,9 m²), del orden de la potencia útil de descarga. La constante de autodescarga sale τ ≈ m·c·R_th ≈ 1,5 días.
    - Consecuencia: el prototipo sirve para ciclos diarios, no para almacenar semanas. Polar Night consigue meses gracias a la escala.
    - Este número conviene calcularlo bien en la ingeniería básica, porque condiciona la temperatura máxima de diseño y el espesor de aislación. Ojo: la lana de vidrio común no soporta 500 °C, y el poliuretano tampoco. Para la capa caliente hace falta lana de roca, manta cerámica o silicato de calcio.
6. **Validación instrumental.** Copiá la estrategia del paper: termocuplas K en varias alturas (y en tu caso también radios), comparadas contra la simulación. Es exactamente lo que ya planeás en tus Fases 5 y 6.