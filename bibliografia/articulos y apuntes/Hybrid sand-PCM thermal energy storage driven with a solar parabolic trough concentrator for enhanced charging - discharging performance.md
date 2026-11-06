---
Titulo esp.: Almacenamiento de energía térmica híbrido de arena y PCM impulsado con un concentrador solar de canal parabólico para mejorar el rendimiento de carga y descarga
Año: 2026
URL:
Padre: "[[CUDAR - Desarrollo de Pila de Arena]]"
Importancia:
  - C
---
El artículo presenta un estudio experimental sobre un sistema híbrido de almacenamiento de energía térmica (TES) que combina arena y material de cambio de fase (PCM). El objetivo es mejorar el rendimiento de carga y descarga en aplicaciones solares de temperatura media.
### Objetivo y Contexto
El trabajo aborda una limitación común en los sistemas de almacenamiento térmico: los materiales de calor sensible (como la arena) cargan rápido pero retienen poco, mientras que los PCM almacenan mucha energía pero cargan y descargan lentamente. Para resolverlo, los autores proponen un sistema **térmicamente desacoplado** de doble medio (arena + PCM) integrado con un concentrador solar de canal parabólico de seguimiento dual. El fin es lograr un almacenamiento secuencial: primero calor sensible rápido y luego calor latente duradero, para aplicaciones como precalentamiento industrial, calefacción y agua caliente sanitaria.

> [!NOTE] **PCM** 
> - un PCM significa Phase Change Material, o material de cambio de fase. Es un material que almacena energía térmica aprovechando el cambio de fase 
> 	- Por ejemplo: el hielo al derretirse absorbe mucho calor sin subir su T, el agua al congelarse libera ese calor sin bajar de 0°
> - En este articulo el PCM que se usa es parafina, que cambia de fase en el rango de trabajo aproximado de 30-60°C
> - Un PCM almacena mucha energía en poco volumen, mantiene la T mas estable durante la carga y descarga, y libera calor durante bastante tiempo al solidificarse 
> 	- Desventajas: tiene baja conductividad térmica, necesita aletas, serpentines o particiones metálicas para mejorar el intercambio de calor
> - Un PCM es una reserva térmica lenta pero duradera que guarda calor latente
### Metodología
El sistema se diseñó para que el fluido calentado por el sol transfiera energía a través de una **bobina de cobre** inmersa en lecho de arena (calentamiento sensible rápido). Luego, el calor pasa por conducción a través de una **partición metálica** hacia una cámara con PCM de parafina, donde se almacena como calor latente.

Los autores verificaron la idoneidad y estabilidad de los materiales con técnicas como **XRD, SEM-EDS, Raman, TGA, DSC** y análisis de propiedades térmicas con KD 2 Pro. Además, realizaron experimentos comparativos en tres configuraciones bajo condiciones idénticas: **solo arena**, **solo PCM** y **sistema integrado arena-PCM**.

> [!NOTE] Integración del PCM en la batería de arena 
> Se diseña un **sistema hibrido y desacoplado térmicamente** con dos medios separados:
> 	- concentrador solar de canal parabólico: calienta un fluido térmico 
> 	- serpentín de cobre dentro de la arena: el fluido caliente circula por una bobina de cobre inmersa en un lecho de arena. La arena se calienta rápido y se produce el almacenamiento por calor sensible 
> 	- partición metálica: la cámara de arena esta separada de la cámara de PCM por una pared metálica 
> 	- Cámara de PCM (parafina): el calor pasa por conducción desde la arena, atraviesa la partición metálica y llega al PCM que se funde y almacena calor latente 

> [!NOTE] Como funciona la carga y la descarga? 
> **Carga**:
> 	- el sol calienta el fluido, el fluido calienta la arena, la arena transmite calor al PCM el cual se funde y guarda energía latente
> **Descarga**:
> 	- el fluido frio circula por el serpentín y extrae calor de la arena 
> 	- la arena comienza a enfriarse y entonces el PCM se solidifica y libera calor latente 
> 	- Ese calor va a la arena y ayuda a mantener la T de salida mas estable durante mas tiempo
> Creo que el sistema es algo asi 
> ![[Hybrid sand-PCM thermal energy storage driven with a solar parabolic trough concentrator for enhanced charging - discharging performance-1791864858949.webp]]
### Resultados Clave
Los hallazgos principales se resumen en la siguiente tabla:

| Configuración | Capacidad de almacenamiento | Eficiencia de carga | Eficiencia de descarga | Duración de descarga | Observaciones |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **Solo arena** | No especificada | No especificada | No especificada | Limitada | Carga rápido (25.7 °C a 53.7 °C en 8 h) pero retención pobre |
| **Solo PCM** | No especificada | Menor | No especificada | Extendida | Liberación térmica prolongada pero carga ineficiente |
| **Integrado (SP)** | **1347.1 kJ/kg** | **95.61 %** | **96.79 %** | **135 min** (en rango 30–60 °C) | Efectividad del 31.46 %; integra las ventajas de ambos medios |

El sistema híbrido logró la **mayor capacidad de almacenamiento** y eficiencias sobresalientes, manteniendo una operación estable en el rango de 30–60 °C durante más de dos horas.
### Conclusiones
Los resultados demuestran que la configuración propuesta **supera a los sistemas de un solo medio y a los lechos empaquetados convencionales**, ofreciendo una solución robusta y escalable para aplicaciones térmicas solares de temperatura media. La combinación de arena y PCM permite un almacenamiento más eficiente y una descarga más estable, lo que podría facilitar la integración de la energía solar térmica en sectores con demanda continua de calor.


